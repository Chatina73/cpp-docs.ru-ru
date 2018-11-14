---
title: Класс basic_stringbuf
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 1ed9deee46f7c99750ee3260a6b2a8de1f0f3397
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329648"
---
# <a name="basicstringbuf-class"></a>Класс basic_stringbuf

Описывает буфер потока, который управляет передачей элементов типа `Elem`, признаки символов которого определяются с помощью класса `Tr`, в последовательность элементов, сохраненную в объекте массива, и из нее.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Параметры

*Alloc*<br/>
Класс распределителя.

*Elem*<br/>
Тип основного элемента строки.

*Tr*<br/>
Признаки символа, соответствующие основному элементу строки.

## <a name="remarks"></a>Примечания

Объект размещается, расширяется и освобождается при необходимости для обеспечения соответствия изменениям в последовательности.

Объект класса basic_stringbuf< `Elem`, `Tr`, `Alloc`> сохраняет копию аргумента `ios_base::`[openmode](../standard-library/ios-base-class.md#openmode) из своего конструктора как свой режим `stringbuf`**mode**:

- Если `mode & ios_base::in` имеет ненулевое значение, входной буфер доступен. Дополнительные сведения см. в разделе [Класс basic_streambuf](../standard-library/basic-streambuf-class.md).

- Если `mode & ios_base::out` имеет ненулевое значение, выходной буфер доступен.

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Создает объект типа `basic_stringbuf`.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[allocator_type](#allocator_type)|Тип является синонимом параметра-шаблона *Alloc*.|
|[char_type](#char_type)|Связывает имя типа с параметром шаблона *Elem*.|
|[int_type](#int_type)|Делает этот тип в `basic_filebuf`по эквивалентным типу с тем же именем в области *Tr* области.|
|[off_type](#off_type)|Делает этот тип в `basic_filebuf`по эквивалентным типу с тем же именем в области *Tr* области.|
|[pos_type](#pos_type)|Делает этот тип в `basic_filebuf`по эквивалентным типу с тем же именем в области *Tr* области.|
|[traits_type](#traits_type)|Связывает имя типа с параметром шаблона *Tr*.|

### <a name="member-functions"></a>Функции-члены

|Функция-член|Описание|
|-|-|
|[overflow](#overflow)|Защищенная виртуальная функция, которая может вызываться при вставке нового символа в полный буфер.|
|[pbackfail](#pbackfail)|Защищенная виртуальная функция-член пытается поместить элемент обратно во входной буфер, затем делает его текущим (на него указывает следующий указатель).|
|[seekoff](#seekoff)|Защищенная виртуальная функция-член пытается изменить текущие положения управляемых потоков.|
|[seekpos](#seekpos)|Защищенная виртуальная функция-член пытается изменить текущие положения управляемых потоков.|
|[str](#str)|Задает или получает текст в буфере строк без изменения позиции записи.|
|swap||
|[underflow](#underflow)|Защищенная виртуальная функция-член для извлечения текущего элемента из входного потока.|

## <a name="requirements"></a>Требования

**Заголовок:** \<sstream>

**Пространство имен:** std

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

Тип является синонимом параметра-шаблона *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>  basic_stringbuf::basic_stringbuf

Создает объект типа `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Параметры

*_Режим*<br/>
Одно из перечислений в [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Объект типа [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Примечания

Первый конструктор сохраняет пустой указатель во всех указателях, управляющих входным и выходным буферами. Дополнительные сведения см. в разделе "Примечания" для [класса basic_streambuf](../standard-library/basic-streambuf-class.md). Он также хранит *_режим* в качестве режима stringbuf. Дополнительные сведения см. в разделе "Примечания" для [класса basic_stringbuf](../standard-library/basic-stringbuf-class.md).

Второй конструктор выделяет копию последовательности, управляемой строковым объектом *str*. Если `_Mode & ios_base::in` имеет ненулевое значение, то он задает входной буфер для чтения в начале последовательности. Если `_Mode & ios_base::out` имеет ненулевое значение, то он задает выходной буфер для записи в начале последовательности. Он также хранит *_режим* в качестве режима stringbuf. Дополнительные сведения см. в разделе "Примечания" для [класса basic_stringbuf](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Связывает имя типа с параметром шаблона *Elem*.

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Делает этот тип в области basic_filebuf эквивалентным типу с тем же именем в `Tr` области.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Делает этот тип в области basic_filebuf эквивалентным типу с тем же именем в `Tr` области.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::overflow

Защищенная виртуальная функция, которая может вызываться при вставке нового символа в полный буфер.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Параметры

*_Meta*<br/>
Символ для вставки в буфер или `traits_type::eof`.

### <a name="return-value"></a>Возвращаемое значение

Если функции не удалось выполниться успешно, возвращается значение `traits_type::eof`. В противном случае она возвращает **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Примечания

Если  *\_Meta* не считаются равными **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), защищенная функция-член пытается вставить элемент  **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) в выходной буфер. Для этого существует несколько способов.

- Если позиция записи доступна, можно сохранить элемент в позиции записи и увеличить следующий указатель для выходного буфера.

- Можно сделать позицию записи доступной, выделяя новое или дополнительное хранилище для выходного буфера. Расширение выходного буфера таким способом также расширяет любой связанный входной буфер.

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

Защищенная виртуальная функция-член пытается поместить элемент обратно во входной буфер, а затем делает его текущим (на него указывает следующий указатель).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Параметры

*_Meta*<br/>
Символ для вставки в буфер или `traits_type::eof`.

### <a name="return-value"></a>Возвращаемое значение

Если функции не удалось выполниться успешно, возвращается значение `traits_type::eof`. В противном случае она возвращает **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Примечания

Если *_Meta* равно сравнивает **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), элемент, который необходимо передать обратно, фактически уже в потоке перед текущим элементом. В противном случае этот элемент заменяется на **byte** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Функция может передать элемент обратно различными способами.

- Если позиция возврата доступна и сохраненный там элемент оценивается как равный byte, функция может уменьшить следующий указатель для входного буфера.

- Если позиция возврата доступна и режим stringbuf позволяет изменять последовательность (**mode & ios_base::out** не равно нулю), то функция может сохранить byte в позиции возврата и уменьшить следующий указатель для входного буфера.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Делает этот тип в области basic_filebuf эквивалентным типу с тем же именем в `Tr` области.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Защищенная виртуальная функция-член пытается изменить текущие положения управляемых потоков.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Параметры

*_Off*<br/>
Позиция для поиска относительно *_Way*. Дополнительные сведения см. в разделе [basic_stringbuf::off_type](#off_type).

*_Way*<br/>
Начальная точка для операций смещения. Возможные значения см. в разделе [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir).

*_Режим*<br/>
Задает режим для положения указателя. По умолчанию разрешается изменять позиции чтения и записи. Дополнительные сведения см. в разделе [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Возвращаемое значение

Возвращает новую позицию или недопустимую позицию потока.

### <a name="remarks"></a>Примечания

Для объекта класса `basic_stringbuf<Elem, Tr, Alloc>` позиция потока состоит исключительно из смещения потока. Нулевое смещение обозначает первый элемент управляемой последовательности.

Новая позиция определяется следующим образом.

- Если `_Way`  ==  `ios_base::beg`, новая позиция — это начало потока плюс *_Off*.

- Если `_Way`  ==  `ios_base::cur`, новая позиция — текущую позицию в потоке, а также *_Off*.

- Если `_Way`  ==  `ios_base::end`, новая позиция — это конец потока плюс *_Off*.

Если `_Mode & ios_base::in` имеет ненулевое значение, функция изменяет следующую позицию для чтения во входном буфере. Если `_Mode & ios_base::out` имеет ненулевое значение, функция изменяет следующую позицию для записи в выходном буфере. Для затрагиваемого потока должен существовать свой буфер. Для успешного выполнения операции размещения итоговая позиция потока должна находиться в управляемой последовательности. Если функция влияет на обе позиции потока, *_Way* должно быть `ios_base::beg` или `ios_base::end` и оба потоки располагаются в том же элементе. В противном случае (или если не затрагивается ни одна позиция) операция размещения завершится неудачно.

Если функция успешно изменила одну или обе позиции потока, то она возвращает итоговую позицию потока. В противном случае она завершается неудачно и возвращает недопустимую позицию потока.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

Защищенная виртуальная функция-член пытается изменить текущие положения управляемых потоков.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Параметры

*_Sp*<br/>
Позиция для поиска.

*_Режим*<br/>
Задает режим для положения указателя. По умолчанию разрешается изменять позиции чтения и записи.

### <a name="return-value"></a>Возвращаемое значение

Если функция успешно изменила одну или обе позиции потока, то она возвращает итоговую позицию потока. В противном случае она завершается неудачно и возвращает недопустимую позицию потока. Чтобы определить, является ли позиция потока недопустимой, сравните возвращаемое значение с `pos_type(off_type(-1))`.

### <a name="remarks"></a>Примечания

Для объекта класса basic_stringbuf< **Elem**, **Tr**, `Alloc`> позиция потока состоит исключительно из смещения потока. Нулевое смещение обозначает первый элемент управляемой последовательности. Новая позиция определяется объектом *Sp*.

Если **mode & ios_base::in** имеет ненулевое значение, функция изменяет следующую позицию для чтения во входном буфере. Если **mode & ios_base::out** имеет ненулевое значение, функция изменяет следующую позицию для записи в выходном буфере. Для затрагиваемого потока должен существовать свой буфер. Для успешного выполнения операции размещения итоговая позиция потока должна находиться в управляемой последовательности. В противном случае (или если не затрагивается ни одна позиция) операция размещения завершится неудачно.

## <a name="str"></a>  basic_stringbuf::str

Задает или получает текст в буфере строк без изменения позиции записи.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Параметры

*_Newstr*<br/>
Новая строка.

### <a name="return-value"></a>Возвращаемое значение

Возвращает объект класса [basic_string](../standard-library/basic-string-class.md)\< **Elem**, **Tr**, Alloc **>,**, управляемая последовательность которого является копией последовательности, управляемой **\*this**.

### <a name="remarks"></a>Примечания

Первая функция-член возвращает объект класса basic_string< **Elem**, **Tr**, `Alloc`>, управляемая последовательность которого является копией последовательности, управляемой **\*this**. Скопированная последовательность зависит от сохраненного режима stringbuf:

- если **mode & ios_base::out** имеет ненулевое значение и существует выходной буфер, последовательность представляет собой весь выходной буфер (элементы [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase), начиная с `pbase`);

- если **mode & ios_base::in** имеет ненулевое значение и существует входной буфер, последовательность представляет собой весь входной буфер (элементы [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback), начиная с `eback`).

- В противном случае скопированная последовательность пуста.

Вторая функция-член освобождает все последовательности, в текущий момент управляемые **\*this**. Затем она выделяет копию последовательности, управляемой *_Newstr*. Если **mode & ios_base::in** имеет ненулевое значение, то она задает входной буфер для чтения в начале последовательности. Если **mode & ios_base::out** имеет ненулевое значение, то она задает выходной буфер для записи в начале последовательности.

### <a name="example"></a>Пример

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="traits_type"></a>  basic_stringbuf::traits_type

Связывает имя типа с параметром шаблона *Tr*.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Примечания

Этот тип является синонимом для параметра-шаблона *Tr*.

## <a name="underflow"></a>  basic_stringbuf::underflow

Защищенная виртуальная функция для извлечения текущего элемента из входного потока.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Возвращаемое значение

Если функция не может выполниться успешно, она возвращает **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). В противном случае она возвращает текущий элемент во входном потоке, который был преобразован.

### <a name="remarks"></a>Примечания

Защищенная функция-член пытается извлечь текущий элемент `byte` из входного буфера, переместить текущую позицию в потоке и возвратить элемент как **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **байтов**). Это можно сделать одним способом: если позиция чтения доступна, функция принимает `byte` как элемента, хранящегося в этой позиции чтения и перемещает следующий указатель для входного буфера.

## <a name="swap"></a>  basic_streambuf::swap

Меняет местами содержимое данного буфера строк и другого буфера строк.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Параметры

*other*<br/>
Буфер basic_stringbuf, содержимое которого будет заменено содержимым этого буфера basic_stringbuf.

### <a name="remarks"></a>Примечания

## <a name="op_eq"></a>  basic_stringbuf::operator=

Назначает содержимое basic_stringbuf справа от оператора функции basic_stringbuf слева.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Параметры

*other*<br/>
basic_stringbuf, содержимое которого, включая признаки языкового стандарта, будут назначены функции stringbuf слева от оператора.

### <a name="remarks"></a>Примечания

## <a name="see-also"></a>См. также

[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Программирование iostream](../standard-library/iostream-programming.md)<br/>
[Соглашения iostreams](../standard-library/iostreams-conventions.md)<br/>
