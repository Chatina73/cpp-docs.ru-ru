---
title: Класс basic_istream
ms.date: 11/04/2016
f1_keywords:
- istream/std::basic_istream
- istream/std::basic_istream::gcount
- istream/std::basic_istream::get
- istream/std::basic_istream::getline
- 'istream/std::basic_istream::'
- istream/std::basic_istream::peek
- istream/std::basic_istream::putback
- istream/std::basic_istream::read
- istream/std::basic_istream::readsome
- istream/std::basic_istream::seekg
- istream/std::basic_istream::sentry
- istream/std::basic_istream::swap
- istream/std::basic_istream::sync
- istream/std::basic_istream::tellg
- istream/std::basic_istream::unget
helpviewer_keywords:
- std::basic_istream [C++]
- std::basic_istream [C++], gcount
- std::basic_istream [C++], get
- std::basic_istream [C++], getline
- std::basic_istream [C++], OVERWRITE
- std::basic_istream [C++], peek
- std::basic_istream [C++], putback
- std::basic_istream [C++], read
- std::basic_istream [C++], readsome
- std::basic_istream [C++], seekg
- std::basic_istream [C++], sentry
- std::basic_istream [C++], swap
- std::basic_istream [C++], sync
- std::basic_istream [C++], tellg
- std::basic_istream [C++], unget
ms.assetid: c7c27111-de6d-42b4-95a3-a7e65259bf17
ms.openlocfilehash: d1a76e9c639ac56ca693527543ecff5c597456f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452552"
---
# <a name="basicistream-class"></a>Класс basic_istream

Описывает объект, управляющий извлечением элементов и закодированных объектов из буфера потока с элементами типа `Elem`, также называемого [char_type](../standard-library/basic-ios-class.md#char_type). Их признаки символов определяются классом *Tr*, также называемым [traits_type](../standard-library/basic-ios-class.md#traits_type).

## <a name="syntax"></a>Синтаксис

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_istream : virtual public basic_ios<Elem, Tr>
```

## <a name="remarks"></a>Примечания

Большинство функций-членов, которые перегружают [оператор>>](#op_gt_gt), — это форматированные входные функции. Они следуют этому шаблону:

```cpp
iostate state = goodbit;
const sentry ok(*this);

if (ok)
{
    try
    {
        /*extract elements and convert
            accumulate flags in state.
            store a successful conversion*/
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);

return (*this);
```

Многие другие функции-члены — это неформатированные входные функции. Они следуют этому шаблону:

```cpp
iostate state = goodbit;
count = 0;    // the value returned by gcount
const sentry ok(*this, true);

if (ok)
{
    try
    {
        /* extract elements and deliver
            count extracted elements in count
            accumulate flags in state */
    }
    catch (...)
    {
        try
        {
            setstate(badbit);

        }
        catch (...)
        {
        }
        if ((exceptions()& badbit) != 0)
            throw;
    }
}
setstate(state);
```

Обе группы функций вызывают [SetState](../standard-library/basic-ios-class.md#setstate)(`eofbit`), если они обнаруживают конец файла при извлечении элементов.

Объект класса `basic_istream`< `Elem`, *Tr*> хранит:

- виртуальный открытый базовый объект класса [basic_ios](../standard-library/basic-ios-class.md)< `Elem`*Tr*> `.`;

- Счетчик извлечений для последней неформатированной операции ввода (вызывается `count` в предыдущем коде).

## <a name="example"></a>Пример

Подробнее о входных потоках см. в примере для [класса basic_ifstream](../standard-library/basic-ifstream-class.md).

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[basic_istream](#basic_istream)|Создает объект типа `basic_istream`.|

### <a name="member-functions"></a>Функции-члены

|Функция Member|Описание|
|-|-|
|[gcount](#gcount)|Возвращает число символов, считанных во время последнего неформатированного ввода.|
|[get](#get)|Считывает один или несколько символов из входного потока.|
|[getline](#getline)|Считывает строку из входного потока.|
|[ignore](#ignore)|Пропускает несколько элементов после текущей позиции чтения.|
|[peek](#peek)|Возвращает следующий символ для чтения.|
|[putback](#putback)|Помещает указанный символ в поток.|
|[read](#read)|Считывает указанное количество символов из потока и сохраняет их в массиве.|
|[readsome](#readsome)|Чтение только из буфера.|
|[seekg](#seekg)|Перемещает позицию чтения в потоке.|
|[sentry](#sentry)|Вложенный класс описывает объект, объявление которого структурирует форматированные и неформатированные входные функции.|
|[swap](#swap)|Меняет местами этот объект `basic_istream` с указанным параметром объекта `basic_istream`.|
|[sync](#sync)|Синхронизирует устройство ввода, связанное с потоком, с буфером потока.|
|[tellg](#tellg)|Сообщает текущую позицию чтения в потоке.|
|[unget](#unget)|Помещает самый последний считанный символ обратно в поток.|

### <a name="operators"></a>Операторы

|Оператор|Описание|
|-|-|
|[оператор>>](#op_gt_gt)|Вызывает функцию для входного потока или считывает форматированные данные из входного потока.|
|[оператор=](#op_eq)|Назначает `basic_istream` справа от оператора этому объекту. Это назначение перемещения с использованием ссылки `rvalue`, после которого не остается копии.|

## <a name="requirements"></a>Требования

**Заголовок:** \<istream>

**Пространство имен:** std

## <a name="basic_istream"></a>  basic_istream::basic_istream

Создает объект типа `basic_istream`.

```cpp
explicit basic_istream(
    basic_streambuf<Elem, Tr>* strbuf,
    bool _Isstd = false);

basic_istream(basic_istream&& right);
```

### <a name="parameters"></a>Параметры

*strBuf*\
Объект типа [basic_streambuf](../standard-library/basic-streambuf-class.md).

*_Isstd*\
**значение true** , если это стандартный поток; в противном случае — **значение false**.

*Правильно*\
Объект `basic_istream` для копирования.

### <a name="remarks"></a>Примечания

Первый конструктор инициализирует базовый класс путем вызова [init](../standard-library/basic-ios-class.md#init)(_S `trbuf`). Он также хранит нуль в счетчике извлечений. Дополнительные сведения об этом счетчике извлечений см. в разделе "Примечания" [класса basic_istream](../standard-library/basic-istream-class.md).

Второй конструктор инициализирует базовый класс путем вызова `move( right)`. Он также сохраняет _R `ight.gcount()` в счетчике извлечений и сохраняет нуль в счетчике извлечений для _R `ight`.

### <a name="example"></a>Пример

Дополнительные сведения о входных потоках см. в примере для [класса basic_ifstream](../standard-library/basic-ifstream-class.md#basic_ifstream).

## <a name="gcount"></a>  basic_istream::gcount

Возвращает число символов, считанных во время последнего неформатированного ввода.

```cpp
streamsize gcount() const;
```

### <a name="return-value"></a>Возвращаемое значение

Счетчик извлечений.

### <a name="remarks"></a>Примечания

Используйте [basic_istream::get](#get) для чтения символов без форматирования.

### <a name="example"></a>Пример

```cpp
// basic_istream_gcount.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   cout << "Type the letter 'a': ";

   ws( cin );
   char c[10];

   cin.get( &c[0],9 );
   cout << c << endl;

   cout << cin.gcount( ) << endl;
}
```

```Input
a
```

```Output
Type the letter 'a': a
1
```

## <a name="get"></a>  basic_istream::get

Считывает один или несколько символов из входного потока.

```cpp
int_type get();

basic_istream<Elem, Tr>& get(Elem& Ch);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count);
basic_istream<Elem, Tr>& get(Elem* str, streamsize count, Elem Delim);

basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf);
basic_istream<Elem, Tr>& get(basic_streambuf<Elem, Tr>& strbuf, Elem Delim);
```

### <a name="parameters"></a>Параметры

*расчета*\
Число символов для чтения из `strbuf`.

*Delim*\
Символ, который должен завершать чтение, если он встретился до *Count*.

*str*\
Строка, в которую должна выполняться запись.

*Канал*\
Символ для получения.

*strBuf*\
Буфер, в который должна выполняться запись.

### <a name="return-value"></a>Возвращаемое значение

Форма get без параметров возвращает чтение элементов как целое число либо конец файла. Прочие формы возвращают поток (* `this`).

### <a name="remarks"></a>Примечания

Первая из этих неформатированных входных функций извлекает элемент, если это возможно, как при возврате `rdbuf` ->  `sbumpc`. В противном случае она возвращает **traits_type::** [eof](../standard-library/char-traits-struct.md#eof). Если функция не извлекает ни одного элемента, она вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`failbit`).

Вторая функция извлекает элемент [int_type](../standard-library/basic-ios-class.md#int_type) `meta` таким же образом. Если при сравнении `meta` оценивается как эквивалентный **traits_type::eof**, эта функция вызывает `setstate`( **failbit**). В противном случае она сохраняет **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( `meta`) в `Ch`. Функция возвращает **\*this**.

Третья функция возвращает **get**(_ *Str*, `count`, `widen`('\ **n**')).

Четвертая функция извлекает до *Count* -1 элементов и сохраняет их в массиве, начиная с _ *str*. Она всегда сохраняет `char_type` после сохранения всех извлеченных элементов. В целях тестирования извлечение останавливается:

- Конец файла.

- После того как функция извлекает элемент, который сравнивается со значением *delim*, в этом случае элемент возвращается в управляемую последовательность.

- После извлечения функцией значения *Count* -1 элементов.

Если функция не извлекает ни один элемент, то она вызывает `setstate`( **failbit**). В любом случае она возвращает **\*this**.

Пятая функция возвращает **get**( **strbuf**, `widen`('\ **n**')).

Шестая функция извлекает элементы и вставляет их в `strbuf`. Извлечение останавливается в конце файла или на элементе, который при сравнении оценивается как эквивалентный _ *Delim,* и не извлекается. Оно также останавливается без извлечения соответствующего элемента, если вставка завершается неудачно или создает исключение (которое перехватывается, но не создается повторно). Если функция не извлекает ни один элемент, то она вызывает `setstate`( **failbit**). В любом случае эта функция возвращает **\*this**.

### <a name="example"></a>Пример

```cpp
// basic_istream_get.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   c[0] = cin.get( );
   cin.get( c[1] );
   cin.get( &c[2],3 );
   cin.get( &c[4], 4, '7' );

   cout << c << endl;
}
```

```Output
1111
```

## <a name="getline"></a>  basic_istream::getline

Получает строку из входного потока.

```cpp
basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count);

basic_istream<Elem, Tr>& getline(
    char_type* str,
    streamsize count,
    char_type Delim);
```

### <a name="parameters"></a>Параметры

*расчета*\
Число символов для чтения из `strbuf`.

*Delim*\
Символ, который должен завершать чтение, если он встретился до *Count*.

*str*\
Строка, в которую должна выполняться запись.

### <a name="return-value"></a>Возвращаемое значение

Поток ( **\*this**).

### <a name="remarks"></a>Примечания

Первая из этих неформатированных входных функций возвращает **getline**(_ *Str*, `count`, `widen`(' `\`**n**')).

Вторая функция извлекает до *Count* -1 элементов и сохраняет их в массиве, начиная с _ *str*. Она всегда сохраняет символ окончания строки после сохранения всех извлеченных элементов. В целях тестирования извлечение останавливается:

- Конец файла.

- После того как функция извлекает элемент, который сравнивается со значением *delim*, в этом случае элемент не будет ни вернуться, ни присоединен к управляемой последовательности.

- После извлечения функцией значения *Count* -1 элементов.

Если функция не извлекает элементы или *Count* -1 элементов, она вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`failbit`). В любом случае она возвращает **\*this**.

### <a name="example"></a>Пример

```cpp
// basic_istream_getline.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10];

   cin.getline( &c[0], 5, '2' );
   cout << c << endl;
}
```

```Output
121
```

## <a name="ignore"></a>  basic_istream::ignore

Пропускает несколько элементов после текущей позиции чтения.

```cpp
basic_istream<Elem, Tr>& ignore(
    streamsize count = 1,
    int_type Delim = traits_type::eof());
```

### <a name="parameters"></a>Параметры

*расчета*\
Количество пропускаемых элементов от текущей позиции чтения.

*Delim*\
Элемент, который, если он встретился до Count `ignore` , вызывает возврат и разрешает чтение всех элементов после *delim* .

### <a name="return-value"></a>Возвращаемое значение

Поток ( **\*this**).

### <a name="remarks"></a>Примечания

Неформатированная входная функция извлекает до подсчета элементов и отклоняет их. Однако если значение *Count* равно **numeric_limits\<int >:: Max**, то оно принимается как произвольное большое. Извлечение останавливается `Ch` на раннем конце файла или в элементе, так что **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `Ch`) сравнивается со значением *delim* (который также извлекается). Функция возвращает **\*this**.

### <a name="example"></a>Пример

```cpp
// basic_istream_ignore.cpp
// compile with: /EHsc
#include <iostream>
int main( )
{
   using namespace std;
   char chararray[10];
   cout << "Type 'abcdef': ";
   cin.ignore( 5, 'c' );
   cin >> chararray;
   cout << chararray;
}
```

```Output
Type 'abcdef': abcdef
def
```

## <a name="op_gt_gt"></a>Базовый\_оператор IStream:: operator > >

Вызывает функцию для входного потока или считывает форматированные данные из входного потока.

```cpp
basic_istream& operator>>(basic_istream& (* Pfn)(basic_istream&));
basic_istream& operator>>(ios_base& (* Pfn)(ios_base&));
basic_istream& operator>>(basic_ios<Elem, Tr>& (* Pfn)(basic_ios<Elem, Tr>&));
basic_istream& operator>>(basic_streambuf<Elem, Tr>* strbuf);
basic_istream& operator>>(bool& val);
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

### <a name="parameters"></a>Параметры

*PFN*\
Указатель функции.

*strBuf*\
Объект типа `stream_buf`.

*Val*\
Значение для чтения из потока.

### <a name="return-value"></a>Возвращаемое значение

Поток ( **\*this**).

### <a name="remarks"></a>Примечания

Заголовок \<IStream > также определяет несколько глобальных операторов извлечения. Дополнительные сведения см. в разделе [оператор>> (\<istream>)](../standard-library/istream-operators.md#op_gt_gt).

Первая функция-член обеспечивает, чтобы выражение в форме **istr** >> `ws` вызывало [ws](../standard-library/istream-functions.md#ws)( **istr**), а затем возвращалось **\*this**. Вторая и третья функции обеспечивают аналогичное поведение других манипуляторов, таких как [hex](../standard-library/ios-functions.md#hex). Остальные функции — это форматированные входные функции.

Функция:

```cpp
basic_istream& operator>>(
    basic_streambuf<Elem, Tr>* strbuf);
```

Извлекает элементы, если _ *strBuf* не является пустым указателем, и вставляет их в *strBuf*. Извлечение останавливается в конце файла. Оно также останавливается без извлечения соответствующего элемента, если вставка завершается неудачно, или создает исключение (которое перехватывается, но не создается повторно). Если функция не извлекает элементы, она вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`failbit`). В любом случае эта функция возвращает **\*this**.

Функция:

```cpp
basic_istream& operator>>(bool& val);
```

извлекает поле и преобразует его в значение типа Boolean, вызывая [use_facet](../standard-library/basic-filebuf-class.md#open) < `num_get`\< **Elem**, **InIt**>( [getloc](../standard-library/ios-base-class.md#getloc)). [get](../standard-library/ios-base-class.md#getloc)( **InIt**( [rdbuf](../standard-library/basic-ios-class.md#rdbuf)), `Init`(0), **\*this**, `getloc`, `val`). Здесь **InIt** задается как [istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)\< **Elem**, **Tr**>. Функция возвращает **\*this**.

Каждая из следующих функций

```cpp
basic_istream& operator>>(short& val);
basic_istream& operator>>(unsigned short& val);
basic_istream& operator>>(int& val);
basic_istream& operator>>(unsigned int& val);
basic_istream& operator>>(long& val);
basic_istream& operator>>(unsigned long& val);
basic_istream& operator>>(long long& val);
basic_istream& operator>>(unsigned long long& val);
basic_istream& operator>>(void *& val);
```

извлекает поле и преобразует его в числовое значение путем вызова `use_facet`< `num_get`\< **Elem**, **InIt**>( `getloc`). [get](#get)( **InIt**( `rdbuf`), `Init`(0), **\*this**, `getloc`, `val`). Здесь **init** `istreambuf_iterator` определяется как `val`  <strong>\*</strong>    Elem, TR > и имеет небольшую длину, неподписанные long или void при необходимости. \<

Если преобразованное значение не может быть представлено типом `val`, функция вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`failbit`). В любом случае эта функция возвращает **\*this**.

Каждая из следующих функций

```cpp
basic_istream& operator>>(float& val);
basic_istream& operator>>(double& val);
basic_istream& operator>>(long double& val);
```

извлекает поле и преобразует его в числовое значение путем вызова `use_facet`< `num_get`\< **Elem**, **InIt**>( `getloc`). **get**( **InIt**( `rdbuf`), `Init`(0), **\*this**, `getloc`, `val`). `istreambuf_iterator`    Здесь определяется как`val` Elem, TR > и имеет тип Double или long double, если это необходимо. \< `InIt`

Если преобразованное значение невозможно представить как тип `val`, то функция вызывает `setstate`( **failbit**). В любом случае она возвращает **\*this**.

### <a name="example"></a>Пример

```cpp
// istream_basic_istream_op_is.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

ios_base& hex2( ios_base& ib )
{
   ib.unsetf( ios_base::dec );
   ib.setf( ios_base::hex );
   return ib;
}

basic_istream<char, char_traits<char> >& somefunc(basic_istream<char, char_traits<char> > &i)
{
   if ( i == cin )
   {
      cerr << "i is cin" << endl;
   }
   return i;
}

int main( )
{
   int i = 0;
   cin >> somefunc;
   cin >> i;
   cout << i << endl;
   cin >> hex2;
   cin >> i;
   cout << i << endl;
}
```

## <a name="op_eq"></a>  basic_istream::operator=

Назначает `basic_istream` справа от оператора этому объекту. Это назначение перемещения с использованием ссылки `rvalue`, после которого не остается копии.

```cpp
basic_istream& operator=(basic_istream&& right);
```

### <a name="parameters"></a>Параметры

*Правильно*\
Ссылка `rvalue` на объект `basic_ifstream`.

### <a name="return-value"></a>Возвращаемое значение

Возвращает *this.

### <a name="remarks"></a>Примечания

Оператор-член вызывает swap `( right)`.

## <a name="peek"></a>  basic_istream::peek

Возвращает следующий символ для чтения.

```cpp
int_type peek();
```

### <a name="return-value"></a>Возвращаемое значение

Следующий символ для чтения.

### <a name="remarks"></a>Примечания

Неформатированная входная функция извлекает элемент, если это возможно, как при возврате из `rdbuf` -> [sgetc](../standard-library/basic-streambuf-class.md#sgetc). В противном случае она возвращает **traits_type::** [eof](../standard-library/char-traits-struct.md#eof).

### <a name="example"></a>Пример

```cpp
// basic_istream_peek.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;
   cout << "Type 'abcde': ";

   c2 = cin.peek( );
   cin.getline( &c[0], 9 );

   cout << c2 << " " << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
a abcde
```

## <a name="putback"></a>  basic_istream::putback

Помещает указанный символ в поток.

```cpp
basic_istream<Elem, Tr>& putback(
    char_type Ch);
```

### <a name="parameters"></a>Параметры

*Канал*\
Символ для помещения обратно в поток.

### <a name="return-value"></a>Возвращаемое значение

Поток ( **\*this**).

### <a name="remarks"></a>Примечания

Неформатированная [входная функция](../standard-library/basic-istream-class.md) по возможности возвращает канал, как если бы это можно было сделать путем вызова [rdbuf](../standard-library/basic-ios-class.md#rdbuf)`->`[sputbackc](../standard-library/basic-streambuf-class.md#sputbackc). Если rdbuf является `sputbackc` пустым указателем или вызов метода возвращает **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), функция вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`badbit`). В любом случае она возвращает **\*this**.

### <a name="example"></a>Пример

```cpp
// basic_istream_putback.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2, c3;

   c2 = cin.get( );
   c3 = cin.get( );
   cin.putback( c2 );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Output
qwq
```

## <a name="read"></a>  basic_istream::read

Считывает указанное количество символов из потока и сохраняет их в массиве.

Этот метод является потенциально опасным, так как зависит от вызывающего объекта при проверке правильности переданных значений.

```cpp
basic_istream<Elem, Tr>& read(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Параметры

*str*\
Массив, из которого должны считываться символы.

*расчета*\
Число символов для чтения.

### <a name="return-value"></a>Возвращаемое значение

Поток ( `*this`).

### <a name="remarks"></a>Примечания

Неформатированная входная функция извлекает до подсчета элементов и сохраняет их в массиве, начиная `Str`с _. Извлечение останавливается на раннем конце файла, в этом случае функция вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`failbit`). В любом случае она возвращает `*this`.

### <a name="example"></a>Пример

```cpp
// basic_istream_read.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
    char c[10];
    int count = 5;

    cout << "Type 'abcde': ";

    // Note: cin::read is potentially unsafe, consider
    // using cin::_Read_s instead.
    cin.read(&c[0], count);
    c[count] = 0;

    cout << c << endl;
}
```

```Input
abcde
```

```Output
Type 'abcde': abcde
abcde
```

## <a name="readsome"></a>  basic_istream::readsome

Считывает указанное число значений символов.

Этот метод является потенциально опасным, так как зависит от вызывающего объекта при проверке правильности переданных значений.

```cpp
streamsize readsome(
    char_type* str,
    streamsize count);
```

### <a name="parameters"></a>Параметры

*str*\
Массив, в котором `readsome` сохраняет символы, которые считывает.

*расчета*\
Число символов для чтения.

### <a name="return-value"></a>Возвращаемое значение

Число фактически прочитанных символов [gcount](#gcount).

### <a name="remarks"></a>Примечания

Эта неформатированная входная функция извлекается  до подсчета элементов из входного потока и сохраняет их в *str*массива.

Эта функция не ожидает входных данных. Она считывает все доступные данные.

### <a name="example"></a>Пример

```cpp
// basic_istream_readsome.cpp
// compile with: /EHsc /W3
#include <iostream>
using namespace std;

int main( )
{
   char c[10];
   int count = 5;

   cout << "Type 'abcdefgh': ";

   // cin.read blocks until user types input.
   // Note: cin::read is potentially unsafe, consider
   // using cin::_Read_s instead.
   cin.read(&c[0], 2);

   // Note: cin::readsome is potentially unsafe, consider
   // using cin::_Readsome_s instead.
   int n = cin.readsome(&c[0], count);  // C4996
   c[n] = 0;
   cout << n << " characters read" << endl;
   cout << c << endl;
}
```

## <a name="seekg"></a>  basic_istream::seekg

Перемещает позицию чтения в потоке.

```cpp
basic_istream<Elem, Tr>& seekg(pos_type pos);

basic_istream<Elem, Tr>& seekg(off_type off, ios_base::seekdir way);
```

### <a name="parameters"></a>Параметры

*POS*\
Абсолютное положение, в которое следует переместить указатель чтения.

*автоном*\
Смещение для перемещения указателя чтения относительно *пути*.

*одностороннюю*\
Одно из перечислений [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

### <a name="return-value"></a>Возвращаемое значение

Поток ( **\*this**).

### <a name="remarks"></a>Примечания

Первая функция-член выполняет как абсолютный поиск, вторая функция-член выполняет относительный поиск.

> [!NOTE]
> Не используйте вторую функцию-член с текстовыми файлами, так как стандартный C++ не поддерживает относительный поиск в текстовых файлах.

Если значение [Fail](../standard-library/basic-ios-class.md#fail) равно false, первая функция-член **вызывает newpos** = [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekpos](../standard-library/basic-streambuf-class.md#pubseekpos) `pos`() для некоторого `pos_type` временного объекта. `newpos` Если `fail` имеет значение false, вторая функция вызывает **newpos** = **rdbuf** -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)( `off`, `way`). В любом случае, если ( `off_type`) **newpos** = = ( `off_type`) (-1) (операция позиционирования завершается ошибкой), функция вызывает `istr`. [SetState](../standard-library/basic-ios-class.md#setstate) (`failbit`). Обе функции возвращают **\*this**.

Если [fail](../standard-library/basic-ios-class.md#fail) имеет значение true, функции-члены не делают ничего.

### <a name="example"></a>Пример

```cpp
// basic_istream_seekg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main ( )
{
   using namespace std;
   ifstream file;
   char c, c1;

   file.open( "basic_istream_seekg.txt" );
   file.seekg(2);   // seek to position 2
   file >> c;
   cout << c << endl;
}
```

## <a name="sentry"></a>  basic_istream::sentry

Вложенный класс описывает объект, объявление которого структурирует форматированные и неформатированные входные функции.

класс Sentry {public: явный Sentry (basic_istream\<Elem, TR > & _Istr, bool _Noskip = false); operator bool () const;};

### <a name="remarks"></a>Примечания

Если `_Istr.`[good](../standard-library/basic-ios-class.md#good) имеет значение true, то конструктор:

- Вызывает `_Istr`. [tie](../standard-library/basic-ios-class.md#tie) -> [flush](../standard-library/basic-ostream-class.md#flush), если `_Istr`. `tie` не является пустым указателем.

- Эффективно вызывает [ws](../standard-library/istream-functions.md#ws)( `_Istr`), если `_Istr`. [flags](../standard-library/ios-base-class.md#flags) **&** [skipws](../standard-library/ios-functions.md#skipws) не равно нулю.

Если после такой подготовки `_Istr`. `good`имеет значение false, конструктор вызывает `_Istr`. [SetState](../standard-library/basic-ios-class.md#setstate) (`failbit`). В любом случае конструктор сохраняет значение, возвращенное `_Istr`. `good`в `status`. Последующий вызов метода `operator bool` для доставки этого сохраненного значения.

## <a name="swap"></a>  basic_istream::swap

Меняет местами содержимое двух объектов `basic_istream`.

```cpp
void swap(basic_istream& right);
```

### <a name="parameters"></a>Параметры

*Правильно*\
Ссылка lvalue на объект `basic_istream`.

### <a name="remarks"></a>Примечания

Эта функция-член вызывает [basic_ios::swap](../standard-library/basic-ios-class.md#swap)`(right)`. Он также обменивается счетчиком извлечения с числом извлечений *справа*.

## <a name="sync"></a>  basic_istream::sync

Синхронизирует устройство ввода, связанное с потоком, с буфером потока.

```cpp
int sync();
```

### <a name="return-value"></a>Возвращаемое значение

Если [rdbuf](../standard-library/basic-ios-class.md#rdbuf) является пустым указателем, функция возвращает значение –1. В противном случае она вызывает `rdbuf`  ->  [pubsync](../standard-library/basic-streambuf-class.md#pubsync). Если возвращается значение-1, функция вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`badbit`) и возвращает-1. В противном случае функция возвращает нуль.

## <a name="tellg"></a>  basic_istream::tellg

Сообщает текущую позицию чтения в потоке.

```cpp
pos_type tellg();
```

### <a name="return-value"></a>Возвращаемое значение

Текущая позиция в потоке.

### <a name="remarks"></a>Примечания

Если [fail](../standard-library/basic-ios-class.md#fail) имеет значение false, то функция-член возвращает [rdbuf](../standard-library/basic-ios-class.md#rdbuf) -> [pubseekoff](../standard-library/basic-streambuf-class.md#pubseekoff)(0, `cur`, **in**). В противном случае она возвращает `pos_type`(–1).

### <a name="example"></a>Пример

```cpp
// basic_istream_tellg.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main()
{
    using namespace std;
    ifstream file;
    char c;
    streamoff i;

    file.open("basic_istream_tellg.txt");
    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;

    i = file.tellg();
    file >> c;
    cout << c << " " << i << endl;
}
```

## <a name="unget"></a>  basic_istream::unget

Помещает самый последний считанный символ обратно в поток.

```cpp
basic_istream<Elem, Tr>& unget();
```

### <a name="return-value"></a>Возвращаемое значение

Поток ( **\*this**).

### <a name="remarks"></a>Примечания

[Неформатированная входная функция](../standard-library/basic-istream-class.md) отправляет предыдущий элемент обратно в поток, если это возможно, как при вызове `rdbuf`  ->  [sungetc](../standard-library/basic-streambuf-class.md#sungetc). Если [rdbuf](../standard-library/basic-ios-class.md#rdbuf) `sungetc` является пустым указателем или вызов метода возвращает **traits_type::** [EOF](../standard-library/basic-ios-class.md#eof), функция вызывает [SetState](../standard-library/basic-ios-class.md#setstate)(`badbit`). В любом случае она возвращает **\*this**.

Сведения о том, как `unget` может завершиться ошибкой, см. в разделе [basic_streambuf::sungetc](../standard-library/basic-streambuf-class.md#sungetc).

### <a name="example"></a>Пример

```cpp
// basic_istream_unget.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   char c[10], c2;

   cout << "Type 'abc': ";
   c2 = cin.get( );
   cin.unget( );
   cin.getline( &c[0], 9 );
   cout << c << endl;
}
```

```Input
abc
```

```Output
Type 'abc': abc
abc
```

## <a name="see-also"></a>См. также

[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Программирование iostream](../standard-library/iostream-programming.md)\
[Соглашения iostreams](../standard-library/iostreams-conventions.md)
