---
title: Операторы &lt;regex&gt;
ms.date: 11/04/2016
f1_keywords:
- regex/std::operator!=
- regex/std::operator>
- regex/std::operator>=
- regex/std::operator<
- regex/std::operator<=
- regex/std::operator==
- regex/std::operator<<
ms.assetid: ec623e65-c186-491f-aa18-6b12b47e1127
ms.openlocfilehash: 8795d0f1c387fb87c44f2d68c45aa27d1edbfb79
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689073"
---
# <a name="ltregexgt-operators"></a>Операторы &lt;regex&gt;

||||
|-|-|-|
|[оператор!= ](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|
|[оператор==](#op_eq_eq)|

## <a name="op_neq"></a> operator!=

Сравнение различных объектов на неравенство.

```cpp
template <class BidIt>
bool operator!=(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator!=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator!=(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator!=(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator!=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator!=(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator!=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);

template <class BidIt, class Alloc>
bool operator!=(const match_results<BidIt, Alloc>& left,
    const match_results<BidIt, Alloc>& right);
```

### <a name="parameters"></a>Параметры

@No__t_1 с *двунаправленным письмом*
Тип итератора.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

*left* \
Левый из сравниваемых объектов.

*справа* \
Правый из сравниваемых объектов.

### <a name="remarks"></a>Заметки

Каждый оператор-шаблон возвращает `!(left == right)`.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_ne.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "match == " << mr.str() << std::endl;
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "match != match == " << std::boolalpha
        << (mr != mr) << std::endl;
    std::cout << "sub != sub == " << std::boolalpha
        << (sub != sub) << std::endl;

    std::cout << "string(\"aab\") != sub == " << std::boolalpha
        << (Mystr("aab") != sub) << std::endl;
    std::cout << "sub != string(\"aab\") == " << std::boolalpha
        << (sub != Mystr("aab")) << std::endl;

    std::cout << "\"aab\" != sub == " << std::boolalpha
        << ("aab" != sub) << std::endl;
    std::cout << "sub != \"aab\" == " << std::boolalpha
        << (sub != "aab") << std::endl;

    std::cout << "'a' != sub == " << std::boolalpha
        << ('a' != sub) << std::endl;
    std::cout << "sub != 'a' == " << std::boolalpha
        << (sub != 'a') << std::endl;

    return (0);
    }
```

```Output
match == caaa
sub == aaa

match != match == false
sub != sub == false
string("aab") != sub == true
sub != string("aab") == true
"aab" != sub == true
sub != "aab" == true
'a' != sub == true
sub != 'a' == true
```

## <a name="op_lt"></a> operator&lt;

Сравнение "меньше, чем" для различных объектов.

```cpp
template <class BidIt>
bool operator<(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator<(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator<(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Параметры

@No__t_1 с *двунаправленным письмом*
Тип итератора.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

*left* \
Левый из сравниваемых объектов.

*справа* \
Правый из сравниваемых объектов.

### <a name="remarks"></a>Заметки

Каждый оператор-шаблон преобразует свои аргументы в строковый тип и возвращает значение true, только если преобразованное значение *Left* сравнивается со значением *right*.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_lt.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub < sub == " << std::boolalpha
        << (sub < sub) << std::endl;

    std::cout << "string(\"aab\") < sub == " << std::boolalpha
        << (Mystr("aab") < sub) << std::endl;
    std::cout << "sub < string(\"aab\") == " << std::boolalpha
        << (sub < Mystr("aab")) << std::endl;

    std::cout << "\"aab\" < sub == " << std::boolalpha
        << ("aab" < sub) << std::endl;
    std::cout << "sub < \"aab\" == " << std::boolalpha
        << (sub < "aab") << std::endl;

    std::cout << "'a' < sub == " << std::boolalpha
        << ('a' < sub) << std::endl;
    std::cout << "sub < 'a' == " << std::boolalpha
        << (sub < 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub < sub == false
string("aab") < sub == false
sub < string("aab") == true
"aab" < sub == false
sub < "aab" == true
'a' < sub == true
sub < 'a' == false
```

## <a name="op_lt_lt"></a> operator&lt;&lt;

Вставляет в поток sub_match.

```cpp
template <class Elem, class IOtraits, class Alloc, class BidIt>
basic_ostream<Elem, IOtraits>& operator<<(basic_ostream<Elem, IOtraits>& os,
    const sub_match<BidIt>& right);
```

### <a name="parameters"></a>Параметры

*Elem* \
Тип элемента.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

@No__t_1 с *двунаправленным письмом*
Тип итератора.

\ *ОС*
Выходной поток.

*справа* \
Вставляемый объект.

### <a name="remarks"></a>Заметки

Оператор-шаблон возвращает `os << right.str()`.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_ins.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[0];
    std::cout << "whole match: " << sub << std::endl;

    return (0);
    }
```

```Output
whole match: caaa
```

## <a name="op_lt_eq"></a> operator&lt;=

Сравнение "меньше или равно" для различных объектов.

```cpp
template <class BidIt>
bool operator<=(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator<=(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator<=(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator<=(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator<=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Параметры

@No__t_1 с *двунаправленным письмом*
Тип итератора.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

*left* \
Левый из сравниваемых объектов.

*справа* \
Правый из сравниваемых объектов.

### <a name="remarks"></a>Заметки

Каждый оператор-шаблон возвращает `!(right < left)`.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_le.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub <= sub == " << std::boolalpha
        << (sub <= sub) << std::endl;

    std::cout << "string(\"aab\") <= sub == " << std::boolalpha
        << (Mystr("aab") <= sub) << std::endl;
    std::cout << "sub <= string(\"aab\") == " << std::boolalpha
        << (sub <= Mystr("aab")) << std::endl;

    std::cout << "\"aab\" <= sub == " << std::boolalpha
        << ("aab" <= sub) << std::endl;
    std::cout << "sub <= \"aab\" == " << std::boolalpha
        << (sub <= "aab") << std::endl;

    std::cout << "'a' <= sub == " << std::boolalpha
        << ('a' <= sub) << std::endl;
    std::cout << "sub <= 'a' == " << std::boolalpha
        << (sub <= 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub <= sub == true
string("aab") <= sub == false
sub <= string("aab") == true
"aab" <= sub == false
sub <= "aab" == true
'a' <= sub == true
sub <= 'a' == false
```

## <a name="op_eq_eq"></a> operator==

Сравнение различных объектов на равенство.

```cpp
template <class BidIt>
bool operator==(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator==(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator==(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator==(const typename iterator_traits<BidIt>::value_type* left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator==(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type* right);

template <class BidIt>
bool operator==(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator==(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);

template <class BidIt, class Alloc>
bool operator==(const match_results<BidIt, Alloc>& left,
    const match_results<BidIt, Alloc>& right);
```

### <a name="parameters"></a>Параметры

@No__t_1 с *двунаправленным письмом*
Тип итератора.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

*left* \
Левый из сравниваемых объектов.

*справа* \
Правый из сравниваемых объектов.

### <a name="remarks"></a>Заметки

Каждый оператор-шаблон преобразует каждый из своих аргументов в тип string и возвращает результат сравнения преобразованных объектов на равенство.

При преобразовании аргументов в тип string оператор-шаблон использует первое из следующего списка преобразований, которое можно применить:

аргументы, типы которых являются специализацией шаблона класса `match_results` или `sub_match` преобразуются путем вызова `str` функции-члена.

аргументы, типы которых являются специализацией шаблона класса `basic_string`, не изменяются;

все остальные типы аргументов преобразуются путем передачи значения аргумента в конструктор для соответствующей специализации шаблона класса `basic_string`.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_eq.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "match == " << mr.str() << std::endl;
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "match == match == " << std::boolalpha
        << (mr == mr) << std::endl;
    std::cout << "sub == sub == " << std::boolalpha
        << (sub == sub) << std::endl;

    std::cout << "string(\"aab\") == sub == " << std::boolalpha
        << (Mystr("aab") == sub) << std::endl;
    std::cout << "sub == string(\"aab\") == " << std::boolalpha
        << (sub == Mystr("aab")) << std::endl;

    std::cout << "\"aab\" == sub == " << std::boolalpha
        << ("aab" == sub) << std::endl;
    std::cout << "sub == \"aab\" == " << std::boolalpha
        << (sub == "aab") << std::endl;

    std::cout << "'a' == sub == " << std::boolalpha
        << ('a' == sub) << std::endl;
    std::cout << "sub == 'a' == " << std::boolalpha
        << (sub == 'a') << std::endl;

    return (0);
    }
```

```Output
match == caaa
sub == aaa

match == match == true
sub == sub == true
string("aab") == sub == false
sub == string("aab") == false
"aab" == sub == false
sub == "aab" == false
'a' == sub == false
sub == 'a' == false
```

## <a name="op_gt"></a> operator&gt;

Сравнение "больше, чем" для различных объектов.

```cpp
template <class BidIt>
bool operator>(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator>(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator>(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Параметры

@No__t_1 с *двунаправленным письмом*
Тип итератора.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

*left* \
Левый из сравниваемых объектов.

*справа* \
Правый из сравниваемых объектов.

### <a name="remarks"></a>Заметки

Каждый оператор-шаблон возвращает `right < left`.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_gt.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub > sub == " << std::boolalpha
        << (sub > sub) << std::endl;

    std::cout << "string(\"aab\") > sub == " << std::boolalpha
        << (Mystr("aab") > sub) << std::endl;
    std::cout << "sub > string(\"aab\") == " << std::boolalpha
        << (sub > Mystr("aab")) << std::endl;

    std::cout << "\"aab\" > sub == " << std::boolalpha
        << ("aab" > sub) << std::endl;
    std::cout << "sub > \"aab\" == " << std::boolalpha
        << (sub > "aab") << std::endl;

    std::cout << "'a' > sub == " << std::boolalpha
        << ('a' > sub) << std::endl;
    std::cout << "sub > 'a' == " << std::boolalpha
        << (sub > 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub > sub == false
string("aab") > sub == true
sub > string("aab") == false
"aab" > sub == true
sub > "aab" == false
'a' > sub == false
sub > 'a' == true
```

## <a name="op_gt_eq"></a> operator&gt;=

Сравнение "больше или равно" для различных объектов.

```cpp
template <class BidIt>
bool operator>=(const sub_match<BidIt>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>=(
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& left,
    const sub_match<BidIt>& right);

template <class BidIt, class IOtraits, class Alloc>
bool operator>=(const sub_match<BidIt>& left,
    const basic_string<typename iterator_traits<BidIt>::value_type, IOtraits, Alloc>& right);

template <class BidIt>
bool operator>=(const typename iterator_traits<BidIt>::value_type *left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type *right);

template <class BidIt>
bool operator>=(const typename iterator_traits<BidIt>::value_type& left,
    const sub_match<BidIt>& right);

template <class BidIt>
bool operator>=(const sub_match<BidIt>& left,
    const typename iterator_traits<BidIt>::value_type& right);
```

### <a name="parameters"></a>Параметры

@No__t_1 с *двунаправленным письмом*
Тип итератора.

*Иотраитс* \
Класс характеристик строки.

@No__t_1 *выделения*
Класс распределителя.

*left* \
Левый из сравниваемых объектов.

*справа* \
Правый из сравниваемых объектов.

### <a name="remarks"></a>Заметки

Каждый оператор-шаблон возвращает `!(left < right)`.

### <a name="example"></a>Пример

```cpp
// std__regex__operator_ge.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

typedef std::cmatch::string_type Mystr;
int main()
    {
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::csub_match sub = mr[1];
    std::cout << "sub == " << sub << std::endl;
    std::cout << std::endl;

    std::cout << "sub >= sub == " << std::boolalpha
        << (sub >= sub) << std::endl;

    std::cout << "string(\"aab\") >= sub == " << std::boolalpha
        << (Mystr("aab") >= sub) << std::endl;
    std::cout << "sub >= string(\"aab\") == " << std::boolalpha
        << (sub >= Mystr("aab")) << std::endl;

    std::cout << "\"aab\" >= sub == " << std::boolalpha
        << ("aab" >= sub) << std::endl;
    std::cout << "sub >= \"aab\" == " << std::boolalpha
        << (sub >= "aab") << std::endl;

    std::cout << "'a' >= sub == " << std::boolalpha
        << ('a' >= sub) << std::endl;
    std::cout << "sub >= 'a' == " << std::boolalpha
        << (sub >= 'a') << std::endl;

    return (0);
    }
```

```Output
sub == aaa

sub >= sub == true
string("aab") >= sub == true
sub >= string("aab") == false
"aab" >= sub == true
sub >= "aab" == false
'a' >= sub == false
sub >= 'a' == true
```

## <a name="see-also"></a>См. также

[\<regex>](../standard-library/regex.md)\
\ [класса regex_constants](../standard-library/regex-constants-class.md)
\ [класса regex_error](../standard-library/regex-error-class.md)
[функции > \<regex](../standard-library/regex-functions.md) \
\ [класса regex_iterator](../standard-library/regex-iterator-class.md)
\ [класса regex_token_iterator](../standard-library/regex-token-iterator-class.md)
\ [класса regex_traits](../standard-library/regex-traits-class.md)
[Определения типов \<regex>](../standard-library/regex-typedefs.md)
