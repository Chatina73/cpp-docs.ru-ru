---
title: Класс wstring_convert
ms.date: 11/04/2016
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
ms.openlocfilehash: f09f12d9100e9faad849de608a9124f457da23df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366369"
---
# <a name="wstring_convert-class"></a>Класс wstring_convert

Шаблон `wstring_convert` класса выполняет преобразования между широкой строкой и строкой байт.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Параметры

*Кодексвт*\
Аспект [языкового стандарта](../standard-library/locale-class.md), представляющий объект преобразования.

*Elem*\
Тип двухбайтового элемента.

## <a name="remarks"></a>Remarks

Шаблон класса описывает объект, который управляет преобразованиями `std::basic_string<Elem>` между широкими струнами `std::basic_string<char>` объектов `std::string`класса и объектами строки типа (также известный как). Шаблон класса определяет `wide_string` типы `byte_string` и как синонимы для этих двух типов. Преобразование между последовательностями значений `Elem` (хранятся в объекте `wide_string`) и многобайтовыми последовательностями (хранятся в объекте `byte_string`) выполняется объектом класса `Codecvt<Elem, char, std::mbstate_t>`, который соответствует требованиям аспекта стандартного преобразования кода `std::codecvt<Elem, char, std::mbstate_t>`.

Объект этого класса шаблон амра:

- Однобайтовую строку для отображения при ошибках

- Двухбайтовую строку для отображения при ошибках

- Указатель на назначенный объект преобразования (высвобождается при уничтожении объекта wbuffer_convert)

- Объект состояния для преобразования типа [state_type](#state_type)

- Счетчик преобразований

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[wstring_convert](#wstring_convert)|Создает объект типа `wstring_convert`.|

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[byte_string](#byte_string)|Тип, представляющий однобайтную строку.|
|[wide_string](#wide_string)|Тип, представляющий двухбайтную строку.|
|[state_type](#state_type)|Тип, представляющий состояние преобразования.|
|[int_type](#int_type)|Тип, представляющий целое число.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[from_bytes](#from_bytes)|Преобразует строку однобайтовых символов в строку двухбайтовых символов.|
|[to_bytes](#to_bytes)|Преобразует двухбайтовую строку в однобайтовую.|
|[converted](#converted)|Возвращает количество успешных преобразований.|
|[Государства](#state)|Возвращает объект, представляющий состояние преобразования.|

## <a name="requirements"></a>Требования

**Заголовок:** \<locale>

**Пространство имен:** std

## <a name="wstring_convertbyte_string"></a><a name="byte_string"></a>wstring_convert::byte_string

Тип, представляющий однобайтную строку.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Remarks

Тип является синонимом `std::basic_string<char>`.

## <a name="wstring_convertconverted"></a><a name="converted"></a>wstring_convert::преобразовано

Возвращает количество успешных преобразований.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Возвращаемое значение

Число успешных преобразований.

### <a name="remarks"></a>Remarks

Число успешных преобразований хранится в объекте счетчика преобразований.

## <a name="wstring_convertfrom_bytes"></a><a name="from_bytes"></a>wstring_convert::from_bytes

Преобразует строку однобайтовых символов в строку двухбайтовых символов.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*Byte*|Последовательность одноэлементных байт для преобразования.|
|*Ptr*|Последовательность символов в стиле С, оканчивающаяся нулем, для преобразования.|
|*Bstr*|Строка [byte_string](#byte_string) для преобразования.|
|*Первый*|Первый символ в диапазоне символов для преобразования.|
|*Последний*|Последний символ в диапазоне символов для преобразования.|

### <a name="return-value"></a>Возвращаемое значение

Объект строки двухбайтовых символов, полученный в результате преобразования.

### <a name="remarks"></a>Remarks

Если объект [состояния преобразования](../standard-library/wstring-convert-class.md) *не* был построен с явным значением, он устанавливается в его значение по умолчанию (начальное состояние преобразования) до начала преобразования. В противном случае он остается неизменным.

Число успешно преобразованных входных элементов сохраняется в объекте счетчика преобразований. При отсутствии ошибок преобразования функция-член возвращает преобразованную двухбайтовую строку. В противном случае, если объект был создан с помощью инициализатора сообщения об ошибке в двухбайтовой строке, функция-член возвращает объект сообщения об ошибке в двухбайтовой строке. В противном случае функция-член создает объект класса [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertint_type"></a><a name="int_type"></a>wstring_convert::int_type

Тип, представляющий целое число.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Remarks

Тип является синонимом `wide_string::traits_type::int_type`.

## <a name="wstring_convertstate"></a><a name="state"></a>wstring_convert::государство

Возвращает объект, представляющий состояние преобразования.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Возвращаемое значение

Объект [состояния преобразования](../standard-library/wstring-convert-class.md), который представляет состояние преобразования.

### <a name="remarks"></a>Remarks

## <a name="wstring_convertstate_type"></a><a name="state_type"></a>wstring_convert::state_type

Тип, представляющий состояние преобразования.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Remarks

Тип описывает объект, который может представлять состояние преобразования. Тип является синонимом `Codecvt::state_type`.

## <a name="wstring_convertto_bytes"></a><a name="to_bytes"></a>wstring_convert::to_bytes

Преобразует двухбайтовую строку в однобайтовую.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*Char*|Расширенный символ для преобразования.|
|*Wptr*|Последовательность в стиле C, оканчивающаяся нулем, начинающаяся с `wptr`, для преобразования.|
|*Встр*|Строка [wide_string](#wide_string) для преобразования.|
|*Первый*|Первый элемент в диапазоне преобразуемых элементов.|
|*Последний*|Последний элемент в диапазоне преобразуемых элементов.|

### <a name="remarks"></a>Remarks

Если объект [состояния преобразования](../standard-library/wstring-convert-class.md) *не* был построен с явным значением, он устанавливается в его значение по умолчанию (начальное состояние преобразования) до начала преобразования. В противном случае он остается неизменным.

Число успешно преобразованных входных элементов сохраняется в объекте счетчика преобразований. При отсутствии ошибок преобразования, функция-член возвращает преобразованную однобайтовую строку. В противном случае, если объект был создан с помощью инициализатора сообщения об ошибке в однобайтовой строке, функция-член возвращает объект сообщения об ошибке в однобайтовой строке. В противном случае функция-член создает объект класса [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertwide_string"></a><a name="wide_string"></a>wstring_convert::wide_string

Тип, представляющий двухбайтную строку.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Remarks

Тип является синонимом `std::basic_string<Elem>`.

## <a name="wstring_convertwstring_convert"></a><a name="wstring_convert"></a>wstring_convert::wstring_convert

Создает объект типа `wstring_convert`.

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*\*Пквт*|Объект типа `Codecvt` для выполнения преобразования.|
|*_state*|Объект типа [state_type](#state_type), представляющий состояние преобразования.|
|*_Berr*|Объект [byte_string](#byte_string) для отображения ошибок.|
|*Верр*|Объект [wide_string](#wide_string) для отображения ошибок.|

### <a name="remarks"></a>Remarks

Первый конструктор сохраняет *Pcvt_arg* в [объекте преобразования](../standard-library/wstring-convert-class.md)
