---
description: 'Дополнительные сведения: &lt; строка&gt;'
title: '&lt;string&gt;'
ms.date: 11/04/2016
f1_keywords:
- <string>
helpviewer_keywords:
- string header
ms.assetid: a2fb9d00-d7ae-4170-bfea-2dc337aa37cf
ms.openlocfilehash: d8b89bf1a9621e863f6608e46557d374cd8e6245
ms.sourcegitcommit: a89eac9acdbd54a181e3bd5d5bc71a3ef3c1abca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106506121"
---
# `<string>`

Определяет шаблон класса контейнера `basic_string` и различные вспомогательные шаблоны.

Дополнительные сведения о `basic_string` см. в разделе [ `basic_string` класс](../standard-library/basic-string-class.md) .

## <a name="syntax"></a>Синтаксис

```cpp
#include <string>
```

## <a name="remarks"></a>Remarks

Язык C++ и библиотека Standard C++ поддерживают два типа строк:

- Массивы символов, оканчивающиеся нулевым символов, часто называют строками C.

- объекты шаблона класса типа `basic_string` , которые обрабатывали **`char`** аргументы шаблона, имеющие вид.

### <a name="typedefs"></a>Определения типов

|Имя типа|Описание|
|-|-|
|[`string`](../standard-library/string-typedefs.md#string)|Тип, описывающий специализацию шаблона класса `basic_string` с элементами типа **`char`** как `string` .|
|[`wstring`](../standard-library/string-typedefs.md#wstring)|Тип, описывающий специализацию шаблона класса `basic_string` с элементами типа **`wchar_t`** как `wstring` .|
|[`u16string`](../standard-library/string-typedefs.md#u16string)|Тип, описывающий специализацию шаблона класса `basic_string` на основе элементов типа **`char16_t`** .|
|[`u32string`](../standard-library/string-typedefs.md#u32string)|Тип, описывающий специализацию шаблона класса `basic_string` на основе элементов типа **`char32_t`** .|

### <a name="operators"></a>Операторы

|Оператор|Описание|
|-|-|
|[`operator+`](../standard-library/string-operators.md#op_add)|Сцепляет два строковых объекта.|
|[`operator!=`](../standard-library/string-operators.md#op_neq)|Проверяет, что строковый объект слева от оператора не равен строковому объекту справа от оператора. |
|[`operator==`](../standard-library/string-operators.md#op_eq_eq)|Проверяет, равен ли строковый объект слева от оператора строковому объекту справа от оператора.|
|[`operator<`](../standard-library/string-operators.md#op_lt)|Проверяет, что строковый объект слева от оператора меньше строкового объекта справа от оператора.|
|[`operator<=`](../standard-library/string-operators.md#op_lt_eq)|Проверяет, что строковый объект слева от оператора меньше или равен строковому объекту справа от оператора.|
|[`operator<<`](../standard-library/string-operators.md#op_lt_lt)|Функция шаблона, вставляющая строку в выходной поток.|
|[`operator>`](../standard-library/string-operators.md#op_gt)|Проверяет, что строковый объект слева от оператора больше строкового объекта справа от оператора.|
|[`operator>=`](../standard-library/string-operators.md#op_gt_eq)|Проверяет, что строковый объект слева от оператора больше или равен строковому объекту справа от оператора.|
|[`operator>>`](../standard-library/string-operators.md#op_gt_gt)|Функция шаблона, извлекающая строку из входного потока.|

### <a name="specialized-template-functions"></a>Специализированные функции шаблонов

|Имя|Описание|
|-|-|
|`hash`|Создает хэш строки.|
|[`swap`](../standard-library/string-functions.md#swap)|Меняет местами массивы символов двух строк.|
|[`stod`](../standard-library/string-functions.md#stod)|Преобразует последовательность символов в **`double`** .|
|[`stof`](../standard-library/string-functions.md#stof)|Преобразует последовательность символов в **`float`** .|
|[`stoi`](../standard-library/string-functions.md#stoi)|Преобразует последовательность символов в **`int`** .|
|[`stold`](../standard-library/string-functions.md#stold)|Преобразует последовательность символов в **`long double`** .|
|[`stoll`](../standard-library/string-functions.md#stoll)|Преобразует последовательность символов в **`long long`** .|
|[`stoul`](../standard-library/string-functions.md#stoul)|Преобразует последовательность символов в **`unsigned long`** .|
|[`stoull`](../standard-library/string-functions.md#stoull)|Преобразует последовательность символов в **`unsigned long long`** .|
|[`to_string`](../standard-library/string-functions.md#to_string)|Преобразует значение в `string`.|
|[`to_wstring`](../standard-library/string-functions.md#to_wstring)|Преобразует значение в расширенную строку.|

### <a name="functions"></a>Функции

|Компонент|Описание|
|-|-|
|[`getline` Шаблон](../standard-library/string-functions.md#getline)|Извлеките объект `string` , построчно, из входного потока.|

### <a name="classes"></a>Классы

|Класс|Описание|
|-|-|
|[`basic_string` См](../standard-library/basic-string-class.md)|Шаблон класса, описывающий объекты, которые могут хранить последовательность произвольных символьно-подобных объектов.|
|[`char_traits` Struct](../standard-library/char-traits-struct.md)|Шаблон класса, описывающий атрибуты, связанные с символом типа `CharType`|

### <a name="specializations"></a>Специализации

|Имя|Описание|
|-|-|
|[`char_traits<char>` Struct](../standard-library/char-traits-char-struct.md)|Структура, которая является специализацией структуры шаблона `char_traits<CharType>` для элемента типа **`char`** .|
|[`char_traits<wchar_t>` Struct](../standard-library/char-traits-wchar-t-struct.md)|Структура, которая является специализацией структуры шаблона `char_traits<CharType>` для элемента типа **`wchar_t`** .|
|[`char_traits<char16_t>` Struct](../standard-library/char-traits-char16-t-struct.md)|Структура, которая является специализацией структуры шаблона `char_traits<CharType>` для элемента типа **`char16_t`** .|
|[`char_traits<char32_t>` Struct](../standard-library/char-traits-char32-t-struct.md)|Структура, которая является специализацией структуры шаблона `char_traits<CharType>` для элемента типа **`char32_t`** .|

## <a name="requirements"></a>Требования

- **Заголовок:**`<string>`

- **Пространство имен:** std

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
