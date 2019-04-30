---
title: Класс basic_stringstream
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringstream
- sstream/std::basic_stringstream::allocator_type
- sstream/std::basic_stringstream::rdbuf
- sstream/std::basic_stringstream::str
helpviewer_keywords:
- std::basic_stringstream [C++]
- std::basic_stringstream [C++], allocator_type
- std::basic_stringstream [C++], rdbuf
- std::basic_stringstream [C++], str
ms.assetid: 49629814-ca37-45c5-931b-4ff894e6ebd2
ms.openlocfilehash: 7e39d5dabf27ffbe15e519c006592935076a45c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414117"
---
# <a name="basicstringstream-class"></a>Класс basic_stringstream

Описывает объект, управляющий вставкой и извлечением элементов и закодированных объектов с помощью буфера потока класса [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Elem, class Tr = char_traits<Elem>, class Alloc = allocator<Elem>>
class basic_stringstream : public basic_iostream<Elem, Tr>
```

### <a name="parameters"></a>Параметры

*Alloc*<br/>
Класс распределителя.

*Elem*<br/>
Тип основного элемента строки.

*Tr*<br/>
Признаки символа, соответствующие основному элементу строки.

## <a name="remarks"></a>Примечания

Класс шаблона описывает объект, управляющий вставкой и извлечением элементов и закодированных объектов с помощью буфера потока класса [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>, с элементами типа `Elem`, признаки символов определяются классом `Tr`, а элементы выделяются распределителем класса `Alloc`. Этот объект сохраняет объект класса basic_stringbuf< **Elem**, **Tr**, `Alloc`>.

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[basic_stringstream](#basic_stringstream)|Создает объект типа `basic_stringstream`.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[allocator_type](#allocator_type)|Этот тип является синонимом для параметра шаблона `Alloc`.|

### <a name="member-functions"></a>Функции-члены

|Функция-член|Описание|
|-|-|
|[rdbuf](#rdbuf)|Возвращает адрес буфера сохраненного потока типа `pointer` в [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`, `Alloc`>.|
|[str](#str)|Задает или получает текст в буфере строк без изменения позиции записи.|

## <a name="requirements"></a>Требования

**Заголовок:** \<sstream>

**Пространство имен:** std

## <a name="allocator_type"></a>  basic_stringstream::allocator_type

Этот тип является синонимом для параметра шаблона `Alloc`.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringstream"></a>  basic_stringstream::basic_stringstream

Создает объект типа `basic_stringstream`.

```cpp
explicit basic_stringstream(ios_base::openmode _Mode = ios_base::in | ios_base::out);

explicit basic_stringstream(const basic_string<Elem, Tr, Alloc>& str, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Параметры

*_Mode*<br/>
Одно из перечислений в [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Объект типа `basic_string`.

### <a name="remarks"></a>Примечания

Первый конструктор инициализирует базовый класс путем вызова [basic_iostream](../standard-library/basic-iostream-class.md)( **sb**), где `sb` является сохраненным объектом класса [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  **Elem**, **Tr**, `Alloc`>. Он также инициализирует `sb` путем вызова basic_stringbuf < **Elem**, **Tr**, `Alloc`> ( `_Mode`).

Второй конструктор инициализирует базовый класс путем вызова basic_iostream( **sb**). Он также инициализирует `sb` путем вызова basic_stringbuf < **Elem**, **Tr**, `Alloc`> (_ *Str*, `_Mode`).

## <a name="rdbuf"></a>  basic_stringstream::rdbuf

Возвращает адрес буфера сохраненного потока типа **pointer** в [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< **Elem**, **Tr**, `Alloc`>.

```cpp
basic_stringbuf<Elem, Tr, Alloc> *rdbuf() const;
```

### <a name="return-value"></a>Возвращаемое значение

Адрес буфера сохраненного потока типа `pointer` в basic_stringbuf < **Elem**, **Tr**, `Alloc`>.

### <a name="example"></a>Пример

Пример, в котором используется `rdbuf`, см. в разделе [basic_filebuf::close](../standard-library/basic-filebuf-class.md#close).

## <a name="str"></a>  basic_stringstream::str

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

Возвращает объект класса [basic_string](../standard-library/basic-string-class.md)< **Elem**, **Tr**, `Alloc`>, управляемая последовательность которого является копией последовательности, управляемой **\*this**.

### <a name="remarks"></a>Примечания

Первая функция-член возвращает [rdbuf](#rdbuf) -> [str](../standard-library/basic-stringbuf-class.md#str). Вторая функция-член вызывает `rdbuf` -> **str**( `_Newstr`).

### <a name="example"></a>Пример

См. в разделе [basic_stringbuf::str](../standard-library/basic-stringbuf-class.md#str) пример, использующий `str`.

## <a name="see-also"></a>См. также

[Потокобезопасность в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Программирование iostream](../standard-library/iostream-programming.md)<br/>
[Соглашения iostreams](../standard-library/iostreams-conventions.md)<br/>
