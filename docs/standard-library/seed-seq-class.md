---
title: Класс seed_seq
ms.date: 11/04/2016
f1_keywords:
- random/std::seed_seq
- random/std::seed_seq::result_type
- random/std::seed_seq::generate
- random/std::seed_seq::size
- random/std::seed_seq::param
helpviewer_keywords:
- std::seed_seq [C++]
- std::seed_seq [C++], result_type
- std::seed_seq [C++], generate
- std::seed_seq [C++], size
- std::seed_seq [C++], param
ms.assetid: cba114f7-9ac6-4f2f-b773-9c84805401d6
ms.openlocfilehash: 5309042e9f26875e0cf5c2024cc74910fef21148
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295725"
---
# <a name="seedseq-class"></a>Класс seed_seq

Хранит вектор беззнаковых целых значений, которые можно использовать как начальное значения для механизма получения случайных чисел.

## <a name="syntax"></a>Синтаксис

```cpp
class seed_seq
   {
public:
   // types
   typedef unsigned int result_type;

   // constructors
   seed_seq();
   template <class T>
      seed_seq(initializer_list<T> initlist);
   template <class InputIterator>
      seed_seq(InputIterator begin, InputIterator end);

   // generating functions
   template <class RandomAccessIterator>
      void generate(RandomAccessIterator begin, RandomAccessIterator end);

   // property functions
   size_t size() const;
   template <class OutputIterator>
      void param(OutputIterator dest) const;

   // no copy functions
   seed_seq(const seed_seq&) = delete;
   void operator=(const seed_seq&) = delete;
   };
```

## <a name="types"></a>Типы

```cpp
typedef unsigned int result_type;
```

Тип элементов начальной последовательности. 32-разрядный целочисленный тип без знака.

## <a name="constructors"></a>Конструкторы

```cpp
seed_seq();
```

Конструктор по умолчанию, инициализируется с пустой внутренней последовательностью.

```cpp
template<class T>
seed_seq(initializer_list<T> initlist);
```

Использует `initlist` для установки внутренней последовательности.
Типом `T` должен быть целочисленный тип.

```cpp
template<class InputIterator>
seed_seq(InputIterator begin, InputIterator end);
```

Инициализирует внутреннюю последовательность, используя все элементы в заданном диапазоне итератора.
Типом `iterator_traits<InputIterator>::value_type` должен быть целочисленный тип.

## <a name="members"></a>Участники

### <a name="generating-functions"></a>Генерирующие функции

```cpp
template<class RandomAccessIterator>
void generate(RandomAccessIterator begin,
          RandomAccessIterator end);
```

Заполняет элементы предоставленной последовательности, используя внутренний алгоритм. На этот алгоритм влияет внутренняя последовательность, с помощью которой инициализируется `seed_seq`.
Ничего не делает, если `begin == end`.

### <a name="property-functions"></a>Функции свойств

```cpp
size_t size() const;
```

Возвращает количество элементов в контейнере `seed_seq`.

```cpp
template<class OutputIterator>
void param(OutputIterator dest) const;
```

Копирует внутреннюю последовательность в выходной итератор `dest`.

## <a name="example"></a>Пример

В следующем примере кода используются три конструктора, а при назначении массиву из полученных экземпляров `seed_seq` создаются выходные данные. Пример использования `seed_seq` с генератором случайных чисел см. в разделе [\<random>](../standard-library/random.md).

```cpp
#include <iostream>
#include <random>
#include <string>
#include <array>

using namespace std;

void test(const seed_seq& sseq) {
    cout << endl << "seed_seq::size(): " << sseq.size() << endl;

    cout << "seed_seq::param(): ";
    ostream_iterator<unsigned int> out(cout, " ");
    sseq.param(out);
    cout << endl;

    cout << "Generating a sequence of 5 elements into an array: " << endl;
    array<unsigned int, 5> seq;
    sseq.generate(seq.begin(), seq.end());
    for (unsigned x : seq) { cout << x << endl; }
}

int main()
{
    seed_seq seed1;
    test(seed1);

    seed_seq seed2 = { 1701, 1729, 1791 };
    test(seed2);

    string sstr = "A B C D"; // seed string
    seed_seq seed3(sstr.begin(), sstr.end());
    test(seed3);
}
```

```Output
seed_seq::size(): 0
seed_seq::param():
Generating a sequence of 5 elements into an array:
505382999
163489202
3932644188
763126080
73937346

seed_seq::size(): 3
seed_seq::param(): 1701 1729 1791
Generating a sequence of 5 elements into an array:
1730669648
1954224479
2809786021
1172893117
2393473414

seed_seq::size(): 7
seed_seq::param(): 65 32 66 32 67 32 68
Generating a sequence of 5 elements into an array:
3139879222
3775111734
1084804564
2485037668
1985355432
```

## <a name="remarks"></a>Примечания

Функции-члены этого класса не вызывают исключений.

## <a name="requirements"></a>Требования

**Заголовок:** \<random>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[\<random>](../standard-library/random.md)<br/>
