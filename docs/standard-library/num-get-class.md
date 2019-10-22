---
title: Класс num_get
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 5c6fec7002541b519d7cf7d043eed3e5c932bcb9
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689230"
---
# <a name="num_get-class"></a>Класс num_get

Шаблон класса, описывающий объект, который может служить в качестве аспекта языкового стандарта для управления преобразованием последовательностей типа `CharType` в числовые значения.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>Параметры

*CharType* \
Тип, используемый внутри программы для кодирования символов в языковом стандарте.

*InputIterator* \
Тип итератора, из которого функции получения числовых значений считывают своих входные данные.

## <a name="remarks"></a>Заметки

Как и в случае любого другого аспекта языкового стандарта, начальное сохраненное значение статического идентификатора объекта равно нулю. Первая попытка получить доступ к сохраненному значению сохранит уникальное положительное значение в **id.**

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[num_get](#num_get)|Конструктор для объектов типа `num_get`, используемых для извлечения числовых значений из последовательностей.|

### <a name="typedefs"></a>Typedefs

|Имя типа|Описание|
|-|-|
|[char_type](#char_type)|Тип, используемый для описания символа, используемого языковым стандартом.|
|[iter_type](#iter_type)|Тип, который описывает итератор ввода.|

### <a name="member-functions"></a>Функции-члены

|Функция Member|Описание|
|-|-|
|[do_get](#do_get)|Виртуальная функция, вызываемая для извлечения числового или логического значения из последовательности символов, представляющей денежное значение.|
|[get](#get)|Извлекает числовое или логическое значение из последовательности символов.|

## <a name="requirements"></a>Требования

**Заголовок:** \<locale>

**Пространство имен:** std

## <a name="char_type"></a>  num_get::char_type

Тип, используемый для описания символа, используемого языковым стандартом.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Заметки

Тип является синонимом параметра-шаблона **CharType**.

## <a name="do_get"></a>  num_get::do_get

Виртуальная функция, вызываемая для извлечения числового или логического значения из последовательности символов, представляющей денежное значение.

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

### <a name="parameters"></a>Параметры

*первый* \
Начало диапазона символов для чтения числа.

*последние* \
Конец диапазона символов для чтения числа.

*_Iosbase* \
[Ios_base](../standard-library/ios-base-class.md), флаги которого используются для преобразования.

*_State* \
Состояние, к которому при сбое добавляется failbit (см. [ios_base::iostate](../standard-library/ios-base-class.md#iostate)).

*val* \
Прочитанное значение.

### <a name="return-value"></a>Возвращаемое значение

Итератор после чтения значения.

### <a name="remarks"></a>Заметки

Первая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```

сопоставляет последовательные элементы, начиная с *первого* в последовательности, `[first, last)`, пока не распознает полное непустое целочисленное поле ввода. В случае успешного выполнения он преобразует это поле в эквивалентное значение типа **Long**и сохраняет результат в *Val*. Она возвращает итератор, обозначающий первый элемент после числового поля ввода. В противном случае функция сохраняет ничего в *Val* и задает `ios_base::failbit` в `state`. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого целочисленного поля ввода. В любом случае, если возвращаемое значение равно `last`, функция устанавливает `ios_base::eofbit` в `state`.

Целочисленное поле ввода преобразуется теми же правилами, которые используются функциями просмотра для сопоставления и преобразования последовательности элементов **char** из файла. (Предполагается, что каждый такой элемент **char** сопоставлен с эквивалентным элементом типа `Elem` простым, «один к одному», сопоставлению.) Эквивалентная спецификация преобразования сканирования определяется следующим образом.

Если `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct), спецификация преобразования имеет значение `lo`.

Если `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex), спецификация преобразования имеет значение `lx`.

Если `iosbase.flags() & ios_base::basefield == 0`, спецификация преобразования имеет значение `li`.

В противном случае спецификация преобразования имеет значение `ld`.

Формат целочисленного поля вывода далее определяется [аспектом языкового стандарта](../standard-library/locale-class.md#facet_class)`fac`, возвращаемым вызовом [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())`. В частности:

`fac.` [numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` определяет, как группируются цифры слева от любого десятичного разделителя;

`fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` определяет последовательность, которая разделяет группы цифр слева от любого десятичного разделителя.

Если в числовом поле ввода нет экземпляров `fac.thousands_sep()`, то ограничения группировки не применяются. В противном случае применяются ограничения группировки, накладываемые `fac.grouping()`, и разделители удаляются перед выполнением преобразования сканирования.

Четвертая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

ведет себя так же, как первая, за исключением того, что она заменяет спецификацию преобразования `ld` на `lu`. При успешном выполнении он преобразует числовое поле ввода в значение типа **без знака Long** и сохраняет это значение в *Val*.

Пятая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```

ведет себя так же, как первая, за исключением того, что она заменяет спецификацию преобразования `ld` на `lld`. При успешном выполнении он преобразует числовое поле ввода в значение типа **Long** Long и сохраняет это значение в *Val*.

Шестая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```

ведет себя так же, как первая, за исключением того, что она заменяет спецификацию преобразования `ld` на `llu`. При успешном выполнении он преобразует числовое поле ввода в значение типа **без знака** Long и сохраняет это значение в *Val*.

Седьмая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```

ведет себя так же, как первая, за исключением того, что она пытается сопоставить полное, непустое вещественное поле ввода. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` определяет последовательность, которая отделяет цифры целой части от цифр дробной части. Эквивалентный спецификатор преобразования сканирования — `lf`.

Восьмая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

ведет себя так же, как первая, за исключением того, что она пытается сопоставить полное, непустое вещественное поле ввода. `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` определяет последовательность, которая отделяет цифры целой части от цифр дробной части. Эквивалентный спецификатор преобразования сканирования — `lf`.

Девятая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

ведет себя так же, как восьмая, за исключением того, что эквивалентный спецификатор преобразования сканирования — `Lf`.

Десятая виртуальная Защищенная функция — член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

ведет себя так же, как первая, за исключением того, что эквивалентный спецификатор преобразования сканирования — `p`.

Последняя (одиннадцатая) виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

ведет себя так же, как первая, за исключением того, что она пытается сопоставить полное, непустое логическое поле ввода. При успешном выполнении он преобразует логическое поле ввода в значение типа **bool** и сохраняет это значение в *Val*.

Логическое поле ввода может иметь одну из двух форм. Если `iosbase.flags() & ios_base::` [boolalpha](../standard-library/ios-functions.md#boolalpha) имеет значение false, поле совпадает с целочисленным полем ввода, за исключением того, что преобразованное значение должно быть 0 (false) или 1 (true). В противном случае последовательность должна соответствовать либо `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#falsename)`()` (для false), либо `fac.`[numpunct::truename](../standard-library/numpunct-class.md#truename)`()` (для true).

### <a name="example"></a>Пример

См. пример для [get](#get), где виртуальная функция-член вызывается из `do_get`.

## <a name="get"></a>  num_get::get

Извлекает числовое или логическое значение из последовательности символов.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

### <a name="parameters"></a>Параметры

*первый* \
Начало диапазона символов для чтения числа.

*последние* \
Конец диапазона символов для чтения числа.

*_Iosbase* \
[Ios_base](../standard-library/ios-base-class.md), флаги которого используются для преобразования.

*_State* \
Состояние, к которому при сбое добавляется failbit (см. [ios_base::iostate](../standard-library/ios-base-class.md#iostate)).

*val* \
Прочитанное значение.

### <a name="return-value"></a>Возвращаемое значение

Итератор после чтения значения.

### <a name="remarks"></a>Заметки

Все функции-члены возвращают [do_get](#do_get)(`first`, `last`, `_Iosbase`, `_State`, `val`).

Первая защищенная виртуальная функция-член пытается сопоставить последовательные элементы, начиная с первого в последовательности [`first`, `last`), пока не распознает полное, непустое целочисленное поле ввода. В случае успешного выполнения он преобразует это поле в эквивалентное значение типа **Long** и сохраняет результат в *Val*. Она возвращает итератор, обозначающий первый элемент после числового поля ввода. В противном случае функция сохраняет ничего в *Val* и задает `ios_base::failbit` в _ *состоянии*. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого целочисленного поля ввода. В любом случае, если возвращаемое значение равно *Last*, функция устанавливает `ios_base::eofbit` в *_State*.

Целочисленное поле ввода преобразуется теми же правилами, которые используются функциями просмотра для сопоставления и преобразования последовательности элементов **char** из файла. Предполагается, что каждый такой элемент **char** сопоставлен с эквивалентным элементом типа `CharType` простым сопоставлением «один к одному». Эквивалентная спецификация преобразования сканирования определяется следующим образом:

- Если `iosbase`. [Флаги](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[Oct](../standard-library/ios-functions.md#oct), спецификация преобразования — .`lo`

- Если **iosbase. flags**  & **ios_base:: basefield**  ==  `ios_base::`[Hex](../standard-library/ios-functions.md#hex), спецификация преобразования `lx`.

- If **iosbase.flags** & **ios_base::basefield** == 0, спецификация преобразования будет иметь значение `li`.

- В противном случае спецификация преобразования имеет значение `ld`.

Формат целочисленного поля ввода далее определяется [аспектом языкового стандарта](../standard-library/locale-class.md#facet_class)**fac**, возвращаемым вызовом [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>(**iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). В частности:

- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) определяет, как группируются цифры слева от любого десятичного разделителя.

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) определяет последовательность, которая разделяет группы цифр слева от любого десятичного разделителя.

Если в части значения числового поля ввода не появляется экземпляров **fac**. `thousands_sep`, то ограничения группировки не применяются. В противном случае применяются любые ограничения группировки, определяемые в **fac**. **grouping**, и разделители удаляются перед преобразованием сканирования.

Вторая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```

ведет себя так же, как первая, за исключением того, что она заменяет спецификацию преобразования `ld` на `lu`. В случае успешного выполнения он преобразует числовое поле ввода в значение типа **без знака Long** и сохраняет это значение в *Val*.

Третья виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```

ведет себя так же, как первая, за исключением того, что она пытается сопоставить полное, непустое вещественное поле ввода. **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) определяет последовательность, которая отделяет цифры целой части от цифр дробной части. Эквивалентный спецификатор преобразования сканирования — `lf`.

Четвертая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```

ведет себя аналогично третьему, за исключением того, что эквивалентный спецификатор преобразования сканирования `Lf`.

Пятая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```

ведет себя так же, как первая, за исключением того, что эквивалентный спецификатор преобразования сканирования — `p`.

Шестая виртуальная защищенная функция-член:

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```

ведет себя так же, как первая, за исключением того, что она пытается сопоставить полное, непустое логическое поле ввода. При успешном выполнении он преобразует логическое поле ввода в значение типа **bool** и сохраняет это значение в *Val*.

Логическое поле ввода может иметь одну из двух форм. Если **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) имеет значение **false** — это то же самое, что и целочисленное поле ввода, за исключением того, что преобразованное значение должно быть либо 0 (для **false**), либо 1 (для **true**). В противном случае последовательность должна соответствовать либо **fac**. [falsename](../standard-library/numpunct-class.md#falsename) (для значения **false**), либо **fac**. [truename](../standard-library/numpunct-class.md#truename) (для значения **true**).

### <a name="example"></a>Пример

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="iter_type"></a>  num_get::iter_type

Тип, который описывает итератор ввода.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Заметки

Этот тип является синонимом для параметра шаблона `InputIterator`.

## <a name="num_get"></a>  num_get::num_get

Конструктор для объектов типа `num_get`, используемых для извлечения числовых значений из последовательностей.

```cpp
explicit num_get(size_t _Refs = 0);
```

### <a name="parameters"></a>Параметры

*_Refs* \
Целочисленное значение, используемое для указания типа управления памятью для объекта.

### <a name="remarks"></a>Заметки

Возможные значения для параметра *_Refs* и их значимость:

- 0: время существования объекта управляется языковыми стандартами, которые его содержат.

- 1: время существования объекта должно управляться вручную.

- \> 1: эти значения не определены.

Прямые примеры привести нельзя, так как деструктор защищен.

Конструктор инициализирует свой базовый объект с **locale::** [facet](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="see-also"></a>См. также

[\<locale>](../standard-library/locale.md)\
[Класс facet](../standard-library/locale-class.md#facet_class)\
[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
