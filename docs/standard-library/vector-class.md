---
title: vector - класс
description: Справочник по реализации класса Vector в стандартной библиотеке Microsoft C++.
ms.date: 02/23/2021
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.openlocfilehash: bcc6049c5b1040ea2bf3772a851ed26d40a4c608
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099291"
---
# <a name="vector-class"></a>Класс `vector`

Класс вектора стандартной библиотеки C++ является шаблоном класса для контейнеров последовательности. Вектор хранит элементы заданного типа в линейном упорядочении и обеспечивает быстрый произвольный доступ к любому элементу. Вектор является предпочтительным контейнером для последовательности, когда производительность произвольного доступа имеет уровень "Премиум".

## <a name="syntax"></a>Синтаксис

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>Параметры

*`Type`*\
Тип данных элементов, сохраняемых в векторе.

*`Allocator`*\
Тип, представляющий сохраненный объект распределителя, содержащий сведения о распределении и отмене распределения памяти для вектора. Этот аргумент является необязательным, и значением по умолчанию является `allocator<Type>`.

## <a name="remarks"></a>Комментарии

Для векторов время выполнения вставок и удалений элементов в конце последовательности является постоянной величиной. Время вставки и удаления элементов в середине вектора меняется линейно. Контейнер [ `deque` класса](../standard-library/deque-class.md) выполняется быстрее при вставке и удалении в начале и в конце последовательности. Контейнер [ `list` класса](../standard-library/list-class.md) выполняется быстрее при вставке и удалении в любом месте в последовательности.

Расширение вектора происходит, когда функции-члену требуется увеличить последовательность в объекте вектора сверх его текущей емкости. Другие операции вставки и стирания могут изменять различные адреса хранения внутри последовательности. Во всех таких случаях итераторы или ссылки, указывающие на изменившиеся части последовательности, становятся недействительными. Если расширения не происходит, действительными остаются только итераторы и ссылки перед точкой вставки или удаления.

[ `vector<bool>` Класс](../standard-library/vector-bool-class.md) является полной специализацией вектора шаблона класса для элементов типа **`bool`** . Он имеет распределитель для базового типа, используемого специализацией.

[ `vector<bool>` Ссылочный класс](../standard-library/vector-bool-class.md#reference_class) — это вложенный класс, объекты которого могут предоставлять ссылки на элементы (одиночные биты) внутри `vector<bool>` объекта.

## <a name="members"></a>Члены

### <a name="constructors"></a>Конструкторы

|Имя|Описание|
|-|-|
|[`vector`](#vector)|Создает вектор определенного размера, вектор с элементами определенного значения, вектор с определенным `allocator`, или вектор как копию какого-либо другого вектора.|

### <a name="typedefs"></a>Определения типов

|Имя|Описание|
|-|-|
|`[allocator_type]`(#allocator_type)|Тип, представляющий класс `allocator` для объекта вектора.|
|[`const_iterator`](#const_iterator)|Тип, предоставляющий итератор произвольного доступа, который может считывать **`const`** элемент в векторе.|
|[`const_pointer`](#const_pointer)|Тип, предоставляющий указатель на **`const`** элемент в векторе.|
|[`const_reference`](#const_reference)|Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в векторе. Он используется для чтения и выполнения **`const`** операций.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать любой **`const`** элемент в векторе.|
|[`difference_type`](#difference_type)|Тип, представляющий различие между адресами двух элементов в векторе.|
|[`iterator`](#iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать или изменять любой элемент в векторе.|
|[`pointer`](#pointer)|Тип, предоставляющий указатель на элемент в векторе.|
|[`reference`](#reference)|Тип, предоставляющий ссылку на элемент, хранящийся в векторе.|
|[`reverse_iterator`](#reverse_iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать или изменять любой элемент в обратном векторе.|
|[`size_type`](#size_type)|Тип, считающий количество элементов в векторе.|
|[`value_type`](#value_type)|Тип, представляющий тип данных, хранящихся в векторе.|

### <a name="functions"></a>Функции

|Имя|Описание|
|-|-|
|[`assign`](#assign)|Удаляет вектор и копирует указанные элементы в пустой вектор.|
|[`at`](#at)|Возвращает ссылку на элемент в заданном положении в векторе.|
|[`back`](#back)|Возвращает ссылку на последний элемент вектора.|
|[`begin`](#begin)|Возвращает итератор произвольного доступа, указывающий на первый элемент в векторе.|
|[`capacity`](#capacity)|Возвращает число элементов, которое вектор может содержать без выделения дополнительного пространства.|
|[`cbegin`](#cbegin)|Возвращает постоянный итератор произвольного доступа, указывающий на первый элемент в векторе.|
|[`cend`](#cend)|Возвращает константный итератор произвольного доступа, указывающий на позицию, следующую за концом вектора.|
|[`crbegin`](#crbegin)|Возвращает константный итератор, который указывает на первый элемент в обратном векторе.|
|[`crend`](#crend)|Возвращает константный итератор, который указывает на последний элемент в обратном векторе.|
|[`clear`](#clear)|Очищает элементы вектора.|
|[`data`](#data)|Возвращает указатель на первый элемент в векторе.|
|[`emplace`](#emplace)|Вставляет элемент, созданный на месте, в указанное положение в векторе.|
|[`emplace_back`](#emplace_back)|Добавляет элемент, созданный на месте, в конец вектора.|
|[`empty`](#empty)|Проверяет, пуст ли контейнер вектора.|
|[`end`](#end)|Возвращает итератор произвольного доступа, который указывает на конец вектора.|
|[`erase`](#erase)|Удаляет элемент или диапазон элементов в векторе из заданных позиций.|
|[`front`](#front)|Возвращает ссылку на первый элемент в векторе.|
|[`get_allocator`](#get_allocator)|Возвращает объект классу `allocator`, используемому вектором.|
|[`insert`](#insert)|Вставляет элемент или множество элементов в заданную позиции в вектор.|
|[`max_size`](#max_size)|Возвращает максимальную длину вектора.|
|[`pop_back`](#pop_back)|Удаляет элемент в конце вектора.|
|[`push_back`](#push_back)|Добавляет элемент в конец вектора.|
|[`rbegin`](#rbegin)|Возвращает итератор, указывающий на первый элемент в обратном векторе.|
|[`rend`](#rend)|Возвращает итератор, который указывает на последний элемент в обратном векторе.|
|[`reserve`](#reserve)|Резервирует минимальную длину хранилища для объекта вектора.|
|[`resize`](#resize)|Определяет новый размер вектора.|
|[`shrink_to_fit`](#shrink_to_fit)|Удаляет лишнюю емкость.|
|[`size`](#size)|Возвращает количество элементов в векторе.|
|[`swap`](#swap)|Меняет местами элементы двух векторов.|

### <a name="operators"></a>Операторы

|Имя|Описание|
|-|-|
|[`operator[]`](#op_at)|Возвращает ссылку на элемент вектора в указанной позиции.|
|[`operator=`](#op_eq)|Заменяет элементы вектора копией другого вектора.|

## <a name="allocator_type"></a><a name="allocator_type"></a> `allocator_type`

Тип, представляющий класс распределителя для объекта вектора.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Комментарии

`allocator_type` является синонимом для параметра-шаблона `Allocator`.

### <a name="example"></a>Пример

Пример использования `allocator_type` см. в разделе [get_allocator](#get_allocator).

## <a name="assign"></a><a name="assign"></a> `assign`

Удаляет вектор и копирует указанные элементы в пустой вектор.

```cpp
void assign(size_type count, const Type& value);
void assign(initializer_list<Type> init_list);

template <class InputIterator>
void assign(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>Параметры

*`first`*\
Положение первого элемента в диапазоне копируемых элементов.

*`last`*\
Положение первого элемента за пределами диапазона копируемых элементов.

*`count`*\
Количество копий элемента, вставляемых в вектор.

*`value`*\
Значение элемента, вставляемого в вектор.

*`init_list`*\
Объект initializer_list, содержащий вставляемые элементы.

### <a name="remarks"></a>Комментарии

`assign`Во-первых, удаляет все существующие элементы в векторе. Затем `assign` либо Вставляет указанный диапазон элементов из исходного вектора в вектор, либо вставляет копии нового указанного элемента value в вектор.

### <a name="example"></a>Пример

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}
```

## <a name="at"></a><a name="at"></a> `at`

Возвращает ссылку на элемент в заданном положении в векторе.

```cpp
reference at(size_type position);

const_reference at(size_type position) const;
```

### <a name="parameters"></a>Параметры

*`position`*\
Номер нижнего индекса или позиции элемента, на который включается ссылка в векторе.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на элемент, индекс которого указан в аргументе. Если *`position`* значение больше размера вектора, `at` вызывает исключение.

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `at` присваивается `const_reference` , то объект Vector изменить нельзя. Если возвращаемое значение `at` присвоено `reference`, то объект вектора можно изменить.

### <a name="example"></a>Пример

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a><a name="back"></a> `back`

Возвращает ссылку на последний элемент вектора.

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>Возвращаемое значение

Последний элемент вектора. Если вектор пуст, возвращаемое значение не определено.

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `back` присваивается `const_reference` , то объект Vector изменить нельзя. Если возвращаемое значение `back` присвоено `reference`, то объект вектора можно изменить.

При компиляции с помощью, [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) заданного как 1 или 2, возникает ошибка времени выполнения при попытке получить доступ к элементу в пустом векторе. Дополнительные сведения см. в разделе [проверенные итераторы](../standard-library/checked-iterators.md).

### <a name="example"></a>Пример

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a><a name="begin"></a> `begin`

Возвращает итератор произвольного доступа, указывающий на первый элемент в векторе.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Возвращаемое значение

Итератор произвольного доступа, который указывает на первый элемент в `vector` или на элемент, следующий за пустым `vector`. Всегда сравнивайте значение, возвращаемое с, [`vector::end`](#end) чтобы убедиться, что оно является допустимым.

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `begin` присваивается [`vector::const_iterator`](#const_iterator) , то `vector` объект нельзя изменить. Если возвращаемое значение `begin` присваивается [`vector::iterator`](#iterator) , `vector` объект может быть изменен.

### <a name="example"></a>Пример

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a><a name="capacity"></a> `capacity`

Возвращает число элементов, которое вектор может содержать без выделения дополнительного пространства.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Возвращаемое значение

Текущая длина хранилища, выделенного вектору.

### <a name="remarks"></a>Комментарии

Функция-член [`resize`](#resize) будет более эффективной, если выделить достаточно памяти для ее размещения. Используйте функцию члена, [`reserve`](#reserve) чтобы указать объем выделенной памяти.

### <a name="example"></a>Пример

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a><a name="cbegin"></a> `cbegin`

Возвращает **`const`** итератор, который обращается к первому элементу в диапазоне.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`const`** Итератор произвольного доступа, указывающий на первый элемент диапазона, или расположение непосредственно за концом пустого диапазона (для пустого диапазона `cbegin() == cend()` ).

### <a name="remarks"></a>Комментарии

С возвращаемым значением `cbegin` элементы в диапазоне нельзя изменять.

Эту функцию-член можно использовать вместо функции-члена `begin()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется в с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `begin()` и `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a><a name="cend"></a> `cend`

Возвращает **`const`** итератор после конца, указывающий на элемент, следующий за последним элементом вектора.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Возвращаемое значение

`const`Завершающий итератор для вектора. Он указывает на элемент, следующий за последним элементом вектора. Этот элемент является заполнителем и не должен быть разыменован. Используйте его только для сравнения. Если Vector является пустым, то `vector::cend() == vector::cbegin()` .

### <a name="remarks"></a>Комментарии

`cend` используется для проверки того, прошел ли итератор конец диапазона.

Эту функцию-член можно использовать вместо функции-члена `end()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- **`const`** ) контейнер любого типа, который поддерживает `end()` и `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Значение, возвращаемое, `cend` не должно быть разыменовано. Используйте его только для сравнения.

## <a name="clear"></a><a name="clear"></a> `clear`

Очищает элементы вектора.

```cpp
void clear();
```

### <a name="example"></a>Пример

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a><a name="const_iterator"></a> `const_iterator`

Тип, предоставляющий итератор произвольного доступа, который может считывать **`const`** элемент в векторе.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `const_iterator` нельзя использовать для изменения значения элемента.

### <a name="example"></a>Пример

Пример использования [back](#back) см. в разделе `const_iterator`.

## <a name="const_pointer"></a><a name="const_pointer"></a> `const_pointer`

Тип, предоставляющий указатель на **`const`** элемент в векторе.

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>Комментарии

Тип `const_pointer` нельзя использовать для изменения значения элемента.

Для доступа к элементу вектора обычно используется [iterator](#iterator).

## <a name="const_reference"></a><a name="const_reference"></a> `const_reference`

Тип, предоставляющий ссылку на **`const`** элемент, хранящийся в векторе. Он используется для чтения и выполнения **`const`** операций.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Комментарии

Тип `const_reference` нельзя использовать для изменения значения элемента.

### <a name="example"></a>Пример

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a><a name="const_reverse_iterator"></a> `const_reverse_iterator`

Тип, предоставляющий итератор произвольного доступа, который может читать любой **`const`** элемент в векторе.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `const_reverse_iterator` не может изменять значение элемента и используется для прохода по вектору в обратную.

### <a name="example"></a>Пример

См [`rbegin`](#rbegin) . Пример объявления и использования итератора.

## <a name="crbegin"></a><a name="crbegin"></a> `crbegin`

Возвращает константный итератор, который указывает на первый элемент в обратном векторе.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Константный реверсивный итератор произвольного доступа, обращающийся к первому элементу в обратную [`vector`](../standard-library/vector-class.md) или обращающуюся к последнему элементу в необращенном порядке `vector` .

### <a name="remarks"></a>Комментарии

При возвращении значения `crbegin` `vector` объект не может быть изменен.

### <a name="example"></a>Пример

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a><a name="crend"></a> `crend`

Возвращает обратный реверсивный `const` итератор, указывающий на элемент, следующий за последним элементом в инвертированном векторе.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Возвращаемое значение

`const`Обратный завершающий итератор для инвертированного вектора. Он указывает элемент, следующий за последним элементом в инвертированном векторе, который совпадает с элементом перед первым элементом неинвертированного вектора. Этот элемент является заполнителем и не должен быть разыменован. Используйте его только для сравнения.

### <a name="remarks"></a>Комментарии

`crend` используется с обратным `vector` так же, как используется [`vector::cend`](#cend) с `vector` .

При возвращении значения `crend` (с соответствующим уменьшением) `vector` объект изменить нельзя.

`crend` используется, чтобы проверить, достиг ли итератор конца `vector`.

Значение, возвращаемое, `crend` не должно быть разыменовано. Используйте его только для сравнения.

### <a name="example"></a>Пример

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a><a name="data"></a> `data`

Возвращает указатель на первый элемент в векторе.

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на первый элемент в [`vector`](../standard-library/vector-class.md) или в позицию, где выполняется пустое значение `vector` .

### <a name="example"></a>Пример

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1_ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_ptr = c1.data();
    *c1_ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1_ptr++)
    {
        cout << " " << *c1_ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a><a name="difference_type"></a> `difference_type`

Тип, предоставляющий разницу между двумя итераторами, ссылающимися на элементы в одном и том же векторе.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Комментарии

`difference_type` также можно описать как число элементов между двумя указателями, так как указатель на элемент содержит его адрес.

Для доступа к элементу вектора обычно используется [iterator](#iterator).

### <a name="example"></a>Пример

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

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

Вставляет элемент, созданный на месте, в указанное положение в векторе.

```cpp
template <class... Types>
iterator emplace(
    const_iterator position,
    Types&&... args);
```

### <a name="parameters"></a>Параметры

*`position`*\
Место [`vector`](../standard-library/vector-class.md) вставки первого элемента.

*`args`*\
Аргументы конструктора. Функция определяет перегрузку конструктора, которую нужно вызвать, на основе переданных аргументов.

### <a name="return-value"></a>Возвращаемое значение

Функция возвращают итератор, указывающий на положение вставки нового элемента в `vector`.

### <a name="remarks"></a>Комментарии

Любая операция вставки может быть дорогостоящей, см. раздел [ `vector` класс](../standard-library/vector-class.md) для обсуждения `vector` производительности.

### <a name="example"></a>Пример

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a><a name="emplace_back"></a> `emplace_back`

Добавляет элемент, созданный на месте, в конец вектора.

```cpp
template <class... Types>
void emplace_back(Types&&... args);
```

### <a name="parameters"></a>Параметры

*`args`*\
Аргументы конструктора. Функция определяет перегрузку конструктора, которую нужно вызвать, на основе переданных аргументов.

### <a name="example"></a>Пример

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}
```

## <a name="empty"></a><a name="empty"></a> `empty`

Проверяет, пуст ли вектор.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

**`true`** значение, если вектор пуст; **`false`** значение, если вектор не пуст.

### <a name="example"></a>Пример

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a><a name="end"></a> `end`

Возвращает итератор после конца, указывающий на элемент, следующий за последним элементом вектора.

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>Возвращаемое значение

Завершающий итератор для вектора. Он указывает на элемент, следующий за последним элементом вектора. Этот элемент является заполнителем и не должен быть разыменован. Используйте его только для сравнения. Если Vector является пустым, то `vector::end() == vector::begin()` .

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `end` присваивается переменной типа `const_iterator` , объект Vector изменить нельзя. Если возвращаемое значение `end` присваивается переменной типа `iterator` , то объект Vector можно изменить.

### <a name="example"></a>Пример

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a><a name="erase"></a> `erase`

Удаляет элемент или диапазон элементов в векторе из заданных позиций.

```cpp
iterator erase(
    const_iterator position);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Параметры

*`position`*\
Положение элемента, удаляемого из вектора.

*`first`*\
Положение первого элемента, удаляемого из вектора.

*`last`*\
Положение после последнего элемента, удаляемого из вектора.

### <a name="return-value"></a>Возвращаемое значение

Итератор, указывающий на первый элемент, оставшийся после удаленных элементов, или на указатель конца вектора, если такого элемента не существует.

### <a name="example"></a>Пример

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a><a name="front"></a> `front`

Возвращает ссылку на первый элемент в векторе.

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ссылка на первый элемент в объекте вектора. Если вектор пуст, возвращаемое значение не определено.

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `front` присваивается `const_reference` , то объект Vector изменить нельзя. Если возвращаемое значение `front` присваивается **`reference`** , то объект Vector можно изменить.

При компиляции с помощью, [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) заданного как 1 или 2, возникает ошибка времени выполнения при попытке получить доступ к элементу в пустом векторе. Дополнительные сведения см. в разделе [проверенные итераторы](../standard-library/checked-iterators.md).

### <a name="example"></a>Пример

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a><a name="get_allocator"></a> `get_allocator`

Возвращает копию объекта allocator, используемого для создания вектора.

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Распределитель, используемый вектором.

### <a name="remarks"></a>Комментарии

Распределители для класса вектора определяют, как этот класс управляет хранилищем. Распределителей по умолчанию в классах контейнеров стандартной библиотеки C++ достаточно для большинства задач программирования. Написание и использование собственного класса распределителя является расширенной функцией C++.

### <a name="example"></a>Пример

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a><a name="insert"></a> `insert`

Вставляет элемент или несколько элементов или диапазон элементов в указанную позиции в вектор.

```cpp
iterator insert(
    const_iterator position,
    const Type& value);

iterator insert(
    const_iterator position,
    Type&& value);

void insert(
    const_iterator position,
    size_type count,
    const Type& value);

template <class InputIterator>
void insert(
    const_iterator position,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>Параметры

*`position`*\
Позиция в векторе, куда вставляется первый элемент.

*`value`*\
Значение элемента, вставляемого в вектор.

*`count`*\
Количество элементов, вставляемых в вектор.

*`first`*\
Положение первого элемента в диапазоне копируемых элементов.

*`last`*\
Положение первого элемента после диапазона копируемых элементов.

### <a name="return-value"></a>Возвращаемое значение

Две первые функции `insert` возвращают итератор, указывающий на положение вставки нового элемента в вектор.

### <a name="remarks"></a>Комментарии

В качестве предусловия *`first`* и *`last`* не должны быть итераторами в векторе или поведение не определено. Любая операция вставки может быть дорогостоящей, см. раздел [ `vector` класс](../standard-library/vector-class.md) для обсуждения `vector` производительности.

### <a name="example"></a>Пример

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a><a name="iterator"></a> `iterator`

Тип, предоставляющий итератор произвольного доступа, который может читать или изменять любой элемент в векторе.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Комментарии

Тип **`iterator`** можно использовать для изменения значения элемента.

### <a name="example"></a>Пример

См. пример для [`begin`](#begin) .

## <a name="max_size"></a><a name="max_size"></a> `max_size`

Возвращает максимальную длину вектора.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Максимально возможная длина вектора.

### <a name="example"></a>Пример

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="operator"></a><a name="op_at"></a> `operator[]`

Возвращает ссылку на элемент вектора в указанной позиции.

```cpp
reference operator[](size_type position);

const_reference operator[](size_type position) const;
```

### <a name="parameters"></a>Параметры

*`position`*\
Позиция элемента вектора.

### <a name="return-value"></a>Возвращаемое значение

Если заданная позиция больше или равна размеру контейнера, результат не определен.

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `operator[]` присваивается `const_reference` , то объект Vector изменить нельзя. Если возвращаемое значение `operator[]` присвоено ссылке, то объект вектора можно изменить.

При компиляции с помощью параметра, [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) заданного как 1 или 2, возникает ошибка времени выполнения при попытке доступа к элементу за пределами вектора. Дополнительные сведения см. в разделе [проверенные итераторы](../standard-library/checked-iterators.md).

### <a name="example"></a>Пример

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="operator"></a><a name="op_eq"></a> `operator=`

Заменяет элементы вектора копией другого вектора.

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Объект, который [`vector`](../standard-library/vector-class.md) копируется в `vector` .

### <a name="remarks"></a>Комментарии

После стирания любых существующих элементов в `vector` , `operator=` копирует или перемещает содержимое *`right`* в `vector` .

### <a name="example"></a>Пример

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

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
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a><a name="pointer"></a> `pointer`

Тип, предоставляющий указатель на элемент в векторе.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Комментарии

Тип **`pointer`** можно использовать для изменения значения элемента.

### <a name="example"></a>Пример

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a><a name="pop_back"></a> `pop_back`

Удаляет элемент в конце вектора.

```cpp
void pop_back();
```

### <a name="remarks"></a>Комментарии

Пример кода см. в разделе [vector::push_back()](#push_back).

## <a name="push_back"></a><a name="push_back"></a> `push_back`

Добавляет элемент в конец вектора.

```cpp
void push_back(const T& value);

void push_back(T&& value);
```

### <a name="parameters"></a>Параметры

*`value`*\
Значение, назначаемое элементу, который добавляется в конец вектора.

### <a name="example"></a>Пример

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a><a name="rbegin"></a> `rbegin`

Возвращает итератор, указывающий на первый элемент в обратном векторе.

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Обратный итератор произвольного доступа, указывающий на первый элемент в обратном векторе или на последний элемент в исходном векторе.

### <a name="remarks"></a>Комментарии

Если возвращаемое значение `rbegin` присваивается `const_reverse_iterator` , то объект Vector изменить нельзя. Если возвращаемое значение `rbegin` присвоено `reverse_iterator`, то объект вектора можно изменить.

### <a name="example"></a>Пример

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a><a name="reference"></a> `reference`

Тип, предоставляющий ссылку на элемент, хранящийся в векторе.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>Пример

См [`at`](#at) . Пример использования **`reference`** в классе Vector.

## <a name="rend"></a><a name="rend"></a> `rend`

Возвращает обратный реверсивный итератор, указывающий на элемент, следующий за последним элементом в инвертированном векторе.

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный завершающий итератор для инвертированного вектора. Он указывает элемент, следующий за последним элементом в инвертированном векторе, который совпадает с элементом перед первым элементом неинвертированного вектора. Этот элемент является заполнителем и не должен быть разыменован. Используйте его только для сравнения.

### <a name="remarks"></a>Комментарии

`rend` используется с обратным вектором точно так же, как [`end`](#end) используется с вектором.

Если возвращаемое значение `rend` присваивается `const_reverse_iterator` , то объект Vector изменить нельзя. Если возвращаемое значение `rend` присвоено `reverse_iterator`, то объект вектора можно изменить.

`rend` используется, чтобы проверить, достиг ли обратный итератор конца вектора.

Значение, возвращаемое, `rend` не должно быть разыменовано. Используйте его только для сравнения.

### <a name="example"></a>Пример

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="reserve"></a><a name="reserve"></a> `reserve`

Резервирует минимальную длину хранилища для объекта вектора, при необходимости выделяя пространство.

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>Параметры

*`count`*\
Минимальная длина хранилища, выделяемого для вектора.

### <a name="example"></a>Пример

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a><a name="resize"></a> `resize`

Определяет новый размер вектора.

```cpp
void resize(size_type new_size);
void resize(size_type new_size, Type value);
```

### <a name="parameters"></a>Параметры

*`new_size`*\
Новый размер вектора.

*`value`*\
Значение инициализации новых элементов, добавленных в вектор, если новый размер больше исходного. Если значение опущено, новые объекты используют конструктор по умолчанию.

### <a name="remarks"></a>Комментарии

Если размер контейнера меньше запрошенного размера, *`new_size`* то `resize` добавляет элементы в вектор до тех пор, пока не достигнет запрошенного размера. Если размер контейнера больше запрошенного размера, `resize` удаляет элементы, ближайшие к концу контейнера, пока не достигнет размера *`new_size`* . Если текущий размер контейнера совпадает с запрошенным размером, никакие действия не выполняются.

[`size`](#size) отражает текущий размер вектора.

### <a name="example"></a>Пример

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }
    cout << endl;
}

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a><a name="reverse_iterator"></a> `reverse_iterator`

Тип, предоставляющий итератор произвольного доступа, который может читать или изменять любой элемент в обратном векторе.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `reverse_iterator` используется для последовательного прохождения через вектор в обратную сторону.

### <a name="example"></a>Пример

См. пример для [`rbegin`](#rbegin) .

## <a name="shrink_to_fit"></a><a name="shrink_to_fit"></a> `shrink_to_fit`

Удаляет лишнюю емкость.

```cpp
void shrink_to_fit();
```

### <a name="example"></a>Пример

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a><a name="size"></a> `size`

Возвращает количество элементов в векторе.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Текущая длина вектора.

### <a name="example"></a>Пример

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a><a name="size_type"></a> `size_type`

Тип, считающий количество элементов в векторе.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>Пример

См. пример для [`capacity`](#capacity) .

## <a name="swap"></a><a name="swap"></a> `swap`

Меняет местами элементы двух векторов.

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*`right`*\
Вектор, предоставляющий элементы для обмена. Или вектор, элементы которого должны быть заменены элементами в векторе *`left`* .

*`left`*\
Вектор, элементы которого должны быть заменены элементами в векторе *`right`* .

### <a name="example"></a>Пример

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a><a name="value_type"></a> `value_type`

Тип, представляющий тип данных, хранящихся в векторе.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Комментарии

`value_type` является синонимом для параметра-шаблона `Type`.

### <a name="example"></a>Пример

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a><a name="vector"></a> `vector`

Конструирует вектор. Перегрузки создают вектор определенного размера или с элементами определенного значения. Или, как копия какого-либо другого вектора или его части. Некоторые перегрузки также позволяют указать распределитель для использования.

```cpp
vector();
explicit vector(const Allocator& allocator);
explicit vector(size_type count);
vector(size_type count, const Type& value);
vector(size_type count, const Type& value, const Allocator& allocator);

vector(const vector& source);
vector(vector&& source);
vector(initializer_list<Type> init_list, const Allocator& allocator);

template <class InputIterator>
vector(InputIterator first, InputIterator last);
template <class InputIterator>
vector(InputIterator first, InputIterator last, const Allocator& allocator);
```

### <a name="parameters"></a>Параметры

*`allocator`*\
Класс распределителя для использования с данным объектом. [`get_allocator`](#get_allocator) Возвращает класс распределителя для объекта.

*`count`*\
Количество элементов в создаваемом векторе.

*`value`*\
Значение элементов в создаваемом векторе.

*`source`*\
Вектор, для которого создаваемый вектор станет копией.

*`first`*\
Положение первого элемента в диапазоне копируемых элементов.

*`last`*\
Положение первого элемента за пределами диапазона копируемых элементов.

*`init_list`*\
Объект, `initializer_list` содержащий копируемые элементы.

### <a name="remarks"></a>Комментарии

Все конструкторы хранят объект распределителя ( *`allocator`* ) и инициализируют вектор.

Первые два конструктора определяют пустой исходный вектор. Второй конструктор явно указывает тип распределителя ( *`allocator`* ) для использования.

Третий конструктор задает повторение указанного числа ( *`count`* ) элементов значения по умолчанию для класса `Type` .

Четвертый и пятый конструкторы указывают повторение ( *`count`* ) элементов value *`value`* .

Шестой конструктор задает копию вектора *`source`* .

Седьмой конструктор перемещает вектор *`source`* .

Восьмой конструктор использует initializer_list, чтобы указать элементы.

Девятый и десятый конструкторы копируют диапазон [`first`, `last`) вектора.

### <a name="example"></a>Пример

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}
```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>См. также раздел

[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)
