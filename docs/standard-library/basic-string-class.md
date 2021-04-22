---
title: Класс basic_string
description: Справочник по API для стандартного строкового класса C++, `basic_string` .
ms.date: 01/15/2021
f1_keywords:
- xstring/std::basic_string
- xstring/std::basic_string::allocator_type
- xstring/std::basic_string::const_iterator
- xstring/std::basic_string::const_pointer
- xstring/std::basic_string::const_reference
- xstring/std::basic_string::const_reverse_iterator
- xstring/std::basic_string::difference_type
- xstring/std::basic_string::iterator
- xstring/std::basic_string::npos
- xstring/std::basic_string::pointer
- xstring/std::basic_string::reference
- xstring/std::basic_string::reverse_iterator
- xstring/std::basic_string::size_type
- xstring/std::basic_string::traits_type
- xstring/std::basic_string::value_type
- xstring/std::basic_string::append
- xstring/std::basic_string::assign
- xstring/std::basic_string::at
- xstring/std::basic_string::back
- xstring/std::basic_string::begin
- xstring/std::basic_string::c_str
- xstring/std::basic_string::capacity
- xstring/std::basic_string::cbegin
- xstring/std::basic_string::cend
- xstring/std::basic_string::clear
- xstring/std::basic_string::compare
- xstring/std::basic_string::copy
- xstring/std::basic_string::crbegin
- xstring/std::basic_string::crend
- xstring/std::basic_string::_Copy_s
- xstring/std::basic_string::data
- xstring/std::basic_string::empty
- xstring/std::basic_string::end
- xstring/std::basic_string::erase
- xstring/std::basic_string::find
- xstring/std::basic_string::find_first_not_of
- xstring/std::basic_string::find_first_of
- xstring/std::basic_string::find_last_not_of
- xstring/std::basic_string::find_last_of
- xstring/std::basic_string::front
- xstring/std::basic_string::get_allocator
- xstring/std::basic_string::insert
- xstring/std::basic_string::length
- xstring/std::basic_string::max_size
- xstring/std::basic_string::pop_back
- xstring/std::basic_string::push_back
- xstring/std::basic_string::rbegin
- xstring/std::basic_string::rend
- xstring/std::basic_string::replace
- xstring/std::basic_string::reserve
- xstring/std::basic_string::resize
- xstring/std::basic_string::rfind
- xstring/std::basic_string::shrink_to_fit
- xstring/std::basic_string::size
- xstring/std::basic_string::substr
- xstring/std::basic_string::ends_with
- xstring/std::basic_string::starts_with
- xstring/std::basic_string::swap
- xstring/std::literals::string_literals
- std::literals::string_literals
- string_literals
- xstring/std::literals::string_literals::operator "s
- std::literals::string_literals::operator s
helpviewer_keywords:
- std::basic_string [C++]
- std::basic_string [C++], allocator_type
- std::basic_string [C++], const_iterator
- std::basic_string [C++], const_pointer
- std::basic_string [C++], const_reference
- std::basic_string [C++], const_reverse_iterator
- std::basic_string [C++], difference_type
- std::basic_string [C++], iterator
- std::basic_string [C++], npos
- std::basic_string [C++], pointer
- std::basic_string [C++], reference
- std::basic_string [C++], reverse_iterator
- std::basic_string [C++], size_type
- std::basic_string [C++], traits_type
- std::basic_string [C++], value_type
- std::basic_string [C++], append
- std::basic_string [C++], assign
- std::basic_string [C++], at
- std::basic_string [C++], back
- std::basic_string [C++], begin
- std::basic_string [C++], c_str
- std::basic_string [C++], capacity
- std::basic_string [C++], cbegin
- std::basic_string [C++], cend
- std::basic_string [C++], clear
- std::basic_string [C++], compare
- std::basic_string [C++], copy
- std::basic_string [C++], crbegin
- std::basic_string [C++], crend
- std::basic_string [C++], _Copy_s
- std::basic_string [C++], data
- std::basic_string [C++], empty
- std::basic_string [C++], end
- std::basic_string [C++], erase
- std::basic_string [C++], find
- std::basic_string [C++], find_first_not_of
- std::basic_string [C++], find_first_of
- std::basic_string [C++], find_last_not_of
- std::basic_string [C++], find_last_of
- std::basic_string [C++], front
- std::basic_string [C++], get_allocator
- std::basic_string [C++], insert
- std::basic_string [C++], length
- std::basic_string [C++], max_size
- std::basic_string [C++], pop_back
- std::basic_string [C++], push_back
- std::basic_string [C++], rbegin
- std::basic_string [C++], rend
- std::basic_string [C++], replace
- std::basic_string [C++], reserve
- std::basic_string [C++], resize
- std::basic_string [C++], rfind
- std::basic_string [C++], shrink_to_fit
- std::basic_string [C++], size
- std::basic_string [C++], starts_with
- std::basic_string [C++], ends_with
- std::basic_string [C++], substr
- std::basic_string [C++], swap
ms.openlocfilehash: d4990b58e0f71d095f97435ad8449ade3fa240d7
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099567"
---
# <a name="basic_string-class"></a>Класс `basic_string`

Последовательности, управляемые объектом типа `basic_string` , являются стандартным классом строк C++ и обычно называются строками, но их не следует путать с завершающими нулем строками в стиле C, используемыми во всей стандартной библиотеке C++. Стандартная строка C++ — это контейнер, который позволяет использовать строки как обычные типы, такие как операции сравнения и объединения, итераторы, алгоритмы стандартной библиотеки C++, а также копирование и присваивание памяти, управляемой распределителем классов. Если необходимо преобразовать стандартную строку C++ в строку в стиле C, заканчивающуюся нулем, используйте [`basic_string::c_str`](#c_str) элемент.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType, class Traits = char_traits<CharType>, class Allocator = allocator<CharType>>
class basic_string;
```

### <a name="parameters"></a>Параметры

*`CharType`*\
Тип данных одиночного символа, сохраняемого в строке. Стандартная библиотека C++ предоставляет специализации этого шаблона класса с определениями типов [`string`](../standard-library/string-typedefs.md#string) для элементов типа `char` , [`wstring`](../standard-library/string-typedefs.md#wstring) , для `wchar_t` [`u16string`](../standard-library/string-typedefs.md#u16string) `char16_t` , и [`u32string`](../standard-library/string-typedefs.md#u32string) для `char32_t` .

*`Traits`*\
Различные важные свойства `CharType` элементов в basic_stringной специализации описаны классом `Traits` . Значение по умолчанию — `char_traits`<`CharType`>.

*`Allocator`*\
Тип, представляющий сохраненный объект распределителя, содержащий сведения о распределении строки и отмене распределения памяти. Значение по умолчанию — `allocator<CharType>`.

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[`basic_string`](#basic_string)|Создает пустую строку или строку, инициализируемую с определенными символами, или представляющую собой полную или частичную копию какого-либо другого строкового объекта или С-строки.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[`allocator_type`](#allocator_type)|Тип, представляющий класс `allocator` для объекта строки.|
|[`const_iterator`](#const_iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать элемент `const` в списке.|
|[`const_pointer`](#const_pointer)|Тип, предоставляющий указатель на элемент `const` в списке.|
|[`const_reference`](#const_reference)|Тип, предоставляющий ссылку на элемент `const`, хранящийся в строке, для чтения и выполнения операций `const`.|
|[`const_reverse_iterator`](#const_reverse_iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать любой элемент `const` в строке.|
|[`difference_type`](#difference_type)|Тип, предоставляющий разницу между двумя итераторами, ссылающимися на элементы в одной и той же строке.|
|[`iterator`](#iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать или изменять любой элемент в строке.|
|[`npos`](#npos)|Целочисленное значение без знака, инициализированное значением-1, которое указывает на отсутствие найденных или всех оставшихся символов при сбое функции поиска.|
|[`pointer`](#pointer)|Тип, предоставляющий указатель на символьный элемент в строке или символьном массиве.|
|[`reference`](#reference)|Тип, предоставляющий ссылку на элемент в строке.|
|[`reverse_iterator`](#reverse_iterator)|Тип, предоставляющий итератор произвольного доступа, который может читать или изменять любой элемент в обратной строке.|
|[`size_type`](#size_type)|Интегральный тип без знака для количества элементов в строке.|
|[`traits_type`](#traits_type)|Тип, представляющий признаки символов для элементов, хранящихся в строке.|
|[`value_type`](#value_type)|Тип, представляющий тип символов, хранящихся в строке.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[`append`](#append)|Добавляет символы в конец строки.|
|[`assign`](#assign)|Назначает значения новых символов содержимому строки.|
|[`at`](#at)|Возвращает ссылку на  элемент в заданном положении в строке.|
|[`back`](#back)||
|[`begin`](#begin)|Возвращает итератор, адресующий первый элемент в строке.|
|[`c_str`](#c_str)|Преобразует содержимое строки в С-строку, оканчивающуюся нулевым символом.|
|[`capacity`](#capacity)|Возвращает наибольшее количество элементов, которые можно хранить в строке без увеличения выделения памяти этой строки.|
|[`cbegin`](#cbegin)|Возвращает константный итератор, адресующий первый элемент в строке.|
|[`cend`](#cend)|Возвращает константный итератор, адресующий расположение после последнего элемента в строке.|
|[`clear`](#clear)|Удаляет все элементы строки.|
|[`compare`](#compare)|Сравнивает строку с указанной строкой, чтобы определить их равенство или установить, что одна из строк лексикографически меньше второй.|
|[`copy`](#copy)|Копирует не более указанного количества символов из индексированного положения в исходной строке в массив символов назначения. Не рекомендуется. [`basic_string::_Copy_s`](#copy_s)Вместо этого используйте.|
|[`crbegin`](#crbegin)|Возвращает константный итератор, адресующий первый элемент в обратной строке.|
|[`crend`](#crend)|Возвращает константный итератор, адресующий расположение после последнего элемента в обратной строке.|
|[`_Copy_s`](#copy_s)|Копирует не более указанного количества символов из индексированного положения в исходной строке в массив символов назначения.|
|[`data`](#data)|Преобразует содержимое строки в массив символов.|
|[`empty`](#empty)|Проверяет, содержит ли строка символы.|
|[`end`](#end)|Возвращает итератор, адресующий расположение после последнего элемента в строке.|
|[`ends_with`](#ends_with)<sup>C++ 20</sup>|Проверяет, заканчивается ли строка указанным суффиксом.|
|[`erase`](#erase)|Удаляет элемент или диапазон элементов с указанного положения в строке.|
|[`find`](#find)|Поиск по строке в прямом направлении до первого вхождения подстроки, совпадающей с заданной последовательностью символов.|
|[`find_first_not_of`](#find_first_not_of)|Выполняет поиск первого символа в строке, который не является ни одним элементом указанной строки.|
|[`find_first_of`](#find_first_of)|Выполняет поиск первого символа в строке, совпадающего с любым элементом заданной строки.|
|[`find_last_not_of`](#find_last_not_of)|Выполняет поиск по строке последнего символа, который не является ни одним элементом указанной строки.|
|[`find_last_of`](#find_last_of)|Выполняет поиск последнего символа в строке, совпадающего с любым элементом заданной строки.|
|[`front`](#front)|Возвращает ссылку на первый элемент в строке.|
|[`get_allocator`](#get_allocator)|Возвращает копию объекта объекта `allocator`, использованного для создания строки.|
|[`insert`](#insert)|Вставляет элемент, несколько элементов или диапазон элементов в строку в указанной позиции.|
|[`length`](#length)|Возвращает текущее количество элементов в строке.|
|[`max_size`](#max_size)|Возвращает максимальное количество символов в строке.|
|[`pop_back`](#pop_back)|Удаляет последний элемент строки.|
|[`push_back`](#push_back)|Добавляет элемент в конец строки.|
|[`rbegin`](#rbegin)|Возвращает итератор на первый элемент в обратной строке.|
|[`rend`](#rend)|Возвращает итератор, адресующий расположение после последнего элемента в обратной строке.|
|[`replace`](#replace)|Заменяет элементы в указанном положении в строке на указанные символы или символы, скопированные из других диапазонов, обычных строк или С-строк.|
|[`reserve`](#reserve)|Устанавливает вместимость строки не меньше указанного числа.|
|[`resize`](#resize)|Указывает новый размер строки, добавляя или удаляя элементы по мере необходимости.|
|[`rfind`](#rfind)|Поиск по строке в обратном направлении до первого вхождения подстроки, совпадающей с заданной последовательностью символов.|
|[`shrink_to_fit`](#shrink_to_fit)|Удаляет излишнюю вместимость строки.|
|[`size`](#size)|Возвращает текущее количество элементов в строке.|
|[`starts_with`](#starts_with)<sup>C++ 20</sup>|Проверяет, начинается ли строка с указанного префикса.|
|[`substr`](#substr)|Копирует из указанного положения в строке подстроку, содержащую по крайней мере несколько символов.|
|[`swap`](#swap)|Меняет местами содержимое двух строк.|

### <a name="operators"></a>Операторы

|Оператор|Описание|
|-|-|
|[`operator+=`](#op_add_eq)|Присоединяет символы к строке.|
|[`operator=`](#op_eq)|Назначает значения новых символов содержимому строки.|
|[`operator`&#91;&#93;](#op_at)|Предоставляет ссылку на символ с указанным индексом в строке.|

### <a name="literals"></a>Литералы

Заголовки, определяющие, `basic_string` также определяют следующие [пользовательские литералы](../cpp/user-defined-literals-cpp.md), которые создают строку указанного типа из входных параметров.

| Объявление | Описание |
|--|--|
| `inline string operator"" s(const char* str, size_t len)` | Возвращаемый результат: `string(str, len)` |
| `inline string operator"" s(const wchar_t* str, size_t len)` | Возвращаемый результат: `wstring(str, len)` |
| `inline basic_string<char8_t> operator"" s(const char8_t* str, size_t len)` | Возвращаемый результат: `basic_string<char8_t>(str, len)` |
| `inline u16string operator"" s(const char16_t* str, size_t len)` | Возвращаемый результат: `u16string(str, len)` |
| `inline u32string operator"" s(const char32_t* str, size_t len)` | Возвращаемый результат: `u32string(str, len)` |

## <a name="remarks"></a>Комментарии

Если функция запрашивает создание последовательности дольше [`max_size`](#max_size) , чем элементы, функция сообщает об ошибке длины, вызывая объект типа [`length_error`](../standard-library/length-error-class.md) .

Ссылки, указатели и итераторы, указывающие элементы управляемой последовательности, могут стать недействительными после любого вызова функции, которая изменяет управляемую последовательность, или после первого вызова функции, не являющейся `const` членом.

## <a name="requirements"></a>Требования

**Заголовок:**\<string>

**Пространство имен:** std

## <a name="basic_stringallocator_type"></a><a name="allocator_type"></a> `basic_string::allocator_type`

Тип, представляющий класс allocator для объекта строки.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для параметра шаблона `Allocator`.

### <a name="example"></a>Пример

```cpp
// basic_string_allocator_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringappend"></a><a name="append"></a> `basic_string::append`

Добавляет символы в конец строки.

```cpp
basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& append(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& append(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& append(
    size_type count,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& append(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& append(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& append(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
C-строка для добавления.

*`str`*\
Строка, символы которой добавляются.

*`offset`*\
Индекс части исходной строки, предоставляющей добавляемые знаки.

*`count`*\
Максимальное число символов для добавления из исходной строки.

*`char_value`*\
Символьное значение для добавления.

*`first`*\
Входной итератор ввода, указывающий на первый элемент в диапазоне для добавления.

*`last`*\
Входной итератор, или, указывающий на `const_pointer` `const_iterator` расположение объекта после последнего элемента в добавляемом диапазоне.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на добавляемый объект строки с символами, переданными функцией-членом.

### <a name="remarks"></a>Комментарии

Символы могут быть добавлены к строке с помощью [`operator+=`](#op_add_eq) функций или или `append` [`push_back`](#push_back) . `operator+=` Добавляет значения с одним аргументом, а функция-член с несколькими аргументами `append` позволяет указать определенную часть строки для добавления.

### <a name="example"></a>Пример

```cpp
// basic_string_append.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a C-string to a string
   string str1a ( "Hello " );
   cout << "The original string str1 is: " << str1a << endl;
   const char *cstr1a = "Out There ";
   cout << "The C-string cstr1a is: " << cstr1a << endl;
   str1a.append ( cstr1a );
   cout << "Appending the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function
   // appending part of a C-string to a string
   string str1b ( "Hello " );
   cout << "The string str1b is: " << str1b << endl;
   const char *cstr1b = "Out There ";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.append ( cstr1b , 3 );
   cout << "Appending the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function
   // appending part of one string to another
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.append ( str2c , 5 , 5 );
   cout << "The appended string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World " );
   cout << "The  string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;

   // The fifth member function
   // appending characters to a string
   string str1e ( "Hello " );
   str1e.append ( 4 , '!' );
   cout << "The string str1 appended with exclamations is: "
        << str1e << endl << endl;

   // The sixth member function
   // appending a range of one string to another
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.append ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The appended string str1 is: "
        << str1f << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The C-string cstr1a is: Out There
Appending the C-string cstr1a to string str1 gives: Hello Out There .

The string str1b is: Hello
The C-string cstr1b is: Out There
Appending the 1st part of the C-string cstr1b to string str1 gives: Hello Out.

The string str2c is: Wide World
The appended string str1 is: Hello World.

The  string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World .

The string str1 appended with exclamations is: Hello !!!!

The string str2f is: Wide World
The appended string str1 is: Hello World.
```

## <a name="basic_stringassign"></a><a name="assign"></a> `basic_string::assign`

Назначает значения новых символов содержимому строки.

```cpp
basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& assign(
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type off,
    size_type count);

basic_string<CharType, Traits, Allocator>& assign(
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& assign(
    size_type count,
    value_type char_value);

template <class InIt>
basic_string<CharType, Traits, Allocator>& assign(
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& assign(
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& assign(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Указатель на символы C-строки, которые должны быть назначены целевой строке.

*`count`*\
Число символов, назначаемых из исходной строки.

*`str`*\
Исходная строка, символы которой присваиваются целевой строке.

*`char_value`*\
Символьное значение для присваивания.

*`first`*\
Входной итератор, const_pointer или const_iterator, указывающий первый символ в диапазоне исходной строки для присваивания целевому диапазону.

*`last`*\
Входной итератор, const_pointer или const_iterator, указывающий символ сразу за последним символом в диапазоне исходной строки для присваивания целевому диапазону.

*`off`*\
Позиция, начиная с которой должны назначаться новые символы.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на объект строки, которому функция-член будет присваивать новые символы.

### <a name="remarks"></a>Комментарии

Строкам можно присваивать новые символьные значения. Новое значение может быть строкой, C-строкой или одним символом. [`operator=`](#op_eq)Может использоваться, если новое значение можно описать с помощью одного параметра; в противном случае можно использовать функцию-член с `assign` несколькими параметрами, чтобы указать, какая часть строки должна быть назначена целевой строке.

### <a name="example"></a>Пример

```cpp
// basic_string_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning the
   // characters of a C-string to a string
   string str1a;
   const char *cstr1a = "Out There";
   cout << "The C-string cstr1a is: " << cstr1a <<  "." << endl;
   str1a.assign ( cstr1a );
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1a << "." << endl << endl;

   // The second member function assigning a specific
   // number of the of characters a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b.assign ( cstr1b , 3 );
   cout << "Assigning the 1st part of the C-string cstr1b "
        << "to string str1 gives: " << str1b << "."
        << endl << endl;

   // The third member function assigning a specific number
   // of the characters from one string to another string
   string str1c ( "Hello " ), str2c ( "Wide World " );
   cout << "The string str2c is: " << str2c << endl;
   str1c.assign ( str2c , 5 , 5 );
   cout << "The newly assigned string str1 is: "
        << str1c << "." << endl << endl;

   // The fourth member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1d ( "Hello" ), str2d ( "Wide" ), str3d ( "World" );
   cout << "The original string str1 is: " << str1d << "." << endl;
   cout << "The string str2d is: " << str2d << endl;
   str1d.assign ( str2d );
   cout << "The string str1 newly assigned with string str2d is: "
        << str1d << "." << endl;
   cout << "The string str3d is: " << str3d << "." << endl;
   str1d = str3d;
   cout << "The string str1 reassigned with string str3d is: "
        << str1d << "." << endl << endl;

   // The fifth member function assigning a specific
   // number of characters of a certain value to a string
   string str1e ( "Hello " );
   str1e.assign ( 4 , '!' );
   cout << "The string str1 assigned with eclamations is: "
        << str1e << endl << endl;

   // The sixth member function assigning the value from
   // the range of one string to another string
   string str1f ( "Hello " ), str2f ( "Wide World " );
   cout << "The string str2f is: " << str2f << endl;
   str1f.assign ( str2f.begin ( ) + 5 , str2f.end ( ) - 1 );
   cout << "The string str1 assigned a range of string str2f is: "
        << str1f << "." << endl << endl;
}
```

```Output
The C-string cstr1a is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The C-string cstr1b is: Out There
Assigning the 1st part of the C-string cstr1b to string str1 gives: Out.

The string str2c is: Wide World
The newly assigned string str1 is: World.

The original string str1 is: Hello.
The string str2d is: Wide
The string str1 newly assigned with string str2d is: Wide.
The string str3d is: World.
The string str1 reassigned with string str3d is: World.

The string str1 assigned with eclamations is: !!!!

The string str2f is: Wide World
The string str1 assigned a range of string str2f is: World.
```

## <a name="basic_stringat"></a><a name="at"></a> `basic_string::at`

Предоставляет ссылку на символ с указанным индексом в строке.

```cpp
const_reference at(size_type offset) const;

reference at(size_type offset);
```

### <a name="parameters"></a>Параметры

*`offset`*\
Индекс позиции элемента, на который должна быть ссылка.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на символ строки в позиции, указанной с помощью индекса параметра.

### <a name="remarks"></a>Комментарии

Первый элемент строки имеет нулевой индекс, и следующие элементы индексируются последовательно положительными целыми числами, поэтому строка длиной *n* имеет *n*-й элемент, индексируемый по числу *n –* 1.

[ `operator`&#91;&#93;](#op_at) члена работает быстрее, чем функция-член, `at` предоставляющая доступ на чтение и запись к элементам строки.

Элемент не `operator[]` проверяет, является ли индекс, переданный в качестве параметра, допустимым, но функция-член имеет значение `at` , поэтому следует использовать, если действительность не является обязательной. Недопустимый индекс, который является индексом меньше нуля или больше или равен размеру строки, переданный функции-члену, `at` вызывает исключение [ `out_of_range` класса](../standard-library/out-of-range-class.md) . Недопустимый индекс, переданный в `operator[]`, приводит к непредсказуемому поведению, однако индекс, равный длине строки, допустим для константных строк, и при передаче этого индекса оператор возвращает символ NULL.

Возвращаемая ссылка может быть недействительной при перераспределении строк или изменении для не `const` строк.

### <a name="example"></a>Пример

```cpp
// basic_string_at.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string  cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringback"></a><a name="back"></a> `basic_string::back`

Возвращает ссылку на последний элемент строки.

```cpp
const_reference back() const;

reference back();
```

### <a name="return-value"></a>Возвращаемое значение

Ссылка на последний элемент строки, которая не должна быть пустой.

### <a name="remarks"></a>Комментарии

## <a name="basic_stringbasic_string"></a><a name="basic_string"></a> `basic_string::basic_string`

Создает пустую строку, строку, инициализируемую определенными символами или представляющую собой копию всей или части другого строкового объекта или С-строки (с окончанием на null).

```cpp
basic_string();

explicit basic_string(
    const allocator_type& alloc_type);

basic_string(
    const basic_string& right);

basic_string(
    basic_string&& right);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count = npos);

basic_string(
    const basic_string& right,
    size_type right_offset,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr,
    size_type count);

basic_string(
    const value_type* ptr,
    size_type count,
    const allocator_type& alloc_type);

basic_string(
    const value_type* ptr);

basic_string(
    const value_type* ptr,
    const allocator_type& alloc_type);

basic_string(
    size_type count,
    value_type char_value);

basic_string(
    size_type count,
    value_type char_value,
    const allocator_type& alloc_type);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
basic_string(
    InputIterator first,
    InputIterator last,
    const allocator_type& alloc_type);

basic_string(
    const_pointer first,
    const_pointer last);

basic_string(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Параметры

*`ptr`*\
C-строка, символы могут использоваться для инициализации создаваемой строки `string`. Это значение не может быть пустым указателем.

*`alloc_type`*\
Класс распределителя хранилища для создаваемого строкового объекта.

*`count`*\
Количество инициализируемых символов.

*`right`*\
Строка, инициализирующая создаваемую строку.

*`right_offset`*\
Индекс символа в строке, который первым используется для инициализации значений символов создаваемой строки.

*`char_value`*\
Значение символа, копируемое в создаваемую строку.

*`first`*\
Итератор ввода, const_pointer или const_iterator, указывающий на первый элемент в диапазоне источника, который необходимо вставить.

*`last`*\
Итератор ввода, const_pointer или const_iterator, указывающий на положение сразу за последним элементом в диапазоне источника, который необходимо вставить.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на строковый объект, создаваемый конструкторами.

### <a name="remarks"></a>Комментарии

Все конструкторы хранят [`basic_string::allocator_type`](#allocator_type) и инициализируют управляемую последовательность. Объектом распределителя является аргумент `al`, если он существует. Для конструктора копии это `right.get_allocator()` вызов метода [`basic_string::get_allocator`](#get_allocator) . В противном случае распределитель имеет значение `Alloc()` .

Управляемая последовательность инициализируется для копии последовательности операндов, указанной оставшимися операндами. Конструктор без последовательности операндов указывает пустую начальную управляемую последовательность. Если `InputIterator` является целочисленным типом в конструкторе шаблона, последовательность операндов `first,  last` ведет себя так же, как `(size_type) first, (value_type) last` .

### <a name="example"></a>Пример

```cpp
// basic_string_ctor.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function initializing with a C-string
   const char *cstr1a = "Hello Out There.";
   basic_string <char> str1a ( cstr1a , 5);
   cout << "The string initialized by C-string cstr1a is: "
        << str1a << "." << endl;

   // The second member function initializing with a string
   string  str2a ( "How Do You Do" );
   basic_string <char> str2b ( str2a , 7 , 7 );
   cout << "The string initialized by part of the string cstr2a is: "
        << str2b << "." << endl;

   // The third member function initializing a string
   // with a number of characters of a specific value
   basic_string <char> str3a ( 5, '9' );
   cout << "The string initialized by five number 9s is: "
        << str3a << endl;

   // The fourth member function creates an empty string
   // and string with a specified allocator
   basic_string <char> str4a;
   string str4b;
   basic_string <char> str4c ( str4b.get_allocator( ) );
   if (str4c.empty ( ) )
      cout << "The string str4c is empty." << endl;
   else
      cout << "The string str4c is not empty." << endl;

   // The fifth member function initializes a string from
   // another range of characters
   string str5a ( "Hello World" );
   basic_string <char> str5b ( str5a.begin ( ) + 5 , str5a.end ( ) );
   cout << "The string initialized by another range is: "
        << str5b << "." << endl;
}
```

## <a name="basic_stringbegin"></a><a name="begin"></a> `basic_string::begin`

Возвращает итератор, адресующий первый элемент в строке.

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>Возвращаемое значение

Итератор произвольного доступа, указывающий на первый элемент последовательности (или на место сразу за концом пустой последовательности).

### <a name="example"></a>Пример

```cpp
// basic_string_begin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( ) {
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator strp_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.begin ( );
   cout << "The first character of the string str1 is: "
        << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // The dereferenced iterator can be used to modify a character
*str1_Iter = 'G';
   cout << "The first character of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The full modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'g';

   // For an empty string, begin is equivalent to end
   if (  str2.begin ( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The string str2 is not empty." << endl;
}
```

## <a name="basic_stringc_str"></a><a name="c_str"></a> `basic_string::c_str`

Преобразует содержимое строки в С-строку, завершающуюся символом NULL.

```cpp
const value_type *c_str() const;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на версию вызываемой С-строки.  Значение указателя не является допустимым после вызова `const` функции, не являющейся, включая деструктор, в `basic_string` классе объекта.

### <a name="remarks"></a>Комментарии

Объекты типа String, принадлежащие шаблону класса, `basic_string<char>` не обязательно завершаются нулем. Символ NULL `'\0'` используется в качестве специального символа в C-строке для обозначения конца строки, но не имеет особого смысла в объекте типа String и может быть частью строки так же, как любой другой символ. Существует автоматическое преобразование из `const char *` в строки, но класс String не обеспечивает автоматическое преобразование из строк в стиле C в объекты типа `basic_string<char>` .

Возвращаемая строка в стиле C не должна изменяться, что может сделать недействительным указатель на строку или удалить, так как строка имеет ограниченное время существования и принадлежит строке класса.

### <a name="example"></a>Пример

```cpp
// basic_string_c_str.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringcapacity"></a><a name="capacity"></a> `basic_string::capacity`

Возвращает наибольшее количество элементов, которые можно хранить в строке без увеличения выделения памяти этой строки.

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>Возвращаемое значение

Размер хранилища, выделенного в текущий момент в памяти для хранения строки.

### <a name="remarks"></a>Комментарии

Функция-член возвращает хранилище, выделенное в настоящий момент для хранения управляемой последовательности, значение по крайней мере до [`size`](#size) .

### <a name="example"></a>Пример

```cpp
// basic_string_capacity.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringcbegin"></a><a name="cbegin"></a> `basic_string::cbegin`

Возвращает итератор `const`, направленный на первый элемент в диапазоне.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Итератор случайного доступа `const`, который указывает на первый элемент диапазона или расположение прямо за концом пустого диапазона (`cbegin() == cend()` для пустого диапазона).

### <a name="remarks"></a>Комментарии

С возвращаемым значением `cbegin` элементы в диапазоне нельзя изменять.

Эту функцию-член можно использовать вместо функции-члена `begin()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- `const` ) контейнер любого типа, который поддерживает `begin()` и `cbegin()` .

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="basic_stringcend"></a><a name="cend"></a> `basic_string::cend`

Возвращает итератор `const`, который обращается к месту, следующему сразу за последним элементом в диапазоне.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Возвращаемое значение

Итератор `const` с произвольным доступом, который указывает конец диапазона.

### <a name="remarks"></a>Комментарии

`cend` используется для проверки того, прошел ли итератор конец диапазона.

Эту функцию-член можно использовать вместо функции-члена `end()`, чтобы гарантировать, что возвращаемое значение будет `const_iterator`. Как правило, он используется вместе с [`auto`](../cpp/auto-cpp.md) ключевым словом выведения типа, как показано в следующем примере. В этом примере рекомендуется использовать `Container` изменяемый (не- `const` ) контейнер любого типа, который поддерживает `end()` и `cend()` .

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Значение, возвращаемое, `cend` не должно быть разыменовано.

## <a name="basic_stringclear"></a><a name="clear"></a> `basic_string::clear`

Удаляет все элементы строки.

```cpp
void clear();
```

### <a name="remarks"></a>Комментарии

Строка, для которой вызывается функция-член, будет пустой.

### <a name="example"></a>Пример

```cpp
// basic_string_clear.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ("Hello world"), str2;
   basic_string <char>::iterator str_Iter;
   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   str1.clear ( );
   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   //For an empty string, begin is equivalent to end
   if ( str1.begin ( ) == str1.end ( ) )
      cout << "Nothing printed above because "
           << "the string str1 is empty." << endl;
   else
      cout << "The string str1 is not empty." << endl;
}
```

```Output
The original string str1 is: Hello world
The modified string str1 is:
Nothing printed above because the string str1 is empty.
```

## <a name="basic_stringcompare"></a><a name="compare"></a> `basic_string::compare`

Выполняет сравнение с учетом регистра с указанной строкой, чтобы определить, равны ли две строки, или если одна из них лексикографически меньше другой.

```cpp
int compare(
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str) const;

int compare(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count) const;

int compare(
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr) const;

int compare(
    size_type position_1,
    size_type number_1,
    const value_type* ptr
    size_type number_2) const;
```

### <a name="parameters"></a>Параметры

*`str`*\
Строка для сравнения со строкой операнда.

*`position_1`*\
Индекс строки операнда, с которого начинается сравнение.

*`number_1`*\
Максимальное количество символов из строки операнда для сравнения.

*`number_2`*\
Максимальное количество символов из строки параметра для сравнения.

*`offset`*\
Индекс строки параметра, с которого начинается сравнение.

*`count`*\
Максимальное количество символов из строки параметра для сравнения.

*`ptr`*\
С-строка для сравнения со строкой операнда.

### <a name="return-value"></a>Возвращаемое значение

Отрицательное значение, если строка операнда меньше, чем строка параметра; ноль, если две строки равны; или положительное значение, если строка операнда больше, чем строка параметра.

### <a name="remarks"></a>Комментарии

`compare`Функции элементов сравнивают либо все, либо часть строк параметров и операндов в зависимости от используемого объекта.

При сравнении учитывается регистр.

### <a name="example"></a>Пример

```cpp
// basic_string_compare.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function compares
   // an operand string to a parameter string
   int comp1;
   string s1o ( "CAB" );
   string s1p ( "CAB" );
   cout << "The operand string is: " << s1o << endl;
   cout << "The parameter string is: " << s1p << endl;
   comp1 = s1o.compare ( s1p );
   if ( comp1 < 0 )
      cout << "The operand string is less than "
           << "the parameter string." << endl;
   else if ( comp1 == 0 )
      cout << "The operand string is equal to "
           << "the parameter string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The second member function compares part of
   // an operand string to a parameter string
   int comp2a, comp2b;
   string s2o ( "AACAB" );
   string s2p ( "CAB" );
   cout << "The operand string is: " << s2o << endl;
   cout << "The parameter string is: " << s2p << endl;
   comp2a = s2o.compare (  2 , 3 , s2p );
   if ( comp2a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;

   comp2b = s2o.compare (  0 , 3 , s2p );
   if ( comp2b < 0 )
      cout << "The first three characters of "
           << "the operand string\n are less than "
           << "the parameter string." << endl;
   else if ( comp2b == 0 )
      cout << "The first three characters of "
           << "the operand string\n are equal to "
           << "the parameter string." << endl;
   else
      cout << "The first three characters of "
           << "the operand string\n is greater than "
           << "the parameter string." << endl;
   cout << endl;

   // The third member function compares part of
   // an operand string to part of a parameter string
   int comp3a;
   string s3o ( "AACAB" );
   string s3p ( "DCABD" );
   cout << "The operand string is: " << s3o << endl;
   cout << "The parameter string is: " << s3p << endl;
   comp3a = s3o.compare (  2 , 3 , s3p , 1 , 3 );
   if ( comp3a < 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are less than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else if ( comp3a == 0 )
      cout << "The three characters from position 2 of "
           << "the operand string are equal to\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   else
      cout << "The three characters from position 2 of "
           << "the operand string is greater than\n "
           << "the 3 characters parameter string "
           << "from position 1." << endl;
   cout << endl;

   // The fourth member function compares
   // an operand string to a parameter C-string
   int comp4a;
   string s4o ( "ABC" );
   const char* cs4p = "DEF";
   cout << "The operand string is: " << s4o << endl;
   cout << "The parameter C-string is: " << cs4p << endl;
   comp4a = s4o.compare ( cs4p );
   if ( comp4a < 0 )
      cout << "The operand string is less than "
           << "the parameter C-string." << endl;
   else if ( comp4a == 0 )
      cout << "The operand string is equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The operand string is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The fifth member function compares part of
   // an operand string to a parameter C-string
   int comp5a;
   string s5o ( "AACAB" );
   const char* cs5p = "CAB";
   cout << "The operand string is: " << s5o << endl;
   cout << "The parameter string is: " << cs5p << endl;
   comp5a = s5o.compare (  2 , 3 , s2p );
   if ( comp5a < 0 )
      cout << "The last three characters of "
           << "the operand string\n are less than "
           << "the parameter C-string." << endl;
   else if ( comp5a == 0 )
      cout << "The last three characters of "
           << "the operand string\n are equal to "
           << "the parameter C-string." << endl;
   else
      cout << "The last three characters of "
           << "the operand string\n is greater than "
           << "the parameter C-string." << endl;
   cout << endl;

   // The sixth member function compares part of
   // an operand string to part of an equal length of
   // a parameter C-string
   int comp6a;
   string s6o ( "AACAB" );
   const char* cs6p = "ACAB";
   cout << "The operand string is: " << s6o << endl;
   cout << "The parameter C-string is: " << cs6p << endl;
   comp6a = s6o.compare (  1 , 3 , cs6p , 3 );
   if ( comp6a < 0 )
      cout << "The 3 characters from position 1 of "
           << "the operand string are less than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   else if ( comp6a == 0 )
      cout << "The 3 characters from position 2 of "
           << "the operand string are equal to\n "
           << "the first 3 characters of the parameter C-string."
           <<  endl;
   else
      cout << "The 3 characters from position 2 of "
           << "the operand string is greater than\n "
           << "the first 3 characters of the parameter C-string."
           << endl;
   cout << endl;
}
```

```Output
The operand string is: CAB
The parameter string is: CAB
The operand string is equal to the parameter string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter string.
The first three characters of the operand string
are less than the parameter string.

The operand string is: AACAB
The parameter string is: DCABD
The three characters from position 2 of the operand string are equal to
the 3 characters parameter string from position 1.

The operand string is: ABC
The parameter C-string is: DEF
The operand string is less than the parameter C-string.

The operand string is: AACAB
The parameter string is: CAB
The last three characters of the operand string
are equal to the parameter C-string.

The operand string is: AACAB
The parameter C-string is: ACAB
The 3 characters from position 2 of the operand string are equal to
the first 3 characters of the parameter C-string.
```

## <a name="basic_stringconst_iterator"></a><a name="const_iterator"></a> `basic_string::const_iterator`

Тип, предоставляющий итератор произвольного доступа, который может читать элемент `const` в списке.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `const_iterator` нельзя использовать для изменения значения символа и используется для прохода по строке в прямом направлении.

### <a name="example"></a>Пример

[`begin`](#begin)Пример объявления и использования см. в примере для `const_iterator` .

## <a name="basic_stringconst_pointer"></a><a name="const_pointer"></a> `basic_string::const_pointer`

Тип, предоставляющий указатель на элемент `const` в списке.

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Комментарии

Тип является синонимом `allocator_type::const_pointer`.

Для типа `string` он эквивалентен `char*` .

Указатели, объявленные как const, должны инициализироваться при их объявлении. Указатели const всегда указывают на одно и то же расположение в памяти и могут указывать на постоянные или неконстантные данные.

### <a name="example"></a>Пример

```cpp
// basic_string_const_ptr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::const_pointer pstr1a = "In Here";
   const char *cstr1c = "Out There";

   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1c is: " << cstr1c << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1c is: Out There.
```

## <a name="basic_stringconst_reference"></a><a name="const_reference"></a> `basic_string::const_reference`

Тип, предоставляющий ссылку на элемент `const`, хранящийся в строке, для чтения и выполнения операций `const`.

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="remarks"></a>Комментарии

Тип `const_reference` нельзя использовать для изменения значения элемента.

Тип является синонимом `allocator_type::const_reference`. Для типа `string` он эквивалентен const `char&` .

### <a name="example"></a>Пример

[`at`](#at)Пример объявления и использования см. в примере для `const_reference` .

## <a name="basic_stringconst_reverse_iterator"></a><a name="const_reverse_iterator"></a> `basic_string::const_reverse_iterator`

Тип, предоставляющий итератор произвольного доступа, который может читать любой элемент `const` в строке.

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `const_reverse_iterator` не может изменить значение символа и используется для перебора строки в обратную.

### <a name="example"></a>Пример

[`rbegin`](#rbegin)Пример объявления и использования см. в примере для `const_reverse_iterator` .

## <a name="basic_stringcopy"></a><a name="copy"></a> `basic_string::copy`

Копирует не более указанного количества символов из индексированного положения в исходной строке в массив символов назначения.

Этот метод является потенциально опасным, так как зависит от вызывающего объекта при проверке правильности переданных значений. [`basic_string::_Copy_s`](#copy_s)Вместо этого рекомендуется использовать.

```cpp
size_type copy(
    value_type* ptr,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Параметры

*`ptr`*\
Целевой массив символов, в который должны быть скопированы элементы.

*`count`* Число символов, которые будут копироваться не более чем из исходной строки.

*`offset`*\
Начальная позиция в исходной строке, из которой должны быть сделаны копии.

### <a name="return-value"></a>Возвращаемое значение

Число скопированных символов.

### <a name="remarks"></a>Комментарии

Символ NULL не добавляется в конец копии.

### <a name="example"></a>Пример

```cpp
// basic_string_copy.cpp
// compile with: /EHsc /W3
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello World" );
   basic_string <char>::iterator str_Iter;
   char array1 [ 20 ] = { 0 };
   char array2 [ 10 ] = { 0 };
   basic_string <char>:: pointer array1Ptr = array1;
   basic_string <char>:: value_type *array2Ptr = array2;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   basic_string <char>:: size_type nArray1;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray1 = str1.copy ( array1Ptr , 12 );  // C4996
   cout << "The number of copied characters in array1 is: "
        << nArray1 << endl;
   cout << "The copied characters array1 is: " << array1 << endl;

   basic_string <char>:: size_type nArray2;
   // Note: string::copy is potentially unsafe, consider
   // using string::_Copy_s instead.
   nArray2 = str1.copy ( array2Ptr , 5 , 6  );  // C4996
   cout << "The number of copied characters in array2 is: "
           << nArray2 << endl;
   cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringcrbegin"></a><a name="crbegin"></a> `basic_string::crbegin`

Возвращает константный итератор, адресующий первый элемент в обратной строке.

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>Возвращаемое значение

Обратный итератор, который указывает на положение, следующее за концом строки. Позиция задает начало обратной строки.

## <a name="basic_stringcrend"></a><a name="crend"></a> `basic_string::crend`

Возвращает `const` итератор, который обращается к месту, следующему за последним элементом в обращенной строке.

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>Возвращаемое значение

`const`Обратный итератор, который обращается к расположению, следующему за последним элементом в обращенной строке (расположении, предшествующем первому элементу в неизмененной строке).

### <a name="remarks"></a>Комментарии

## <a name="basic_string_copy_s"></a><a name="copy_s"></a> `basic_string::_Copy_s`

Копирует не более указанного количества символов из индексированного положения в исходной строке в массив символов назначения.

```cpp
size_type _Copy_s(
    value_type* dest,
    size_type dest_size,
    size_type count,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Параметры

*`dest`*\
Целевой массив символов, в который должны быть скопированы элементы.

*`dest_size`*\
Размер *dest*.

*`count`* Число символов, которые будут копироваться не более чем из исходной строки.

*`offset`*\
Начальная позиция в исходной строке, из которой должны быть сделаны копии.

### <a name="return-value"></a>Возвращаемое значение

Число фактически скопированных символов.

### <a name="remarks"></a>Комментарии

Символ NULL не добавляется в конец копии.

### <a name="example"></a>Пример

```cpp
// basic_string__Copy_s.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
    using namespace std;
    string str1("Hello World");
    basic_string<char>::iterator str_Iter;
    const int array1_size = 20;
    char array1[array1_size] = { 0 };
    const int array2_size = 10;
    char array2[array2_size] = { 0 };
    basic_string<char>:: pointer array1Ptr = array1;
    basic_string<char>:: value_type *array2Ptr = array2;

    cout << "The original string str1 is: ";
    for (str_Iter = str1.begin(); str_Iter != str1.end(); str_Iter++)
        cout << *str_Iter;
    cout << endl;

    basic_string<char>::size_type nArray1;
    nArray1 = str1._Copy_s(array1Ptr, array1_size, 12);
    cout << "The number of copied characters in array1 is: "
         << nArray1 << endl;
    cout << "The copied characters array1 is: " << array1 << endl;

    basic_string<char>:: size_type nArray2;
    nArray2 = str1._Copy_s(array2Ptr, array2_size, 5, 6);
    cout << "The number of copied characters in array2 is: "
         << nArray2 << endl;
    cout << "The copied characters array2 is: " << array2Ptr << endl;
}
```

```Output
The original string str1 is: Hello World
The number of copied characters in array1 is: 11
The copied characters array1 is: Hello World
The number of copied characters in array2 is: 5
The copied characters array2 is: World
```

## <a name="basic_stringdata"></a><a name="data"></a> `basic_string::data`

Преобразует содержимое строки в массив символов, заканчивающийся нулем.

```cpp
const value_type *data() const noexcept;
value_type *data() noexcept;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на первый элемент массива, заканчивающегося нулем, который содержит содержимое строки. Для пустой строки указатель указывает на один символ null, равный `value_type()` .

### <a name="remarks"></a>Комментарии

Указатель, возвращенный `data` точками в допустимом диапазоне `[data(), data() + size()]` . Каждый элемент в диапазоне соответствует текущим данным в строке. То есть для каждого допустимого смещения *`n`* в диапазоне `data() + n == addressof(operator[](n))` .

При изменении содержимого строки, возвращаемой `const` перегрузкой `data` , поведение не определено. Вы также получаете неопределенное поведение, если символ терминала NULL меняется на любое другое значение. Возвращаемый указатель может быть недействительным, если строка, не `const` ссылающаяся на строку, передается в стандартную функцию библиотеки. Его также можно сделать недействительным при вызове функции, не являющейся `const` членом. Вызовы членов,,,,,, `at` `back` `begin` `end` `front` `rbegin` `rend` и `operator[]` не делают недействительными указатель.

До C++ 11 `data` не гарантирует, что возвращенная строка была прервана нулем. Начиная с C++ 11 `data` , `c_str` оба возвращают строку, завершающуюся нулем, и фактически одинаковы.

В `const` c++ 17 не является перегрузкой. Чтобы использовать его, укажите **`/std:c++17`** **`/std:c++latest`** параметр компилятора или.

### <a name="example"></a>Пример

```cpp
// basic_string_data.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string str1 ( "Hello world" );
   cout << "The original string object str1 is: "
        << str1 << endl;
   cout << "The length of the string object str1 = "
        << str1.length ( ) << endl << endl;

   // Converting a string to an array of characters
   const char *ptr1 = 0;
   ptr1= str1.data ( );
   cout << "The modified string object ptr1 is: " << ptr1
        << endl;
   cout << "The length of character array str1 = "
        << strlen ( ptr1) << endl << endl;

   // Converting a string to a C-style string
   const char *c_str1 = str1.c_str ( );
   cout << "The C-style string c_str1 is: " << c_str1
        << endl;
   cout << "The length of C-style string str1 = "
        << strlen ( c_str1) << endl << endl;
}
```

```Output
The original string object str1 is: Hello world
The length of the string object str1 = 11

The modified string object ptr1 is: Hello world
The length of character array str1 = 11

The C-style string c_str1 is: Hello world
The length of C-style string str1 = 11
```

## <a name="basic_stringdifference_type"></a><a name="difference_type"></a> `basic_string::difference_type`

Тип, предоставляющий разницу между двумя итераторами, ссылающимися на элементы в одной и той же строке.

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Комментарии

Тип целого числа со знаком описывает объект, который может представлять разницу между адресами любых двух элементов в управляемой последовательности.

Для типа `string` он эквивалентен `ptrdiff_t` .

### <a name="example"></a>Пример

```cpp
// basic_string_diff_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "quintillion" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexChFi, indexChLi;

   indexChFi = str1.find_first_of ( "i" );
   indexChLi = str1.find_last_of ( "i" );
   basic_string<char>::difference_type diffi = indexChLi - indexChFi;

   cout << "The first character i is at position: "
        << indexChFi << "." << endl;
   cout << "The last character i is at position: "
        << indexChLi << "." << endl;
   cout << "The difference is: " << diffi << "." << endl;
}
```

```Output
The original string str1 is: quintillion
The first character i is at position: 2.
The last character i is at position: 8.
The difference is: 6.
```

## <a name="basic_stringempty"></a><a name="empty"></a> `basic_string::empty`

Проверяет, содержит ли строка символы.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Возвращаемое значение

`true` значение, если строковый объект не содержит символов; `false` , если у него есть хотя бы один символ.

### <a name="remarks"></a>Комментарии

Функция-член эквивалентна [`size`](#size) = = 0.

### <a name="example"></a>Пример

```cpp
// basic_string_empty.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main() {
   using namespace std;

   bool b1, b2;

   string str1 ("Hello world");
   cout << "The original string object str1 is: " << str1 << endl;
   b1 = str1.empty();
   if (b1)
      cout << "The string object str1 is empty." << endl;
   else
      cout << "The string object str1 is not empty." << endl;
   cout << endl;

   // An example of an empty string object
   string str2;
   b2 = str2.empty();
   if (b2)
      cout << "The string object str2 is empty." << endl;
   else
      cout << "The string object str2 is not empty." << endl;
}
```

## <a name="basic_stringend"></a><a name="end"></a> `basic_string::end`

Возвращает итератор, адресующий расположение после последнего элемента в строке.

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает итератор произвольного доступа, указывающий расположение за последним элементом в строке.

### <a name="remarks"></a>Комментарии

`end` часто используется для проверки того, достиг ли итератор конца строки. Значение, возвращаемое, `end` не должно быть разыменовано.

Если возвращаемое значение `end` присваивается `const_iterator` , то строковый объект не может быть изменен. Если возвращаемое значение `end` присваивается `iterator` , то строковый объект может быть изменен.

### <a name="example"></a>Пример

```cpp
// basic_string_end.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "No way out." ), str2;
   basic_string <char>::iterator str_Iter, str1_Iter, str2_Iter;
   basic_string <char>::const_iterator str1_cIter;

   str1_Iter = str1.end ( );
   str1_Iter--;
   str1_Iter--;
   cout << "The last character-letter of the string str1 is: " << *str1_Iter << endl;
   cout << "The full original string str1 is: " << str1 << endl;

   // end used to test when an iterator has reached the end of its string
   cout << "The string is now: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_Iter = 'T';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;
   cout << "The modified string str1 is now: " << str1 << endl;

   // The following line would be an error because iterator is const
   // *str1_cIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.begin( ) == str2.end ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the string str1 is: t
The full original string str1 is: No way out.
The string is now: No way out.
The last character-letter of the modified str1 is now: T
The modified string str1 is now: No way ouT.
The string str2 is empty.
```

## <a name="basic_stringends_with"></a><a name="ends_with"></a> `basic_string::ends_with`

Проверьте, заканчивается ли строка указанным суффиксом.

```cpp
bool ends_with(const CharType c) const noexcept;
bool ends_with(const CharType* const x) const noexcept;
bool ends_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>Параметры

*`c`*\
Искомый суффикс одиночных символов.

*`sv`*\
Строковое представление, содержащее суффикс для поиска. \
Можно передать `std::basic_string` , который преобразует в строковое представление.

*`x`*\
Строка символов, завершающаяся нулем, содержащая суффикс для поиска.

### <a name="return-value"></a>Возвращаемое значение

`true` значение, если строка заканчивается указанным суффиксом; `false` в противном случае — значение.

### <a name="remarks"></a>Комментарии

`ends_with()` Новое в C++ 20. Чтобы использовать его, укажите [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) параметр компилятора.

[`starts_with`](#starts_with)Проверить, начинается ли строка с указанного префикса, см. в разделе.

### <a name="example"></a>Пример

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'
    std::cout << str.ends_with('g') << '\n';
    std::cout << str.ends_with("eFg") << '\n';

    std::basic_string<char> str2 = "efg";
    std::cout << str.ends_with(str2);

    return 0;
}
```

```Output
true
false
true
```

## <a name="basic_stringerase"></a><a name="erase"></a> `basic_string::erase`

Удаляет элемент или диапазон элементов с указанного положения в строке.

```cpp
iterator erase(
    iterator first,
    iterator last);

iterator erase(
    iterator iter);

basic_string<CharType, Traits, Allocator>& erase(
    size_type offset = 0,
    size_type count = npos);
```

### <a name="parameters"></a>Параметры

*`first`*\
Итератор, указывающий позицию первого элемента в диапазоне для очистки.

*`last`*\
Итератор, указывающий позицию первого, следующую за последним элементом в диапазоне для очистки.

*`iter`*\
Итератор, указывающий позицию элемента в строке для очистки.

*`offset`*\
Индекс первого символа в строке для удаления.

*`count`*\
Число элементов, которые будут удалены, если в диапазоне строки, начинающейся с *`offset`* .

### <a name="return-value"></a>Возвращаемое значение

Для первых двух функций-членов это итератор, указывающий первый символ после последнего символа, удаленного функцией-членом. Для третьей функции-члена это ссылка на объект string, из которого удалены элементы.

### <a name="remarks"></a>Комментарии

Третья функция – член возвращает значение `*this` .

### <a name="example"></a>Пример

```cpp
// basic_string_erase.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The 1st member function using a range demarcated
   // by iterators
   string str1 ( "Hello world" );
   basic_string <char>::iterator str1_Iter;
   cout << "The original string object str1 is: "
        << str1 << "." << endl;
   str1_Iter = str1.erase ( str1.begin ( ) + 3 , str1.end ( ) - 1 );
   cout << "The first element after those removed is: "
        << *str1_Iter << "." << endl;
   cout << "The modified string object str1 is: " << str1
           << "." << endl << endl;

   // The 2nd member function erasing a char pointed to
   // by an iterator
   string str2 ( "Hello World" );
   basic_string <char>::iterator str2_Iter;
   cout << "The original string object str2 is: " << str2
        << "." << endl;
   str2_Iter = str2.erase ( str2.begin ( ) + 5 );
   cout << "The first element after those removed is: "
        << *str2_Iter << "." << endl;
   cout << "The modified string object str2 is: " << str2
        << "." << endl << endl;

   // The 3rd member function erasing a number of chars
   // after a char
   string str3 ( "Hello computer" ), str3m;
   basic_string <char>::iterator str3_Iter;
   cout << "The original string object str3 is: "
        << str3 << "." << endl;
   str3m = str3.erase ( 6 , 8 );
   cout << "The modified string object str3m is: "
        << str3m << "." << endl;
}
```

```Output
The original string object str1 is: Hello world.
The first element after those removed is: d.
The modified string object str1 is: Held.

The original string object str2 is: Hello World.
The first element after those removed is: W.
The modified string object str2 is: HelloWorld.

The original string object str3 is: Hello computer.
The modified string object str3m is: Hello .
```

## <a name="basic_stringfind"></a><a name="find"></a> `basic_string::find`

Поиск по строке в прямом направлении до первого вхождения подстроки, совпадающей с заданной последовательностью символов.

```cpp
size_type find(
    value_type char_value,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Значение символа, для которого следует искать функцию-член.

*`offset`*\
Индекс позиции, в которой следует начать поиск.

*`ptr`*\
Строка C-string, для которой следует искать функцию-член.

*`count`*\
Число символов, начиная с первого, в строке C-string, для которой следует искать функцию-член.

*`str`*\
Строка, для которой следует искать функцию-член.

### <a name="return-value"></a>Возвращаемое значение

Индекс первого символа искомой подстроки, если она успешно найдена; в противном случае — `npos`.

### <a name="example"></a>Пример

```cpp
// basic_string_find.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;

   indexCh1a = str1.find ( "e" , 3 );
   if (indexCh1a != string::npos )
      cout << "The index of the 1st 'e' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.find ( "x" );
   if (indexCh1b != string::npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.find ( cstr2 , 5 );
   if ( indexCh2a != string::npos )
      cout << "The index of the 1st element of 'perfect' "
           << "after\n the 5th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.find ( cstr2b , 0 );
   if (indexCh2b != string::npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "after\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "This is a sample string for this program" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "sample";
   indexCh3a = str3.find ( cstr3a );
   if ( indexCh3a != string::npos )
      cout << "The index of the 1st element of sample "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'sample' was not found in str3 ."
           << endl;

   const char *cstr3b = "for";
   indexCh3b = str3.find ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != string::npos )
      cout << "The index of the next occurrence of 'for' is in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'for' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "clearly this perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.find ( str4a , 5 );
   if ( indexCh4a != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "after\n the 5th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl;

   string str4b ( "clear" );
   indexCh4b = str4.find ( str4b );
   if (indexCh4b != string::npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found after the 3rd position in str1 is: 8
The Character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' after
the 5th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: This is a sample string for this program
The index of the 1st element of sample in str3 is: 10
The index of the next occurrence of 'for' is in str3 begins at: 24

The original string str4 is: clearly this perfectly unclear.
The index of the 1st element of 'clear' after
the 5th position in str4 is: 25
The index of the 1st element of 'clear' in str4 is: 0
```

## <a name="basic_stringfind_first_not_of"></a><a name="find_first_not_of"></a> `basic_string::find_first_not_of`

Выполняет поиск первого символа в строке, который не является элементом указанной строки.

```cpp
size_type find_first_not_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Значение символа, для которого следует искать функцию-член.

*`offset`*\
Индекс позиции, в которой следует начать поиск.

*`ptr`*\
Строка C-string, для которой следует искать функцию-член.

*`count`*\
Число символов, начиная с первого, в строке C-string, для которой следует искать функцию-член.

*`str`*\
Строка, для которой следует искать функцию-член.

### <a name="return-value"></a>Возвращаемое значение

Индекс первого символа искомой подстроки, если она успешно найдена; в противном случае — `npos`.

### <a name="example"></a>Пример

```cpp
// basic_string_find_first_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "xddd-1234-abcd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_not_of ( "d" , 2 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 3rd"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_not_of  ( "x" );
   if (indexCh1b != npos )
      cout << "The index of the 'non x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_not_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not"
           << "\n found in str2 after the 6th position."
           << endl;

   const char *cstr2b = "B2";
   indexCh2b = str2.find_first_not_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'B2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'B2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_first_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_first_not_of ( cstr3b , indexCh3a + 1 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '45G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_not_of ( str4a , 5 );
   if (indexCh4a != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'ba3' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_first_not_of ( str4b  );
   if (indexCh4b != npos )
      cout << "The index of the 1st non occurrence of an "
           << "element of '12' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12' were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: xddd-1234-abcd
The index of the 1st 'd' found after the 3rd position in str1 is: 4
The index of the 'non x' found in str1 is: 1

The original string str2 is: BBB-1111
Elements of the substring 'B1' were not
found in str2 after the 6th position.
The index of the 1st element of 'B2' after
the 0th position in str2 is: 3

The original string str3 is: 444-555-GGG
The index of the 1st occurrence of an element in str3
other than one of the characters in '45G' is: 3
The index of the second occurrence of an element of '45G' in str3
after the 0th position is: 7

The original string str4 is: 12-ab-12-ab
The index of the 1st non occurrence of an element of 'ba3' in str4 after
the 5th position is: 5
The index of the 1st non occurrence of an element of '12' in str4 after
the 0th position is: 2
```

## <a name="basic_stringfind_first_of"></a><a name="find_first_of"></a> `basic_string::find_first_of`

Выполняет поиск первого символа в строке, совпадающего с любым элементом заданной строки.

```cpp
size_type find_first_of(
    value_type char_value,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset = 0) const;

size_type find_first_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_first_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = 0) const;
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Значение символа, для которого следует искать функцию-член.

*`offset`*\
Индекс позиции, в которой следует начать поиск.

*`ptr`*\
Строка C-string, для которой следует искать функцию-член.

*`count`*\
Число символов, начиная с первого, в строке C-string, для которой следует искать функцию-член.

*`str`*\
Строка, для которой следует искать функцию-член.

### <a name="return-value"></a>Возвращаемое значение

Индекс первого символа искомой подстроки, если она успешно найдена; в противном случае — `npos`.

### <a name="example"></a>Пример

```cpp
// basic_string_find_first_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_first_of ( "d" , 5 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'd' found after the 5th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for any element of a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_first_of ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'B1' in str2 after\n the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 after the 10th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_first_of ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for any element of a substring as specified by a C-string
   string str3 ( "123-abc-123-abc-456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "5G";
   indexCh3a = str3.find_first_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of '5G' in str3 after\n the 0th "
           << "position is: " << indexCh3a << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the 0th position."
           << endl;

   const char *cstr3b = "5GF";
   indexCh3b = str3.find_first_of  ( cstr3b , indexCh3a + 1 , 2 );
   if (indexCh3b != npos )
      cout << "The index of the second occurrence of an "
           << "element of '5G' in str3\n after the 0th "
           << "position is: " << indexCh3b << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n after the first occurrrence."
           << endl << endl;

   // The fourth member function searches a string
   // for any element of a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_first_of ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'ba3' in str4 after\n the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_first_of ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st occurrence of an "
           << "element of 'a2' in str4 after\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the 1st 'd' found after the 5th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the 1st occurrence of an element of 'B1' in str2 after
the 6th position is: 11
The index of the 1st element of 'D2' after
the 0th position in str2 is: 3

The original string str3 is: 123-abc-123-abc-456-EFG-456-EFG
The index of the 1st occurrence of an element of '5G' in str3 after
the 0th position is: 17
The index of the second occurrence of an element of '5G' in str3
after the 0th position is: 22

The original string str4 is: 12-ab-12-ab
The index of the 1st occurrence of an element of 'ba3' in str4 after
the 5th position is: 9
The index of the 1st occurrence of an element of 'a2' in str4 after
the 0th position is: 1
```

## <a name="basic_stringfind_last_not_of"></a><a name="find_last_not_of"></a> `basic_string::find_last_not_of`

Выполняет поиск по строке последнего символа, который не является ни одним элементом указанной строки.

```cpp
size_type find_last_not_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_not_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_not_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Значение символа, для которого следует искать функцию-член.

*`offset`*\
Индекс позиции, в которой следует завершить поиск.

*`ptr`*\
Строка C-string, для которой следует искать функцию-член.

*`count`*\
Число символов, начиная с первого, в строке C-string, для которой следует искать функцию-член.

*`str`*\
Строка, для которой следует искать функцию-член.

### <a name="return-value"></a>Возвращаемое значение

Индекс первого символа искомой подстроки, если она успешно найдена; в противном случае — `npos`.

### <a name="example"></a>Пример

```cpp
// basic_string_find_last_not_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "dddd-1dd4-abdd" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_not_of ( "d" , 7 );
   if ( indexCh1a != npos )
      cout << "The index of the last non 'd'\n found before the "
           << "7th position in str1 is: " << indexCh1a << endl;
   else
      cout << "The non 'd' character was not found ." << endl;

   indexCh1b = str1.find_last_not_of  ( "d" );
   if ( indexCh1b != npos )
      cout << "The index of the non 'd' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The Character 'non x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "BBB-1111" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_not_of  ( cstr2 , 6 );
   if ( indexCh2a != npos )
      cout << "The index of the last occurrence of a "
           << "element\n not of 'B1' in str2 before the 6th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements not of the substring 'B1' were not "
           << "\n found in str2 before the 6th position."
           << endl;

   const char *cstr2b = "B-1";
   indexCh2b = str2.find_last_not_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element not "
           << "in 'B-1'\n is: "
           << indexCh2b << endl << endl;
   else
      cout << "The elements of the substring 'B-1' were "
           << "not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "444-555-GGG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "45G";
   indexCh3a = str3.find_last_not_of ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element in str3\n other than one of the "
           << "characters in '45G' is: " << indexCh3a
           << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string  '45G'. "
           << endl;

   const char *cstr3b = "45G";
   indexCh3b = str3.find_last_not_of ( cstr3b , 6 , indexCh3a - 1 );
   if (indexCh3b != npos )
      cout << "The index of the penultimate occurrence of an "
           << "element\n not in '45G' in str3 is: "
           << indexCh3b << endl << endl;
   else
      cout << "Elements in str3 contain only characters "
           << " in the string '45G'. "
           << endl  << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "b-a" );
   indexCh4a = str4.find_last_not_of  ( str4a , 5 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element not\n in 'b-a' in str4 before the 5th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements other than those in the substring"
           << " 'b-a' were not found in the string str4."
           << endl;

   string str4b ( "12" );
   indexCh4b = str4.find_last_not_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element not in '12'\n in str4 before the end "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements other than those in the substring"
           << " '12'\n were not found in the string str4."
           << endl;
}
```

```Output
The original string str1 is: dddd-1dd4-abdd
The index of the last non 'd'
found before the 7th position in str1 is: 5
The index of the non 'd' found in str1 is: 11

The original string str2 is: BBB-1111
The index of the last occurrence of a element
not of 'B1' in str2 before the 6th position is: 3
The elements of the substring 'B-1' were not found in str2 .

The original string str3 is: 444-555-GGG
The index of the last occurrence of an element in str3
other than one of the characters in '45G' is: 7
The index of the penultimate occurrence of an element
not in '45G' in str3 is: 3

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element not
in 'b-a' in str4 before the 5th position is: 1
The index of the last occurrence of an element not in '12'
in str4 before the end position is: 10
```

## <a name="basic_stringfind_last_of"></a><a name="find_last_of"></a> `basic_string::find_last_of`

Выполняет в строке поиск последнего символа, совпадающего с любым элементом заданной строки.

```cpp
size_type find_last_of(
    value_type char_value,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset = npos) const;

size_type find_last_of(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type find_last_of(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Значение символа, для которого следует искать функцию-член.

*`offset`*\
Индекс позиции, в которой следует завершить поиск.

*`ptr`*\
Строка C-string, для которой следует искать функцию-член.

*`count`*\
Число символов, начиная с первого, в строке C-string, для которой следует искать функцию-член.

*`str`*\
Строка, для которой следует искать функцию-член.

### <a name="return-value"></a>Возвращаемое значение

Индекс последнего символа искомой подстроки, если он был успешно найден; в противном случае — `npos`.

### <a name="example"></a>Пример

```cpp
// basic_string_find_last_of.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "abcd-1234-abcd-1234" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.find_last_of ( "d" , 14 );
   if ( indexCh1a != npos )
      cout << "The index of the last 'd' found before the 14th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'd' was not found in str1 ." << endl;

   indexCh1b = str1.find_first_of ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "ABCD-1234-ABCD-1234" );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "B1";
   indexCh2a = str2.find_last_of  ( cstr2 , 12 );
   if (indexCh2a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'B1' in str2 before\n the 12th "
           << "position is: " << indexCh2a << endl;
   else
      cout << "Elements of the substring 'B1' were not "
           << "found in str2 before the 12th position."
           << endl;

   const char *cstr2b = "D2";
   indexCh2b = str2.find_last_of  ( cstr2b );
   if ( indexCh2b != npos )
      cout << "The index of the last element of 'D2' "
           << "after\n the 0th position in str2 is: "
           << indexCh2b << endl << endl;
   else
      cout << "The substring 'D2' was not found in str2 ."
           << endl << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "456-EFG-456-EFG" );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a;

   const char *cstr3a = "5E";
   indexCh3a = str3.find_last_of ( cstr3a , 8 , 8 );
   if ( indexCh3a != npos )
      cout << "The index of the last occurrence of an "
           << "element of '5E' in str3 before\n the 8th "
           << "position is: " << indexCh3a << endl << endl;
   else
      cout << "Elements of the substring '5G' were not "
           << "found in str3\n before the 8th position."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "12-ab-12-ab" );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "ba3" );
   indexCh4a = str4.find_last_of  ( str4a , 8 );
   if ( indexCh4a != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'ba3' in str4 before\n the 8th "
           << "position is: " << indexCh4a << endl;
   else
      cout << "Elements of the substring 'ba3' were not "
           << "found in str4\n after the 0th position."
           << endl;

   string str4b ( "a2" );
   indexCh4b = str4.find_last_of ( str4b  );
   if ( indexCh4b != npos )
      cout << "The index of the last occurrence of an "
           << "element of 'a2' in str4 before\n the 0th "
           << "position is: " << indexCh4b << endl;
   else
      cout << "Elements of the substring 'a2' were not "
           << "found in str4\n after the 0th position."
           << endl;
}
```

```Output
The original string str1 is: abcd-1234-abcd-1234
The index of the last 'd' found before the 14th position in str1 is: 13
The character 'x' was not found in str1.

The original string str2 is: ABCD-1234-ABCD-1234
The index of the last occurrence of an element of 'B1' in str2 before
the 12th position is: 11
The index of the last element of 'D2' after
the 0th position in str2 is: 16

The original string str3 is: 456-EFG-456-EFG
The index of the last occurrence of an element of '5E' in str3 before
the 8th position is: 4

The original string str4 is: 12-ab-12-ab
The index of the last occurrence of an element of 'ba3' in str4 before
the 8th position is: 4
The index of the last occurrence of an element of 'a2' in str4 before
the 0th position is: 9
```

## <a name="basic_stringfront"></a><a name="front"></a> `basic_string::front`

Возвращает ссылку на первый элемент в строке.

```cpp
const_reference front() const;

reference front();
```

### <a name="return-value"></a>Возвращаемое значение

Ссылка на первый элемент строки, который не должен быть пустым.

### <a name="remarks"></a>Комментарии

## <a name="basic_stringget_allocator"></a><a name="get_allocator"></a> `basic_string::get_allocator`

Возвращает копию объекта allocator, используемого для создания строки.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Возвращаемое значение

Распределитель, используемый строкой.

### <a name="remarks"></a>Комментарии

Функция-член возвращает сохраненный объект распределителя.

Распределители для класса string указывают, как этот класс управляет хранилищем. Для большинства задач программирования достаточно распределителей по умолчанию, доступных в классах контейнеров. Написание и использование собственного класса распределителя является расширенной функцией C++.

### <a name="example"></a>Пример

```cpp
// basic_string_get_allocator.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects
   // that use the default allocator.
   string s1;
   basic_string <char> s2;
   basic_string <char, char_traits< char >, allocator< char > > s3;

   // s4 will use the same allocator class as s1
   basic_string <char> s4( s1.get_allocator ( ) );

   basic_string <char>::allocator_type xchar = s1.get_allocator( );
   // You can now call functions on the allocator class xchar used by s1
}
```

## <a name="basic_stringinsert"></a><a name="insert"></a> `basic_string::insert`

Вставляет элемент, несколько элементов или диапазон элементов в строку в указанной позиции.

```cpp
basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const value_type* ptr,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset,
    size_type count);

basic_string<CharType, Traits, Allocator>& insert(
    size_type position,
    size_type count,
    value_type char_value);

iterator insert(
    iterator iter);

iterator insert(
    iterator iter,
    value_type char_value)l
template <class InputIterator>
void insert(
    iterator iter,
    InputIterator first,
    InputIterator last);

void insert(
    iterator iter,
    size_type count,
    value_type char_value);

void insert(
    iterator iter,
    const_pointer first,
    const_pointer last);

void insert(
    iterator iter,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Параметры

*`position`*\
Индекс позиции за точкой вставки новых символов.

*`ptr`*\
C-строка, которая полностью или частично вставляется в строку.

*`count`*\
Число вставляемых знаков.

*`str`*\
Строка, которая полностью или частично вставляется в целевую строку.

*`offset`*\
Индекс части исходной строки, предоставляющей добавляемые знаки.

*`char_value`*\
Символьное значение вставляемых элементов.

*`iter`*\
Итератор, разрешающий положение, за которым вставляется знак.

*`first`*\
Входной итератор, `const_pointer` или `const_iterator` адресация первого элемента в исходном диапазоне для вставки.

*`last`*\
Входной итератор, или, указывающий на `const_pointer` `const_iterator` расположение объекта после последнего элемента в исходном диапазоне для вставки.

### <a name="return-value"></a>Возвращаемое значение

Либо ссылка на объект String, который получает новые символы функцией-членом, либо, в случае вставки отдельных символов, итератор, указывающий на положение вставленного символа, или нет, в зависимости от конкретной функции-члена.

### <a name="example"></a>Пример

```cpp
// basic_string_insert.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function inserting a C-string
   // at a given position
   basic_string <char> str1a ( "way" );
   const char *cstr1a = "a";
   str1a.insert ( 0, cstr1a );
   cout << "The string with a C-string inserted at position 0 is: "
        << str1a << "." << endl;

   // The second member function inserting a C-string
   // at a given position for a specified number of elements
   basic_string <char> str2a ( "Good" );
   const char *cstr2a = "Bye Bye Baby";
   str2a.insert ( 4, cstr2a ,3 );
   cout << "The string with a C-string inserted at the end is: "
        << str2a << "." << endl;

   // The third member function inserting a string
   // at a given position
   basic_string <char> str3a ( "Bye" );
   string str3b ( "Good" );
   str3a.insert ( 0, str3b );
   cout << "The string with a string inserted at position 0 is: "
        << str3a << "." << endl;

   // The fourth member function inserting part of
   // a string at a given position
   basic_string <char> str4a ( "Good " );
   string str4b ( "Bye Bye Baby" );
   str4a.insert ( 5, str4b , 8 , 4 );
   cout << "The string with part of a string inserted at position 4 is: "
        << str4a << "." << endl;

   // The fifth member function inserts a number of characters
   // at a specified position in the string
   string str5 ( "The number is: ." );
   str5.insert ( 15 , 3 , '3' );
   cout << "The string with characters inserted is: "
        << str5 << endl;

   // The sixth member function inserts a character
   // at a specified position in the string
   string str6 ( "ABCDFG" );
   basic_string <char>::iterator str6_Iter = ( str6.begin ( ) + 4 );
   str6.insert ( str6_Iter , 'e' );
   cout << "The string with a character inserted is: "
        << str6 << endl;

   // The seventh member function inserts a range
   // at a specified position in the string
   string str7a ( "ABCDHIJ" );
   string str7b ( "abcdefgh" );
   basic_string <char>::iterator str7a_Iter = (str7a.begin ( ) + 4 );
   str7a.insert ( str7a_Iter , str7b.begin ( ) + 4 , str7b.end ( ) -1 );
   cout << "The string with a character inserted from a range is: "
        << str7a << endl;

   // The eighth member function inserts a number of
   // characters at a specified position in the string
   string str8 ( "ABCDHIJ" );
   basic_string <char>::iterator str8_Iter = ( str8.begin ( ) + 4 );
   str8.insert ( str8_Iter , 3 , 'e' );
   cout << "The string with a character inserted from a range is: "
        << str8 << endl;
}
```

```Output
The string with a C-string inserted at position 0 is: away.
The string with a C-string inserted at the end is: GoodBye.
The string with a string inserted at position 0 is: GoodBye.
The string with part of a string inserted at position 4 is: Good Baby.
The string with characters inserted is: The number is: 333.
The string with a character inserted is: ABCDeFG
The string with a character inserted from a range is: ABCDefgHIJ
The string with a character inserted from a range is: ABCDeeeHIJ
```

## <a name="basic_stringiterator"></a><a name="iterator"></a> `basic_string::iterator`

Тип, предоставляющий итератор произвольного доступа, который может читать элемент `const` в списке.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Комментарии

Тип `iterator` можно использовать для изменения значения символа и используется для прохода по строке в прямом направлении.

### <a name="example"></a>Пример

[`begin`](#begin)Пример объявления и использования см. в примере для `iterator` .

## <a name="basic_stringlength"></a><a name="length"></a> `basic_string::length`

Возвращает текущее количество элементов в строке.

```cpp
size_type length() const;
```

### <a name="remarks"></a>Комментарии

Функция-член совпадает с [`size`](#size) .

### <a name="example"></a>Пример

```cpp
// basic_string_length.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringmax_size"></a><a name="max_size"></a> `basic_string::max_size`

Возвращает максимальное количество символов в строке.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Максимальное количество символов, которое может содержать строка.

### <a name="remarks"></a>Комментарии

Исключение [ `length_error` класса](../standard-library/length-error-class.md) типа создается, когда операция создает строку с длиной, превышающей максимальный размер.

### <a name="example"></a>Пример

```cpp
// basic_string_max_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringnpos"></a><a name="npos"></a> `basic_string::npos`

Целочисленное значение без знака, инициализированное значением-1, которое указывает на отсутствие найденных или всех оставшихся символов при сбое функции поиска.

```cpp
static const size_type npos = -1;
```

### <a name="remarks"></a>Комментарии

Если возвращаемое значение должно быть проверено на `npos` значение, оно может не работать, если только возвращаемое значение не имеет тип [`size_type`](#size_type) , а не либо `int` `unsigned` .

### <a name="example"></a>Пример

[`find`](#find)Пример объявления и использования см. в примере для `npos` .

## <a name="basic_stringoperator"></a><a name="op_add_eq"></a> `basic_string::operator+=`

Присоединяет символы к строке.

```cpp
basic_string<CharType, Traits, Allocator>& operator+=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator+=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator+=(
    const basic_string<CharType, Traits, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Символ значение для добавления.

*`ptr`*\
Символы C-строки для добавления.

*`right`*\
Символы строки для добавления.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на добавляемый объект строки с символами, переданными функцией-членом.

### <a name="remarks"></a>Комментарии

Символы могут быть добавлены к строке с помощью `operator+=` функций или или [`append`](#append) [`push_back`](#push_back) . `operator+=` добавляет значения одиночных аргументов, а функция-член append с несколькими аргументами позволяет указывать для добавления определенную часть строки.

### <a name="example"></a>Пример

```cpp
// basic_string_op_app.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // appending a single character to a string
   string str1a ( "Hello" );
   cout << "The original string str1 is: " << str1a << endl;
   str1a +=  '!' ;
   cout << "The string str1 appended with an exclamation is: "
        << str1a << endl << endl;

   // The second member function
   // appending a C-string to a string
   string  str1b ( "Hello " );
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b << endl;
   str1b +=  cstr1b;
   cout << "Appending the C-string cstr1b to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function
   // appending one string to another in two ways,
   // comparing append and operator [ ]
   string str1d ( "Hello " ), str2d ( "Wide " ), str3d ( "World" );
   cout << "The string str2d is: " << str2d << endl;
   str1d.append ( str2d );
   cout << "The appended string str1d is: "
        << str1d << "." << endl;
   str1d += str3d;
   cout << "The doubly appended strig str1 is: "
        << str1d << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello
The string str1 appended with an exclamation is: Hello!

The C-string cstr1b is: Out There
Appending the C-string cstr1b to string str1 gives: Hello Out There.

The string str2d is: Wide
The appended string str1d is: Hello Wide .
The doubly appended strig str1 is: Hello Wide World.
```

## <a name="basic_stringoperator"></a><a name="op_eq"></a> `basic_string::operator=`

Назначает значения новых символов содержимому строки.

```cpp
basic_string<CharType, Traits, Allocator>& operator=(
    value_type char_value);

basic_string<CharType, Traits, Allocator>& operator=(
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>& right);

basic_string<CharType, Traits, Allocator>& operator=(
    const basic_string<CharType, Traits, Allocator>&& right);
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Символьное значение для присваивания.

*`ptr`*\
Указатель на символы C-строки, которые должны быть назначены целевой строке.

*`right`*\
Исходная строка, символы которой присваиваются целевой строке.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на объект строки, которому функция-член будет присваивать новые символы.

### <a name="remarks"></a>Комментарии

Строкам можно присваивать новые символьные значения. Новое значение может быть строкой, C-строкой или одним символом. `operator=`Может использоваться, если новое значение можно описать с помощью одного параметра, в противном случае можно использовать функцию-член с [`assign`](#assign) несколькими параметрами, чтобы указать, какая часть строки должна быть назначена целевой строке.

### <a name="example"></a>Пример

```cpp
// basic_string_op_assign.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function assigning a
   // character of a certain value to a string
   string str1a ( "Hello " );
   str1a = '0';
   cout << "The string str1 assigned with the zero character is: "
        << str1a << endl << endl;

   // The second member function assigning the
   // characters of a C-string to a string
   string  str1b;
   const char *cstr1b = "Out There";
   cout << "The C-string cstr1b is: " << cstr1b <<  "." << endl;
   str1b = cstr1b;
   cout << "Assigning the C-string cstr1a to string str1 gives: "
        << str1b << "." << endl << endl;

   // The third member function assigning the characters
   // from one string to another string in two equivalent
   // ways, comparing the assign and operator =
   string str1c ( "Hello" ), str2c ( "Wide" ), str3c ( "World" );
   cout << "The original string str1 is: " << str1c << "." << endl;
   cout << "The string str2c is: " << str2c << "." << endl;
   str1c.assign ( str2c );
   cout << "The string str1 newly assigned with string str2c is: "
        << str1c << "." << endl;
   cout << "The string str3c is: " << str3c << "." << endl;
   str1c = str3c;
   cout << "The string str1 reassigned with string str3c is: "
        << str1c << "." << endl << endl;
}
```

```Output
The string str1 assigned with the zero character is: 0

The C-string cstr1b is: Out There.
Assigning the C-string cstr1a to string str1 gives: Out There.

The original string str1 is: Hello.
The string str2c is: Wide.
The string str1 newly assigned with string str2c is: Wide.
The string str3c is: World.
The string str1 reassigned with string str3c is: World.
```

## <a name="basic_stringoperator"></a><a name="op_at"></a> `basic_string::operator[]`

Предоставляет ссылку на символ с указанным индексом в строке.

```cpp
const_reference operator[](size_type offset) const;
reference operator[](size_type offset);
```

### <a name="parameters"></a>Параметры

*`offset`*\
Индекс позиции элемента, на который должна быть ссылка.

### <a name="return-value"></a>Возвращаемое значение

Ссылка на символ строки в позиции, указанной с помощью индекса параметра.

### <a name="remarks"></a>Комментарии

Первый элемент строки имеет нулевой индекс, а следующие элементы последовательно индексируются положительными целыми числами. Это означает, что строка длиной *n* содержит *n*-й элемент, индексируемый по номеру *n* – 1.

`operator[]` работает быстрее, чем функция-член, [`at`](#at) предоставляющая доступ на чтение и запись к элементам строки.

`operator[]` не проверяет допустимость индекса, переданного в качестве параметра, но функция-член имеет значение, `at` поэтому ее следует использовать в действительности не обязательно. Недопустимый индекс (индекс меньше нуля или больше или равен размеру строки), переданный функции-члену, `at` вызывает исключение [ `out_of_range` класса](../standard-library/out-of-range-class.md) . Недопустимый индекс, переданный в `operator[]`, приводит к непредсказуемому поведению, однако индекс, равный длине строки, допустим для константных строк, и при передаче этого индекса оператор возвращает символ NULL.

Возвращаемая ссылка может быть недействительной при перераспределении строк или изменении для не `const` строк.

При компиляции с параметром, [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) равным 1 или 2, при попытке получить доступ к элементу за пределами строки произойдет ошибка времени выполнения. Дополнительные сведения см. в разделе [Проверенные итераторы](../standard-library/checked-iterators.md).

### <a name="example"></a>Пример

```cpp
// basic_string_op_ref.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" ), str2 ( "Goodbye world" );
   const string cstr1 ( "Hello there" ), cstr2 ( "Goodbye now" );
   cout << "The original string str1 is: " << str1 << endl;
   cout << "The original string str2 is: " << str2 << endl;

   // Element access to the non-const strings
   basic_string <char>::reference refStr1 = str1 [6];
   basic_string <char>::reference refStr2 = str2.at ( 3 );

   cout << "The character with an index of 6 in string str1 is: "
        << refStr1 << "." << endl;
   cout << "The character with an index of 3 in string str2 is: "
        << refStr2 << "." << endl;

   // Element access to the const strings
   basic_string <char>::const_reference crefStr1 = cstr1 [ cstr1.length ( ) ];
   basic_string <char>::const_reference crefStr2 = cstr2.at ( 8 );

   if ( crefStr1 == '\0' )
      cout << "The null character is returned as a valid reference."
           << endl;
   else
      cout << "The null character is not returned." << endl;
   cout << "The character with index of 8 in the const string cstr2 is: "
        << crefStr2 << "." << endl;
}
```

## <a name="basic_stringpointer"></a><a name="pointer"></a> `basic_string::pointer`

Тип, предоставляющий указатель на символьный элемент в строке или символьном массиве.

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Комментарии

Тип является синонимом `allocator_type::pointer`.

Для типа `string` он эквивалентен `char *` .

### <a name="example"></a>Пример

```cpp
// basic_string_pointer.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   basic_string<char>::pointer pstr1a = "In Here";
   char *cstr1b = "Out There";
   cout << "The string pstr1a is: " << pstr1a <<  "." << endl;
   cout << "The C-string cstr1b is: " << cstr1b << "." << endl;
}
```

```Output
The string pstr1a is: In Here.
The C-string cstr1b is: Out There.
```

## <a name="basic_stringpop_back"></a><a name="pop_back"></a> `basic_string::pop_back`

Удаляет последний элемент строки.

```cpp
void pop_back();
```

### <a name="remarks"></a>Комментарии

Эта функция-член вызывает `erase(size() - 1)`, чтобы удалить последний элемент последовательности, который должен быть непустым.

## <a name="basic_stringpush_back"></a><a name="push_back"></a> `basic_string::push_back`

Добавляет элемент в конец строки.

```cpp
void push_back(value_type char_value);
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Символ, который нужно добавить в конец строки.

### <a name="remarks"></a>Комментарии

Функция члена фактически вызывает `insert( end, char_value )` . Дополнительные сведения см. в разделах [`insert`](#insert) и [`end`](#end).

### <a name="example"></a>Пример

```cpp
// basic_string_push_back.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "abc" );
   basic_string <char>::iterator str_Iter, str1_Iter;

   cout << "The original string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;

   // str1.push_back ( 'd' );
   str1_Iter = str1.end ( );
   str1_Iter--;
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_Iter << endl;

   cout << "The modified string str1 is: ";
   for ( str_Iter = str1.begin( ); str_Iter != str1.end( ); str_Iter++ )
      cout << *str_Iter;
   cout << endl;
}
```

```Output
The original string str1 is: abc
The last character-letter of the modified str1 is now: c
The modified string str1 is: abc
```

## <a name="basic_stringrbegin"></a><a name="rbegin"></a> `basic_string::rbegin`

Возвращает итератор на первый элемент в обратной строке.

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает итератор произвольного доступа в первый элемент обращенной строки, указывая элемент, который был бы последним элементом в соответствующей необращенной строке.

### <a name="remarks"></a>Комментарии

`rbegin` используется с обратным строкой так же, как [`begin`](#begin) используется со строкой.

Если возвращаемое значение `rbegin` присваивается `const_reverse_iterator` , то строковый объект не может быть изменен. Если возвращаемое значение `rbegin` присваивается `reverse_iterator`, то объект string может быть изменен.

`rbegin`можно использовать для инициализации итерации по строке в обратном направлении.

### <a name="example"></a>Пример

```cpp
// basic_string_rbegin.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Able was I ere I saw Elba" ), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rbegin ( );
   // str1_rIter--;
   cout << "The first character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_rIter = 'A';
   cout << "The first character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'A';

   // For an empty string, begin is equivalent to end
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The first character-letter of the reversed string str1 is: a
The full reversed string str1 is:
ablE was I ere I saw elbA
The first character-letter of the modified str1 is now: A
The full modified reversed string str1 is now:
AblE was I ere I saw elbA
The string str2 is empty.
```

## <a name="basic_stringreference"></a><a name="reference"></a> `basic_string::reference`

Тип, предоставляющий ссылку на элемент в строке.

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="remarks"></a>Комментарии

Тип `reference` можно использовать для изменения значения элемента.

Тип является синонимом `allocator_type::reference`.

Для типа `string` он эквивалентен `chr&` .

### <a name="example"></a>Пример

[`at`](#at)Пример объявления и использования см. в примере для `reference` .

## <a name="basic_stringrend"></a><a name="rend"></a> `basic_string::rend`

Возвращает итератор, который указывает место, следующее за последним элементом в обращенной строке.

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>Возвращаемое значение

Обратный итератор произвольного доступа, который указывает место, следующее за последним элементом в обращенной строке.

### <a name="remarks"></a>Комментарии

`rend` используется с обратным строкой так же, как [`end`](#end) используется со строкой.

Если возвращаемое значение `rend` присваивается `const_reverse_iterator` , то строковый объект не может быть изменен. Если возвращаемое значение `rend` присваивается `reverse_iterator`, то объект string может быть изменен.

`rend` можно использовать, чтобы проверить, достиг ли обратный итератор конца очереди.

Значение, возвращаемое, `rend` не должно быть разыменовано.

### <a name="example"></a>Пример

```cpp
// basic_string_rend.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Able was I ere I saw Elba"), str2;
   basic_string <char>::reverse_iterator str_rIter, str1_rIter, str2_rIter;
   basic_string <char>::const_reverse_iterator str1_rcIter;

   str1_rIter = str1.rend ( );
   str1_rIter--;
   cout << "The last character-letter of the reversed string str1 is: "
        << *str1_rIter << endl;
   cout << "The full reversed string str1 is:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The dereferenced iterator can be used to modify a character
   *str1_rIter = 'o';
   cout << "The last character-letter of the modified str1 is now: "
        << *str1_rIter << endl;
   cout << "The full modified reversed string str1 is now:\n ";
   for ( str_rIter = str1.rbegin( ); str_rIter != str1.rend( ); str_rIter++ )
      cout << *str_rIter;
   cout << endl;

   // The following line would be an error because iterator is const
   // *str1_rcIter = 'T';

   // For an empty string, end is equivalent to begin
   if ( str2.rbegin( ) == str2.rend ( ) )
      cout << "The string str2 is empty." << endl;
   else
      cout << "The stringstr2  is not empty." << endl;
}
```

```Output
The last character-letter of the reversed string str1 is: A
The full reversed string str1 is:
ablE was I ere I saw elbA
The last character-letter of the modified str1 is now: o
The full modified reversed string str1 is now:
ablE was I ere I saw elbo
The string str2 is empty.
```

## <a name="basic_stringreplace"></a><a name="replace"></a> `basic_string::replace`

Заменяет элементы в строке в указанной позиции заданными символами или символами, скопированными из других диапазонов, строк или C-строк.

```cpp
basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    const basic_string<CharType, Traits, Allocator>& str,
    size_type position_2,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    size_type position_1,
    size_type number_1,
    size_type count,
    value_type char_value);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const basic_string<CharType, Traits, Allocator>& str);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const value_type* ptr,
    size_type number_2);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    size_type number_2,
    value_type char_value);

template <class InputIterator>
basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    InputIterator first,
    InputIterator last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_pointer first,
    const_pointer last);

basic_string<CharType, Traits, Allocator>& replace(
    iterator first0,
    iterator last0,
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>Параметры

*`str`*\
Строка, представляющая источник символов для строки операнда.

*`position_1`*\
Индекс строки операнда, в котором начинается замена.

*`number_1`*\
Максимальное количество заменяемых символов в строке операнда.

*`position_2`*\
Индекс строки параметра, в котором начинается копирование.

*`number_2`*\
Максимальное количество используемых символов из C-строки параметра.

*`ptr`*\
C-строка, представляющая источник символов для строки операнда.

*`char_value`*\
Символ, который должен копироваться в строку операнда.

*`first0`*\
Итератор, указывающий первый удаляемый символ в строке операнда.

*`last0`*\
Итератор, указывающий последний удаляемый символ в строке операнда.

*`first`*\
Итератор, const_pointer или const_iterator, указывающий первый символ, который должен копироваться в строку параметра.

*`last`*\
Итератор, const_pointer или const_iterator, указывающий последний символ, который должен копироваться в строку параметра.

*`count`*\
Количество раз, которое *`char_value`* копируется в строку операнда.

### <a name="return-value"></a>Возвращаемое значение

Строка операнда с выполненной заменой.

### <a name="example"></a>Пример

```cpp
// basic_string_replace.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first two member functions replace
   // part of the operand string with
   // characters from a parameter string or C-string
   string result1a, result1b;
   string s1o ( "AAAAAAAA" );
   string s1p ( "BBB" );
   const char* cs1p = "CCC";
   cout << "The operand string s1o is: " << s1o << endl;
   cout << "The parameter string s1p is: " << s1p << endl;
   cout << "The parameter C-string cs1p is: " << cs1p << endl;
   result1a = s1o.replace ( 1 , 3 , s1p );
   cout << "The result of s1o.replace ( 1 , 3 , s1p )\n is "
        << "the string: " << result1a << "." << endl;
   result1b = s1o.replace ( 5 , 3 , cs1p );
   cout << "The result of s1o.replace ( 5 , 3 , cs1p )\n is "
        << "the string: " << result1b << "." << endl;
   cout << endl;

   // The third & fourth member function replace
   // part of the operand string with characters
   // form part of a parameter string or C-string
   string result2a, result2b;
   string s2o ( "AAAAAAAA" );
   string s2p ( "BBB" );
   const char* cs2p = "CCC";
   cout << "The operand string s2o is: " << s2o << endl;
   cout << "The parameter string s1p is: " << s2p << endl;
   cout << "The parameter C-string cs2p is: " << cs2p << endl;
   result2a = s2o.replace ( 1 , 3 , s2p , 1 , 2 );
   cout << "The result of s2o.replace (1, 3, s2p, 1, 2)\n is "
        << "the string: " << result2a << "." << endl;
   result2b = s2o.replace ( 4 , 3 , cs2p , 1 );
   cout << "The result of s2o.replace (4 ,3 ,cs2p)\n is "
        << "the string: " << result2b << "." << endl;
   cout << endl;

   // The fifth member function replaces
   // part of the operand string with characters
   string result3a;
   string s3o ( "AAAAAAAA" );
   char ch3p = 'C';
   cout << "The operand string s3o is: " << s3o << endl;
   cout << "The parameter character c1p is: " << ch3p << endl;
   result3a = s3o.replace ( 1 , 3 , 4 , ch3p );
   cout << "The result of s3o.replace(1, 3, 4, ch3p)\n is "
        << "the string: " << result3a << "." << endl;
   cout << endl;

   // The sixth & seventh member functions replace
   // part of the operand string, delineated with iterators,
   // with a parameter string or C-string
   string s4o ( "AAAAAAAA" );
   string s4p ( "BBB" );
   const char* cs4p = "CCC";
   cout << "The operand string s4o is: " << s4o << endl;
   cout << "The parameter string s4p is: " << s4p << endl;
   cout << "The parameter C-string cs4p is: " << cs4p << endl;
   basic_string<char>::iterator IterF0, IterL0;
   IterF0 = s4o.begin ( );
   IterL0 = s4o.begin ( ) + 3;
   string result4a, result4b;
   result4a = s4o.replace ( IterF0 , IterL0 , s4p );
   cout << "The result of s1o.replace (IterF0, IterL0, s4p)\n is "
        << "the string: " << result4a << "." << endl;
   result4b = s4o.replace ( IterF0 , IterL0 , cs4p );
   cout << "The result of s4o.replace (IterF0, IterL0, cs4p)\n is "
        << "the string: " << result4b << "." << endl;
   cout << endl;

   // The 8th member function replaces
   // part of the operand string delineated with iterators
   // with a number of characters from a parameter C-string
   string s5o ( "AAAAAAAF" );
   const char* cs5p = "CCCBB";
   cout << "The operand string s5o is: " << s5o << endl;
   cout << "The parameter C-string cs5p is: " << cs5p << endl;
   basic_string<char>::iterator IterF1, IterL1;
   IterF1 = s5o.begin ( );
   IterL1 = s5o.begin ( ) + 4;
   string result5a;
   result5a = s5o.replace ( IterF1 , IterL1 , cs5p , 4 );
   cout << "The result of s5o.replace (IterF1, IterL1, cs4p ,4)\n is "
        << "the string: " << result5a << "." << endl;
   cout << endl;

   // The 9th member function replaces
   // part of the operand string delineated with iterators
   // with specified characters
   string s6o ( "AAAAAAAG" );
   char ch6p = 'q';
   cout << "The operand string s6o is: " << s6o << endl;
   cout << "The parameter character ch6p is: " << ch6p << endl;
   basic_string<char>::iterator IterF2, IterL2;
   IterF2 = s6o.begin ( );
   IterL2 = s6o.begin ( ) + 3;
   string result6a;
   result6a = s6o.replace ( IterF2 , IterL2 , 4 , ch6p );
   cout << "The result of s6o.replace (IterF1, IterL1, 4, ch6p)\n is "
        << "the string: " << result6a << "." << endl;
   cout << endl;

   // The 10th member function replaces
   // part of the operand string delineated with iterators
   // with part of a parameter string delineated with iterators
   string s7o ( "OOOOOOO" );
   string s7p ( "PPPP" );
   cout << "The operand string s7o is: " << s7o << endl;
   cout << "The parameter string s7p is: " << s7p << endl;
   basic_string<char>::iterator IterF3, IterL3, IterF4, IterL4;
   IterF3 = s7o.begin ( ) + 1;
   IterL3 = s7o.begin ( ) + 3;
   IterF4 = s7p.begin ( );
   IterL4 = s7p.begin ( ) + 2;
   string result7a;
   result7a = s7o.replace ( IterF3 , IterL3 , IterF4 , IterL4 );
   cout << "The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)\n is "
        << "the string: " << result7a << "." << endl;
   cout << endl;
}
```

```Output
The operand string s1o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs1p is: CCC
The result of s1o.replace ( 1 , 3 , s1p )
is the string: ABBBAAAA.
The result of s1o.replace ( 5 , 3 , cs1p )
is the string: ABBBACCC.

The operand string s2o is: AAAAAAAA
The parameter string s1p is: BBB
The parameter C-string cs2p is: CCC
The result of s2o.replace (1, 3, s2p, 1, 2)
is the string: ABBAAAA.
The result of s2o.replace (4 ,3 ,cs2p)
is the string: ABBAC.

The operand string s3o is: AAAAAAAA
The parameter character c1p is: C
The result of s3o.replace(1, 3, 4, ch3p)
is the string: ACCCCAAAA.

The operand string s4o is: AAAAAAAA
The parameter string s4p is: BBB
The parameter C-string cs4p is: CCC
The result of s1o.replace (IterF0, IterL0, s4p)
is the string: BBBAAAAA.
The result of s4o.replace (IterF0, IterL0, cs4p)
is the string: CCCAAAAA.

The operand string s5o is: AAAAAAAF
The parameter C-string cs5p is: CCCBB
The result of s5o.replace (IterF1, IterL1, cs4p ,4)
is the string: CCCBAAAF.

The operand string s6o is: AAAAAAAG
The parameter character ch6p is: q
The result of s6o.replace (IterF1, IterL1, 4, ch6p)
is the string: qqqqAAAAG.

The operand string s7o is: OOOOOOO
The parameter string s7p is: PPPP
The result of s7o.replace (IterF3 ,IterL3 ,IterF4 ,IterL4)
is the string: OPPOOOO.
```

## <a name="basic_stringreserve"></a><a name="reserve"></a> `basic_string::reserve`

Устанавливает вместимость строки не меньше указанного числа.

```cpp
void reserve(size_type count = 0);
```

### <a name="parameters"></a>Параметры

*`count`*\
Число символов, для которых резервируется память.

### <a name="remarks"></a>Комментарии

Наличие достаточной емкости важно, так как перераспределение занимает много времени. И он делает недействительными все ссылки, указатели и итераторы, ссылающиеся на символы в строке.

Концепция емкости для строковых типов объектов аналогична для объектов типа `vector` . В отличие от `vector` , функция члена `reserve` может быть вызвана для уменьшения емкости объекта. Это запрос без привязки и может как произойти, так и не произойти. Как значение по умолчанию для параметра равно нулю, вызов является несвязанным `reserve` запросом для сжатия емкости строки в соответствии с количеством символов, находящихся в настоящий момент в строке. Емкость никогда не уменьшается ниже текущего количества символов.

Вызов `reserve` является единственно возможным способом уменьшения емкости строки. Однако, как указано выше, это запрос без привязки и может не произойти.

### <a name="example"></a>Пример

```cpp
// basic_string_reserve.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1, sizerStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1, caprStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with added capacity
   str1.reserve ( 40 );
   sizerStr1 = str1.size ( );
   caprStr1 = str1.capacity ( );

   cout << "The string str1with augmented capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizerStr1 << "." << endl;
   cout << "The new capacity of string str1 is: "
        << caprStr1 << "." << endl << endl;

   // Compare size & capacity of the string
   // with downsized capacity
   str1.reserve ( );
   basic_string <char>::size_type sizedStr1;
   basic_string <char>::size_type capdStr1;
   sizedStr1 = str1.size ( );
   capdStr1 = str1.capacity ( );

   cout << "The string str1 with downsized capacity is: "
        << str1 << endl;
   cout << "The current size of string str1 is: "
        << sizedStr1 << "." << endl;
   cout << "The reduced capacity of string str1 is: "
        << capdStr1 << "." << endl << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The string str1with augmented capacity is: Hello world
The current size of string str1 is: 11.
The new capacity of string str1 is: 47.

The string str1 with downsized capacity is: Hello world
The current size of string str1 is: 11.
The reduced capacity of string str1 is: 47.
```

## <a name="basic_stringresize"></a><a name="resize"></a> `basic_string::resize`

Указывает новый размер строки, добавляя или удаляя элементы по мере необходимости.

```cpp
void resize(
    size_type count,);

void resize(
    size_type count,
    value_type char_value);
```

### <a name="parameters"></a>Параметры

*`count`*\
Новый размер строки.

*`char_value`*\
Значение, которое присоединяемые символы инициализируется с помощью, если требуется больше элементов.

### <a name="remarks"></a>Комментарии

Если конечный размер превышает максимальное количество символов, форма вызывает `length_error`.

### <a name="example"></a>Пример

```cpp
// basic_string_resize.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string  str1 ( "Hello world" );
   cout << "The original string str1 is: " << str1 << endl;

   basic_string <char>::size_type sizeStr1;
   sizeStr1 = str1.size ( );
   basic_string <char>::size_type capStr1;
   capStr1 = str1.capacity ( );

   // Compare size & capacity of the original string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 2 elements: exclamations
   str1.resize ( str1.size ( ) + 2 , '!' );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   cout << "The current size of resized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of resized string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to increase size by 20 elements:
   str1.resize ( str1.size ( ) + 20 );
   cout << "The resized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   capStr1 = str1.capacity ( );

   // Compare size & capacity of a string after resizing
   // note capacity increases automatically as required
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl << endl;

   // Use resize to downsize by 28 elements:
   str1.resize ( str1.size ( ) - 28 );
   cout << "The downsized string str1 is: " << str1 << endl;

   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   // Compare size & capacity of a string after downsizing
   cout << "The current size of downsized string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of downsized string str1 is: "
        << capStr1 << "." << endl;
}
```

```Output
The original string str1 is: Hello world
The current size of original string str1 is: 11.
The capacity of original string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of resized string str1 is: 13.
The capacity of resized string str1 is: 15.

The resized string str1 is: Hello world!!
The current size of modified string str1 is: 33.
The capacity of modified string str1 is: 47.

The downsized string str1 is: Hello
The current size of downsized string str1 is: 5.
The capacity of downsized string str1 is: 47.
```

## <a name="basic_stringreverse_iterator"></a><a name="reverse_iterator"></a> `basic_string::reverse_iterator`

Тип, предоставляющий ссылку на элемент в строке.

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Комментарии

Тип `reverse_iterator` может изменять значение символа и используется для последовательного выполнения итерации по строке в обратном направлении.

### <a name="example"></a>Пример

[`rbegin`](#rbegin)Пример объявления и использования см. в примере для `reverse_iterator` .

## <a name="basic_stringrfind"></a><a name="rfind"></a> `basic_string::rfind`

Поиск по строке в обратном направлении до первого вхождения подстроки, совпадающей с заданной последовательностью символов.

```cpp
size_type rfind(
    value_type char_value,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset = npos) const;

size_type rfind(
    const value_type* ptr,
    size_type offset,
    size_type count) const;

size_type rfind(
    const basic_string<CharType, Traits, Allocator>& str,
    size_type offset = npos) const;
```

### <a name="parameters"></a>Параметры

*`char_value`*\
Значение символа, для которого следует искать функцию-член.

*`offset`*\
Индекс позиции, в которой следует начать поиск.

*`ptr`*\
Строка C-string, для которой следует искать функцию-член.

*`count`*\
Число символов, начиная с первого, в строке C-string, для которой следует искать функцию-член.

*`str`*\
Строка, для которой следует искать функцию-член.

### <a name="return-value"></a>Возвращаемое значение

Индекс последнего вхождения первого символа искомой подстроки при поиске в обратном направлении, если она успешно найдена; в противном случае — `npos`.

### <a name="example"></a>Пример

```cpp
// basic_string_rfind.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function
   // searches for a single character in a string
   string str1 ( "Hello Everyone" );
   cout << "The original string str1 is: " << str1 << endl;
   basic_string <char>::size_type indexCh1a, indexCh1b;
   static const basic_string <char>::size_type npos = -1;

   indexCh1a = str1.rfind ( "e" , 9 );
   if ( indexCh1a != npos )
      cout << "The index of the 1st 'e' found before the 9th"
           << " position in str1 is: " << indexCh1a << endl;
   else
      cout << "The character 'e' was not found in str1 ." << endl;

   indexCh1b = str1.rfind ( "x" );
   if ( indexCh1b != npos )
      cout << "The index of the 'x' found in str1 is: "
           << indexCh1b << endl << endl;
   else
      cout << "The character 'x' was not found in str1."
           << endl << endl;

   // The second member function searches a string
   // for a substring as specified by a C-string
   string str2 ( "Let me make this perfectly clear." );
   cout << "The original string str2 is: " << str2 << endl;
   basic_string <char>::size_type indexCh2a, indexCh2b;

   const char *cstr2 = "perfect";
   indexCh2a = str2.rfind ( cstr2 , 30 );
   if ( indexCh2a != npos )
      cout << "The index of the 1st element of 'perfect' "
           << "before\n the 30th position in str2 is: "
           << indexCh2a << endl;
   else
      cout << "The substring 'perfect' was not found in str2 ."
           << endl;

   const char *cstr2b = "imperfectly";
   indexCh2b = str2.rfind ( cstr2b , 30 );
   if ( indexCh2b != npos )
      cout << "The index of the 1st element of 'imperfect' "
           << "before\n the 5th position in str3 is: "
           << indexCh2b << endl;
   else
      cout << "The substring 'imperfect' was not found in str2 ."
           << endl << endl;

   // The third member function searches a string
   // for a substring as specified by a C-string
   string str3 ( "It is a nice day. I am happy." );
   cout << "The original string str3 is: " << str3 << endl;
   basic_string <char>::size_type indexCh3a, indexCh3b;

   const char *cstr3a = "nice";
   indexCh3a = str3.rfind ( cstr3a );
   if ( indexCh3a != npos )
      cout << "The index of the 1st element of 'nice' "
           << "in str3 is: " << indexCh3a << endl;
   else
      cout << "The substring 'nice' was not found in str3 ."
           << endl;

   const char *cstr3b = "am";
   indexCh3b = str3.rfind ( cstr3b , indexCh3a + 25 , 2 );
   if ( indexCh3b != npos )
      cout << "The index of the next occurrence of 'am' in "
           << "str3 begins at: " << indexCh3b << endl << endl;
   else
      cout << "There is no next occurrence of 'am' in str3 ."
           << endl << endl;

   // The fourth member function searches a string
   // for a substring as specified by a string
   string str4 ( "This perfectly unclear." );
   cout << "The original string str4 is: " << str4 << endl;
   basic_string <char>::size_type indexCh4a, indexCh4b;

   string str4a ( "clear" );
   indexCh4a = str4.rfind ( str4a , 15 );
   if (indexCh4a != npos )
      cout << "The index of the 1st element of 'clear' "
           << "before\n the 15th position in str4 is: "
           << indexCh4a << endl;
   else
      cout << "The substring 'clear' was not found in str4 "
           << "before the 15th position." << endl;

   string str4b ( "clear" );
   indexCh4b = str4.rfind ( str4b );
   if ( indexCh4b != npos )
      cout << "The index of the 1st element of 'clear' "
           << "in str4 is: "
           << indexCh4b << endl;
   else
      cout << "The substring 'clear' was not found in str4 ."
           << endl << endl;
}
```

```Output
The original string str1 is: Hello Everyone
The index of the 1st 'e' found before the 9th position in str1 is: 8
The character 'x' was not found in str1.

The original string str2 is: Let me make this perfectly clear.
The index of the 1st element of 'perfect' before
the 30th position in str2 is: 17
The substring 'imperfect' was not found in str2 .

The original string str3 is: It is a nice day. I am happy.
The index of the 1st element of 'nice' in str3 is: 8
The index of the next occurrence of 'am' in str3 begins at: 20

The original string str4 is: This perfectly unclear.
The substring 'clear' was not found in str4 before the 15th position.
The index of the 1st element of 'clear' in str4 is: 17
```

## <a name="basic_stringshrink_to_fit"></a><a name="shrink_to_fit"></a> `basic_string::shrink_to_fit`

Удаляет излишнюю вместимость строки.

```cpp
void shrink_to_fit();
```

### <a name="remarks"></a>Комментарии

Эта функция-член удаляет все ненужное хранилище в контейнере.

## <a name="basic_stringsize"></a><a name="size"></a> `basic_string::size`

Возвращает текущее количество элементов в строке.

```cpp
size_type size() const;
```

### <a name="return-value"></a>Возвращаемое значение

Длина строки.

### <a name="example"></a>Пример

```cpp
// basic_string_size.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ("Hello world");
   cout << "The original string str1 is: " << str1 << endl;

   // The size and length member functions differ in name only
   basic_string <char>::size_type sizeStr1, lenStr1;
   sizeStr1 = str1.size (  );
   lenStr1 = str1.length (  );

   basic_string <char>::size_type capStr1, max_sizeStr1;
   capStr1 = str1.capacity (  );
   max_sizeStr1 = str1.max_size (  );

   // Compare size, length, capacity & max_size of a string
   cout << "The current size of original string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of original string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of original string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of original string str1 is: "
        << max_sizeStr1 << "." << endl << endl;

   str1.erase ( 6, 5 );
   cout << "The modified string str1 is: " << str1 << endl;

   sizeStr1 = str1.size ( );
   lenStr1 = str1.length ( );
   capStr1 = str1.capacity ( );
   max_sizeStr1 = str1.max_size ( );

   // Compare size, length, capacity & max_size of a string
   // after erasing part of the original string
   cout << "The current size of modified string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The current length of modified string str1 is: "
        << lenStr1 << "." << endl;
   cout << "The capacity of modified string str1 is: "
        << capStr1 << "." << endl;
   cout << "The max_size of modified string str1 is: "
        << max_sizeStr1 << "." << endl;
}
```

## <a name="basic_stringsize_type"></a><a name="size_type"></a> `basic_string::size_type`

Тип целого числа без знака, который может представлять число элементов и индексов в строке.

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="remarks"></a>Комментарии

Он эквивалентен `allocator_type::size_type` .

Для типа `string` он эквивалентен `size_t` .

### <a name="example"></a>Пример

```cpp
// basic_string_size_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;
   string str1 ( "Hello world" );

   basic_string <char>::size_type sizeStr1, capStr1;
   sizeStr1 = str1.size (  );
   capStr1 = str1.capacity (  );

   cout << "The current size of string str1 is: "
        << sizeStr1 << "." << endl;
   cout << "The capacity of string str1 is: " << capStr1
         << "." << endl;
}
```

```Output
The current size of string str1 is: 11.
The capacity of string str1 is: 15.
```

## <a name="basic_stringstarts_with"></a><a name="starts_with"></a> `basic_string::starts_with`

Проверьте, начинается ли строка с указанного префикса.

```cpp
bool starts_with(const CharType c) const noexcept;
bool starts_with(const CharType* const x) const noexcept;
bool starts_with(const basic_string_view sv) const noexcept;
```

### <a name="parameters"></a>Параметры

*`c`*\
Искомый префикс одного символа.

*`sv`*\
Строковое представление, содержащее префикс для поиска. \
Можно передать `std::basic_string` , который преобразует в строковое представление.

*`x`*\
Строка символов, завершающаяся нулем, содержащая префикс для поиска.

### <a name="return-value"></a>Возвращаемое значение

`true` значение, если строка начинается с указанного префикса; `false` в противном случае — значение.

### <a name="remarks"></a>Комментарии

`starts_with()` Новое в C++ 20. Чтобы использовать его, укажите [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) параметр компилятора.

Сведения о [`ends_with`](#ends_with) том, заканчивается ли строка указанным суффиксом, см. в разделе.

### <a name="example"></a>Пример

```cpp
// Requires /std:c++latest
#include <string>
#include <iostream>

int main()
{
    std::basic_string<char> str = "abcdefg";

    std::cout << std::boolalpha; // so booleans show as 'true'/'false'
    std::cout << str.starts_with('b') << '\n';
    std::cout << str.starts_with("aBc") << '\n';

    std::basic_string<char> str2 = "abc";
    std::cout << str.starts_with(str2);

    return 0;
}
```

```Output
false
false
true
```

## <a name="basic_stringsubstr"></a><a name="substr"></a> `basic_string::substr`

Копирует из указанного положения в строке подстроку, содержащую по крайней мере несколько символов.

```cpp
basic_string<CharType, Traits, Allocator> substr(
    size_type offset = 0,
    size_type count = npos) const;
```

### <a name="parameters"></a>Параметры

*`offset`*\
Индекс поиска элемента в позиции, от которой делается копия строки; значение по умолчанию — 0.

*`count`*\
Количество символов, копируемых при их наличии.

### <a name="return-value"></a>Возвращаемое значение

Объект подстроки, который является копией элементов строкового операнда, начиная с позиции, заданной первым аргументом.

### <a name="example"></a>Пример

```cpp
// basic_string_substr.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   string  str1 ("Heterological paradoxes are persistent.");
   cout << "The original string str1 is: \n " << str1
        << endl << endl;

   basic_string <char> str2 = str1.substr ( 6 , 7 );
   cout << "The substring str1 copied is: " << str2
        << endl << endl;

   basic_string <char> str3 = str1.substr (  );
   cout << "The default substring str3 is: \n " << str3
        <<  "\n which is the entire original string." << endl;
}
```

```Output
The original string str1 is:
Heterological paradoxes are persistent.

The substring str1 copied is: logical

The default substring str3 is:
Heterological paradoxes are persistent.
which is the entire original string.
```

## <a name="basic_stringswap"></a><a name="swap"></a> `basic_string::swap`

Меняет местами содержимое двух строк.

```cpp
void swap(
    basic_string<CharType, Traits, Allocator>& str);
```

### <a name="parameters"></a>Параметры

*`str`*\
Исходная строка, элементы которой должны быть заменены на объекты в целевой строке.

### <a name="remarks"></a>Комментарии

Если переставляемые строки имеют один и тот же объект allocator, то функция-член `swap`:

- происходит в постоянное время;
- не вызывает исключений;
- не делает недействительными никакие ссылки, указатели и итераторы, обозначающие элементы в этих двух строках.

В противном случае присваивания элементов и вызовы конструктора выделяются пропорционально числу элементов в двух управляемых последовательностях.

### <a name="example"></a>Пример

```cpp
// basic_string_swap.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   // Declaring an objects of type basic_string<char>
   string s1 ( "Tweedledee" );
   string s2 ( "Tweedledum" );
   cout << "Before swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;

   s1.swap ( s2 );
   cout << "After swapping string s1 and s2:" << endl;
   cout << " The basic_string s1 = " << s1 << "." << endl;
   cout << " The basic_string s2 = " << s2 << "." << endl;
}
```

```Output
Before swapping string s1 and s2:
The basic_string s1 = Tweedledee.
The basic_string s2 = Tweedledum.
After swapping string s1 and s2:
The basic_string s1 = Tweedledum.
The basic_string s2 = Tweedledee.
```

## <a name="basic_stringtraits_type"></a><a name="traits_type"></a> `basic_string::traits_type`

Тип, представляющий признаки символов для элементов, хранящихся в строке.

```cpp
typedef Traits traits_type;
```

### <a name="remarks"></a>Комментарии

Тип является синонимом второго параметра шаблона `Traits` .

Для типа `string` он эквивалентен `char_traits<char>` .

### <a name="example"></a>Пример

[`copy`](../standard-library/char-traits-struct.md#copy)Пример объявления и использования см. в примере для `traits_type` .

## <a name="basic_stringvalue_type"></a><a name="value_type"></a> `basic_string::value_type`

Тип, представляющий тип символов, хранящихся в строке.

```cpp
typedef typename allocator_type::value_type value_type;
```

### <a name="remarks"></a>Комментарии

Он эквивалентен `traits_type::char_type` и эквивалентен `char` для объектов типа `string` .

### <a name="example"></a>Пример

```cpp
// basic_string_value_type.cpp
// compile with: /EHsc
#include <string>
#include <iostream>

int main( )
{
   using namespace std;

   basic_string<char>::value_type ch1 = 'G';

   char ch2 = 'H';

   cout << "The character ch1 is: " << ch1 << "." << endl;
   cout << "The character ch2 is: " << ch2 << "." << endl;
}
```

```Output
The character ch1 is: G.
The character ch2 is: H.
```

## <a name="see-also"></a>См. также раздел

[`<string>`](../standard-library/string.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
