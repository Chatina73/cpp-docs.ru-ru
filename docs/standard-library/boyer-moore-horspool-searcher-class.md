---
description: 'Дополнительные сведения о: boyer_moore_horspool_searcher классе'
title: класс boyer_moore_horspool_searcher
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_horspool_searcher
helpviewer_keywords:
- std::boyer_moore_horspool_searcher [C++]
ms.openlocfilehash: 727af034dbb20bd1a0d09ae7de8f88da16a6ba36
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325429"
---
# <a name="boyer_moore_horspool_searcher-class"></a>класс boyer_moore_horspool_searcher

`boyer_moore_horspool_searcher`Класс является типом объекта функции, который использует алгоритм Бойера-Мура-хорспул для поиска последовательности, указанной в конструкторе объекта. Поиск выполняется в другой последовательности, предоставленной оператору вызова функции объекта. Этот класс передается в качестве параметра в одну из перегрузок [std:: Search](algorithm-functions.md#search).

## <a name="syntax"></a>Синтаксис

```cpp
template <
    class RandomAccessIterator,
    class Hash = hash<typename iterator_traits<RandomAccessIterator>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_horspool_searcher
{
    boyer_moore_horspool_searcher(
        RandomAccessIterator pat_first,
        RandomAccessIterator pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>Члены

| Член | Описание |
| - | - |
| **Конструктор** | |
| [boyer_moore_horspool_searcher](#boyer-moore-horspool-searcher-constructor) | Конструирует экземпляр службы поиска. |
| **Операторы** | |
| [оператор ()](#operator-call) | Вызывает операцию в последовательности. |

## <a name="boyer_moore_horspool_searcher-constructor"></a><a name="boyer-moore-horspool-searcher-constructor"></a> Конструктор boyer_moore_horspool_searcher

Конструирует `boyer_moore_horspool_searcher` объект функции, используя последовательность для поиска, объект хэш-функции и предикат равенства.

```cpp
boyer_moore_horspool_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>Параметры

*pat_first*\
Начальный элемент последовательности для поиска.

*pat_last*\
Конец последовательности для поиска.

*HF*\
Вызываемый объект, используемый для хэширования элементов последовательности.

*Возможен*\
Необязательный предикат сравнения равенства для элементов последовательности. Если тип сравнения на равенство не указан, по умолчанию используется значение `std::equal_to` .

### <a name="remarks"></a>Комментарии

Создает исключение, созданное конструктором копий типов *бинарипредикате*, *hash* или *Рандомакцесситератор* , или оператор Call *бинарипредикате* или *hash*.

Этот класс впервые появились в C++ 17.

## <a name="operator"></a><a name="operator-call"></a> оператор ()

Оператор Call объекта Function. Ищет в последовательности аргументов `[first, last)` последовательность, указанную в конструкторе.

```cpp
template <class ForwardIterator2>   // C++17
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>Параметры

*началь*\
Начальный элемент последовательности, в которой необходимо выполнить поиск.

*Последняя*\
Конец последовательности, в которой необходимо выполнить поиск.

### <a name="remarks"></a>Комментарии

Если шаблон поиска `[pat_first, pat_last)` пуст, возвращает значение `make_pair(first, first)` . Если шаблон поиска не найден, возвращает `make_pair(last, last)` . В противном случае возвращает пару итераторов в начало и конец последовательности в таком же порядке, что и в соответствии с допустимым `[first, last)` `[pat_first, pat_last)` предикатом. 

Этот класс впервые появились в C++ 17.

## <a name="see-also"></a>См. также раздел

[\<functional>](functional.md)\
[функции алгоритма](algorithm-functions.md)\
[класс boyer_moore_searcher](boyer-moore-searcher-class.md)\
[std:: Search](algorithm-functions.md#search)
