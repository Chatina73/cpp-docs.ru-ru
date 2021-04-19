---
description: Дополнительные сведения о классе List
title: Класс list
ms.date: 11/04/2016
f1_keywords:
- list/std::list
- list/std::list::allocator_type
- list/std::list::const_iterator
- list/std::list::const_pointer
- list/std::list::const_reference
- list/std::list::const_reverse_iterator
- list/std::list::difference_type
- list/std::list::iterator
- list/std::list::pointer
- list/std::list::reference
- list/std::list::reverse_iterator
- list/std::list::size_type
- list/std::list::value_type
- list/std::list::assign
- list/std::list::back
- list/std::list::begin
- list/std::list::cbegin
- list/std::list::cend
- list/std::list::clear
- list/std::list::crbegin
- list/std::list::crend
- list/std::list::emplace
- list/std::list::emplace_back
- list/std::list::emplace_front
- list/std::list::empty
- list/std::list::end
- list/std::list::erase
- list/std::list::front
- list/std::list::get_allocator
- list/std::list::insert
- list/std::list::max_size
- list/std::list::merge
- list/std::list::pop_back
- list/std::list::pop_front
- list/std::list::push_back
- list/std::list::push_front
- list/std::list::rbegin
- list/std::list::remove
- list/std::list::remove_if
- list/std::list::rend
- list/std::list::resize
- list/std::list::reverse
- list/std::list::size
- list/std::list::sort
- list/std::list::splice
- list/std::list::swap
- list/std::list::unique
helpviewer_keywords:
- std::list [C++]
- std::list [C++], allocator_type
- std::list [C++], const_iterator
- std::list [C++], const_pointer
- std::list [C++], const_reference
- std::list [C++], const_reverse_iterator
- std::list [C++], difference_type
- std::list [C++], iterator
- std::list [C++], pointer
- std::list [C++], reference
- std::list [C++], reverse_iterator
- std::list [C++], size_type
- std::list [C++], value_type
- std::list [C++], assign
- std::list [C++], back
- std::list [C++], begin
- std::list [C++], cbegin
- std::list [C++], cend
- std::list [C++], clear
- std::list [C++], crbegin
- std::list [C++], crend
- std::list [C++], emplace
- std::list [C++], emplace_back
- std::list [C++], emplace_front
- std::list [C++], empty
- std::list [C++], end
- std::list [C++], erase
- std::list [C++], front
- std::list [C++], get_allocator
- std::list [C++], insert
- std::list [C++], max_size
- std::list [C++], merge
- std::list [C++], pop_back
- std::list [C++], pop_front
- std::list [C++], push_back
- std::list [C++], push_front
- std::list [C++], rbegin
- std::list [C++], remove
- std::list [C++], remove_if
- std::list [C++], rend
- std::list [C++], resize
- std::list [C++], reverse
- std::list [C++], size
- std::list [C++], sort
- std::list [C++], splice
- std::list [C++], swap
- std::list [C++], unique
ms.assetid: d3707f4a-10fd-444f-b856-f9ca2077c1cd
ms.openlocfilehash: 67334c6e1e2c596c973aa7290c4ea3007de37923
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721437"
---
# <a name="list-class"></a>Класс `list`

Класс списка стандартной библиотеки C++ — это шаблон класса контейнеров последовательностей, который сохраняет свои элементы в линейном упорядочении и позволяет выполнять операции вставки и удаления в любом расположении в последовательности. Последовательность хранится в виде двунаправленного связанного списка элементов, каждый из которых содержит элемент какого-либо типа *`Type`* .

## <a name="syntax"></a>Синтаксис

```cpp
template <class Type, class Allocator= allocator<Type>>
class list
```

### <a name="parameters"></a>Параметры

*`Type`*\
Тип данных элементов, сохраняемых в списке.

*`Allocator`*\
Тип, представляющий сохраненный объект распределителя, содержащий сведения о распределении списка и отмене распределения памяти. Этот аргумент является необязательным, и в качестве значения по умолчанию используется `allocator<Type>`.

## <a name="remarks"></a>Замечания

Выбор типа контейнера должен в общем случае производиться на основе типа поиска и вставки, который требуется приложению. Векторы должны быть предпочитаемыми контейнерами для управления последовательностями, когда важен произвольный доступ к любому элементу, а вставка и удаление элементов требуется лишь в конце последовательности. Производительность контейнера класса двусторонней очереди выше, когда требуется произвольный доступ, а также вставка и удаление элементов и в начале последовательности, и в ее конце.

Функции-члены списка [`merge`](#merge) ,,, [`reverse`](#reverse) и были [`unique`](#unique) [`remove`](#remove) [`remove_if`](#remove_if) оптимизированы для работы с объектами списка и предлагают высокопроизводительную альтернативу их универсальным аналогам.

Перераспределение списка происходит, когда функция-член должна вставить или удалить элементы списка. Во всех таких случаях только итераторы или ссылки, указывающие на удаленные части последовательности, становятся недействительными .

Включите стандартный заголовок стандартной библиотеки C++, `<list>` чтобы определить [`container`](../standard-library/stl-containers.md) список шаблонов классов и несколько вспомогательных шаблонов.

## <a name="members"></a>Члены

### <a name="constructors"></a>Конструкторы

|Имя|Описание|
|-|-|
|[`list`](#list)|Создает список определенного размера, или с элементами определенного значения, или с определенным `allocator`, или в качестве копии какого-либо другого списка.|

### <a name="typedefs"></a>Определения типов

|Имя|Описание|
|-|-|
|[`allocator_type`](#allocator_type)|Тип, представляющий класс `allocator` для объекта списка.|
|[`const_iterator`](#const_iterator)|Тип, предоставляющий двунаправленный итератор, который может читать **`const`** элемент в списке.|
|[`const_pointer`](#const_pointer)|Тип, предоставляющий указатель на **`const`** элемент в списке.|
|[`const_reference`](#const_reference)|Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в списке, для чтения и выполнения **`const`** операций.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Тип, предоставляющий двунаправленный итератор, который может читать любой **`const`** элемент в списке.|
|[`difference_type`](#difference_type)|Тип, предоставляющий разницу между двумя итераторами, ссылающимися на элементы в одном и том же списке.|
|[`iterator`](#iterator)|Тип, предоставляющий двунаправленный итератор, который может читать или изменять любой элемент в списке.|
|[`pointer`](#pointer)|Тип, предоставляющий указатель на элемент в списке.|
|[`reference`](#reference)|Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в списке, для чтения и выполнения **`const`** операций.|
|[`reverse_iterator`](#reverse_iterator)|Тип, предоставляющий двунаправленный итератор, который может читать или изменять любой элемент в обратном списке.|
|[`size_type`](#size_type)|Тип, считающий количество элементов в списке.|
|[`value_type`](#value_type)|Тип, представляющий тип данных, хранящихся в списке.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[`assign`](#assign)|Удаляет элементы из списка и копирует новый набор элементов в список назначения.|
|[`back`](#back)|Возвращает ссылку на последний элемент в списке.|
|[`begin`](#begin)|Возвращает итератор, адресующий первый элемент в списке.|
|[`cbegin`](#cbegin)|Возвращает константный итератор, адресующий первый элемент в списке.|
|[`cend`](#cend)|Возвращает константный итератор, адресующий расположение после последнего элемента в списке.|
|[`clear`](#clear)|Удаляет все элементы списка.|
|[`crbegin`](#crbegin)|Возвращает константный итератор, адресующий первый элемент в обратном списке.|
|[`crend`](#crend)|Возвращает константный итератор, адресующий расположение после последнего элемента в обратном списке.|
|[`emplace`](#emplace)|Вставляет элемент, созданный на месте, в указанное положение в списке.|
|[`emplace_back`](#emplace_back)|Добавляет элемент, созданный на месте, в конец списка.|
|[`emplace_front`](#emplace_front)|Добавляет элемент, созданный на месте, в начало списка.|
|[`empty`](#empty)|Проверяет, пуст ли список.|
|[`end`](#end)|Возвращает итератор, адресующий расположение после последнего элемента в списке.|
|[`erase`](#erase)|Удаляет элемент или диапазон элементов с указанных положений в списке.|
|[`front`](#front)|Возвращает ссылку на первый элемент в списке.|
|[`get_allocator`](#get_allocator)|Возвращает копию объекта объекта `allocator`, использованного для создания списка.|
|[`insert`](#insert)|Вставляет элемент или количество элементов или диапазон элементов в указанное положение в списке.|
|[`max_size`](#max_size)|Возвращает максимальную длину списка.|
|[`merge`](#merge)|Удаляет элементы из списка аргументов, вставляет их в список назначения и сортирует новый объединенный набор элементов по возрастанию или в ином указанном порядке.|
|[`pop_back`](#pop_back)|Удаляет элемент в конце списка.|
|[`pop_front`](#pop_front)|Удаляет элемент в начале списка.|
|[`push_back`](#push_back)|Добавляет элемент в конец списка.|
|[`push_front`](#push_front)|Добавляет элемент в начало списка.|
|[`rbegin`](#rbegin)|Возвращает итератор, адресующий первый элемент в обратном списке.|
|[`remove`](#remove)|Удаляет из списка элементы, совпадающие с заданным значением.|
|[`remove_if`](#remove_if)|Удаляет из списка элементы, для которых выполняется заданный предикат.|
|[`rend`](#rend)|Возвращает итератор, адресующий расположение после последнего элемента в обратном списке.|
|[`resize`](#resize)|Указывает новый размер списка.|
|[`reverse`](#reverse)|Изменяет порядок следования элементов в списке на обратный.|
|[`size`](#size)|Возвращает количество элементов в списке.|
|[`sort`](#sort)|Упорядочивает элементы списка по возрастанию или в другом порядке.|
|[`splice`](#splice)|Удаляет элементы из списка аргументов и вставляет их в список назначения.|
|[`swap`](#swap)|Меняет местами элементы двух списков.|
|[`unique`](#unique)|Удаляет из списка повторяющиеся соседние элементы или соседние элементы, удовлетворяющие условию какого-либо другого двоичного предиката.|

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[`operator=`](#op_eq)|Заменяет элементы списка копией другого списка.|

## <a name="requirements"></a>Требования

**Заголовок**: `<list>`

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

Тип, представляющий класс распределителя для объекта списка.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Замечания

`allocator_type` является синонимом для параметра-шаблона *`Allocator`* .

### <a name="example"></a>Пример

См. пример для [`get_allocator`](#get_allocator) .

## <a name="assign"></a><a name="assign"></a> `assign`

Удаляет элементы из списка и копирует новый набор элементов в список назначения.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign
    initializer_list<Type> IList);

template <class InputIterator>
void assign(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>Параметры

*`First`*\
Положение первого элемента в диапазоне элементов, копируемых из списка аргументов.

*`Last`*\
Положение первого элемента после диапазона элементов, копируемых из списка аргументов.

*`Count`*\
Количество копий элемента, вставляемых в список.

*`Val`*\
Значение элемента, вставляемого в список.

*`IList`*\
Список initializer_list содержит вставляемые элементы.

### <a name="remarks"></a>Замечания

После удаления любых существующих элементов в списке назначения операция назначения либо вставляет указанный диапазон элементов из исходного списка или какого-либо другого списка в список назначения, либо вставляет копии нового элемента указанного значения в список назначения

### <a name="example"></a>Пример

```cpp
// list_assign.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    list<int> c1, c2;
    list<int>::const_iterator cIter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(++c2.begin(), c2.end());
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign(7, 4);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.assign({ 10, 20, 30, 40 });
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 10 20 30c1 = 50 60c1 = 4 4 4 4 4 4 4c1 = 10 20 30 40
```

## <a name="back"></a><a name="back"></a> `back`

Возвращает ссылку на последний элемент в списке.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Возвращаемое значение

Последний элемент списка. Если список пуст, возвращаемое значение не определено.

### <a name="remarks"></a>Замечания

Если возвращаемое значение `back` назначается `const_reference`, то объект списка невозможно изменить. Если возвращаемое значение `back` назначается `reference`, то объект списка изменить нельзя.

При компиляции с помощью, [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) заданного как 1 или 2, возникнет ошибка времени выполнения при попытке доступа к элементу в пустом списке.  Дополнительные сведения см. в разделе [Проверяемые итераторы](../standard-library/checked-iterators.md).

### <a name="example"></a>Пример

```cpp
// list_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 11 );

   int& i = c1.back( );
   const int& ii = c1.front( );

   cout << "The last integer of c1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of c1 is " << ii << endl;
}
```

```Output
The last integer of c1 is 11
The next-to-last integer of c1 is 10
```

## <a name="begin"></a><a name="begin"></a> `begin`

Возвращает итератор, адресующий первый элемент в списке.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Возвращаемое значение

Двунаправленный итератор, адресующий расположение первого элемента в списке или расположение после пустого списка.

### <a name="remarks"></a>Замечания

Если возвращаемое значение `begin` присваивается `const_iterator` , то элементы в объекте списка не могут быть изменены. Если возвращаемое значение `begin` присваивается `iterator` , то элементы в объекте списка можно изменить.

### <a name="example"></a>Пример

```cpp
// list_begin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::const_iterator c1_cIter;

   c1.push_back( 1 );
   c1.push_back( 2 );

   c1_Iter = c1.begin( );
   cout << "The first element of c1 is " << *c1_Iter << endl;

*c1_Iter = 20;
   c1_Iter = c1.begin( );
   cout << "The first element of c1 is now " << *c1_Iter << endl;

   // The following line would be an error because iterator is const
   // *c1_cIter = 200;
}
```

```Output
The first element of c1 is 1
The first element of c1 is now 20
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

Возвращает **`const`** итератор, который обращается к первому элементу в диапазоне.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор двунаправленного доступа, указывающий на первый элемент диапазона, или расположение непосредственно за концом пустого диапазона (для пустого диапазона `cbegin() == cend()` ).

### <a name="remarks"></a>Замечания

Элементы в диапазоне нельзя изменить с помощью возвращаемого значения `cbegin`.

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

Значение, возвращаемое `cend`, не должно быть подвергнуто удалению ссылки.

## <a name="clear"></a><a name="clear"></a> открытым

Удаляет все элементы списка.

```cpp
void clear();
```

### <a name="example"></a>Пример

```cpp
// list_clear.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "The size of the list is initially " << c1.size( ) << endl;
   c1.clear( );
   cout << "The size of list after clearing is " << c1.size( ) << endl;
}
```

```Output
The size of the list is initially 3
The size of list after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать **`const`** элемент в списке.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Замечания

Тип `const_iterator`нельзя использовать для изменения значения элемента.

### <a name="example"></a>Пример

См. пример для [`back`](#back) .

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

Предоставляет указатель на **`const`** элемент в списке.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Замечания

Тип `const_pointer`нельзя использовать для изменения значения элемента.

В большинстве случаев [`iterator`](#iterator) для доступа к элементам в объекте списка следует использовать.

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в списке, для чтения и выполнения **`const`** операций.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Замечания

Тип `const_reference`нельзя использовать для изменения значения элемента.

### <a name="example"></a>Пример

```cpp
// list_const_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   const list <int> c2 = c1;
   const int &i = c2.front( );
   const int &j = c2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error because c2 is const
   // c2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать любой **`const`** элемент в списке.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Замечания

Тип `const_reverse_iterator` не может изменять значение элемента и используется для последовательного прохождения через список в обратную сторону.

### <a name="example"></a>Пример

См. пример для [`rbegin`](#rbegin) .

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

Возвращает константный итератор, адресующий первый элемент в обратном списке.

```cpp
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный обратный двунаправленный итератор, адресующий первый элемент в обратном списке (или адресующий элемент, ранее бывший первым элементом в `list` до изменения его порядка на обратный).

### <a name="remarks"></a>Замечания

`crbegin` используется с обратным списком точно так же, как используется [`list::begin`](#begin) с `list` .

Если возвращаемое значение `crbegin`, то объект списка невозможно изменить. [`list::rbegin`](#rbegin) может использоваться для прохода по списку в обратном порядке.

### <a name="example"></a>Пример

```cpp
// list_crbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_crIter = c1.crbegin( );
   cout << "The last element in the list is " << *c1_crIter << "." << endl;
}
```

```Output
The last element in the list is 30.
```

## <a name="crend"></a><a name="crend"></a> `crend`

Возвращает константный итератор, адресующий расположение после последнего элемента в обратном списке.

```cpp
const_reverse_iterator rend() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный Обратный двунаправленный итератор, который обращается к расположению, следующему за последним элементом в обращении [`list`](../standard-library/list-class.md) (расположении, предшествующем первому элементу в неизмененном порядке `list` ).

### <a name="remarks"></a>Замечания

`crend` используется с обратным списком точно так же, как используется [`list::end`](#end) с `list` .

Если возвращаемое значение `crend`, то объект `list` невозможно изменить.

`crend` используется, чтобы проверить, достиг ли итератор конца `list`.

Значение, возвращаемое `crend`, не должно быть подвергнуто удалению ссылки.

### <a name="example"></a>Пример

```cpp
// list_crend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::const_reverse_iterator c1_crIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_crIter = c1.crend( );
   c1_crIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_crIter << endl;
}
```

```Output
The first element in the list is: 10
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

Тип целого числа со знаком, который можно использовать для представления количества элементов в списке в диапазоне между элементами, на которые указывают итераторы.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Замечания

`difference_type` — тип, возвращаемый при вычитании или приращении через итераторы контейнера. `difference_type` обычно используется для представления количества элементов в диапазоне [`first`, `last`) между итераторами `first` и `last`, включает элемент, на который указывает `first`, и диапазон элементов до элемента (не включая этот элемент), на который указывает `last`.

Обратите внимание, что хотя `difference_type` доступен для всех итераторов, удовлетворяющих требованиям итератора ввода, который включает класс двунаправленных итераторов, поддерживаемых обратимыми контейнерами, такими как Set, вычитание между итераторами поддерживается только итераторами произвольного доступа, предоставляемыми контейнером произвольного доступа, например [ `vector` классом](../standard-library/vector-class.md).

### <a name="example"></a>Пример

```cpp
// list_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <list>
#include <algorithm>

int main( )
{
   using namespace std;

   list <int> c1;
   list <int>::iterator   c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

    list <int>::difference_type df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a><a name="emplace"></a> `emplace`

Вставляет элемент, созданный на месте, в указанное положение в списке.

```cpp
void emplace(iterator Where, Type&& val);
```

### <a name="parameters"></a>Параметры

*`Where`*\
Место в целевом объекте, [`list`](../standard-library/list-class.md) куда вставляется первый элемент.

*`val`*\
Элемент, добавляемый в конец `list`.

### <a name="remarks"></a>Замечания

При создании исключения `list` не изменяется, а исключение создается снова.

### <a name="example"></a>Пример

```cpp
// list_emplace.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace(c2.begin(), move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_back"></a><a name="emplace_back"></a> `emplace_back`

Добавляет элемент, созданный на месте, в конец списка.

```cpp
void emplace_back(Type&& val);
```

### <a name="parameters"></a>Параметры

*`val`*\
Элемент, добавляемый в конец [`list`](../standard-library/list-class.md) .

### <a name="remarks"></a>Замечания

При создании исключения `list` не изменяется, а исключение создается снова.

### <a name="example"></a>Пример

```cpp
// list_emplace_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="emplace_front"></a><a name="emplace_front"></a> `emplace_front`

Добавляет элемент, созданный на месте, в начало списка.

```cpp
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Параметры

*`val`*\
Элемент, добавляемый в начало [`list`](../standard-library/list-class.md) .

### <a name="remarks"></a>Замечания

При создании исключения `list` не изменяется, а исключение создается снова.

### <a name="example"></a>Пример

```cpp
// list_emplace_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <string> c2;
   string str("a");

   c2.emplace_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
Moved first element: a
```

## <a name="empty"></a><a name="empty"></a> `empty`

Проверяет, пуст ли список.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если список пуст; **`false`** значение, если список не пуст.

### <a name="example"></a>Пример

```cpp
// list_empty.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   if ( c1.empty( ) )
      cout << "The list is empty." << endl;
   else
      cout << "The list is not empty." << endl;
}
```

```Output
The list is not empty.
```

## <a name="end"></a><a name="end"></a> `end`

Возвращает итератор, адресующий расположение после последнего элемента в списке.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Возвращаемое значение

Двунаправленный итератор, адресующий расположение после последнего элемента в списке. Если список пуст, то `list::end == list::begin`.

### <a name="remarks"></a>Замечания

`end` используется для проверки того, достиг ли итератор конца своего списка.

### <a name="example"></a>Пример

```cpp
// list_end.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_Iter = c1.end( );
   c1_Iter--;
   cout << "The last integer of c1 is " << *c1_Iter << endl;

   c1_Iter--;
*c1_Iter = 400;
   cout << "The new next-to-last integer of c1 is "
        << *c1_Iter << endl;

   // If a const iterator had been declared instead with the line:
   // list <int>::const_iterator c1_Iter;
   // an error would have resulted when inserting the 400

   cout << "The list is now:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
}
```

```Output
The last integer of c1 is 30
The new next-to-last integer of c1 is 400
The list is now: 10 400 30
```

## <a name="erase"></a><a name="erase"></a> `erase`

Удаляет элемент или диапазон элементов с указанных положений в списке.

```cpp
iterator erase(iterator Where);
iterator erase(iterator first, iterator last);
```

### <a name="parameters"></a>Параметры

*`Where`*\
Положение элемента, удаляемого из списка.

*`first`*\
Положение первого элемента, удаленного из списка.

*`last`*\
Положение после последнего элемента, удаленного из списка.

### <a name="return-value"></a>Возвращаемое значение

Двунаправленный итератор, указывающий на первый элемент, оставшийся после удаленных элементов, или на указатель конца списка, если такого элемента не существует.

### <a name="remarks"></a>Замечания

Перераспределение не происходит, поэтому итераторы и ссылки становятся недействительными только для удаленных элементов.

`erase` никогда не создает исключений.

### <a name="example"></a>Пример

```cpp
// list_erase.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 40 );
   c1.push_back( 50 );
   cout << "The initial list is:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

   c1.erase( c1.begin( ) );
   cout << "After erasing the first element, the list becomes:";
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
   Iter = c1.begin( );
   Iter++;
   c1.erase( Iter, c1.end( ) );
   cout << "After erasing all elements but the first, the list becomes: ";
   for (Iter = c1.begin( ); Iter != c1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
The initial list is: 10 20 30 40 50
After erasing the first element, the list becomes: 20 30 40 50
After erasing all elements but the first, the list becomes:  20
```

## <a name="front"></a><a name="front"></a> `front`

Возвращает ссылку на первый элемент в списке.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Возвращаемое значение

Если список пуст, возвращаемое значение не определено.

### <a name="remarks"></a>Замечания

Если возвращаемое значение `front` назначается `const_reference`, то объект списка невозможно изменить. Если возвращаемое значение `front` назначается `reference`, то объект списка изменить нельзя.

При компиляции с помощью, [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) заданного как 1 или 2, возникнет ошибка времени выполнения при попытке доступа к элементу в пустом списке.  Дополнительные сведения см. в разделе [Проверяемые итераторы](../standard-library/checked-iterators.md).

### <a name="example"></a>Пример

```cpp
// list_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main() {
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );

   int& i = c1.front();
   const int& ii = c1.front();

   cout << "The first integer of c1 is " << i << endl;
   i++;
   cout << "The first integer of c1 is " << ii << endl;
}
```

```Output
The first integer of c1 is 10
The first integer of c1 is 11
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

Возвращает копию объекта объекта распределителя, использованного для создания списка.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Распределитель, используемый списком.

### <a name="remarks"></a>Замечания

Распределители для класса списка определяют, как это класс управляет хранилищем. Распределителей по умолчанию в классах контейнеров стандартной библиотеки C++ достаточно для большинства задач программирования. Написание и использование собственного класса распределителя требует расширенных навыков работы с C++.

### <a name="example"></a>Пример

```cpp
// list_get_allocator.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   list <int> c1;
   list <int, allocator<int> > c2 = list <int, allocator<int> >( allocator<int>( ) );

   // c3 will use the same allocator class as c1
   list <int> c3( c1.get_allocator( ) );

   list<int>::allocator_type xlst = c1.get_allocator( );
   // You can now call functions on the allocator class used by c1
}
```

## <a name="insert"></a><a name="insert"></a> `insert`

Вставляет элемент или количество элементов или диапазон элементов в указанное положение в списке.

```cpp
iterator insert(iterator Where, const Type& Val);
iterator insert(iterator Where, Type&& Val);

void insert(iterator Where, size_type Count, const Type& Val);
iterator insert(iterator Where, initializer_list<Type> IList);

template <class InputIterator>
void insert(iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Параметры

*`Where`*\
Положение в целевом списке, куда вставляется первый элемент.

*`Val`*\
Значение элемента, вставляемого в список.

*`Count`*\
Количество элементов, вставляемых в список.

*`First`*\
Положение первого элемента в диапазоне элементов в копируемом списке аргументов.

*`Last`*\
Положение первого элемента после диапазона элементов в копируемом списке аргументов.

### <a name="return-value"></a>Возвращаемое значение

Две первые функции вставки возвращают итератор, указывающий на положение вставки нового элемента в список.

### <a name="example"></a>Пример

```cpp
// list_class_insert.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    list <int> c1, c2;
    list <int>::iterator Iter;

    c1.push_back(10);
    c1.push_back(20);
    c1.push_back(30);
    c2.push_back(40);
    c2.push_back(50);
    c2.push_back(60);

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    c1.insert(Iter, 100);
    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    Iter = c1.begin();
    Iter++;
    Iter++;
    c1.insert(Iter, 2, 200);

    cout << "c1 =";
    for(auto c : c1)
        cout << " " << c;
    cout << endl;

    c1.insert(++c1.begin(), c2.begin(), --c2.end());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    // initialize a list of strings by moving
    list < string > c3;
    string str("a");

    c3.insert(c3.begin(), move(str));
    cout << "Moved first element: " << c3.front() << endl;

    // Assign with an initializer_list
    list <int> c4{ {1, 2, 3, 4} };
    c4.insert(c4.begin(), { 5, 6, 7, 8 });

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;
}
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

Тип, предоставляющий двунаправленный итератор, который может читать или изменять любой элемент в списке.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Замечания

Тип `iterator` можно использовать для изменения значения элемента.

### <a name="example"></a>Пример

См. пример для [`begin`](#begin) .

## <a name="list"></a><a name="list"></a> `list`

Создает список определенного размера, или с элементами определенного значения, или с определенным распределителем, или в качестве копии какого-либо другого списка или его части.

```cpp
list();
explicit list(const Allocator& Al);
explicit list(size_type Count);
list(size_type Count, const Type& Val);
list(size_type Count, const Type& Val, const Allocator& Al);

list(const list& Right);
list(list&& Right);
list(initializer_list<Type> IList, const Allocator& Al);

template <class InputIterator>
list(InputIterator First, InputIterator Last);

template <class InputIterator>
list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Параметры

*`Al`*\
Класс распределителя для использования с данным объектом.

*`Count`*\
Количество элементов в создаваемом списке.

*`Val`*\
Значение элементов в списке.

*`Right`*\
Список, для которого создаваемый список станет копией.

*`First`*\
Положение первого элемента в диапазоне копируемых элементов.

*`Last`*\
Положение первого элемента после диапазона копируемых элементов.

*`IList`*\
Список initializer_list с элементами, которые необходимо скопировать.

### <a name="remarks"></a>Замечания

Все конструкторы хранят объект распределителя ( *`Al`* ) и инициализируют список.

[`get_allocator`](#get_allocator) Возвращает копию объекта распределителя, используемого для создания списка.

Первые два конструктора указывают пустой начальный список, второй задает тип распределителя ( *`Al`* ) для использования.

Третий конструктор задает повторение указанного числа ( *`Count`* ) элементов значения по умолчанию для класса `Type` .

Четвертый и пятый конструкторы указывают повторение ( *`Count`* ) элементов value *`Val`* .

Шестой конструктор указывает копию списка *`Right`* .

Седьмой конструктор перемещает список *`Right`* .

Восьмой конструктор использует initializer_list, чтобы указать элементы.

Два следующих конструктора копируют диапазон `[First, Last)` списка.

Ни один из конструкторов не выполняет промежуточные перераспределения.

### <a name="example"></a>Пример

```cpp
// list_class_list.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty list c0
    list <int> c0;

    // Create a list c1 with 3 elements of default value 0
    list <int> c1(3);

    // Create a list c2 with 5 elements of value 2
    list <int> c2(5, 2);

    // Create a list c3 with 3 elements of value 1 and with the
    // allocator of list c2
    list <int> c3(3, 1, c2.get_allocator());

    // Create a copy, list c4, of list c2
    list <int> c4(c2);

    // Create a list c5 by copying the range c4[ first,  last)
    list <int>::iterator c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    list <int> c5(c4.begin(), c4_Iter);

    // Create a list c6 by copying the range c4[ first,  last) and with
    // the allocator of list c2
    c4_Iter = c4.begin();
    c4_Iter++;
    c4_Iter++;
    c4_Iter++;
    list <int> c6(c4.begin(), c4_Iter, c2.get_allocator());

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c4 =";
    for (auto c : c4)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;

    cout << "c6 =";
    for (auto c : c6)
        cout << " " << c;
    cout << endl;

    // Move list c6 to list c7
    list <int> c7(move(c6));
    cout << "c7 =";
    for (auto c : c7)
        cout << " " << c;
    cout << endl;

    // Construct with initializer_list
    list<int> c8({ 1, 2, 3, 4 });
    cout << "c8 =";
    for (auto c : c8)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 0 0 0c2 = 2 2 2 2 2c3 = 1 1 1c4 = 2 2 2 2 2c5 = 2 2c6 = 2 2 2c7 = 2 2 2c8 = 1 2 3 4
```

## <a name="max_size"></a><a name="max_size"></a> `max_size`

Возвращает максимальную длину списка.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Максимально возможная длина списка.

### <a name="example"></a>Пример

```cpp
// list_max_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   i = c1.max_size( );
   cout << "Maximum possible length of the list is " << i << "." << endl;
}
```

## <a name="merge"></a><a name="merge"></a> `merge`

Удаляет элементы из списка аргументов, вставляет их в список назначения и сортирует новый объединенный набор элементов по возрастанию или в ином указанном порядке.

```cpp
void merge(list<Type, Allocator>& right);

template <class Traits>
void merge(list<Type, Allocator>& right, Traits comp);
```

### <a name="parameters"></a>Параметры

*`right`*\
Список аргументов для слияния со списком назначения.

*`comp`*\
Оператор сравнения, использованный для упорядочения элементов списка назначения.

### <a name="remarks"></a>Замечания

Список аргументов *`right`* объединяется с целевым списком.

И список аргументов, и список назначения должны быть упорядочены с использованием того же отношения сравнения, по которому должно быть упорядочена готовая последовательность. По умолчанию для первой функции-члена используется порядок по возрастанию. Вторая функция-член накладывает определяемую пользователем операцию сравнения *`comp`* класса `Traits` .

### <a name="example"></a>Пример

```cpp
// list_merge.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter, c2_Iter, c3_Iter;

   c1.push_back( 3 );
   c1.push_back( 6 );
   c2.push_back( 2 );
   c2.push_back( 4 );
   c3.push_back( 5 );
   c3.push_back( 1 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   cout << "c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   c2.merge( c1 );  // Merge c1 into c2 in (default) ascending order
   c2.sort( greater<int>( ) );
   cout << "After merging c1 with c2 and sorting with >: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   cout << "c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;

   c2.merge( c3, greater<int>( ) );
   cout << "After merging c3 with c2 according to the '>' comparison relation: c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
c1 = 3 6
c2 = 2 4
After merging c1 with c2 and sorting with >: c2 = 6 4 3 2
c3 = 5 1
After merging c3 with c2 according to the '>' comparison relation: c2 = 6 5 4 3 2 1
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

Заменяет элементы списка копией другого списка.

```cpp
list& operator=(const list& right);
list& operator=(list&& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Объект, который [`list`](../standard-library/list-class.md) копируется в `list` .

### <a name="remarks"></a>Замечания

После удаления любых существующих элементов в `list` оператор копирует или перемещает содержимое *`right`* в `list` .

### <a name="example"></a>Пример

```cpp
// list_operator_as.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int> v1, v2, v3;
   list<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

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
   v2 = forward< list<int> >(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> `pointer`

Предоставляет указатель на элемент в списке.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Замечания

Тип `pointer` можно использовать для изменения значения элемента.

В большинстве случаев [`iterator`](#iterator) для доступа к элементам в объекте списка следует использовать.

## <a name="pop_back"></a><a name="pop_back"></a> `pop_back`

Удаляет элемент в конце списка.

```cpp
void pop_back();
```

### <a name="remarks"></a>Замечания

Последний элемент не должен быть пустым. `pop_back` никогда не создает исключений.

### <a name="example"></a>Пример

```cpp
// list_pop_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The last element is: " << c1.back( ) << endl;

   c1.pop_back( );
   cout << "After deleting the element at the end of the list, "
           "the last element is: " << c1.back( ) << endl;
}
```

```Output
The first element is: 1
The last element is: 2
After deleting the element at the end of the list, the last element is: 1
```

## <a name="pop_front"></a><a name="pop_front"></a> `pop_front`

Удаляет элемент в начале списка.

```cpp
void pop_front();
```

### <a name="remarks"></a>Замечания

Первый элемент не должен быть пустым. `pop_front` никогда не создает исключений.

### <a name="example"></a>Пример

```cpp
// list_pop_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   c1.push_back( 2 );
   cout << "The first element is: " << c1.front( ) << endl;
   cout << "The second element is: " << c1.back( ) << endl;

   c1.pop_front( );
   cout << "After deleting the element at the beginning of the list, "
         "the first element is: " << c1.front( ) << endl;
}
```

```Output
The first element is: 1
The second element is: 2
After deleting the element at the beginning of the list, the first element is: 2
```

## <a name="push_back"></a><a name="push_back"></a> `push_back`

Добавляет элемент в конец списка.

```cpp
void push_back(const Type& val);
void push_back(Type&& val);
```

### <a name="parameters"></a>Параметры

*`val`*\
Элемент, добавляемый в конец списка.

### <a name="remarks"></a>Замечания

При создании исключения список не изменяется, а исключение создается снова.

### <a name="example"></a>Пример

```cpp
// list_push_back.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 1 );
   if ( c1.size( ) != 0 )
      cout << "Last element: " << c1.back( ) << endl;

   c1.push_back( 2 );
   if ( c1.size( ) != 0 )
      cout << "New last element: " << c1.back( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_back( move( str ) );
   cout << "Moved first element: " << c2.back( ) << endl;
}
```

```Output
Last element: 1
New last element: 2
Moved first element: a
```

## <a name="push_front"></a><a name="push_front"></a> `push_front`

Добавляет элемент в начало списка.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Параметры

*`val`*\
Элемент, добавляемый в начало списка.

### <a name="remarks"></a>Замечания

При создании исключения список не изменяется, а исключение создается снова.

### <a name="example"></a>Пример

```cpp
// list_push_front.cpp
// compile with: /EHsc
#include <list>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_front( 1 );
   if ( c1.size( ) != 0 )
      cout << "First element: " << c1.front( ) << endl;

   c1.push_front( 2 );
   if ( c1.size( ) != 0 )
      cout << "New first element: " << c1.front( ) << endl;

// move initialize a list of strings
   list <string> c2;
   string str("a");

   c2.push_front( move( str ) );
   cout << "Moved first element: " << c2.front( ) << endl;
}
```

```Output
First element: 1
New first element: 2
Moved first element: a
```

## <a name="rbegin"></a><a name="rbegin"></a> `rbegin`

Возвращает итератор, который адресует первый элемент в обратном списке.

```cpp
const_reverse_iterator rbegin() const;
reverse_iterator rbegin();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный двунаправленный итератор, адресующий первый элемент в обратном списке (или элемент, бывший последним в списке до изменения его порядка на обратный).

### <a name="remarks"></a>Замечания

`rbegin` используется с обратным списком так же, как используется [`begin`](#begin) со списком.

Если возвращаемое значение `rbegin` назначается `const_reverse_iterator`, то объект списка невозможно изменить. Если возвращаемое значение `rbegin` назначается `reverse_iterator`, то объект списка изменить нельзя.

`rbegin` можно использовать для последовательного прохождения по списку в обратную сторону.

### <a name="example"></a>Пример

```cpp
// list_rbegin.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line replaced the line above, *c1_rIter = 40;
   // (below) would be an error
   //list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1_rIter = c1.rbegin( );
   cout << "The last element in the list is " << *c1_rIter << "." << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration through a list in
   // reverse order
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rbegin( );
*c1_rIter = 40;
   cout << "The last element in the list is now " << *c1_rIter << "." << endl;
}
```

```Output
The last element in the list is 30.
The list is: 10 20 30
The reversed list is: 30 20 10
The last element in the list is now 40.
```

## <a name="reference"></a><a name="reference"></a> `reference`

Тип, предоставляющий ссылку на элемент в списке.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Пример

```cpp
// list_ref.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );

   int &i = c1.front( );
   int &j = c1.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="remove"></a><a name="remove"></a> `remove`

Удаляет из списка элементы, совпадающие с заданным значением.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Параметры

*`val`*\
Значение, которое должен иметь элемент для удаления этого элемента из списка.

### <a name="remarks"></a>Замечания

Порядок оставшихся элементов не изменяется.

### <a name="example"></a>Пример

```cpp
// list_remove.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 5 );
   c1.push_back( 100 );
   c1.push_back( 5 );
   c1.push_back( 200 );
   c1.push_back( 5 );
   c1.push_back( 300 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove( 5 );
   cout << "After removing elements with value 5, the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 5 100 5 200 5 300
After removing elements with value 5, the list becomes c2 = 100 200 300
```

## <a name="remove_if"></a><a name="remove_if"></a> `remove_if`

Удаляет из списка элементы, для которых выполняется заданный предикат.

```cpp
template <class Predicate>
void remove_if(Predicate pred)
```

### <a name="parameters"></a>Параметры

*`pred`*\
Унарный предикат, который в случае совпадения с элементом приводит к удалению этого элемента из списка.

### <a name="example"></a>Пример

```cpp
// list_remove_if.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

template <class T> class is_odd : public std::unary_function<T, bool>
{
public:
   bool operator( ) ( T& val )
   {
   return ( val % 2 ) == 1;
   }
};

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 3 );
   c1.push_back( 4 );
   c1.push_back( 5 );
   c1.push_back( 6 );
   c1.push_back( 7 );
   c1.push_back( 8 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.remove_if( is_odd<int>( ) );

   cout << "After removing the odd elements, "
        << "the list becomes c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = 3 4 5 6 7 8
After removing the odd elements, the list becomes c2 = 4 6 8
```

## <a name="rend"></a><a name="rend"></a> `rend`

Возвращает итератор, адресующий расположение после последнего элемента в обратном списке.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный двунаправленный итератор, адресующий расположение после последнего элемента в обратном списке (расположение перед первым элементом в списке до изменения его порядка на обратный).

### <a name="remarks"></a>Замечания

`rend` используется с обратным списком так же, как используется [`end`](#end) со списком.

Если возвращаемое значение `rend` назначается `const_reverse_iterator`, то объект списка невозможно изменить. Если возвращаемое значение `rend` назначается `reverse_iterator`, то объект списка изменить нельзя.

`rend` можно использовать для проверки, достиг ли итератор конца списка.

Значение, возвращаемое `rend`, не должно быть подвергнуто удалению ссылки.

### <a name="example"></a>Пример

```cpp
// list_rend.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;
   list <int>::reverse_iterator c1_rIter;

   // If the following line had replaced the line above, an error would
   // have resulted in the line modifying an element (commented below)
   // because the iterator would have been const
   // list <int>::const_reverse_iterator c1_rIter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1_rIter = c1.rend( );
   c1_rIter --;  // Decrementing a reverse iterator moves it forward in
                 // the list (to point to the first element here)
   cout << "The first element in the list is: " << *c1_rIter << endl;

   cout << "The list is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   // rend can be used to test if an iteration is through all of the
   // elements of a reversed list
   cout << "The reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;

   c1_rIter = c1.rend( );
   c1_rIter--;  // Decrementing the reverse iterator moves it backward
                // in the reversed list (to the last element here)

*c1_rIter = 40;  // This modification of the last element would have
                    // caused an error if a const_reverse iterator had
                    // been declared (as noted above)

   cout << "The modified reversed list is:";
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )
      cout << " " << *c1_rIter;
   cout << endl;
}
```

```Output
The first element in the list is: 10
The list is: 10 20 30
The reversed list is: 30 20 10
The modified reversed list is: 30 20 40
```

## <a name="resize"></a><a name="resize"></a> `resize`

Указывает новый размер списка.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, Type val);
```

### <a name="parameters"></a>Параметры

*`_Newsize`*\
Новый размер списка.

*`val`*\
Значение новых элементов для добавления в список, если новый размер больше исходного. Если значение не задано, новым элементам назначается значение по умолчанию для класса.

### <a name="remarks"></a>Замечания

Если размер списка меньше запрошенного размера, *`_Newsize`* элементы добавляются в список до тех пор, пока не достигнет запрошенного размера.

Если размер списка больше запрошенного размера, то элементы, ближайшие к концу списка, удаляются до тех пор, пока список не достигнет размера *`_Newsize`* .

Если текущий размер списка совпадает с запрошенным, никакие действия не выполняются.

[`size`](#size) отражает текущий размер списка.

### <a name="example"></a>Пример

```cpp
// list_resize.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   c1.resize( 4,40 );
   cout << "The size of c1 is " << c1.size( ) << endl;
   cout << "The value of the last element is " << c1.back( ) << endl;

   c1.resize( 5 );
   cout << "The size of c1 is now " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;

   c1.resize( 2 );
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;
   cout << "The value of the last element is now " << c1.back( ) << endl;
}
```

```Output
The size of c1 is 4
The value of the last element is 40
The size of c1 is now 5
The value of the last element is now 0
The reduced size of c1 is: 2
The value of the last element is now 20
```

## <a name="reverse"></a><a name="reverse"></a> `reverse`

Изменяет порядок следования элементов в списке на обратный.

```cpp
void reverse();
```

### <a name="example"></a>Пример

```cpp
// list_reverse.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 30 );

   cout << "c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.reverse( );
   cout << "Reversed c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
c1 = 10 20 30
Reversed c1 = 30 20 10
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

Тип, предоставляющий двунаправленный итератор, который может читать или изменять любой элемент в обратном списке.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Замечания

Тип `reverse_iterator` используется для последовательного прохождения через список в обратную сторону.

### <a name="example"></a>Пример

См. пример для [`rbegin`](#rbegin) .

## <a name="size"></a><a name="size"></a> `size`

Возвращает количество элементов в списке.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Текущая длина списка.

### <a name="example"></a>Пример

```cpp
// list_size.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::size_type i;

   c1.push_back( 5 );
   i = c1.size( );
   cout << "List length is " << i << "." << endl;

   c1.push_back( 7 );
   i = c1.size( );
   cout << "List length is now " << i << "." << endl;
}
```

```Output
List length is 1.
List length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

Тип, считающий количество элементов в списке.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Пример

См. пример для [`size`](#size) .

## <a name="sort"></a><a name="sort"></a> `sort`

Упорядочивает элементы списка по возрастанию или в другом указанном пользователем порядке.

```cpp
void sort();

template <class Traits>
    void sort(Traits comp);
```

### <a name="parameters"></a>Параметры

*`comp`*\
Оператор сравнения, использованный для упорядочивания последовательных элементов.

### <a name="remarks"></a>Замечания

Первая функция-член по умолчанию помещает элементы в порядке возрастания.

Функция шаблона элемента упорядочивает элементы в соответствии с определяемой пользователем операцией сравнения *`comp`* класса `Traits` .

### <a name="example"></a>Пример

```cpp
// list_sort.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter;

   c1.push_back( 20 );
   c1.push_back( 10 );
   c1.push_back( 30 );

   cout << "Before sorting: c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( );
   cout << "After sorting c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.sort( greater<int>( ) );
   cout << "After sorting with 'greater than' operation, c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
Before sorting: c1 = 20 10 30
After sorting c1 = 10 20 30
After sorting with 'greater than' operation, c1 = 30 20 10
```

## <a name="splice"></a><a name="splice"></a> `splice`

Удаляет элементы из исходного списка и вставляет их в целевой список.

```cpp
// insert the entire source list
void splice(const_iterator Where, list<Type, Allocator>& Source);
void splice(const_iterator Where, list<Type, Allocator>&& Source);

// insert one element of the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator Iter);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator Iter);

// insert a range of elements from the source list
void splice(const_iterator Where, list<Type, Allocator>& Source, const_iterator First, const_iterator Last);
void splice(const_iterator Where, list<Type, Allocator>&& Source, const_iterator First, const_iterator Last);
```

### <a name="parameters"></a>Параметры

*`Where`*\
Позиция в целевом списке, после которого будут вставлены элементы.

*`Source`*\
Исходный список, который необходимо вставить в целевой список.

*`Iter`*\
Элемент, который будет вставлен из исходного списка.

*`First`*\
Первый элемент в диапазоне, который будет вставлен из исходного списка.

*`Last`*\
Первая позиция за пределами диапазона, в которой будут вставлены элементы из исходного списка.

### <a name="remarks"></a>Замечания

Первая пара функций элементов вставляет все элементы из исходного списка в список назначения перед позицией, на которую ссылается, *`Where`* и удаляет все элементы из исходного списка. ( `&Source` не должно быть равно **`this`** .)

Вторая пара функций элементов вставляет элемент, на который ссылается, *`Iter`* перед позицией в конечном списке, на которую ссылается, *`Where`* и удаляет *iter* из исходного списка. (Если `Where == Iter || Where == ++Iter`, изменения не происходят.)

Третья пара функций-членов вставляет диапазон, обозначенный [ `First` , `Last` ), перед элементом в конечном списке, на который ссылается, *`Where`* и удаляет этот диапазон элементов из исходного списка. (Если `&Source == this` значение, диапазон `[First, Last)` не должен включать элемент, на который указывает *`Where`* .)

Если элемент объединения с диапазоном вставляет `N` элементы, а `&Source != this` объект класса [`iterator`](../standard-library/forward-list-class.md#iterator) увеличивается `N` раз.

Во всех случаях итераторы, указатели и ссылки, указывающие на соединенные элементы, остаются действительными и переносятся в целевой контейнер.

### <a name="example"></a>Пример

```cpp
// list_splice.cpp
// compile with: /EHsc /W4
#include <list>
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
    list<int> c1{10,11};
    list<int> c2{20,21,22};
    list<int> c3{30,31};
    list<int> c4{40,41,42,43};

    list<int>::iterator where_iter;
    list<int>::iterator first_iter;
    list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    --last_iter;
    c2.splice(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = 2 elements: (10) (11)c2 = 3 elements: (20) (21) (22)c3 = 2 elements: (30) (31)c4 = 4 elements: (40) (41) (42) (43)After splicing c1 into c2:c1 = 0 elements:c2 = 5 elements: (20) (10) (11) (21) (22)After splicing the first element of c3 into c2:c3 = 1 elements: (31)c2 = 6 elements: (20) (10) (11) (30) (21) (22)After splicing a range of c4 into c2:c4 = 2 elements: (40) (43)c2 = 8 elements: (20) (10) (11) (30) (41) (42) (21) (22)
```

## <a name="swap"></a><a name="swap"></a> `swap`

Меняет местами элементы двух списков.

```cpp
void swap(list<Type, Allocator>& right);
friend void swap(list<Type, Allocator>& left, list<Type, Allocator>& right)
```

### <a name="parameters"></a>Параметры

*`right`*\
Список, предоставляющий элементы для переключения, или список, элементы которого должны быть заменены списками *`left`* .

*`left`*\
Список, элементы которого должны быть заменены списками *`right`* .

### <a name="example"></a>Пример

```cpp
// list_swap.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1, c2, c3;
   list <int>::iterator c1_Iter;

   c1.push_back( 1 );
   c1.push_back( 2 );
   c1.push_back( 3 );
   c2.push_back( 10 );
   c2.push_back( 20 );
   c3.push_back( 100 );

   cout << "The original list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   c1.swap( c2 );

   cout << "After swapping with c2, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   swap( c1,c3 );

   cout << "After swapping with c3, list c1 is:";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;
}
```

```Output
The original list c1 is: 1 2 3
After swapping with c2, list c1 is: 10 20
After swapping with c3, list c1 is: 100
```

## <a name="unique"></a><a name="unique"></a> `unique`

Удаляет из списка повторяющиеся соседние элементы или соседние элементы, удовлетворяющие условию какого-либо другого двоичного предиката.

```cpp
void unique();

template <class BinaryPredicate>
void unique(BinaryPredicate pred);
```

### <a name="parameters"></a>Параметры

*`pred`*\
Двоичный предикат, используемый для сравнения последовательных элементов.

### <a name="remarks"></a>Замечания

Эта функция исходит из того, что список упорядочен, поэтому все повторяющиеся элементы находятся рядом друг с другом. Повторяющиеся элементы, находящиеся не рядом друг с другом, не будут удалены.

Первая функция-член удаляет каждый элемент, равный предшествующему элементу.

Вторая функция – член удаляет каждый элемент, удовлетворяющий функции предиката, *`pred`* по сравнению с предыдущим элементом. Можно использовать любой объект бинарной функции, объявленный в `<functional>` заголовке аргумента, *`pred`* или создать собственный.

### <a name="example"></a>Пример

```cpp
// list_unique.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list <int> c1;
   list <int>::iterator c1_Iter, c2_Iter,c3_Iter;
   not_equal_to<int> mypred;

   c1.push_back( -10 );
   c1.push_back( 10 );
   c1.push_back( 10 );
   c1.push_back( 20 );
   c1.push_back( 20 );
   c1.push_back( -10 );

   cout << "The initial list is c1 =";
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )
      cout << " " << *c1_Iter;
   cout << endl;

   list <int> c2 = c1;
   c2.unique( );
   cout << "After removing successive duplicate elements, c2 =";
   for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )
      cout << " " << *c2_Iter;
   cout << endl;

   list <int> c3 = c2;
   c3.unique( mypred );
   cout << "After removing successive unequal elements, c3 =";
   for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )
      cout << " " << *c3_Iter;
   cout << endl;
}
```

```Output
The initial list is c1 = -10 10 10 20 20 -10
After removing successive duplicate elements, c2 = -10 10 20 -10
After removing successive unequal elements, c3 = -10 -10
```

## <a name="value_type"></a><a name="value_type"></a> `value_type`

Тип, представляющий тип данных, хранящихся в списке.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Замечания

`value_type` является синонимом для параметра-шаблона *`Type`* .

### <a name="example"></a>Пример

```cpp
// list_value_type.cpp
// compile with: /EHsc
#include <list>
#include <iostream>

int main( )
{
   using namespace std;
   list<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```
