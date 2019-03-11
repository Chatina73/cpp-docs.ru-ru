---
title: Класс Platform::String
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: ac9ee843f5f11d4a42377b16ec77b266238fc461
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746192"
---
# <a name="platformstring-class"></a>Класс Platform::String

Представляет упорядоченную коллекцию символов Юникода, используемую для представления текста. Дополнительные сведения и примеры см. в разделе [строки](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Синтаксис

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Итераторы

Две функции итераторов, не являющиеся членами класса String, можно использовать с функциями шаблона `std::for_each` для перечисления символов в объекте String.

|Член|Описание:|
|------------|-----------------|
|`const char16* begin(String^ s)`|Возвращает указатель на начало указанного объекта String.|
|`const char16* end(String^ s)`|Возвращает указатель на позицию после окончания указанного объекта String.|

### <a name="members"></a>Участники

Класс String наследует от класса Object и интерфейсов IDisposable, IEquatable и IPrintable.

Класс String имеет также следующие типы членов.

**Конструкторы**

|Член|Описание:|
|------------|-----------------|
|[String::String](#ctor)|Инициализирует новый экземпляр класса String.|

**Методы**

Класс String наследует методы Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() и ToString() от класса [Platform::Object Class](../cppcx/platform-object-class.md). Класс String содержит также следующие методы.

|Метод|Описание:|
|------------|-----------------|
|[String::Begin](#begin)|Возвращает указатель на начало текущей строки.|
|[String::CompareOrdinal](#compareordinal)|Сравнивает два объекта `String` , оценивая числовые значения соответствующих символов в двух строковых значениях, представленных объектами.|
|[String::Concat](#concat)|Объединяет значения двух объектов String.|
|[String::Data](#data)|Возвращает указатель на начало текущей строки.|
|[String::Dispose](#dispose)|Высвобождает ресурсы.|
|[String::End](#end)|Возвращает указатель на позицию после конца текущей строки.|
|[String::Equals](#equals)|Указывает, равен ли указанный объект текущему объекту.|
|[String::GetHashCode](#gethashcode)|Возвращает хэш-код данного экземпляра.|
|[String::IsEmpty](#isempty)|Указывает, является ли объект String пустым.|
|[String::IsFastPass](#isfastpass)|Указывает, участвует ли текущий строковый объект в *быстрой передачи* операции. В операции быстрой передачи подсчет ссылок приостанавливается.|
|[String::Length](#length)|Получает длину текущего объекта String.|
|[String::ToString](#tostring)|Возвращает объект String, значение которого совпадает со значением текущей строки.|

**Инструкции**

Класс String имеет следующие операторы.

|Член|Описание:|
|------------|-----------------|
|[String::operator ==-оператор](#operator-equality)|Указывает, равны ли значения двух указанных объектов String.|
|[Оператор operator+](#operator-plus)|Сцепляет два объекта String в новый объект String.|
|[String::operator > оператор](#operator-greater-than)|Указывает, является ли значение одного объекта String большим, чем значение второго объекта String.|
|[String::operator > =-оператор](#operator-greater-than-or-equals)|Указывает, является ли значение одного объекта String больше или равным значению второго объекта String.|
|[String::operator! =-оператор](#operator-inequality)|Указывает, различны ли значения двух указанных объектов String.|
|[String::operator < оператор](#operator-less-than)|Указывает, является ли значение одного объекта String меньшим, чем значение второго объекта String.|

### <a name="requirements"></a>Требования

**Минимальный поддерживаемый клиент:** Windows 8

**Минимальный поддерживаемый сервер:** Windows Server 2012

**Пространство имен:** Platform

**Заголовок** vccorlib.h (включается по умолчанию)

## <a name="begin"></a>  Метод String::BEGIN

Возвращает указатель на начало текущей строки.

### <a name="syntax"></a>Синтаксис

```cpp
char16* Begin();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на начало текущей строки.

## <a name="compareordinal"></a>  Метод String::CompareOrdinal

Сравнивает два объекта `String` , оценивая числовые значения соответствующих символов в двух строковых значениях, представленных объектами.

### <a name="syntax"></a>Синтаксис

```cpp
int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый объект String.

*str2*<br/>
Второй объект String.

### <a name="return-value"></a>Возвращаемое значение

Целое число, выражающее лексическое соотношение двух сравниваемых значений. В следующей таблице перечислены возможные возвращаемые значения.

|Значение|Условие|
|-----------|---------------|
|-1|Значение `str1` меньше `str2`.|
|0|Значение `str1` равно значению `str2`.|
|1|Значение `str1` больше значения `str2`.|

## <a name="concat"></a>  Метод String::concat

Объединяет значения двух объектов String.

### <a name="syntax"></a>Синтаксис

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый объект String или значение `null`.

*str2*<br/>
Второй объект String или значение `null`.

### <a name="return-value"></a>Возвращаемое значение

Новый объект String^, значение которого является объединением значений `str1` и `str2`.

Если `str1` имеет значение `null`, а `str2` — значение, отличное от null, возвращается значение `str1`. Если `str2` имеет значение `null`, а `str1` — значение, отличное от null, возвращается значение `str2`. Если оба параметра `str1` и `str2` имеют значение `null`, возвращается пустая строка (L"").

## <a name="data"></a>  Метод String::Data

Возвращает указатель на начало буфера данных объекта в качестве массива элементов `char16` (`wchar_t`) в стиле языка C.

### <a name="syntax"></a>Синтаксис

```
const char16* Data();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на начало `const char16` массива символов Юникода (`char16` является определением типа для `wchar_t`).

### <a name="remarks"></a>Примечания

Используйте этот метод для преобразования из `Platform::String^` в `wchar_t*`. Когда объект `String` выходит за пределы области, указатель Data больше не является гарантированно допустимым. Для хранения данных вне пределов продолжительности исходного `String` , используйте [wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) для копирования массива в память, которую вы выделили самостоятельно.

## <a name="dispose"></a>  Метод String::Dispose

Высвобождает ресурсы.

### <a name="syntax"></a>Синтаксис

```cpp
virtual override void Dispose();
```

## <a name="end"></a>  Метод String::End

Возвращает указатель на позицию после конца текущей строки.

### <a name="syntax"></a>Синтаксис

```cpp
char16* End();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на позицию после конца текущей строки.

### <a name="remarks"></a>Примечания

End() возвращает Begin() + Length.

## <a name="equals"></a>  Метод String::Equals

Указывает, совпадает ли значение заданного объекта String со значением текущего объекта.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Параметры

*str*<br/>
Объект для сравнения.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если `str` равен текущему объекту; в противном случае — значение **false**.

### <a name="remarks"></a>Примечания

Этот метод эквивалентен [String::CompareOrdinal](#compareordinal). В первой перегрузке предполагается, что параметр `str` может быть приведен к объекту String^.

## <a name="gethashcode"></a>  Метод String::GetHashCode

Возвращает хэш-код данного экземпляра.

### <a name="syntax"></a>Синтаксис

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Возвращаемое значение

Хэш-код данного экземпляра.

## <a name="isempty"></a>  Метод String::IsEmpty

Указывает, является ли объект String пустым.

### <a name="syntax"></a>Синтаксис

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если текущий `String` объект **null** или является пустой строкой (L» "); в противном случае **false**.

## <a name="isfastpass"></a>  Метод String::IsFastPass

Указывает, участвует ли текущий строковый объект в *быстрой передачи* операции. В операции быстрой передачи подсчет ссылок приостанавливается.

### <a name="syntax"></a>Синтаксис

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если текущий `String` объекта быстрой передачи; в противном случае **false**.

### <a name="remarks"></a>Примечания

При вызове функции, где в качестве параметра используется объект с подсчетом ссылок и вызываемая функция обращается к этому объекту только для чтения, компилятор может безопасно приостановить подсчет ссылок, чтобы повысить производительность вызова. Это свойство не дает никакой дополнительной пользы для вашего кода. Система обрабатывает все сведения.

## <a name="length"></a>  Метод String::length

Возвращает число символов в текущем `String` объекта.

### <a name="syntax"></a>Синтаксис

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Возвращаемое значение

Число символов в текущем `String` объекта.

### <a name="remarks"></a>Примечания

Длина объекта String без символов равна нулю. Длина следующего объекта String равна 5.

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Массив символов, возвращаемых [String::Data](#data) имеет один дополнительный символ — завершающий NULL или «\0». Этот символ также имеет длину 2 байта.

## <a name="operator-plus"></a>  Оператор String::operator +

Сцепляет два [строка](../cppcx/platform-string-class.md) объектов в новый [строка](../cppcx/platform-string-class.md) объекта.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый объект `String`.

*str2*<br/>
Второй объект `String`, содержимое которого будет добавлено в `str1`.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если *str1* равен *str2*; в противном случае **false**.

### <a name="remarks"></a>Примечания

Этот оператор создает объект `String^`, содержащий данные из двух операндов. Используйте его для удобства, если производительность не играет решающей роли. Несколько вызовов "`+`" в функции, скорее всего, не будут иметь последствий, но если вы имеете дело с большими объектами или текстовыми данными в сложном цикле, используйте стандартные механизмы и типы C++.

##  <a name="operator-equality"></a> String::operator ==-оператор

Указывает, равны ли текстовые значения двух указанных объектов String.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый из сравниваемых объектов `String`.

*str2*<br/>
Второй из сравниваемых объектов `String`.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если содержание `str1` равны `str2`; в противном случае **false**.

### <a name="remarks"></a>Примечания

Этот оператор эквивалентен [String::CompareOrdinal](#compareordinal).

##  <a name="operator-greater-than"></a>  String::operator&gt;

Указывает ли значение одного `String` объект больше, чем значение второго `String` объекта.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый объект `String`.

*str2*<br/>
Второй объект `String`.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если значение `str1` больше, чем значение `str2`; в противном случае **false**.

### <a name="remarks"></a>Примечания

Этот оператор эквивалентен явного вызова [String::CompareOrdinal](#compareordinal) и полученный результат больше нуля.

## <a name="operator-greater-than-or-equals"></a> String::operator&gt;=

Указывает ли значение одного `String` объекта больше или равно значению второго `String` объекта.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый объект `String`.

*str2*<br/>
Второй объект `String`.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если значение `str1` больше или равно значению `str2`; в противном случае **false**.

## <a name="operator-inequality"></a> String::operator! =

Указывает ли два указанных `String` объекты имеют разные значения.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый из сравниваемых объектов `String`.

*str2*<br/>
Второй из сравниваемых объектов `String`.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если `str1` не равно `str2`; в противном случае **false**.

## <a name="operator-less-than"></a> String::operator&lt;

Указывает, является ли значение одного `String` объект меньше, чем значение второго `String` объекта.

### <a name="syntax"></a>Синтаксис

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Параметры

*str1*<br/>
Первый объект `String`.

*str2*<br/>
Второй объект `String`.

### <a name="return-value"></a>Возвращаемое значение

**значение true,** Если значение *str1* меньше, чем значение *str2*; в противном случае **false**.

## <a name="ctor"></a> Конструктор String::String

Инициализирует новый экземпляр класса `String` класс копию данных входной строки.

### <a name="syntax"></a>Синтаксис

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Параметры

*s*<br/>
Серия расширенных символов, инициализирующих строку.  char16

*n*<br/>
Число, указывающее длину строки.

### <a name="remarks"></a>Примечания

Если важна производительность, и управления временем существования исходной строки, можно использовать [Platform::StringReference](../cppcx/platform-stringreference-class.md) вместо строки.
### <a name="example"></a>Пример

```cpp
String^ s = L"Hello!";
```

## <a name="tostring"></a> String::ToString

Возвращает `String` объект, значение которого совпадает со значением текущей строки.

### <a name="syntax"></a>Синтаксис

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Возвращаемое значение

Объект `String` объект, значение которого совпадает со значением текущей строки.

## <a name="see-also"></a>См. также

[Пространство имен Platform](../cppcx/platform-namespace-c-cx.md)
