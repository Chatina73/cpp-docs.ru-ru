---
title: Класс time_get
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get
- locale/std::time_get::char_type
- locale/std::time_get::iter_type
- locale/std::time_get::date_order
- locale/std::time_get::do_date_order
- locale/std::time_get::do_get
- locale/std::time_get::do_get_date
- locale/std::time_get::do_get_monthname
- locale/std::time_get::do_get_time
- locale/std::time_get::do_get_weekday
- locale/std::time_get::do_get_year
- locale/std::time_get::get
- locale/std::time_get::get_date
- locale/std::time_get::get_monthname
- locale/std::time_get::get_time
- locale/std::time_get::get_weekday
- locale/std::time_get::get_year
helpviewer_keywords:
- std::time_get [C++]
- std::time_get [C++], char_type
- std::time_get [C++], iter_type
- std::time_get [C++], date_order
- std::time_get [C++], do_date_order
- std::time_get [C++], do_get
- std::time_get [C++], do_get_date
- std::time_get [C++], do_get_monthname
- std::time_get [C++], do_get_time
- std::time_get [C++], do_get_weekday
- std::time_get [C++], do_get_year
- std::time_get [C++], get
- std::time_get [C++], get_date
- std::time_get [C++], get_monthname
- std::time_get [C++], get_time
- std::time_get [C++], get_weekday
- std::time_get [C++], get_year
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
ms.openlocfilehash: df5a6da3995b1485585a3105ac027f19a27dc8eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505187"
---
# <a name="timeget-class"></a>Класс time_get

Данный класс шаблона описывает объект, который можно использовать как аспект языкового стандарта для управления преобразованиями последовательностей типа `CharType` в значения времени.

## <a name="syntax"></a>Синтаксис

```cpp
template <class CharType,
    class InputIterator = istreambuf_iterator<CharType>>
class time_get : public time_base;
```

### <a name="parameters"></a>Параметры

*CharType*<br/>
Тип, используемый внутри программы для кодирования символов.

*InputIterator*<br/>
Итератор, из которого считываются значения времени.

## <a name="remarks"></a>Примечания

Как и в случае любого другого аспекта языкового стандарта, начальное сохраненное значение статического идентификатора объекта равно нулю. Первая попытка получить доступ к сохраненному значению сохранит уникальное положительное значение в **id.**

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[time_get](#time_get)|Конструктор для объектов типа `time_get`.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[char_type](#char_type)|Тип, используемый для описания символа, используемого языковым стандартом.|
|[iter_type](#iter_type)|Тип, который описывает итератор ввода.|

### <a name="member-functions"></a>Функции-члены

|Функция-член|Описание|
|-|-|
|[date_order](#date_order)|Возвращает порядок даты, используемый аспектом.|
|[do_date_order](#do_date_order)|Защищенная виртуальная функция-член, вызываемая для возврата порядка даты использовала аспектом.|
|[do_get](#do_get)|Считывает и преобразует символьные данные в значение времени.|
|[do_get_date](#do_get_date)|Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве даты, созданной спецификатором `x` для `strftime`.|
|[do_get_monthname](#do_get_monthname)|Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве названия месяца.|
|[do_get_time](#do_get_time)|Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве даты, созданной спецификатором `X` для `strftime`.|
|[do_get_weekday](#do_get_weekday)|Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве названия дня недели.|
|[do_get_year](#do_get_year)|Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве названия года.|
|[get](#get)|Считывает данные из источника символьных данных и преобразует их в значение времени, сохраняемое в структуре времени.|
|[get_date](#get_date)|Анализирует строку как дату, созданную спецификатором `x` для `strftime`.|
|[get_monthname](#get_monthname)|Анализирует строку как название месяца.|
|[get_time](#get_time)|Анализирует строку как дату, созданную спецификатором `X` для `strftime`.|
|[get_weekday](#get_weekday)|Анализирует строку как название дня недели.|
|[get_year](#get_year)|Анализирует строку как название года.|

## <a name="requirements"></a>Требования

**Заголовок:** \<locale>

**Пространство имен:** std

## <a name="char_type"></a> time_get::char_type

Тип, используемый для описания символа, используемого языковым стандартом.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Примечания

Тип является синонимом для параметра-шаблона **CharType**.

## <a name="date_order"></a> time_get::date_order

Возвращает порядок даты, используемый аспектом.

```cpp
dateorder date_order() const;
```

### <a name="return-value"></a>Возвращаемое значение

Порядок даты, используемый аспектом.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_date_order](#do_date_order).

### <a name="example"></a>Пример

```cpp
// time_get_date_order.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
void po( char *p )
{
   locale loc( p );

   time_get <char>::dateorder order = use_facet <time_get <char> >( loc ).date_order ( );
   cout << loc.name( );
   switch (order){
      case time_base::dmy: cout << "(day, month, year)" << endl;
      break;
      case time_base::mdy: cout << "(month, day, year)" << endl;
      break;
      case time_base::ydm: cout << "(year, day, month)" << endl;
      break;
      case time_base::ymd: cout << "(year, month, day)"<< endl;
      break;
      case time_base::no_order: cout << "(no_order)"<< endl;
      break;
   }
}

int main( )
{
   po( "C" );
   po( "german" );
   po( "English_Britain" );
}
```

```Output
C(month, day, year)
German_Germany.1252(day, month, year)
English_United Kingdom.1252(day, month, year)
```

## <a name="do_date_order"></a> time_get::do_date_order

Защищенная виртуальная функция-член, вызываемая для возврата порядка даты использовала аспектом.

```cpp
virtual dateorder do_date_order() const;
```

### <a name="return-value"></a>Возвращаемое значение

Порядок даты, используемый аспектом.

### <a name="remarks"></a>Примечания

Виртуальная защищенная функция-член возвращает значение типа **time_base::dateorder**, которое описывает порядок сопоставления компонентов данных типом [do_get_date](#do_get_date). В этой реализации используется значение **time_base::mdy**, соответствующее датам в форме 2 декабря 1979.

### <a name="example"></a>Пример

См. тип [date_order](#date_order), вызывающий `do_date_order`, в примере.

## <a name="do_get"></a> time_get::do_get

Считывает и преобразует символьные данные в значение времени. Принимает один описатель преобразования и модификатор.

```cpp
virtual iter_type
    do_get(
iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, который указывает на начало преобразуемой последовательности.

*последний*<br/>
Входной итератор, который указывает на конец последовательности.

*iosbase*<br/>
Объект потока.

*state*<br/>
Поле в iosbase где задаются соответствующие элементы битовой маски для указания ошибок.

*ptm*<br/>
Указатель на структуру времени, где будет храниться время.

*FMT*<br/>
Символ описателя преобразования.

*Mod*<br/>
Необязательный символ модификатора.

### <a name="return-value"></a>Возвращаемое значение

Возвращает итератор, назначающий первый непреобразованный элемент. Ошибка преобразования устанавливает `ios_base::failbit` в `state` и возвращает *первый*.

### <a name="remarks"></a>Примечания

Виртуальная функция-член преобразует и пропускает один или несколько входных элементов в диапазоне [`first`, `last`) для определения значения, хранящиеся в один или несколько членов `*pt`. Ошибка преобразования устанавливает `ios_base::failbit` в `state` и возвращает *первый*. В противном случае функция возвращает итератор, назначающий первый непреобразованный элемент.

Описатели преобразования:

`'a'` или `'A'` — ведет себя так же, как [time_get::get_weekday](#get_weekday).

`'b'`, `'B'` или `'h'` — ведет себя так же, как [time_get::get_monthname](#get_monthname).

`'c'` — аналогичен `"%b %d %H : %M : %S %Y"`.

`'C'` — преобразует десятичное поле ввода в диапазоне [0, 99] в значение `val` и сохраняет `val * 100 - 1900` в `pt-&tm_year`.

`'d'` или `'e'` — преобразует десятичное поле ввода в диапазоне [1, 31] и сохраняет его значение в `pt-&tm_mday`.

`'D'` — аналогичен `"%m / %d / %y"`.

`'H'` — преобразует десятичное поле ввода в диапазоне [0, 23] и сохраняет его значение в `pt-&tm_hour`.

`'I'` — преобразует десятичное поле ввода в диапазоне [0, 11] и сохраняет его значение в `pt-&tm_hour`.

`'j'` — преобразует десятичное поле ввода в диапазоне [1, 366] и сохраняет его значение в `pt-&tm_yday`.

`'m'` — преобразует десятичное поле ввода в диапазоне [1, 12] в значение `val` и сохраняет `val - 1` в `pt-&tm_mon`.

`'M'` — преобразует десятичное поле ввода в диапазоне [0, 59] и сохраняет его значение в `pt-&tm_min`.

`'n'` или `'t'` — аналогичен `" "`.

`'p'` — преобразует AM или am в ноль, а PM или pm — в 12 и добавляет это значение к `pt-&tm_hour`.

`'r'` — аналогичен `"%I : %M : %S %p"`.

`'R'` — аналогичен `"%H %M"`.

`'S'` — преобразует десятичное поле ввода в диапазоне [0, 59] и сохраняет его значение в `pt-&tm_sec`.

`'T'` или `'X'` — аналогичен `"%H : %M : S"`.

`'U'` — преобразует десятичное поле ввода в диапазоне [0, 53] и сохраняет его значение в `pt-&tm_yday`.

`'w'` — преобразует десятичное поле ввода в диапазоне [0, 6] и сохраняет его значение в `pt-&tm_wday`.

`'W'` — преобразует десятичное поле ввода в диапазоне [0, 53] и сохраняет его значение в `pt-&tm_yday`.

`'x'` — аналогичен `"%d / %m / %y"`.

`'y'` — преобразует десятичное поле ввода в диапазоне [0, 99] в значение `val` и сохраняет `val < 69  val + 100 : val` в `pt-&tm_year`.

`'Y'` — ведет себя так же, как [time_get::get_year](#get_year).

Все другие описатели преобразования устанавливают `ios_base::failbit` в `state` и возвращают значение. В этой реализации любой модификатор не оказывает влияния.

## <a name="do_get_date"></a> time_get::do_get_date

Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве даты, созданной спецификатором *x* для `strftime`.

```cpp
virtual iter_type do_get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о дате.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Виртуальная защищенная функция-член пытается сопоставить последовательные элементы, начиная с первого в последовательности [`first`, `last`), пока не распознает полное, непустое целочисленное поле ввода даты. При успешном выполнении она преобразует это поле в его эквивалентное значение как компоненты **tm::tm\_понедельник**, **tm::tm\_день**, и **tm::tm\_год** и сохраняет результаты в `ptm->tm_mon`, `ptm->tm_day`, и `ptm->tm_year`, соответственно. Она возвращает итератор, обозначающий первый элемент после поля ввода даты. В противном случае функция задает `iosbase::failbit` в *состояние*. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого поля ввода даты. В любом случае, если возвращаемое значение равно *последнего*, функция задает `ios_base::eofbit` в *состояние*.

Формат для поля ввода даты зависит от языкового стандарта. Для языкового стандарта по умолчанию поле ввода даты имеет вид МММ ДД, ГГГГ, где:

- MMM сопоставляется вызовом метода [get_monthname](#get_monthname), это месяц.

- ДД — это последовательность десятичных цифр, соответствующее числовое значение которой должно находиться в диапазоне [1, 31], это день месяца.

- ГГГГ сопоставляется вызовом метода [get_year](#get_year), это год.

Литеральные пробелы и запятые должны соответствовать соответствующим элементам во входной последовательности.

### <a name="example"></a>Пример

См. пример для [get_date](#get_date), который вызывает `do_get_date`.

## <a name="do_get_monthname"></a> time_get::do_get_monthname

Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве названия месяца.

```cpp
virtual iter_type do_get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Не используется.

*state*<br/>
Выходной параметр, задающий нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о месяце.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Виртуальная защищенная функция-член пытается сопоставить последовательные элементы, начиная с первого в последовательности [`first`, `last`), пока не распознает полное, непустое целочисленное поле ввода месяца. При успешном выполнении она преобразует это поле в его эквивалентное значение как компонент **tm::tm\_понедельник**и сохраняет результат в `ptm->tm_mon`. Она возвращает итератор, обозначающий первый элемент после поля ввода месяца. В противном случае функция задает `ios_base::failbit` в *состояние*. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого поля ввода месяца. В любом случае, если возвращаемое значение равно *последнего*, функция задает `ios_base::eofbit` в *состояние*.

Поле ввода месяца это последовательность, соответствующая самому длинному множеству последовательностей с учетом языковых стандартов, таких как "янв.", "январь", "фев.", "февраль" и т. д. Преобразованное значение — количество месяцев с января.

### <a name="example"></a>Пример

См. пример для [get_monthname](#get_monthname), который вызывает `do_get_monthname`.

## <a name="do_get_time"></a> time_get::do_get_time

Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве даты, созданной спецификатором *x* для `strftime`.

```cpp
virtual iter_type do_get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Не используется.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о дате.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Виртуальная защищенная функция-член пытается сопоставить последовательные элементы, начиная с первого в последовательности [`first`, `last`), пока не распознает полное, непустое целочисленное поле ввода времени. При успешном выполнении она преобразует это поле в его эквивалентное значение как компоненты `tm::tm_hour`, `tm::tm_min`, и `tm::tm_sec`и сохраняет результаты в `ptm->tm_hour`, `ptm->tm_min`, и `ptm->tm_sec`, соответственно. Она возвращает итератор, обозначающий первый элемент после поля ввода даты. В противном случае функция задает `ios_base::failbit` в *состояние*. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого поля ввода времени. В любом случае, если возвращаемое значение равно *последнего*, функция задает `ios_base::eofbit` в *состояние*.

В этой реализации поле ввода времени имеет вид ЧЧ:ММ:СС, где:

- ЧЧ — это последовательность десятичных цифр, соответствующее числовое значение которой должно находиться в диапазоне [0, 24), это час дня;

- ММ — это последовательность десятичных цифр, соответствующее числовое значение которой должно находиться в диапазоне [0, 60), это минуты часа;

- СС — это последовательность десятичных цифр, соответствующее числовое значение которой должно находиться в диапазоне [0, 60), это секунды минуты.

Литеральные двоеточия должны соответствовать соответствующим элементам во входной последовательности.

### <a name="example"></a>Пример

См. пример для [get_time](#get_time), который вызывает `do_get_time`.

## <a name="do_get_weekday"></a> time_get::do_get_weekday

Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве названия дня недели.

```cpp
virtual iter_type do_get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о дне недели.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Виртуальный защищенная функция-член пытается сопоставить последовательные элементы, начиная с *первый* в последовательности [ `first`, `last`) пока распознает полное, непустое weekday поле ввода. При успешном выполнении она преобразует это поле в его эквивалентное значение как компонент **tm::tm\_поля wday**и сохраняет результат в `ptm->tm_wday`. Она возвращает итератор, обозначающий первый элемент после поля ввода дня недели. В противном случае функция задает `ios_base::failbit` в *состояние*. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого поля ввода дня недели. В любом случае, если возвращаемое значение равно *последнего*, функция задает `ios_base::eofbit` в *состояние*.

Поле ввода дня недели — это последовательность, соответствующая самому длинному множеству последовательностей с учетом языковых стандартов, таких как "пнд", "понедельник", "втр", "вторник" и т. д. Преобразованное значение — количество дней с понедельника.

### <a name="example"></a>Пример

См. пример для [get_weekday](#get_weekday), который вызывает `do_get_weekday`.

## <a name="do_get_year"></a> time_get::do_get_year

Защищенная виртуальная функция-член, вызываемая для того, чтобы выполнить синтаксический анализ строки в качестве названия года.

```cpp
virtual iter_type do_get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о годе.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Виртуальный защищенная функция-член пытается сопоставить последовательные элементы, начиная с *первый* в последовательности [ `first`, `last`) пока распознает полное, непустое год поле ввода. При успешном выполнении она преобразует это поле в его эквивалентное значение как компонент **tm::tm\_год**и сохраняет результат в `ptm->tm_year`. Она возвращает итератор, обозначающий первый элемент после поля ввода года. В противном случае функция задает `ios_base::failbit` в *состояние*. Она возвращает итератор, обозначающий первый элемент после любого префикса допустимого поля ввода года. В любом случае, если возвращаемое значение равно *последнего*, функция задает `ios_base::eofbit` в *состояние*.

Поле ввода года — это последовательность десятичных цифр, соответствующее числовое значение которой должно находиться в диапазоне [1900, 2036). Сохраненное значение — это значение минус 1900. В этой реализации значения в диапазоне [69, 136) представляют диапазон лет [1969, 2036). Значения в диапазоне [0, 69) также допустимы, но они могут представлять либо диапазон лет [1900, 1969), либо [2000, 2069) в зависимости от конкретной среды перевода.

### <a name="example"></a>Пример

См. пример для [get_year](#get_year), который вызывает `do_get_year`.

## <a name="get"></a> time_get::get

Считывает данные из источника символьных данных и преобразует их в значение времени, сохраняемое в структуре времени. Первая функция принимает один описатель и модификатор преобразования, а вторая — несколько.

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char fmt,
    char mod) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm,
    char_type* fmt_first,
    char_type* fmt_last) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, который указывает начало преобразуемой последовательности.

*последний*<br/>
Входной итератор, который указывает конец преобразуемой последовательности.

*iosbase*<br/>
Поток.

*state*<br/>
Для состояния потока задаются соответствующие элементы битовой маски для указания ошибок.

*ptm*<br/>
Указатель на структуру времени, где будет храниться время.

*FMT*<br/>
Символ описателя преобразования.

*Mod*<br/>
Необязательный символ модификатора.

*fmt_first*<br/>
Указывает на начало директив формата.

*fmt_last*<br/>
Указывает на конец директив формата.

### <a name="return-value"></a>Возвращаемое значение

Возвращает итератор, указывающий на первый символ после данных, который был использован для назначения структуры времени `*ptm`.

### <a name="remarks"></a>Примечания

Первая функция-член возвращает значение `do_get(first, last, iosbase, state, ptm, fmt, mod)`.

Вторая функция-член вызывает `do_get` в формате с разделением `[fmt_first, fmt_last)`. Она воспринимает формат как последовательность полей, каждое из которых определяет преобразование нуля или большего числа входных элементов, разделенных `[first, last)`. Возвращает итератор, назначающий первый непреобразованный элемент. Существует три типа полей.

Знак процента (%) в формате, с последующим необязательным модификатором *mod* в наборе [EOQ #], затем следует описатель преобразования *fmt*, заменяет *первый* значением, возвращенным по `do_get(first, last, iosbase, state, ptm, fmt, mod)`. Ошибка преобразования устанавливает `ios_base::failbit` в *состояние* и возвращает.

Элемент пробела в формате пропускает ноль или более последних входных элементов пробелов.

Любой другой элемент в формате должен соответствовать следующему входному элементу, который пропускается. Ошибка сопоставления устанавливает `ios_base::failbit` в *состояние* и возвращает.

## <a name="get_date"></a> time_get::get_date

Анализирует строку как дату, созданную спецификатором *x* для `strftime`.

```cpp
iter_type get_date(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о дате.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_get_date](#do_get_date)(`first`, `last`, `iosbase`, `state`, `ptm`).

Обратите внимание, что месяцы отсчитываются от 0 до 11.

### <a name="example"></a>Пример

```cpp
// time_get_get_date.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset(&t, 0, sizeof(struct tm));

   pszGetF << "July 4, 2000";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get<char> >
   (loc).get_date(basic_istream<char>::_Iter(pszGetF.rdbuf( ) ),
            basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if ( st & ios_base::failbit )
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(July 4, 2000) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 4
tm_mon: 6
tm_year: 100
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_monthname"></a> time_get::get_monthname

Анализирует строку как название месяца.

```cpp
iter_type get_monthname(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Не используется.

*state*<br/>
Выходной параметр, задающий нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о месяце.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_get_monthname](#do_get_monthname)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Пример

```cpp
// time_get_get_monthname.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "juillet";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet <time_get <char> >
   (loc).get_monthname(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
              basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << "\ntm_mday: " << t.tm_mday
      << "\ntm_mon: " << t.tm_mon
      << "\ntm_year: " << t.tm_year
      << "\ntm_wday: " << t.tm_wday
      << "\ntm_yday: " << t.tm_yday
      << "\ntm_isdst: " << t.tm_isdst
      << endl;
}
```

```Output
time_get(juillet) =
tm_sec: 0
tm_min: 0
tm_hour: 0
tm_mday: 0
tm_mon: 6
tm_year: 0
tm_wday: 0
tm_yday: 0
tm_isdst: 0
```

## <a name="get_time"></a> time_get::get_time

Анализирует строку как дату, созданную спецификатором *x* для `strftime`.

```cpp
iter_type get_time(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Не используется.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о дате.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_get_time](#do_get_time)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Пример

```cpp
// time_get_get_time.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "11:13:20";
   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get <char> >
      (loc).get_time(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_sec: " << t.tm_sec
      << "\ntm_min: " << t.tm_min
      << "\ntm_hour: " << t.tm_hour
      << endl;
}
```

```Output
time_get::get_time(11:13:20) =
tm_sec: 20
tm_min: 13
tm_hour: 11
```

## <a name="get_weekday"></a> time_get::get_weekday

Анализирует строку как название дня недели.

```cpp
iter_type get_weekday(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о дне недели.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_get_weekday](#do_get_weekday)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Пример

```cpp
// time_get_get_weekday.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc ( "French" );
   basic_stringstream< char > pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "mercredi";
   pszGetF.imbue(loc);
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_weekday(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_time("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_wday: " << t.tm_wday
      << endl;
}
```

```Output
time_get::get_time(mercredi) =
tm_wday: 3
```

## <a name="get_year"></a> time_get::get_year

Анализирует строку как название года.

```cpp
iter_type get_year(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    tm* ptm) const;
```

### <a name="parameters"></a>Параметры

*Первый*<br/>
Входной итератор, адресующий начало последовательности для преобразования.

*последний*<br/>
Входной итератор, адресующий конец последовательности для преобразования.

*iosbase*<br/>
Флаг формата, который, будучи установленным, указывает, что символ валюты не обязателен; в противном случае он обязателен.

*state*<br/>
Устанавливает нужные элементы битовой маски для состояния потока согласно тому, успешно ли выполнились операции.

*ptm*<br/>
Указатель на место, где будет храниться информация о годе.

### <a name="return-value"></a>Возвращаемое значение

Входной итератор, адресующий первый элемент после поля ввода.

### <a name="remarks"></a>Примечания

Функция-член возвращает [do_get_year](#do_get_year)(`first`, `last`, `iosbase`, `state`, `ptm`).

### <a name="example"></a>Пример

```cpp
// time_get_get_year.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
#include <time.h>
using namespace std;
int main( )
{
   locale loc;
   basic_stringstream<char> pszGetF, pszPutF, pszGetI, pszPutI;
   ios_base::iostate st = 0;
   struct tm t;
   memset( &t, 0, sizeof( struct tm ) );

   pszGetF << "1928";

   pszGetF.imbue( loc );
   basic_istream<char>::_Iter i = use_facet
      <time_get<char> >
      (loc).get_year(basic_istream<char>::_Iter(pszGetF.rdbuf( )),
               basic_istream<char>::_Iter(0), pszGetF, st, &t);

   if (st & ios_base::failbit)
      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") FAILED on char: " << *i << endl;
   else

      cout << "time_get::get_year("<< pszGetF.rdbuf( )->str( )<< ") ="
      << "\ntm_year: " << t.tm_year
      << endl;
}
```

```Output
time_get::get_year(1928) =
tm_year: 28
```

## <a name="iter_type"></a> time_get::iter_type

Тип, который описывает итератор ввода.

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>Примечания

Этот тип является синонимом для параметра-шаблона **InputIterator**.

## <a name="time_get"></a> time_get::time_get

Конструктор для объектов типа `time_get`.

```cpp
explicit time_get(size_t refs = 0);
```

### <a name="parameters"></a>Параметры

*Refs*<br/>
Целочисленное значение, используемое для указания типа управления памятью для объекта.

### <a name="remarks"></a>Примечания

Возможные значения *refs* параметра и их важность:

- 0: время существования объекта управляется языковыми стандартами, которые его содержат.

- 1: время существования объекта должно управляться вручную.

- \> 1: эти значения не определены.

Прямые примеры привести нельзя, так как деструктор защищен.

Конструктор инициализирует свой базовый объект с **языкового стандарта::**[аспекта](../standard-library/locale-class.md#facet_class)(`refs`).

## <a name="see-also"></a>См. также

[\<locale>](../standard-library/locale.md)<br/>
[Класс time_base](../standard-library/time-base-class.md)<br/>
[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
