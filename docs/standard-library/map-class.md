---
title: Класс map
description: Справочник по API для класса библиотеки стандартных шаблонов C++ (STL) `map` , который используется для хранения и извлечения данных из коллекции, в которой каждый элемент является парой, имеющей как значение данных, так и ключ сортировки.
ms.date: 9/10/2020
f1_keywords:
- map/std::map
- map/std::map::allocator_type
- map/std::map::const_iterator
- map/std::map::const_pointer
- map/std::map::const_reference
- map/std::map::const_reverse_iterator
- map/std::map::difference_type
- map/std::map::iterator
- map/std::map::key_compare
- map/std::map::key_type
- map/std::map::mapped_type
- map/std::map::pointer
- map/std::map::reference
- map/std::map::reverse_iterator
- map/std::map::size_type
- map/std::map::value_type
- map/std::map::at
- map/std::map::begin
- map/std::map::cbegin
- map/std::map::cend
- map/std::map::clear
- map/std::map::count
- map/std::map::contains
- map/std::map::crbegin
- map/std::map::crend
- map/std::map::emplace
- map/std::map::emplace_hint
- map/std::map::empty
- map/std::map::end
- map/std::map::equal_range
- map/std::map::erase
- map/std::map::find
- map/std::map::get_allocator
- map/std::map::insert
- map/std::map::key_comp
- map/std::map::lower_bound
- map/std::map::max_size
- map/std::map::rbegin
- map/std::map::rend
- map/std::map::size
- map/std::map::swap
- map/std::map::upper_bound
- map/std::map::value_comp
helpviewer_keywords:
- std::map [C++]
- std::map [C++], allocator_type
- std::map [C++], const_iterator
- std::map [C++], const_pointer
- std::map [C++], const_reference
- std::map [C++], const_reverse_iterator
- std::map [C++], difference_type
- std::map [C++], iterator
- std::map [C++], key_compare
- std::map [C++], key_type
- std::map [C++], mapped_type
- std::map [C++], pointer
- std::map [C++], reference
- std::map [C++], reverse_iterator
- std::map [C++], size_type
- std::map [C++], value_type
- std::map [C++], at
- std::map [C++], begin
- std::map [C++], cbegin
- std::map [C++], cend
- std::map [C++], clear
- std::map [C++], count
- std::map [C++], contains
- std::map [C++], crbegin
- std::map [C++], crend
- std::map [C++], emplace
- std::map [C++], emplace_hint
- std::map [C++], empty
- std::map [C++], end
- std::map [C++], equal_range
- std::map [C++], erase
- std::map [C++], find
- std::map [C++], get_allocator
- std::map [C++], insert
- std::map [C++], key_comp
- std::map [C++], lower_bound
- std::map [C++], max_size
- std::map [C++], rbegin
- std::map [C++], rend
- std::map [C++], size
- std::map [C++], swap
- std::map [C++], upper_bound
- std::map [C++], value_comp
ms.openlocfilehash: 7d8e4c674e525f1b67f000403791c7ccdb2f9673
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099746"
---
# <a name="map-class"></a>Класс `map`

Используется для хранения и извлечения данных из коллекции, в которой каждый элемент является парой, обладающей одновременно значением данных и ключом сортировки. Значение ключа уникально и применяется для автоматической сортировки данных.

Значение элемента в сопоставлении можно изменить напрямую. Значение ключа является константой и не может быть изменено. Вместо этого значения ключей, связанные со старыми элементами, необходимо удалить и вставить новые значения ключей для новых элементов.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Key,
    class Type,
    class Traits = less<Key>,
    class Allocator=allocator<pair <const Key, Type>>>
class map;
```

### <a name="parameters"></a>Параметры

*`Key`*\
Тип данных ключа, который должен храниться в `map` .

*`Type`*\
Тип данных элемента для сохранения в `map`.

*`Traits`*\
Тип, предоставляющий объект функции, который может сравнить два значения элементов как ключи сортировки для определения их относительного порядка в `map` . Этот аргумент является необязательным, и в качестве значения по умолчанию используется бинарный предикат `less<Key>`.

В C++ 14 можно включить разнородный Уточняющий запрос, указав `std::less<>` предикат, не имеющий параметров типа. Дополнительные сведения см. [в разделе разнородный Уточняющий запрос в ассоциативных контейнерах](../standard-library/stl-containers.md#sequence_containers) .

*`Allocator`*\
Тип, представляющий сохраненный объект распределителя, который инкапсулирует сведения о выделении и освобождении памяти для сопоставления. Этот аргумент является необязательным, и значением по умолчанию является `allocator<pair<const Key, Type> >`.

## <a name="remarks"></a>Комментарии

Класс map в стандартной библиотеке С++ — это:

- Контейнер переменного размера, фактически извлекающий значения элементов на основе связанных значений ключей.

- Реверсивный, поскольку он предоставляет двунаправленные итераторы для получения доступа к его элементам.

- Сортируется, поскольку его элементы упорядочены по значениям ключей в соответствии с заданной функцией сравнения.

- Является уникальным, поскольку каждый его элемент должен обладать уникальным ключом.

- Является контейнером ассоциативной пары, поскольку его значения данных элементов отличаются от его значений ключей.

- Шаблон класса, поскольку предоставляемые им функциональные возможности являются универсальными и не зависят от типа элемента или ключа. Типы данных, используемые для элементов и ключей, определяются как параметры в шаблоне класса вместе с функцией и распределителем сравнения.

Итератор, предоставляемый классом Map, является двунаправленным итератором, [`insert`](#insert) но [`map`](#map) функции-члены класса и имеют версии, принимающие в качестве параметров шаблона более слабый итератор ввода, чьи функциональные требования меньше, чем гарантированные классом двунаправленных итераторов. Различные концепции итераторов связаны уточнениями функциональности. Каждая концепция итератора обладает собственным набором требований, и совместимые с ней алгоритмы должны быть ограничены этими требованиями. Итератор ввода может быть разыменован для обращения к определенному объекту и инкрементирован следующему итератору в последовательности.

Рекомендуется выбирать тип контейнера на основе типа поиска и вставки, который требуется приложению. Ассоциативные контейнеры оптимизированы для операций поиска, вставки и удаления. Функции-члены, которые явно поддерживают эти операции, выполняются в наихудшем времени, пропорционально логарифму числа элементов в контейнере. Вставка элементов не делает итераторы недействительными, а при удалении элементов недействительными становятся только итераторы, указывающие конкретно на удаленные элементы.

Рекомендуется сделать сопоставление предпочтительным ассоциативным контейнером, где условия, ассоциирующие значения с ключами, удовлетворяют требованиям приложения. Модель для этого типа структуры представляет собой упорядоченный список уникальных ключевых слов, с которыми связаны значения строк, предоставляющие определения. Если слово имеет несколько правильных определений, поэтому ключ не уникален, то multimap будет являться контейнером выбора. Если сохранен обычный список слов, подходящим контейнером будет набор. Если допускается многократное использование слов, допустимым вариантом будет множественный набор.

Таблица упорядочивает элементы, которыми она управляет, путем вызова хранимой функции типа [`key_compare`](#key_compare) . Этот сохраненный объект является функцией сравнения, доступ к которой осуществляется путем вызова [`key_comp`](#key_comp) метода. В общем случае все два заданных элемента сравниваются, чтобы определить, меньше ли один из них или эквивалентен ли он. После сравнения всех элементов создается упорядоченная последовательность неэквивалентных элементов.

> [!NOTE]
> Функция сравнения — это бинарный предикат, который вызывает строгое слабое упорядочение в стандартном математически смысле. Бинарный предикат f (x, y) — это объект функции, имеющий два объекта-аргумента x и y, а также возвращаемое значение **`true`** или **`false`** . Порядок, накладываемый на набор, является строгим слабым порядком, если бинарный предикат является нерефлексивным, антисимметричным и транзитивным, и если эквивалентность является транзитивным, то два объекта x и y определяются как эквивалентные, если используются значения f (x, y) и f (y, x) **`false`** . Если более строгое условие равенства между ключами заменяет условие эквивалентности, порядок становится общим (т. е. все элементы упорядочиваются в соответствии друг с другом) и сопоставленные ключи будут неотличимы друг от друга.
>
> В C++ 14 можно включить разнородный Уточняющий запрос, указав `std::less<>` предикат или `std::greater<>` , не имеющий параметров типа. Дополнительные сведения см. [в разделе разнородный Уточняющий запрос в ассоциативных контейнерах](../standard-library/stl-containers.md#sequence_containers) .

## <a name="members"></a>Члены

### <a name="constructors"></a>Конструкторы

|Имя|Описание|
|-|-|
|[`map`](#map)|Создание списка определенного размера или с элементами, обладающими указанным значением или указанным `allocator`, либо в качестве копии другого сопоставления.|

### <a name="typedefs"></a>Определения типов

|Имя|Описание|
|-|-|
|[`allocator_type`](#allocator_type)|Typedef для класса `allocator` для объекта сопоставления.|
|[`const_iterator`](#const_iterator)|Typedef для двунаправленного итератора, который может читать **`const`** элемент в `map` .|
|[`const_pointer`](#const_pointer)|Typedef для указателя на **`const`** элемент в сопоставлении.|
|[`const_reference`](#const_reference)|Typedef для ссылки на **`const`** элемент, хранящийся в сопоставлении для чтения и выполнения **`const`** операций.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Тип, предоставляющий двунаправленный итератор, который может читать любой **`const`** элемент в `map` .|
|[`difference_type`](#difference_type)|Цельночисленный Typedef со знаком для числа элементов в сопоставлении, в диапазоне между элементами, на которые указывают итераторы.|
|[`iterator`](#iterator)|Typedef для двунаправленного итератора, который может считывать или изменять любой элемент в сопоставлении.|
|[`key_compare`](#key_compare)|Typedef для объекта функции, который может сравнить два ключа сортировки для определения относительного порядка двух элементов в `map`.|
|[`key_type`](#key_type)|Typedef для ключа сортировки, хранящегося в каждом элементе сопоставления.|
|[`mapped_type`](#mapped_type)|Typedef для данных, хранящихся в каждом элементе сопоставления.|
|[`pointer`](#pointer)|Typedef для указателя на **`const`** элемент в сопоставлении.|
|[`reference`](#reference)|Typedef для ссылки на элемент, сохраненный в сопоставлении.|
|[`reverse_iterator`](#reverse_iterator)|Typedef для двунаправленного итератора, который может считывать или изменять элемент в обратном сопоставлении.|
|[`size_type`](#size_type)|Целочисленный Typedef без знака для числа элементов в сопоставлении|
|[`value_type`](#value_type)|Typedef для типа объекта, хранящейся в виде элемента в сопоставлении.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[`at`](#at)|Находит элемент с указанным значением ключа.|
|[`begin`](#begin)|Возвращает итератор, указывающий на первый элемент в `map`.|
|[`cbegin`](#cbegin)|Возвращает константный итератор, указывающий на первый элемент в `map` .|
|[`cend`](#cend)|Возврат итератора const после конца.|
|[`clear`](#clear)|Стирает все элементы в `map`.|
|[`contains`](#contains)<sup>C++ 20</sup>|Проверьте, существует ли элемент с указанным ключом в `map` .|
|[`count`](#count)|Возврат числа элементов в сопоставлении, ключ которого соответствует ключу, заданному в параметре.|
|[`crbegin`](#crbegin)|Возвращает константный итератор, указывающий на первый элемент в обращении `map` .|
|[`crend`](#crend)|Возвращает константный итератор, указывающий на положение после последнего элемента в обращенном операторе `map` .|
|[`emplace`](#emplace)|Вставляет элемент, созданный на месте, в `map` .|
|[`emplace_hint`](#emplace_hint)|Вставляет элемент, созданный на месте `map` , с указанием размещения.|
|[`empty`](#empty)|Возвращает, **`true`** Если объект `map` пуст.|
|[`end`](#end)|Возврат итератора после конца.|
|[`equal_range`](#equal_range)|Возвращает пару итераторов. Первый итератор в паре указывает на первый элемент в `map` с ключом, который больше указанного ключа. Второй итератор в паре указывает на первый элемент в `map` с ключом, который больше или равен данному ключу.|
|[`erase`](#erase)|Удаление элемента или диапазона элементов в сопоставлении с заданных позиций.|
|[`find`](#find)|Возвращает итератор, указывающий на расположение элемента в с `map` ключом, равным указанному ключу.|
|[`get_allocator`](#get_allocator)|Возвращает копию объекта `allocator`, который используется для создания `map`.|
|[`insert`](#insert)|Вставляет элемент или диапазон элементов в `map` в заданной позиции.|
|[`key_comp`](#key_comp)|Возвращает копию объекта сравнения, который использовался для упорядочивания ключей в `map` .|
|[`lower_bound`](#lower_bound)|Возвращает итератор к первому элементу в `map` , имеющему значение ключа, которое больше или равно значению указанного ключа.|
|[`max_size`](#max_size)|Возвращает максимальную длину `map`.|
|[`rbegin`](#rbegin)|Возвращает итератор, указывающий на первый элемент в обратном `map`.|
|[`rend`](#rend)|Возвращает итератор, указывающий на положение после последнего элемента в обращенном операторе `map` .|
|[`size`](#size)|Возвращает количество элементов в контейнере `map`.|
|[`swap`](#swap)|Обмен элементами между двумя сопоставлениями.|
|[`upper_bound`](#upper_bound)|Возвращает итератор к первому элементу в `map` , имеющему значение ключа, которое больше указанного ключа.|
|[`value_comp`](#value_comp)|Извлекает копию объекта сравнения, который используется для упорядочивания значений элементов в `map`.|

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[`operator[]`](#op_at)|Вставка элемента в сопоставление с заданным значением ключа.|
|[`operator=`](#op_eq)|Замена элементов сопоставления копией другого сопоставления.|

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

Тип, представляющий класс распределителя для объекта-сопоставления.

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>Пример

См. пример для [`get_allocator`](#get_allocator) для примера, в котором используется `allocator_type` .

## <a name="at"></a><a name="at"></a> `at`

Поиск элемента с заданным значением ключа.

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Значение ключа, которое необходимо найти.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на значение данных найденного элемента.

### <a name="remarks"></a>Комментарии

Если значение ключа аргумента не найдено, функция создает [ `out_of_range` объект класса класса.](../standard-library/out-of-range-class.md)

### <a name="example"></a>Пример

```cpp
// map_at.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

typedef std::map<char, int> Mymap;
int main()
    {
    Mymap c1;

    c1.insert(Mymap::value_type('a', 1));
    c1.insert(Mymap::value_type('b', 2));
    c1.insert(Mymap::value_type('c', 3));

// find and show elements
    std::cout << "c1.at('a') == " << c1.at('a') << std::endl;
    std::cout << "c1.at('b') == " << c1.at('b') << std::endl;
    std::cout << "c1.at('c') == " << c1.at('c') << std::endl;

    return (0);
    }
```

## <a name="begin"></a><a name="begin"></a> `begin`

Возвращает итератор, обращающийся к первый элемент в контейнере `map`.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Возвращаемое значение

Двунаправленный итератор, обращающийся к первому элементу в `map` или местоположению, на котором заканчивается пустая схема.

### <a name="example"></a>Пример

```cpp
// map_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err because the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "The first element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
The first element of m1 is now 1
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

Возвращает **`const`** итератор, который обращается к расположению сразу за последним элементом в диапазоне.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Двунаправленный итератор, обращающийся к первому элементу в диапазоне или расположению непосредственно за концом пустого диапазона (для пустого диапазона `cbegin() == cend()` ).

### <a name="remarks"></a>Комментарии

С возвращаемым значением `cbegin` элементы в диапазоне нельзя изменять.

Эту функцию-член можно использовать вместо функции-члена `begin()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `begin()` и `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>` cend`

Возвращает **`const`** итератор, который обращается к расположению сразу за последним элементом в диапазоне.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор двунаправленного доступа, указывающий на сразу за концом диапазона.

### <a name="remarks"></a>Комментарии

`cend` используется для проверки того, прошел ли итератор конец диапазона.

Эту функцию-член можно использовать вместо функции-члена `end()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `end()` и `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Значение, возвращаемое `cend`, не должно быть подвергнуто удалению ссылки.

## <a name="clear"></a><a name="clear"></a> `clear`

Стирает все элементы в сопоставлении.

```cpp
void clear();
```

### <a name="example"></a>Пример

В следующем примере демонстрируется использование `map::clear` функции члена.

```cpp
// map_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 4));

    i = m1.size();
    cout << "The size of the map is initially "
         << i << "." << endl;

    m1.clear();
    i = m1.size();
    cout << "The size of the map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the map is initially 2.
The size of the map after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать **`const`** элемент в `map` .

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `const_iterator` нельзя использовать для изменения значения элемента.

Объект, `const_iterator` определенный сопоставлением, указывает на элементы, являющиеся объектами [`value_type`](#value_type) типа `pair<constKey, Type>` , первый элемент которых является ключом элемента, а второй — сопоставленной частью, которая удерживается элементом.

Для разыменования объекта, `const_iterator` `cIter` указывающего на элемент в сопоставлении, используйте `->` оператор.

Чтобы получить доступ к значению ключа для элемента, используйте `cIter`  ->  **`first`** , что эквивалентно ( \* `cIter` ). **`first`**.

Чтобы получить доступ к значению сопоставленной части элемента, используйте `cIter`  ->  **`second`** , что эквивалентно ( \* `cIter` ). **`second`**.

### <a name="example"></a>Пример

См. пример для [`begin`](#begin) для примера, в котором используется `const_iterator` .

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

Тип, предоставляющий указатель на **`const`** элемент в сопоставлении.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Комментарии

Тип `const_pointer` нельзя использовать для изменения значения элемента.

В большинстве случаев [`iterator`](#iterator) для доступа к элементам в объекте Map следует использовать.

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в сопоставлении для чтения и выполнения **`const`** операций.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Пример

```cpp
// map_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать любой **`const`** элемент в `map` .

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `const_reverse_iterator` не может изменять значение элемента и используется для прохода по карте в обратную.

Объект, `const_reverse_iterator` определенный сопоставлением, указывает на элементы, являющиеся объектами [`value_type`](#value_type) типа `pair<const Key, Type>` , первый элемент которых является ключом элемента, а второй — сопоставленной частью, которая удерживается элементом.

Для разыменования `const_reverse_iterator crIter`, указывающего на элемент в сопоставлении, используйте оператор `->`.

Чтобы получить значение ключа для элемента, используйте `crIter`  ->  **`first`** , что эквивалентно ( \* `crIter` ). **`first`**

Чтобы получить доступ к значению сопоставленной версии элемента, используйте `crIter`  ->  **`second`** , что эквивалентно ( \* `crIter` ). **`first`**

### <a name="example"></a>Пример

[`rend`](#rend)Пример объявления и использования см. в примере для `const_reverse_iterator` .

## <a name="count"></a><a name="count"></a> `count`

Возвращает число элементов в объекте map, ключи которых соответствуют ключу, заданному параметром.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Значение ключа для сравнения с ключами элементов объекта map.

### <a name="return-value"></a>Возвращаемое значение

1, если объект map содержит элемент, ключ сортировки которого совпадает с ключом параметра. 0, если объект map не содержит ни одного элемента с соответствующим ключом.

### <a name="remarks"></a>Комментарии

Функция-член возвращает количество элементов *x* в диапазоне

\[ lower_bound (*ключ*), upper_bound (*ключ*))

— 0 или 1 для map, который является уникальным ассоциативным контейнером.

### <a name="example"></a>Пример

В следующем примере демонстрируется использование `map::count` функции члена.

```cpp
// map_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Keys must be unique in map, so duplicates are ignored
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 1.
The number of elements in m1 with a sort key of 2 is: 1.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="contains"></a><a name="contains"></a> `contains`

Проверяет, существует ли элемент с указанным ключом в `map` .

```cpp
bool contains(const Key& key) const;
template<class K> bool contains(const K& key) const;
```

### <a name="parameters"></a>Параметры

*`K`*\
Тип ключа.

*`key`*\
Искомое значение ключа элемента.

### <a name="return-value"></a>Возвращаемое значение

`true` значение, если элемент найден в контейнере; `false` в противном случае — значение.

### <a name="remarks"></a>Комментарии

`contains()` Новое в C++ 20. Чтобы использовать его, укажите [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) параметр компилятора.

`template<class K> bool contains(const K& key) const` принимает участие в разрешении перегрузки только в `key_compare` том случае, если является прозрачным. Дополнительные сведения см. [в разделе разнородный Уточняющий запрос в ассоциативных контейнерах](./stl-containers.md#heterogeneous-lookup-in-associative-containers-c14) .

### <a name="example"></a>Пример

```cpp
// Requires /std:c++latest
#include <map>
#include <string>
#include <iostream>
#include <functional>

int main()
{
    std::map<int, bool> m = {{0, true},{1, false}};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << m.contains(1) << '\n';
    std::cout << m.contains(2) << '\n';

    // call template function
    std::map<std::string, int, std::less<>> m2 = {{"ten", 10}, {"twenty", 20}, {"thirty", 30}};
    std::cout << m2.contains("ten");

    return 0;
}
```

```Output
true
false
true
```

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

Возвращает константный итератор на первый элемент в обратной карте.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный Обратный двунаправленный итератор, обращающийся к первому элементу в обратную [`map`](../standard-library/map-class.md) или обращающийся к последнему элементу в необращенном порядке `map` .

### <a name="remarks"></a>Комментарии

`crbegin` используется с обратным `map` так же, как используется [`begin`](#begin) с `map` .

При возвращении значения `crbegin` `map` объект не может быть изменен

`crbegin` можно использовать для перебора `map` в обратном порядке.

### <a name="example"></a>Пример

```cpp
// map_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
```

## <a name="crend"></a><a name="crend"></a> `crend`

Возвращает константный итератор, адресующий положение после последнего элемента в обратном сопоставлении.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный Обратный двунаправленный итератор, который обращается к расположению, следующему за последним элементом в обращении [`map`](../standard-library/map-class.md) (расположении, предшествующем первому элементу в неизмененном порядке `map` ).

### <a name="remarks"></a>Комментарии

`crend` используется с обратным сопоставлением так же, как и [`end`](#end) с `map` .

При возвращении значения `crend` `map` объект не может быть изменен.

`crend` используется, чтобы проверить, достиг ли итератор конца `map`.

Значение, возвращаемое `crend`, не должно быть подвергнуто удалению ссылки.

### <a name="example"></a>Пример

```cpp
// map_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

Целочисленный тип со знаком, который можно использовать для представления количества элементов в сопоставлении в диапазоне между элементами, на которые указывают итераторы.

```cpp
typedef allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Комментарии

`difference_type` — тип, возвращаемый при вычитании или приращении через итераторы контейнера. `difference_type` обычно используется для представления количества элементов в диапазоне *[ first,  last)* между итераторами `first` и `last`, включая элемент, на который указывает `first`, и диапазон элементов до элемента, на который указывает `last`, но не включая его.

Несмотря на то, `difference_type` что доступен для всех итераторов, удовлетворяющих требованиям итератора ввода, который включает класс двунаправленных итераторов, поддерживаемых обратимыми контейнерами, такими как набор, вычитание между итераторами поддерживается только итераторами произвольного доступа, предоставляемыми контейнером произвольного доступа, таким как Vector.

### <a name="example"></a>Пример

```cpp
// map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 2, 30 ) );

   map <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a map
   map <int, int>::difference_type  df_count = 1;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter)
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the map m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the map m1 is: 4.
```

## <a name="emplace"></a><a name="emplace"></a> `emplace`

Вставляет в сопоставление элемент, созданный на месте (без выполнения операций копирования или перемещения).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Аргументы, перенаправляемые для создания элемента, который необходимо вставить в карту, если он уже не содержит элемент, значение которого эквивалентно упорядочено.

### <a name="return-value"></a>Возвращаемое значение

Объект [`pair`](../standard-library/pair-structure.md) , **`bool`** компонент которого имеет значение `true` , если была сделана вставка, и `false` если она уже содержала элемент эквивалентного значения в упорядочении. Компонент итератора пары "возвращаемое значение" указывает на вновь вставленный элемент, если **`bool`** компонент имеет значение true, или на существующий элемент, если **`bool`** компонент имеет значение false.

Для доступа к компоненту-итератору `pair` `pr` используйте `pr.first`; для разыменования его используйте `*pr.first`. Чтобы получить доступ к **`bool`** компоненту, используйте `pr.second` . См. пример кода далее в этой статье.

### <a name="remarks"></a>Комментарии

Эта функция не делает недействительными никакие итераторы или ссылки.

Во время назначения места при возникновении исключения состояние контейнера не изменяется.

[`value_type`](#value_type)Элемент является парой, поэтому значение элемента будет упорядоченной парой, первый компонент которой равен значению ключа, а второй компонент равен значению данных элемента.

### <a name="example"></a>Пример

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<int, string> m1;

    auto ret = m1.emplace(10, "ten");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
        cout << "map not modified" << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;

    ret = m1.emplace(10, "one zero");

    if (!ret.second){
        auto pr = *ret.first;
        cout << "Emplace failed, element with key 10 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "map modified, now contains ";
        print(m1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a><a name="emplace_hint"></a> `emplace_hint`

Вставляет созданный элемент на место (операции копирования или перемещения не выполняются) с указанием о размещении.

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Аргументы, перенаправляемые для создания элемента, который необходимо вставить в карту, если эта схема уже не содержит этот элемент или, в более общем случае, если он уже не содержит элемент, ключ которого эквивалентно упорядочен.

*`where`*\
Место начала поиска правильной точки вставки. (Если точка непосредственно перед *точкой, то* Вставка может выполняться в периодической константе вместо логарифмического времени.)

### <a name="return-value"></a>Возвращаемое значение

Итератор, указывающий на вновь вставленный элемент.

Если вставка не удалась, так как элемент уже существует, возвращается итератор, указывающий на существующий элемент с его ключом.

### <a name="remarks"></a>Комментарии

Эта функция не делает недействительными никакие итераторы или ссылки.

Во время назначения места при возникновении исключения состояние контейнера не изменяется.

[`value_type`](#value_type)Элемент является парой, поэтому значение элемента будет упорядоченной парой, первый компонент которой равен значению ключа, а второй компонент равен значению данных элемента.

### <a name="example"></a>Пример

```cpp
// map_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    map<string, string> m1;

    // Emplace some test data
    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "map starting data: ";
    print(m1);
    cout << endl;

    // Emplace with hint
    // m1.end() should be the "next" element after this emplacement
    m1.emplace_hint(m1.end(), "Doug", "Engineering");

    cout << "map modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> `empty`

Проверяет, что сопоставление пустое.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если схема пуста; **`false`** значение, если схема не пуста.

### <a name="example"></a>Пример

```cpp
// map_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The map m1 is empty." << endl;
   else
      cout << "The map m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The map m2 is empty." << endl;
   else
      cout << "The map m2 is not empty." << endl;
}
```

```Output
The map m1 is not empty.
The map m2 is empty.
```

## <a name="end"></a><a name="end"></a> `end`

Возврат итератора после конца.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Возвращаемое значение

Итератор после конца. Если карта пуста, то `map::end() == map::begin()`.

### <a name="remarks"></a>Комментарии

`end` используется для проверки того, прошел ли итератор конец его сопоставлений.

Значение, возвращаемое `end`, не должно быть подвергнуто удалению ссылки.

Пример кода см. в разделе [`map::find`](#find) .

## <a name="equal_range"></a><a name="equal_range"></a> `equal_range`

Возвращает пару итераторов, представляющих [`lower_bound`](#lower_bound) ключ и [`upper_bound`](#upper_bound) ключ.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Параметры

*`key`*\
Ключевое значение для сравнения с ключом сортировки элемента из сопоставления, в котором ведется поиск.

### <a name="return-value"></a>Возвращаемое значение

Для доступа к первому итератору пары `pr`, возвращаемой функцией-членом, нужно использовать `pr`. во- **первых**, и для разыменования итератора нижней границы используйте \* ( `pr` . **первый**). Для доступа ко второму итератору пары `pr`, возвращаемой функцией-членом, нужно использовать `pr`. **во-вторых**, а для разыменования итератора верхней границы используйте \* ( `pr` . **второй**).

### <a name="example"></a>Пример

```cpp
// map_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef map <int, int, less<int> > IntMap;
   IntMap m1;
   map <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the map m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The map m1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of map m1 with a key >= 40 is: "
           << p2.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the map m1 is: 20.
The upper bound of the element with a key of 2 in the map m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The map m1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> `erase`

Удаляет элемент или диапазон элементов из сопоставления из указанной позиции или удаляет элементы, которые соответствуют указанному ключу.

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>Параметры

*`Where`*\
Положение удаляемого элемента.

*`First`*\
Положение первого удаляемого элемента.

*`Last`*\
Позиция после последнего элемента для удаления.

*`Key`*\
Значение ключа удаляемых элементов.

### <a name="return-value"></a>Возвращаемое значение

Для первых двух функций-членов это двунаправленный итератор, обозначающий первый элемент, остающийся после любых удаленных элементов, или элемент в конце сопоставления, если таких элементов нет.

Третья функция-член возвращает количество элементов, которые были удалены из сопоставления.

### <a name="example"></a>Пример

```cpp
// map_erase.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions
#include <utility>  // make_pair()

using namespace std;

using mymap = map<int, string>;

void printmap(const mymap& m) {
    for (const auto& elem : m) {
        cout << " [" << elem.first << ", " << elem.second << "]";
    }
    cout << endl << "size() == " << m.size() << endl << endl;
}

int main()
{
    mymap m1;

    // Fill in some data to test with, one at a time
    m1.insert(make_pair(1, "A"));
    m1.insert(make_pair(2, "B"));
    m1.insert(make_pair(3, "C"));
    m1.insert(make_pair(4, "D"));
    m1.insert(make_pair(5, "E"));

    cout << "Starting data of map m1 is:" << endl;
    printmap(m1);
    // The 1st member function removes an element at a given position
    m1.erase(next(m1.begin()));
    cout << "After the 2nd element is deleted, the map m1 is:" << endl;
    printmap(m1);

    // Fill in some data to test with, one at a time, using an initializer list
    mymap m2
    {
        { 10, "Bob" },
        { 11, "Rob" },
        { 12, "Robert" },
        { 13, "Bert" },
        { 14, "Bobby" }
    };

    cout << "Starting data of map m2 is:" << endl;
    printmap(m2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    m2.erase(next(m2.begin()), prev(m2.end()));
    cout << "After the middle elements are deleted, the map m2 is:" << endl;
    printmap(m2);

    mymap m3;

    // Fill in some data to test with, one at a time, using emplace
    m3.emplace(1, "red");
    m3.emplace(2, "yellow");
    m3.emplace(3, "blue");
    m3.emplace(4, "green");
    m3.emplace(5, "orange");
    m3.emplace(6, "purple");
    m3.emplace(7, "pink");

    cout << "Starting data of map m3 is:" << endl;
    printmap(m3);
    // The 3rd member function removes elements with a given Key
    mymap::size_type count = m3.erase(2);
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from m3 is: " << count << "." << endl;
    cout << "After the element with a key of 2 is deleted, the map m3 is:" << endl;
    printmap(m3);
}
```

## <a name="find"></a><a name="find"></a> `find`

Возвращает итератор, ссылающийся на элемент в карте, ключ которого эквивалентен заданному ключу.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Значение ключа, с которым сравнивается ключ сортировки элемента из карты, по которой выполняется поиск.

### <a name="return-value"></a>Возвращаемое значение

Итератор, который ссылается на расположение элемента с указанным ключом или расположение после последнего элемента в `map` ( `map::end()` ), если совпадение для ключа не найдено.

### <a name="remarks"></a>Комментарии

Функция-член возвращает итератор, который ссылается на элемент в, `map` ключ сортировки которого эквивалентен ключу аргумента в бинарном предикате, который вызывает упорядочивание на основе отношения сравнения "меньше".

Если возвращаемое значение `find` назначается `const_iterator` , объект Map изменить нельзя. Если возвращаемое значение `find` присваивается `iterator` , то объект Map можно изменить

### <a name="example"></a>Пример

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    map<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting map m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified map m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

Возвращает копию объекта-распределителя, использованного для создания сопоставления.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Распределитель, используемый сопоставлением.

### <a name="remarks"></a>Комментарии

Распределители для класса map определяют, как это класс управляет памятью. Распределителей по умолчанию в классах контейнеров стандартной библиотеки C++ достаточно для большинства задач программирования. Написание и использование собственного класса распределителя требует расширенных навыков работы с C++.

### <a name="example"></a>Пример

```cpp
// map_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int>::allocator_type m1_Alloc;
   map <int, int>::allocator_type m2_Alloc;
   map <int, double>::allocator_type m3_Alloc;
   map <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   map <int, int> m1;
   map <int, int, allocator<int> > m2;
   map <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated\n"
        << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated\n"
        << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a map m4
   // with the allocator of map m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable." << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable." << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> `insert`

Вставляет элемент или диапазон элементов в сопоставление.

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>Параметры

*`Val`*\
Значение элемента, вставляемого в карту, если он уже не содержит элемент, ключ которого эквивалентно упорядочен.

*`Where`*\
Место начала поиска правильной точки вставки. (Если эта точка непосредственно предшествует *`Where`* , то вставка может выполняться в периодической константе вместо логарифмического времени.)

*`ValTy`*\
Параметр шаблона, указывающий тип аргумента, который может использоваться сопоставлением для создания элемента [`value_type`](#value_type) , и идеального перенаправления *`Val`* в качестве аргумента.

*`First`*\
Позиция первого элемента, который следует скопировать.

*`Last`*\
Позиция непосредственно перед последним элементом, который следует скопировать.

*`InputIterator`*\
Аргумент функции-шаблона, соответствующий требованиям [итератора ввода](../standard-library/input-iterator-tag-struct.md) , указывающего на элементы типа, которые могут использоваться для построения [`value_type`](#value_type) объектов.

*`IList`*\
Объект, [`initializer_list`](../standard-library/initializer-list.md) из которого копируются элементы.

### <a name="return-value"></a>Возвращаемое значение

Одноэлементные функции-члены (1) и (2) возвращают объект, [`pair`](../standard-library/pair-structure.md) **`bool`** компонент которого имеет значение true, если была произведена вставка, и значение false, если в карте уже содержится элемент, ключ которого имеет эквивалентное значение в упорядочении. Компонент итератора пары "возвращаемое значение" указывает на вновь вставленный элемент, если **`bool`** компонент имеет значение true, или на существующий элемент, если **`bool`** компонент имеет значение false.

Одноэлементные функции-члены с подсказкой (3) и (4) возвращают итератор, который указывает на позицию, где новый элемент был вставлен, или, если элемент с эквивалентным ключом уже существует, указывает на существующий элемент.

### <a name="remarks"></a>Комментарии

Эта функция не делает никакие итераторы, указатели или ссылки недействительными.

При вставке всего одного элемента при возникновении исключения состояние контейнера не изменяется. Если во время вставки нескольких элементов вызывается исключение, контейнер остается в неопределенном, но допустимом состоянии.

Чтобы получить доступ к компоненту итератора `pair` `pr` , возвращаемому функциями-членами с одним элементом, используйте оператор `pr.first` ; для разыменования итератора в возвращенной паре используйте `*pr.first` , предоставив элемент. Чтобы получить доступ к **`bool`** компоненту, используйте `pr.second` . См. пример кода далее в этой статье.

[`value_type`](#value_type)Контейнером является typedef, принадлежащий контейнеру, а для Map `map<K, V>::value_type` — `pair<const K, V>` . Значение элемента — это упорядоченная пара, в которой первый компонент эквивалентен значению ключа, а второй компонент — значению данных элемента.

Функция-член с диапазоном (5) вставляет последовательность значений элементов в сопоставление, соответствующее каждому элементу, адресованному итератором в диапазоне `[First, Last)`. Следовательно, `Last` не вставляется. Контейнер функции-члена `end()` ссылается на позицию сразу после последнего элемента в контейнере. Например, оператор `m.insert(v.begin(), v.end());` пытается вставить все элементы `v` в `m`. Вставляются только элементы с уникальными значениями в диапазоне. Повторяющиеся значения игнорируются. Чтобы увидеть, какие элементы отклонены, используйте одноэлементные версии `insert`.

Функция-член списка инициализаторов (6) использует [`initializer_list`](../standard-library/initializer-list.md) для копирования элементов в карту.

Для вставки элемента, созданного на месте (т. е. не выполняются операции копирования или перемещения), [`map::emplace`](#emplace) см [`map::emplace_hint`](#emplace_hint) . и.

### <a name="example"></a>Пример

```cpp
// map_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    map<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    auto ret = m1.insert(make_pair(1, 111));
    if (!ret.second){
        auto pr = *ret.first;
        cout << "Insert failed, element with key value 1 already exists."
            << endl << "  The existing element is (" << pr.first << ", " << pr.second << ")"
            << endl;
    }
    else{
        cout << "The modified key and mapped values of m1 are:" << endl;
        print(m1);
    }
    cout << endl;

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    map<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    map<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    map<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

Тип, предоставляющий двунаправленный итератор, который может считывать или изменять любой элемент в сопоставлении.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Комментарии

Итератор, определяемый картой, указывает на элементы, являющиеся объектами [`value_type`](#value_type) типа, `pair<const Key, Type>` первый элемент которых является ключом элемента, а второй элемент — сопоставленная база данных, удерживаемая элементом.

Для разыменования итератора *iter* , указывающего на элемент в сопоставлении, используйте `->` оператор.

Чтобы получить доступ к значению ключа для элемента, используйте `Iter->first` , что эквивалентно `(*Iter).first` . Чтобы получить доступ к значению сопоставленной версии элемента, используйте `Iter->second` , что эквивалентно `(*Iter).second` .

### <a name="example"></a>Пример

[`begin`](#begin)Пример объявления и использования см. в разделе пример `iterator` .

## <a name="key_comp"></a><a name="key_comp"></a> `key_comp`

Извлекает копию объекта сравнения, использованного для упорядочивания ключей в сопоставлении.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает объект-функцию, которую сопоставление использует для упорядочивания своих элементов.

### <a name="remarks"></a>Комментарии

Хранимый объект определяет функцию-член

`bool operator(const Key& left, const Key& right);`

возвращающий значение, **`true`** Если `left` `right` в порядке сортировки предшествует и не равны.

### <a name="example"></a>Пример

```cpp
// map_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   map <int, int, greater<int> > m2;
   map <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a><a name="key_compare"></a> `key_compare`

Тип, предоставляющий объект функции, который может сравнить два ключа сортировки для определения относительного порядка двух элементов в контейнере `map`.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Комментарии

`key_compare` является синонимом для параметра-шаблона *`Traits`* .

Дополнительные сведения о *`Traits`* см. в разделе о [ `map` классе](../standard-library/map-class.md) .

### <a name="example"></a>Пример

[`key_comp`](#key_comp)Пример объявления и использования см. в разделе пример `key_compare` .

## <a name="key_type"></a><a name="key_type"></a> `key_type`

Тип, который описывает ключ сортировки, хранящийся в каждом элементе сопоставления.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Комментарии

`key_type` является синонимом для параметра-шаблона *`Key`* .

Дополнительные сведения о см *`Key`* . в подразделе **"Примечания** " статьи о [ `map` классе](../standard-library/map-class.md) .

### <a name="example"></a>Пример

[`value_type`](#value_type)Пример объявления и использования см. в разделе пример `key_type` .

## <a name="lower_bound"></a><a name="lower_bound"></a> `lower_bound`

Возвращает итератор, указывающий на первый элемент в сопоставлении с ключом, значение которого больше указанного ключа или равно ему.

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Ключевое значение для сравнения с ключом сортировки элемента из сопоставления, в котором ведется поиск.

### <a name="return-value"></a>Возвращаемое значение

Объект `iterator` или `const_iterator` , который обращается к расположению элемента в сопоставлении с ключом, который равен ключу аргумента или больше него, либо обращается к расположению, следующему за последним элементом в, `map` Если совпадение для ключа не найдено.

Если возвращаемое значение `lower_bound` назначается `const_iterator` , объект Map изменить нельзя. Если возвращаемое значение `lower_bound` присваивается `iterator` , то объект Map можно изменить.

### <a name="example"></a>Пример

```cpp
// map_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The first element of map m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for this key, end( ) is returned
   m1_RcIter = m1. lower_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of map m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1. lower_bound ( m1_AcIter -> first );
   cout << "The element of m1 with a key matching "
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key of 2 is: 20.
The map m1 doesn't have an element with a key of 4.
The element of m1 with a key matching that of the last element is: 30.
```

## <a name="map"></a><a name="map"></a> `map`

Создает сопоставление, которое является пустым или копией части или целого другого сопоставления.

```cpp
map();

explicit map(
    const Traits& Comp);

map(
    const Traits& Comp,
    const Allocator& Al);

map(
    const map& Right);

map(
    map&& Right);

map(
    initializer_list<value_type> IList);

map(
    initializer_list<value_type> IList,
    const Traits& Comp);

map(
    initializer_list<value_type> IList,
    const Traits& Comp,
    const Allocator& Allocator);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Параметры

*`Al`*\
Класс распределителя памяти, который будет использоваться для этого объекта-сопоставления. Значение по умолчанию — `Allocator`.

*`Comp`*\
Функция сравнения типа `const Traits`, используемая для упорядочивания элементов в `map`. Значение по умолчанию — `hash_compare`.

*`Right`*\
Сопоставление, копией которого будет создаваемое сопоставление.

*`First`*\
Положение первого элемента в диапазоне копируемых элементов.

*`Last`*\
Положение первого элемента после диапазона копируемых элементов.

*`IList`*\
Объект initializer_list, из которого будут скопированы элементы.

### <a name="remarks"></a>Комментарии

Все конструкторы хранят тип объекта распределителя, который управляет хранилищем памяти для Map и затем может быть возвращен путем вызова метода [`get_allocator`](#get_allocator) . Параметр-распределитель часто не указывается в объявлениях класса и в макросах предварительной обработки, используемых для замены альтернативных распределителей.

Все конструкторы инициализируют свои сопоставления.

Все конструкторы хранят объект функции с признаками типа, который используется для установления порядка ключей в сопоставлении и может быть впоследствии возвращен вызовом [`key_comp`](#key_comp) .

Первые три конструктора задают пустую начальную карту, второй задает тип функции сравнения ( *`Comp`* ), используемой при установлении порядка элементов, а третий явно указывает тип распределителя ( *`Al`* ) для использования. Ключевое слово **`explicit`** подавляет некоторые виды автоматического преобразования типов.

Четвертый конструктор указывает копию схемы *`Right`* .

Пятый конструктор указывает копию Map путем перемещения *`Right`* .

В шестом, седьмом и 8 конструкторах используется объект, `initializer_list` из которого копируются элементы.

Следующие три конструктора копируют диапазон `[First, Last)` сопоставления с повышением точности при указании типа функции сравнения класса `Traits` и распределителя.

### <a name="example"></a>Пример

```cpp
// map_map.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;
    map <int, int>::iterator m1_Iter, m3_Iter, m4_Iter, m5_Iter, m6_Iter, m7_Iter;
    map <int, int, less<int> >::iterator m2_Iter;

    // Create an empty map m0 of key type integer
    map <int, int> m0;

    // Create an empty map m1 with the key comparison
    // function of less than, then insert 4 elements
    map <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty map m2 with the key comparison
    // function of greater than, then insert 2 elements
    map <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a map m3 with the
    // allocator of map m1
    map <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    map <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, map m4, of map m1
    map <int, int> m4(m1);

    // Create a map m5 by copying the range m1[ first,  last)
    map <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    map <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a map m6 by copying the range m4[ first,  last)
    // and with the allocator of map m2
    map <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    map <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for(auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m7 by moving m5
    cout << "m7 =";
    map<int, int> m7(move(m5));
    for (auto i : m7)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m8 by copying in an initializer_list
    map<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m9 with an initializer_list and a comparator
    map<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a map m10 with an initializer_list, a comparator, and an allocator
    map<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;
}
```

## <a name="mapped_type"></a><a name="mapped_type"></a> `mapped_type`

Тип, который представляет данные, хранящиеся в сопоставлении.

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Комментарии

Тип `mapped_type` является синонимом для параметра шаблона *типа* класса.

Дополнительные сведения о *`Type`* см. в разделе о [ `map` классе](../standard-library/map-class.md) .

### <a name="example"></a>Пример

[`value_type`](#value_type)Пример объявления и использования см. в разделе пример `mapped_type` .

## <a name="max_size"></a><a name="max_size"></a> `max_size`

Возврат максимальной длины сопоставления.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Максимально возможная длина сопоставления.

### <a name="example"></a>Пример

```cpp
// map_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="operator"></a><a name="op_at"></a> `operator[]`

Вставка элемента в сопоставление с заданным значением ключа.

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>Параметры

*`key`*\
Значение ключа элемента, который необходимо вставить.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на значение данных вставленного элемента.

### <a name="remarks"></a>Комментарии

Если значение ключа аргумента не найдено, оно вставляется вместе со значением по умолчанию для типа данных.

`operator[]` может использоваться для вставки элементов в карту `m` с помощью `m[key] = DataValue;` WHERE, где `DataValue` — это значение `mapped_type` элемента со значением ключа *`key`* .

При использовании `operator[]` для вставки элементов возвращаемая ссылка не отображает, меняет ли вставка уже существующий элемент или создает новый. Функции-члены [`find`](#find) и [`insert`](#insert) могут использоваться для определения того, существует ли уже элемент с указанным ключом перед вставкой.

### <a name="example"></a>Пример

```cpp
// map_op_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a map using the operator[] member function
   m1[ 1 ] = 10;

   // Compare other ways to insert objects into a map
   m1.insert ( map <int, int> :: value_type ( 2, 20 ) );
   m1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   m1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   m1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

// insert by moving key
    map<string, int> c2;
    string str("abc");
    cout << "c2[move(str)] == " << c2[move(str)] << endl;
    cout << "c2["abc"] == " << c2["abc"] << endl;

    return (0);
}
```

```Output
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
The keys of the mapped elements are now: 1 2 3 5.
The values of the mapped elements are now: 10 40 30 0.
c2[move(str)] == 0
c2["abc"] == 1
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

Замена элементов сопоставления копией другого сопоставления.

```cpp
map& operator=(const map& right);
map& operator=(map&& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Объект, который [`map`](../standard-library/map-class.md) копируется в `map` .

### <a name="remarks"></a>Комментарии

После стирания любых существующих элементов в `map` `operator=` копирует или перемещает содержимое *`right`* в карту.

### <a name="example"></a>Пример

```cpp
// map_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   map<int, int> v1, v2, v3;
   map<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="pointer"></a><a name="pointer"></a> `pointer`

Тип, предоставляющий указатель на элемент в сопоставлении.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Комментарии

Тип `pointer` можно использовать для изменения значения элемента.

В большинстве случаев [`iterator`](#iterator) для доступа к элементам в объекте Map следует использовать.

## <a name="rbegin"></a><a name="rbegin"></a> rbegin

Возвращает итератор, адресующий первый элемент в обратном сопоставлении.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный двунаправленный итератор, адресующий первый элемент в обратном сопоставлении или адресующий элемент, который был последним элементов в сопоставлении до изменения его порядка на противоположный.

### <a name="remarks"></a>Комментарии

`rbegin` используется с обратным картой точно так же, как используется [`begin`](#begin) с картой.

Если возвращаемое значение `rbegin` назначается `const_reverse_iterator` , то объект Map изменить нельзя. Если возвращенное значение `rbegin` назначается `reverse_iterator`, то объект-сопоставление можно изменить.

`rbegin` можно использовать для перебора сопоставления в обратном порядке.

### <a name="example"></a>Пример

```cpp
// map_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed map m1 is 3.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the first element in the reversed map is 2.
```

## <a name="reference"></a><a name="reference"></a> `reference`

Тип, предоставляющий ссылку на элемент, хранящийся в сопоставлении.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Пример

```cpp
// map_reference.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference can't be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the map is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the map is 1.
The data value of first element in the map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a><a name="rend"></a> `rend`

Возвращает итератор, адресующий положение после последнего элемента в обратном сопоставлении.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный двунаправленный итератор, адресующий положение после последнего элемента в обратном сопоставлении (положение, которое предшествовало первому элементу в сопоставлении до изменения его порядка на противоположный).

### <a name="remarks"></a>Комментарии

`rend` используется с обратным картой точно так же, как используется [`end`](#end) с картой.

Если возвращаемое значение `rend` назначается `const_reverse_iterator` , то объект Map изменить нельзя. Если возвращенное значение `rend` назначается `reverse_iterator`, то объект-сопоставление можно изменить.

`rend` можно использовать для проверки, достиг ли итератор конца своего сопоставления.

Значение, возвращаемое `rend`, не должно быть подвергнуто удалению ссылки.

### <a name="example"></a>Пример

```cpp
// map_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;

   map <int, int> :: iterator m1_Iter;
   map <int, int> :: reverse_iterator m1_rIter;
   map <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed map m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a map in a forward order
   cout << "The map is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a map in a reverse order
   cout << "The reversed map is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A map element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed map is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed map m1 is 1.
The map is: 1 2 3 .
The reversed map is: 3 2 1 .
After the erasure, the last element in the reversed map is 2.
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать или изменять элементы в обратном сопоставлении.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `reverse_iterator` не может изменять значение элемента и используется для прохода по карте в обратную.

Объект, `reverse_iterator` определенный сопоставлением, указывает на элементы, являющиеся объектами [`value_type`](#value_type) типа `pair<const Key, Type>` , первый элемент которых является ключом элемента, а второй — сопоставленной частью, которая удерживается элементом.

Для разыменования `reverse_iterator` *спрайта* , указывающего на элемент в сопоставлении, используйте `->` оператор.

Для получения доступа к значению ключа для элемента используйте `rIter` -> **first**, что эквивалентно (\* `rIter`). **сначала**. Для получения доступа к значению сопоставленных данных элемента используйте `rIter` -> **second**, что эквивалентно (\* `rIter`). **сначала**.

### <a name="example"></a>Пример

[`rbegin`](#rbegin)Пример объявления и использования см. в разделе пример `reverse_iterator` .

## <a name="size"></a><a name="size"></a> `size`

Возвращает количество элементов в контейнере `map`.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Текущая длина сопоставления.

### <a name="example"></a>Пример

В следующем примере демонстрируется использование `map::size` функции члена.

```cpp
// map_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    map<int, int> m1, m2;
    map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The map length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The map length is now " << i << "." << endl;
}
```

```Output
The map length is 1.
The map length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

Беззнаковый целочисленный тип, который может представлять количество элементов в сопоставлении.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Пример

[`size`](#size)Пример объявления и использования см. в примере для `size_type` .

## <a name="swap"></a><a name="swap"></a> позиции

Обмен элементами между двумя сопоставлениями.

```cpp
void swap(
    map<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Сопоставление-аргумент предоставляет элементы для обмена с целевым сопоставлением.

### <a name="remarks"></a>Комментарии

Функция-член не делает недействительными никакие ссылки, указатели или итераторы, обозначающие элементы в двух сопоставлениях, между которыми выполняется обмен элементами.

### <a name="example"></a>Пример

```cpp
// map_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1, m2, m3;
   map <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   //m2 is said to be the argument map; m1 the target map
   m1.swap( m2 );

   cout << "After swapping with m2, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, map m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original map m1 is: 10 20 30.
After swapping with m2, map m1 is: 100 200.
After swapping with m3, map m1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> `upper_bound`

Возвращает итератор, указывающий на первый элемент в сопоставлении с ключом, значение которого равно указанному ключу или больше его.

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Аргумент-значение ключа для сравнения с значением ключа сортировки элемента сопоставления, в котором проводится поиск.

### <a name="return-value"></a>Возвращаемое значение

Объект `iterator` или `const_iterator` , который обращается к расположению элемента в сопоставлении с ключом, который больше, чем ключ аргумента, или, который обращается к расположению, следующему за последним элементом в, `map` Если совпадение для ключа не найдено.

Если возвращаемое значение назначено `const_iterator` , объект Map изменить нельзя. Если возвращаемое значение присвоено `iterator` , объект Map можно изменить.

### <a name="example"></a>Пример

```cpp
// map_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   map <int, int> m1;
   map <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of map m1 with a key "
        << "greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   m1_RcIter = m1. upper_bound ( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The map m1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of map m1 with a key > 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the map can be found
   // using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1. upper_bound ( m1_AcIter -> first );
   cout << "The 1st element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The first element of map m1 with a key greater than 2 is: 30.
The map m1 doesn't have an element with a key greater than 4.
The 1st element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> `value_comp`

Функция-член возвращает объект-функцию, которая определяет порядок элементов в сопоставлении путем сравнения значений их ключей.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает объект-функцию сравнения, которую сопоставление использует для упорядочивания своих элементов.

### <a name="remarks"></a>Комментарии

Для Map *m*, если два элемента *E1*(*K1*, *D1*) и *E2*(*априорной оценкой K2*, *D2*) являются объектами типа `value_type` , где *K1* и *K1* — это ключи типа, `key_type` а *D1* и *D2* — их данные типа `mapped_type` , то `m.value_comp(e1, e2)` эквивалентно `m.key_comp(k1, k2)` . Хранимый объект определяет функцию-член

`bool operator( value_type& left, value_type& right);`

Возвращает, **`true`** Если значение ключа `left` предшествует значению ключа в порядке сортировки и не равно ему `right` .

### <a name="example"></a>Пример

```cpp
// map_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   map <int, int, less<int> > m1;
   map <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   pair< map<int,int>::iterator, bool > pr1, pr2;

   pr1= m1.insert ( map <int, int> :: value_type ( 1, 10 ) );
   pr2= m1.insert ( map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if(vc1( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a><a name="value_type"></a> `value_type`

Тип объекта, хранящегося в качестве элемента в сопоставлении.

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>Пример

```cpp
// map_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   map <int, int> m1;
   map <int, int> :: key_type key1;
   map <int, int> :: mapped_type mapped1;
   map <int, int> :: value_type value1;
   map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a map
   m1.insert ( cInt2Int ( 2, 20 ) );
   m1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the map is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type isn't assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

## <a name="see-also"></a>См. также раздел

[Контейнера](./stl-containers.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)
