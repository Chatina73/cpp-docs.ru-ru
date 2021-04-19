---
title: Класс set
description: Справочник по API для класса контейнера стандартной библиотеки C++ `set` , который используется для хранения и извлечения данных из коллекции.
ms.date: 9/9/2020
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::contains
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], contains
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: 64158f868f3296cbedff8a6c87c797a75a4c2b3a
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721567"
---
# <a name="set-class"></a>Класс `set`

Класс контейнера стандартной библиотеки C++ `set` используется для хранения и извлечения данных из коллекции. Значения элементов в `set` являются уникальными и служат в качестве ключевых значений, в соответствии с которыми данные автоматически упорядочиваются. Значение элемента в `set` не может быть изменено напрямую. Вместо этого старые значения необходимо удалить и вставить элементы с новыми значениями.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>Параметры

*`Key`*\
Тип данных элемента для сохранения в наборе.

*`Traits`*\
Тип, предоставляющий объект функции, который может сравнить два значения элемента как ключи сортировки, чтобы определить их относительный порядок в наборе. Этот аргумент является необязательным, а бинарный предикат `less <Key>` — значением по умолчанию.

В C++ 14 можно включить разнородный Уточняющий запрос, указав `std::less<>` предикат или `std::greater<>` , не имеющий параметров типа. Дополнительные сведения см. [в разделе разнородный Уточняющий запрос в ассоциативных контейнерах](../standard-library/stl-containers.md#sequence_containers) .

*`Allocator`*\
Тип, представляющий сохраненный объект распределителя, который инкапсулирует сведения о выделении и освобождении памяти для набора. Этот аргумент является необязательным, и в качестве значения по умолчанию используется `allocator<Key>`.

## <a name="remarks"></a>Замечания

Набор стандартной библиотеки C++ — это:

- Ассоциативный контейнер, который является контейнером переменного размера, поддерживающим эффективное получение значений элементов на основе значения соответствующего ключа. Кроме того, это простой ассоциативный контейнер, поскольку его значения элементов являются его ключевыми значениями.

- Является реверсивным, поскольку предоставляет двунаправленный итератор для получения доступа к его элементам.

- Сортированный, поскольку его элементы упорядочены по значениям ключей в контейнере в соответствии с заданной функцией сравнения.

- Является уникальным, поскольку каждый его элемент должен обладать уникальным ключом. Поскольку набор также является простым ассоциативным контейнером, его элементы также являются уникальными.

Набор также описывается как шаблон класса, так как предоставляемые им функциональные возможности являются универсальными и не зависят от конкретного типа данных, содержащихся в качестве элементов. Тип данных, подлежащий использованию, вместо этого определяется как параметры в шаблоне класса вместе с функцией и распределителем сравнения.

Выбор типа контейнера должен в общем случае производиться на основе типа поиска и вставки, который требуется приложению. Ассоциативные контейнеры оптимизированы для операций поиска, вставки и удаления. Функции-члены, которые явно поддерживают эти операции, являются эффективными, и их выполнение выполняется в среднем пропорционально логарифму числа элементов в контейнере. Вставка элементов сделает недействительными итераторы, а удаление элементов сделает недействительными только те итераторы, которые указывают на удаленные элементы.

Набор рекомендуется использовать в качестве ассоциативного контейнера, если условия, ассоциирующие значения с ключами, удовлетворяются приложением. Элементы набора являются уникальным и используются в качестве своих собственных ключей сортировки. Модель для этого типа структуры — упорядоченный список, например, ключевых слов, в котором слова не должны повторяться. Если допускается повторное использование слов, то подходящей структурой контейнера будет multiset. Если значения вносятся в список уникальных ключевых слов, сопоставление является подходящей структурой для размещения этих данных. Если же ключи не являются уникальными, то multimap будет контейнером выбора.

Набор упорядочивает последовательность, которую он управляет, путем вызова хранимой функции типа [`key_compare`](#key_compare) . Этот сохраненный объект является функцией сравнения, доступ к которой можно получить путем вызова функции-члена [`key_comp`](#key_comp) . Как правило, элементы должны быть просто менее сравнимы, чтобы установить этот порядок, чтобы при наличии любых двух элементов можно было определить, что они эквивалентны (в смысле, что ни одно из них не меньше другого) или что один меньше другого. Это приводит к упорядочению неравнозначных элементов. С более технической точки зрения, функция сравнения является бинарным предикатом, который вызывает строгого слабое упорядочение в стандартном математически смысле. Бинарный предикат *f*(*x, y*) — это объект функции, имеющий два объекта-аргумента *x* и *y* , а также возвращаемое значение **`true`** или **`false`** . Порядок, накладываемый на набор, является строгим слабым порядком, если бинарный предикат является нерефлексивным, антисимметричным и транзитивным и если эквивалентность является транзитивным, где два объекта *x* и *y* определяются как эквивалентные, если значения *f* *x, y* и *f*(*y, x*) равны false. Если более строгое условие равенства между ключами заменяет условие эквивалентности, порядок становится общим (т.е. все элементы упорядочиваются относительно друг друга), и сопоставленные ключи будут неотличимы друг от друга.

В C++ 14 можно включить разнородный Уточняющий запрос, указав `std::less<>` предикат или `std::greater<>` , не имеющий параметров типа. Дополнительные сведения см. [в разделе разнородный Уточняющий запрос в ассоциативных контейнерах](../standard-library/stl-containers.md#sequence_containers) .

Итератор, предоставляемый классом набора, является двунаправленным итератором, но функции-члены класса [`insert`](#insert) и [`set`](#set) имеют версии, принимающие в качестве параметров шаблона более слабый итератор ввода, чьи функциональные требования более минимальны, чем гарантированные классом двунаправленных итераторов. Различные концепции итераторов образуют семейство, связанное уточнениями функциональности. Каждая концепция итератора имеет собственный набор требований, а алгоритмы, работающие с ними, должны ограничивать свои предположения согласно требованиям, предоставляемым этим типом итератора. Можно предположить, что итератор ввода может быть разыменован для обращения к определенному объекту и инкрементирован до следующего итератора в последовательности. Это минимальный набор функциональных возможностей, но достаточно для того, чтобы иметь возможность осмысленно говорить о диапазоне итераторов [ `First` , `Last` ) в контексте функций-членов класса.

### <a name="constructors"></a>Конструкторы

|Имя|Описание|
|-|-|
|[`set`](#set)|Создает набор, который является пустым или копией части или целого другого набора.|

### <a name="typedefs"></a>Определения типов

|Имя|Описание|
|-|-|
|[`allocator_type`](#allocator_type)|Тип, представляющий класс `allocator` для объекта набора.|
|[`const_iterator`](#const_iterator)|Тип, предоставляющий двунаправленный итератор, который может читать **`const`** элемент в наборе.|
|[`const_pointer`](#const_pointer)|Тип, предоставляющий указатель на **`const`** элемент в наборе.|
|[`const_reference`](#const_reference)|Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в наборе для чтения и выполнения **`const`** операций.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Тип, предоставляющий двунаправленный итератор, который может читать любой **`const`** элемент в наборе.|
|[`difference_type`](#difference_type)|Тип целого числа со знаком, пригодный для использования в качестве представления количества элементов в наборе в диапазоне между элементами, на которые указывают итераторы.|
|[`iterator`](#iterator)|Тип, предоставляющий двунаправленный итератор, который может считывать или изменять любой элемент в наборе.|
|[`key_compare`](#key_compare)|Тип, предоставляющий объект функции, который может сравнить два ключа сортировки для определения относительного порядка двух элементов в наборе.|
|[`key_type`](#key_type)|Тип, описывающий объект, сохраненный как элемент набора в смысле его возможностей, присущих ключу сортировки.|
|[`pointer`](#pointer)|Тип, предоставляющий указатель на элемент в наборе.|
|[`reference`](#reference)|Тип, предоставляющий ссылку на элемент, хранящийся в наборе.|
|[`reverse_iterator`](#reverse_iterator)|Тип, предоставляющий двунаправленный итератор, который может считывать или изменять элемент в обращенном наборе.|
|[`size_type`](#size_type)|Тип целого числа без знака, который может представлять число элементов в наборе.|
|[`value_compare`](#value_compare)|Тип, предоставляющий объект функции, который может сравнить два элемента, чтобы определить их относительный порядок в наборе.|
|[`value_type`](#value_type)|Тип, описывающий объект, сохраненный как элемент набора в смысле его возможностей, присущих значению.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[`begin`](#begin)|Возвращает итератор, обращающийся к первому элементу в `set`.|
|[`cbegin`](#cbegin)|Возвращает итератор const, обращающийся к первому элементу в `set`.|
|[`cend`](#cend)|Возвращает итератор const, который обращается к месту, следующему за последним элементом в `set`.|
|[`clear`](#clear)|Стирает все элементы в `set`.|
|[`contains`](#contains)<sup>C++ 20</sup>|Проверьте, существует ли элемент с указанным ключом в `set` .|
|[`count`](#count)|Возвращает число элементов в контейнере `set`, ключи которых соответствуют ключу, заданному параметром.|
|[`crbegin`](#rbegin)|Возвращает итератор const, который обращается к первому элементу в обращенном контейнере `set`.|
|[`crend`](#rend)|Возвращает итератор const, который обращается к месту, следующему за последним элементом в обращенном контейнере `set`.|
|[`emplace`](#emplace)|Вставляет созданный на месте элемент в `set`.|
|[`emplace_hint`](#emplace_hint)|Вставляет созданный на месте элемент в `set` с подсказкой о размещении.|
|[`empty`](#empty)|Проверяет, пуст ли `set`.|
|[`end`](#end)|Возвращает итератор, который обращается к месту, следующему за последним элементом в контейнере `set`.|
|[`equal_range`](#equal_range)|Возвращает пару итераторов соответственно на первый элемент в `set` с ключом, который больше, чем указанный ключ, и на первый элемент в `set` с ключом, который больше или равен данному ключу.|
|[`erase`](#erase)|Удаляет элемент или диапазон элементов в наборе с заданных позиций или удаляет элементы, соответствующие заданному ключу.|
|[`find`](#find)|Возвращает итератор, адресующий расположение элемента в наборе `set` с ключом, эквивалентным указанному ключу.|
|[`get_allocator`](#get_allocator)|Возвращает копию объекта `allocator`, который используется для создания контейнера `set`.|
|[`insert`](#insert)|Вставляет элемент или диапазон элементов в `set`.|
|[`key_comp`](#key_comp)|Извлекает копию объекта сравнения, который используется для упорядочивания ключей в контейнере `set`.|
|[`lower_bound`](#lower_bound)|Возвращает итератор, указывающий на первый элемент в наборе с ключом, который больше или равен указанному ключу.|
|[`max_size`](#max_size)|Возвращает максимальную длину `set`.|
|[`rbegin`](#rbegin)|Возвращает итератор, который обращается к первому элементу в обращенном контейнере `set`.|
|[`rend`](#rend)|Возвращает итератор, который обращается к месту, следующему за последним элементом в обращенном контейнере `set`.|
|[`size`](#size)|Возвращает количество элементов в контейнере `set`.|
|[`swap`](#swap)|Выполняет обмен элементами между двумя объектами `set`.|
|[`upper_bound`](#upper_bound)|Возвращает итератор, указывающий на первый элемент в `set` с ключом, который больше указанного ключа.|
|[`value_comp`](#value_comp)|Извлекает копию объекта сравнения, который используется для упорядочивания значений элементов в наборе `set`.|

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[`operator=`](#op_eq)|Заменяет элементы набора копией другого набора.|

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

Тип, представляющий класс распределителя для объекта-набора.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Замечания

`allocator_type` является синонимом для параметра-шаблона [`Allocator`](../standard-library/set-class.md) .

Возвращает объект-функцию, которую мультинабор использует для упорядочивания своих элементов, который является параметром-шаблоном `Allocator`.

Дополнительные сведения о см `Allocator` . в подразделе "Примечания" статьи о [ `set` классе](../standard-library/set-class.md) .

### <a name="example"></a>Пример

Пример использования см. в примере для [`get_allocator`](#get_allocator) `allocator_type` .

## <a name="begin"></a><a name="begin"></a> `begin`

Возвращает итератор, обращающийся к первому элементу в наборе.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Возвращаемое значение

Двунаправленный итератор, адресующий первый элемент в наборе или положение после пустого набора.

### <a name="remarks"></a>Замечания

Если возвращаемое значение `begin` присваивается `const_iterator` , то элементы в объекте набора нельзя изменить. Если возвращаемое значение `begin` присваивается `iterator` , то элементы в объекте набора могут быть изменены.

### <a name="example"></a>Пример

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

Возвращает **`const`** итератор, который обращается к первому элементу в диапазоне.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор двунаправленного доступа, указывающий на первый элемент диапазона, или расположение непосредственно за концом пустого диапазона (для пустого диапазона `cbegin() == cend()` ).

### <a name="remarks"></a>Замечания

С возвращаемым значением `cbegin` элементы в диапазоне нельзя изменять.

Эту функцию-член можно использовать вместо функции-члена `begin()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `begin()` и `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> `cend`

Возвращает **`const`** итератор, который обращается к расположению сразу за последним элементом в диапазоне.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор двунаправленного доступа, указывающий на сразу за концом диапазона.

### <a name="remarks"></a>Замечания

`cend` используется для проверки того, прошел ли итератор конец диапазона.

Эту функцию-член можно использовать вместо функции-члена `end()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `end()` и `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Значение, возвращаемое, `cend` не должно быть разыменовано.

## <a name="clear"></a><a name="clear"></a> `clear`

Стирает все элементы в наборе.

```cpp
void clear();
```

### <a name="example"></a>Пример

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать **`const`** элемент в наборе.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Замечания

Тип `const_iterator` нельзя использовать для изменения значения элемента.

### <a name="example"></a>Пример

Пример использования см. в примере для [`begin`](#begin) `const_iterator` .

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

Тип, предоставляющий указатель на **`const`** элемент в наборе.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Замечания

Тип `const_pointer` нельзя использовать для изменения значения элемента.

В большинстве случаев [`const_iterator`](#const_iterator) для доступа к элементам в объекте константного набора следует использовать.

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в наборе для чтения и выполнения **`const`** операций.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>Пример

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference can't be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать любой **`const`** элемент в наборе.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Замечания

Тип `const_reverse_iterator` не может изменять значение элемента и используется для прохода по набору в обратную.

### <a name="example"></a>Пример

См [`rend`](#rend) . Пример объявления и использования `const_reverse_iterator` .

## <a name="contains"></a><a name="contains"></a> `contains`

Проверьте, существует ли элемент с указанным ключом в `set` .

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

`true` значение, если элемент найден в `set` ; `false` в противном случае —.

### <a name="remarks"></a>Замечания

`contains()` Новое в C++ 20. Чтобы использовать его, укажите [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) параметр компилятора.

`template<class K> bool contains(const K& key) const` принимает участие в разрешении перегрузки только в `key_compare` том случае, если является прозрачным. Дополнительные сведения см. [в разделе разнородный Уточняющий запрос в ассоциативных контейнерах](./stl-containers.md#heterogeneous-lookup-in-associative-containers-c14) .

### <a name="example"></a>Пример

```cpp
// Requires /std:c++latest
#include <set>
#include <iostream>

int main()
{
    std::set<int> theSet = {1, 2};

    std::cout << std::boolalpha; // so booleans show as 'true' or 'false'
    std::cout << theSet.contains(2) << '\n';
    std::cout << theSet.contains(3) << '\n';

    return 0;
}
```

```Output
true
false
```

## <a name="count"></a><a name="count"></a> `count`

Возвращает число элементов в наборе, ключи которых соответствуют ключу, заданному параметром.

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Ключ для сравнения с ключами элементов набора.

### <a name="return-value"></a>Возвращаемое значение

1, если набор содержит элемент, ключ сортировки которого совпадает с ключом параметра. 0, если набор не содержит элемент с совпадающим ключом.

### <a name="remarks"></a>Замечания

Функция-член возвращает число элементов в следующем диапазоне:

\[ lower_bound ( *`key`* ), upper_bound ( *`key`* )).

### <a name="example"></a>Пример

В следующем примере демонстрируется использование `set::count` функции члена.

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

Возвращает итератор const, который обращается к первому элементу в обращенном наборе.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный обратный двунаправленный итератор, адресующий первый элемент в обратном наборе или элемент, который был последним элементом в наборе до изменения его порядка на противоположный.

### <a name="remarks"></a>Замечания

`crbegin` используется с обратным набором так же, как [`begin`](#begin) используется с набором.

При возвращении значения `crbegin` объект набора нельзя изменить.

### <a name="example"></a>Пример

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a><a name="crend"></a> `crend`

Возвращает итератор const, который обращается к месту, следующему за последним элементом в обращенном наборе.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный обратный двунаправленный итератор, адресующий расположение после последнего элемента в обратном наборе (расположение перед первым элементом в наборе до изменения его порядка на обратный).

### <a name="remarks"></a>Замечания

`crend` используется с обратным набором так же, как [`end`](#end) используется с набором.

При возвращении значения `crend` объект набора нельзя изменить. Значение, возвращаемое, `crend` не должно быть разыменовано.

`crend` используется, чтобы проверить, достиг ли обратный итератор конца набора.

### <a name="example"></a>Пример

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

Тип целого числа со знаком, пригодный для использования в качестве представления количества элементов в наборе в диапазоне между элементами, на которые указывают итераторы.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Замечания

`difference_type` — тип, возвращаемый при вычитании или приращении через итераторы контейнера. `difference_type` обычно используется для представления количества элементов в диапазоне *[ first,  last)* между итераторами `first` и `last`, включая элемент, на который указывает `first`, и диапазон элементов до элемента, на который указывает `last`, но не включая его.

Несмотря на то, `difference_type` что доступен для всех итераторов, удовлетворяющих требованиям итератора ввода, который включает класс двунаправленных итераторов, поддерживаемых обратимыми контейнерами, такими как набор, вычитание между итераторами поддерживается только итераторами произвольного доступа, предоставляемыми контейнером произвольного доступа, таким как Vector.

### <a name="example"></a>Пример

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there's at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a><a name="emplace"></a> `emplace`

Вставляет элемент, созданный на месте (операции копирования или перемещения не выполняются).

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Аргументы, передаваемые для создания элемента для вставки в набор, кроме случаев, когда сопоставление уже содержит элемент, значение которого правильным образом упорядочено.

### <a name="return-value"></a>Возвращаемое значение

Объект, [`pair`](../standard-library/pair-structure.md) логический компонент которого возвращает значение true, если была произведена вставка, и значение false, если в карте уже содержится элемент, значение которого было эквивалентно значению в упорядочении. Компонент итератора пары возвращаемых значений возвращает адрес, где был вставлен новый элемент (если компонент bool имеет значение true) или где уже находился элемент (если компонент bool имеет значение false).

### <a name="remarks"></a>Замечания

Эта функция не делает недействительными никакие итераторы или ссылки.

Во время назначения места при возникновении исключения состояние контейнера не изменяется.

### <a name="example"></a>Пример

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
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
Аргументы, передаваемые для создания элемента, который будет вставлен в набор, кроме ситуации, когда набор уже содержит этот элемент или, в более общем случае, кроме ситуации, когда набор уже содержит элемент, ключ которого правильно упорядочен.

*`where`*\
Место начала поиска правильной точки вставки. (Если эта точка непосредственно предшествует *`where`* , то вставка может выполняться в периодической константе вместо логарифмического времени.)

### <a name="return-value"></a>Возвращаемое значение

Итератор, указывающий на вновь вставленный элемент.

Если не удалось вставить элемент, так как он уже существует, возвращается итератор на существующий элемент.

### <a name="remarks"></a>Замечания

Эта функция не делает недействительными никакие итераторы или ссылки.

Во время назначения места при возникновении исключения состояние контейнера не изменяется.

### <a name="example"></a>Пример

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a><a name="empty"></a> `empty`

Проверяет, пуст ли набор.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если набор пуст; **`false`** значение, если набор не пуст.

### <a name="example"></a>Пример

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a><a name="end"></a> `end`

Возврат итератора после конца.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Возвращаемое значение

Итератор после конца. Если набор пуст, то `set::end() == set::begin()`.

### <a name="remarks"></a>Замечания

**`end`** используется для проверки, прошел ли итератор конец своего набора.

Значение, возвращаемое, **`end`** не должно быть разыменовано.

Пример кода см. в разделе [`set::find`](#find) .

## <a name="equal_range"></a><a name="equal_range"></a> `equal_range`

Возвращает пару итераторов соответственно на первый элемент в наборе с ключом, который не меньше, чем указанный ключ, и на первый элемент в наборе с ключом, который больше данного ключа.

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>Параметры

*`key`*\
Ключ-аргумент, который будет сравниваться с ключом сортировки элемента из набора, в котором выполняется поиск.

### <a name="return-value"></a>Возвращаемое значение

Пара итераторов, первый из которых является ключом, [`lower_bound`](#lower_bound) а второй — [`upper_bound`](#upper_bound) ключом.

Для доступа к первому итератору пары `pr`, возвращаемой функцией-членом, нужно использовать `pr`. во- **первых**, и для разыменования итератора нижней границы используйте \* ( `pr` . **первый**). Для доступа ко второму итератору пары `pr`, возвращаемой функцией-членом, нужно использовать `pr`. **во-вторых**, а для разыменования итератора верхней границы используйте \* ( `pr` . **второй**).

### <a name="example"></a>Пример

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a><a name="erase"></a> `erase`

Удаляет элемент или диапазон элементов в наборе с заданных позиций или удаляет элементы, соответствующие заданному ключу.

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

Для первых двух функций-членов это двунаправленный итератор, обозначающий первый элемент, остающийся после любых удаленных элементов, или элемент в конце набора, если таких элементов нет.

Третья функция-член возвращает количество элементов, которые были удалены из набора.

### <a name="example"></a>Пример

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a><a name="find"></a> `find`

Возвращает итератор, ссылающийся на элемент в наборе, ключ которого эквивалентен заданному ключу.

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>Параметры

*`key`*\
Значение ключа, с которым сравнивается ключ сортировки элемента из набора, по которому выполняется поиск.

### <a name="return-value"></a>Возвращаемое значение

Итератор, ссылающийся на расположение элемента с указанным ключом или на расположение элемента после последнего элемента в наборе (`set::end()`), если для ключа не найдено совпадений.

### <a name="remarks"></a>Замечания

Функция-член возвращает итератор, который ссылается на элемент в наборе, ключ которого эквивалентен *ключу* аргумента в бинарном предикате, который вызывает упорядочивание на основе отношения сравнения "меньше".

Если возвращаемое значение `find` присваивается `const_iterator` , то объект набора нельзя изменить. Если возвращаемое значение `find` присваивается `iterator` , то объект набора можно изменить.

### <a name="example"></a>Пример

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
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
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

Возвращает копию объекта-распределителя, использованного для создания набора.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Распределитель, использующийся набор для управления памятью, который является параметром-шаблоном `Allocator`.

Дополнительные сведения о см `Allocator` . в подразделе "Примечания" статьи о [ `set` классе](../standard-library/set-class.md) .

### <a name="remarks"></a>Замечания

Распределители для класса набора определяют, как этот класс управляет хранилищем. Для большинства задач программирования достаточно иметь распределители по умолчанию, поставляемые вместе с классами контейнеров стандартной библиотеки C++. Написание и использование собственного класса распределителя требует расширенных навыков работы с C++.

### <a name="example"></a>Пример

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a><a name="insert"></a> Вставляет

Вставляет элемент или диапазон элементов в набор.

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
Значение элемента, вставляемого в набор, если оно уже не содержит элемент, значение которого эквивалентно упорядочено.

*`Where`*\
Место начала поиска правильной точки вставки. (Если точка непосредственно перед *точкой, то* Вставка может выполняться в периодической константе вместо логарифмического времени.)

*`ValTy`*\
Параметр шаблона, указывающий тип аргумента, который может использоваться в наборе для создания элемента [`value_type`](../standard-library/map-class.md#value_type) , и функция идеально пересылает *Val* в качестве аргумента.

*`First`*\
Позиция первого элемента, который следует скопировать.

*`Last`*\
Позиция непосредственно перед последним элементом, который следует скопировать.

*`InputIterator`*\
Аргумент функции-шаблона, соответствующий требованиям [итератора ввода](../standard-library/input-iterator-tag-struct.md) , указывающего на элементы типа, которые могут использоваться для построения [`value_type`](../standard-library/map-class.md#value_type) объектов.

*`IList`*\
Объект, [`initializer_list`](../standard-library/initializer-list.md) из которого копируются элементы.

### <a name="return-value"></a>Возвращаемое значение

Одноэлементные функции-члены (1) и (2) возвращают объект, [`pair`](../standard-library/pair-structure.md) **`bool`** компонент которого имеет значение true, если была произведена вставка, и значение false, если набор уже содержал элемент эквивалентного значения в упорядочении. Компонент итератора пары "возвращаемое значение" указывает на вновь вставленный элемент, если **`bool`** компонент имеет значение true, или на существующий элемент, если **`bool`** компонент имеет значение false.

Одноэлеметные функции-члены с подсказкой (3) и (4) возвращают итератор, который указывает на позицию, где новый элемент был вставлен, или, если элемент с эквивалентным ключом уже существует, указывает на существующий элемент.

### <a name="remarks"></a>Замечания

Эта функция не делает никакие итераторы, указатели или ссылки недействительными.

При вставке всего одного элемента при возникновении исключения состояние контейнера не изменяется. Если во время вставки нескольких элементов вызывается исключение, контейнер остается в неопределенном, но допустимом состоянии.

Чтобы получить доступ к компоненту итератора `pair` `pr` , возвращаемому функциями-членами с одним элементом, используйте оператор `pr.first` ; для разыменования итератора в возвращенной паре используйте `*pr.first` , предоставив элемент. Чтобы получить доступ к **`bool`** компоненту, используйте `pr.second` . См. пример кода далее в этой статье.

[`value_type`](../standard-library/map-class.md#value_type)Контейнером является typedef, принадлежащий контейнеру, а для набора `set<V>::value_type` — тип `const V` .

Функция-член Range (5) вставляет последовательность значений элементов в набор, соответствующий каждому элементу, адресованному итератором в диапазоне `[First, Last)` , поэтому `Last` не вставляется. Контейнер функции-члена `end()` ссылается на позицию сразу после последнего элемента в контейнере. Например, оператор `s.insert(v.begin(), v.end());` пытается вставить все элементы `v` в `s`. Вставляются только элементы с уникальными значениями в диапазоне. Повторяющиеся значения игнорируются. Чтобы увидеть, какие элементы отклонены, используйте одноэлементные версии `insert`.

Функция-член списка инициализаторов (6) использует [`initializer_list`](../standard-library/initializer-list.md) для копирования элементов в набор.

Для вставки элемента, созданного на месте (т. е. не выполняются операции копирования или перемещения), [`set::emplace`](#emplace) см [`set::emplace_hint`](#emplace_hint) . и.

### <a name="example"></a>Пример

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

Тип, предоставляющий константный [двунаправленный итератор](../standard-library/bidirectional-iterator-tag-struct.md), который может читать любой элемент в наборе.

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>Пример

См [`begin`](#begin) . Пример объявления и использования `iterator` .

## <a name="key_comp"></a><a name="key_comp"></a> `key_comp`

Извлекает копию объекта сравнения, который используется для упорядочивания ключей в наборе.

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает объект-функцию, которую набор использует для упорядочивания своих элементов, что является параметром-шаблоном `Traits`.

Дополнительные сведения о `Traits` см. в разделе о [ `set` классе](../standard-library/set-class.md) .

### <a name="remarks"></a>Замечания

Сохраненный объект определяет функцию-член:

**bool-оператор ()**(**&const** `_xVal` , **&ключ** const `_yVal` );

возвращающий значение, **`true`** Если `_xVal` `_yVal` в порядке сортировки предшествует и не равны.

[`key_compare`](#key_compare)И [`value_compare`](#value_compare) являются синонимами для параметра шаблона `Traits` . Оба типа предоставляются для классов наборов и мультинаборов, где они идентичны, для совместимости с классами Map и multimap, где они отличаются.

### <a name="example"></a>Пример

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a><a name="key_compare"></a> `key_compare`

Тип, предоставляющий объект функции, который может сравнить два ключа сортировки для определения относительного порядка двух элементов в наборе.

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Замечания

`key_compare` является синонимом для параметра-шаблона `Traits`.

Дополнительные сведения о `Traits` см. в разделе о [ `set` классе](../standard-library/set-class.md) .

`key_compare`И [`value_compare`](#value_compare) являются синонимами для параметра шаблона `Traits` . Оба типа предоставляются для классов наборов и мультинаборов, где они идентичны, для совместимости с классами Map и multimap, где они отличаются.

### <a name="example"></a>Пример

[`key_comp`](#key_comp)Пример объявления и использования см. в примере для `key_compare` .

## <a name="key_type"></a><a name="key_type"></a> `key_type`

Тип, описывающий объект, сохраненный как элемент набора в смысле его возможностей, присущих ключу сортировки.

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Замечания

`key_type` является синонимом для параметра-шаблона `Key`.

Дополнительные сведения о см `Key` . в подразделе "Примечания" статьи о [ `set` классе](../standard-library/set-class.md) .

`key_type`И [`value_type`](#value_type) являются синонимами для параметра шаблона `Key` . Оба типа предоставляются для классов наборов и мультинаборов, где они идентичны, для совместимости с классами Map и multimap, где они отличаются.

### <a name="example"></a>Пример

[`value_type`](#value_type)Пример объявления и использования см. в примере для `key_type` .

## <a name="lower_bound"></a><a name="lower_bound"></a> `lower_bound`

Возвращает итератор, указывающий на первый элемент в наборе с ключом, который больше или равен указанному ключу.

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>Параметры

*`key`*\
Ключ-аргумент, который будет сравниваться с ключом сортировки элемента из набора, в котором выполняется поиск.

### <a name="return-value"></a>Возвращаемое значение

Итератор или `const_iterator`, который адресует положение элемента в наборе с ключом, который равен ключу-аргументу или больше него, либо адресует положение после последнего элемента в наборе, если соответствие для ключа не найдено.

### <a name="example"></a>Пример

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a><a name="max_size"></a> `max_size`

Возвращает максимальную длину набора.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Максимально возможная длина набора.

### <a name="example"></a>Пример

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

Заменяет элементы этого `set` элементами из другого `set`.

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
`set`, предоставляющий новые элементы для назначения `set`.

### <a name="remarks"></a>Замечания

Первая версия `operator=` использует [ссылку lvalue](../cpp/lvalue-reference-declarator-amp.md) для *`right`* , чтобы скопировать элементы из *`right`* в `set` .

Вторая версия использует [ссылку rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) для right. Он перемещает элементы из *`right`* в `set` .

Все элементы в этом `set` до выполнения функции оператора отбрасываются.

### <a name="example"></a>Пример

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
   }
```

## <a name="pointer"></a><a name="pointer"></a> `pointer`

Тип, предоставляющий указатель на элемент в наборе.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Замечания

Тип **`pointer`** можно использовать для изменения значения элемента.

В большинстве случаев [`iterator`](#iterator) для доступа к элементам в объекте набора следует использовать.

## <a name="rbegin"></a><a name="rbegin"></a> `rbegin`

Возвращает итератор, который обращается к первому элементу в обращенном наборе.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный двунаправленный итератор, адресующий первый элемент в обратном наборе или элемент, который был последним элементом в наборе до изменения его порядка на противоположный.

### <a name="remarks"></a>Замечания

`rbegin` используется с обратным набором так же, как [`begin`](#begin) используется с набором.

Если возвращаемое значение `rbegin` присваивается `const_reverse_iterator` , то объект набора нельзя изменить. Если возвращенное значение `rbegin` назначается `reverse_iterator`, то объект-набор можно изменить.

`rbegin` можно использовать для последовательного прохождения по списку в обратную сторону.

### <a name="example"></a>Пример

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a><a name="reference"></a> `reference`

Тип, предоставляющий ссылку на элемент, хранящийся в наборе.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>Пример

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a><a name="rend"></a> `rend`

Возвращает итератор, который обращается к месту, следующему за последним элементом в обращенном наборе.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный двунаправленный итератор, адресующий расположение после последнего элемента в обратном наборе (расположение перед первым элементом в наборе до изменения его порядка на обратный).

### <a name="remarks"></a>Замечания

`rend` используется с обратным набором так же, как [`end`](#end) используется с набором.

Если возвращаемое значение `rend` присваивается `const_reverse_iterator` , то объект набора нельзя изменить. Если возвращенное значение `rend` назначается `reverse_iterator`, то объект-набор можно изменить. Значение, возвращаемое, `rend` не должно быть разыменовано.

`rend` используется, чтобы проверить, достиг ли обратный итератор конца набора.

### <a name="example"></a>Пример

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

Тип, предоставляющий двунаправленный итератор, который может считывать или изменять элемент в обращенном наборе.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Замечания

Тип `reverse_iterator` используется для прохода по набору в обратную.

### <a name="example"></a>Пример

[`rbegin`](#rbegin)Пример объявления и использования см. в примере для `reverse_iterator` .

## <a name="set"></a><a name="set"></a> `set`

Создает набор, который является пустым или копией части или целого другого набора.

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>Параметры

*`Al`*\
Класс распределителя хранилища, используемый для этого объекта Set, который по умолчанию имеет значение `Allocator` .

*`Comp`*\
Функция сравнения типа `const Traits` используется для упорядочивания элементов в наборе, который по умолчанию имеет значение `Compare`.

*`Rght`*\
Набор, для которого создаваемый набор станет копией.

*`First`*\
Положение первого элемента в диапазоне копируемых элементов.

*`Last`*\
Положение первого элемента после диапазона копируемых элементов.

*`IList`*\
Объект initializer_list, из которого копируются элементы.

### <a name="remarks"></a>Замечания

Все конструкторы хранят тип объекта распределителя, который управляет хранилищем памяти для набора и затем может быть возвращен путем вызова метода [`get_allocator`](#get_allocator) . Параметр-распределитель часто не указывается в объявлениях класса и в макросах предварительной обработки, используемых для замены альтернативных распределителей.

Все конструкторы инициализируют свои наборы.

Все конструкторы хранят объект функции типа `Traits` , который используется для установления порядка ключей набора и затем может быть возвращен вызовом [`key_comp`](#key_comp) .

Первые три конструктора указывают пустой начальный набор, второй задает тип функции сравнения ( `comp` ), используемой при установлении порядка элементов, а третий явно указывает тип распределителя ( `al` ) для использования. Ключевое слово **`explicit`** подавляет определенные виды автоматического преобразования типов.

Четвертый конструктор указывает копию набора `right`.

Следующие три конструктора используют initializer_list, чтобы указать элементы.

Следующие три конструктора копируют диапазон [ `first` , `last` ) набора с увеличением явной точности при указании типа функции сравнения класса `Traits` и **`Allocator`** .

Восьмой конструктор указывает копию набора путем перемещения `right`.

### <a name="example"></a>Пример

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a><a name="size"></a> `size`

Возвращает количество элементов в наборе.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Текущая длина набора.

### <a name="example"></a>Пример

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

Тип целого числа без знака, который может представлять число элементов в наборе.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>Пример

См. пример [`size`](#size) объявления и использования `size_type`

## <a name="swap"></a><a name="swap"></a> `swap`

Обмен элементами между двумя наборами.

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Набор-аргумент предоставляет элементы для обмена с целевым набором.

### <a name="remarks"></a>Замечания

Функция-член не делает недействительными никакие ссылки, указатели или итераторы, обозначающие элементы в двух наборах, между которыми выполняется обмен элементами.

### <a name="example"></a>Пример

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a><a name="upper_bound"></a> `upper_bound`

Возвращает итератор, указывающий на первый элемент в наборе с ключом, который больше указанного ключа.

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>Параметры

*`key`*\
Ключ-аргумент, который будет сравниваться с ключом сортировки элемента из набора, в котором выполняется поиск.

### <a name="return-value"></a>Возвращаемое значение

Объект `iterator` или `const_iterator` , который обращается к расположению элемента в наборе, который имеет ключ, превышающий ключ, или который обращается к расположению, следующему за последним элементом в наборе, если совпадение для ключа не найдено.

### <a name="example"></a>Пример

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a><a name="value_comp"></a> `value_comp`

Извлекает копию объекта сравнения, который используется для упорядочивания значений элементов в наборе.

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает объект-функцию, которую набор использует для упорядочивания своих элементов, что является параметром-шаблоном `Traits`.

Дополнительные сведения о `Traits` см. в разделе о [ `set` классе](../standard-library/set-class.md) .

### <a name="remarks"></a>Замечания

Сохраненный объект определяет функцию-член:

**логический оператор**(**&константы** `_xVal` , **ключ const&** `_yVal` );

возвращающий значение, **`true`** Если `_xVal` `_yVal` в порядке сортировки предшествует и не равны.

[`value_compare`](#value_compare)И [`key_compare`](#key_compare) являются синонимами для параметра шаблона `Traits` . Оба типа предоставляются для классов наборов и мультинаборов, где они идентичны, для совместимости с классами Map и multimap, где они отличаются.

### <a name="example"></a>Пример

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a><a name="value_compare"></a> `value_compare`

Тип, предоставляющий объект функции, который может сравнить значениях двух элементов, чтобы определить их относительный порядок в наборе.

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Замечания

`value_compare` является синонимом для параметра-шаблона `Traits`.

Дополнительные сведения о `Traits` см. в разделе о [ `set` классе](../standard-library/set-class.md) .

[`key_compare`](#key_compare)И `value_compare` являются синонимами для параметра шаблона `Traits` . Оба типа предоставляются для классов наборов и мультинаборов, где они идентичны, для совместимости с классами Map и multimap, где они отличаются.

### <a name="example"></a>Пример

[`value_comp`](#value_comp)Пример объявления и использования см. в примере для `value_compare` .

## <a name="value_type"></a><a name="value_type"></a> `value_type`

Тип, описывающий объект, который сохранен как элемент набора в смысле его возможностей, присущих значению.

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Замечания

`value_type` является синонимом для параметра-шаблона `Key`.

Дополнительные сведения о см `Key` . в подразделе "Примечания" статьи о [ `set` классе](../standard-library/set-class.md) .

[`key_type`](#key_type)И `value_type` являются синонимами для параметра шаблона `Key` . Оба типа предоставляются для классов наборов и мультинаборов, где они идентичны, для совместимости с классами Map и multimap, где они отличаются.

### <a name="example"></a>Пример

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
