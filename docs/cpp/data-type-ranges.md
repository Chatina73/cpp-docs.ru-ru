---
description: 'Дополнительные сведения: диапазоны типов данных'
title: Диапазоны типов данных
ms.date: 05/28/2020
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: 8d4ae1b6aae3a4dbf12180248df6000085103efe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339531"
---
# <a name="data-type-ranges"></a>Диапазоны типов данных

Компиляторы Microsoft C++ 32-bit и 64-bit распознают типы в таблице далее в этой статье.

- **`int`** (**`unsigned int`**)

- **`__int8`** (**`unsigned __int8`**)

- **`__int16`** (**`unsigned __int16`**)

- **`__int32`** (**`unsigned __int32`**)

- **`__int64`** (**`unsigned __int64`**)

- **`short`** (**`unsigned short`**)

- **`long`** (**`unsigned long`**)

- **`long long`** (**`unsigned long long`**)

Если имя начинается с двух символов подчеркивания (`__`), тип данных является нестандартным.

Диапазоны, представленные в следующей таблице, включают указанные значения.

|Имя типа|Байты|Другие имена|Диапазон значений|
|---------------|-----------|-----------------|---------------------|
|**`int`**|4|**`signed`**|От -2 147 483 648 до 2 147 483 647|
|**`unsigned int`**|4|**`unsigned`**|От 0 до 4 294 967 295|
|**`__int8`**|1|**`char`**|От -128 до 127|
|**`unsigned __int8`**|1|**`unsigned char`**|От 0 до 255|
|**`__int16`**|2|**`short`**, **`short int`**, **`signed short int`**|От -32 768 до 32 767|
|**`unsigned __int16`**|2|**`unsigned short`**, **`unsigned short int`**|От 0 до 65 535|
|**`__int32`**|4|**`signed`**, **`signed int`**, **`int`**|От -2 147 483 648 до 2 147 483 647|
|**`unsigned __int32`**|4|**`unsigned`**, **`unsigned int`**|От 0 до 4 294 967 295|
|**`__int64`**|8|**`long long`**, **`signed long long`**|От -9 223 372 036 854 775 808 до 9 223 372 036 854 775 807|
|**`unsigned __int64`**|8|**`unsigned long long`**|От 0 до 18 446 744 073 709 551 615|
|**`bool`**|1|нет|**`false`** или **`true`**|
|**`char`**|1|нет|от-128 до 127 по умолчанию<br /><br /> от 0 до 255 при компиляции с помощью [`/J`](../build/reference/j-default-char-type-is-unsigned.md)|
|**`signed char`**|1|нет|От -128 до 127|
|**`unsigned char`**|1|нет|От 0 до 255|
|**`short`**|2|**`short int`**, **`signed short int`**|От -32 768 до 32 767|
|**`unsigned short`**|2|**`unsigned short int`**|От 0 до 65 535|
|**`long`**|4|**`long int`**, **`signed long int`**|От -2 147 483 648 до 2 147 483 647|
|**`unsigned long`**|4|**`unsigned long int`**|От 0 до 4 294 967 295|
|**`long long`**|8|нет (но эквивалентно **`__int64`** )|От -9 223 372 036 854 775 808 до 9 223 372 036 854 775 807|
|**`unsigned long long`**|8|нет (но эквивалентно **`unsigned __int64`** )|От 0 до 18 446 744 073 709 551 615|
|**`enum`**|непостоянно|нет| |
|**`float`**|4|нет|3,4E +/- 38 (7 знаков)|
|**`double`**|8|нет|1,7E +/- 308 (15 знаков)|
|**`long double`**|то же, что **`double`**|нет|То же, что **`double`**|
|**`wchar_t`**|2|**`__wchar_t`**|От 0 до 65 535|

В зависимости от того, как он используется, переменная **`__wchar_t`** определяет либо тип расширенного символа, либо многобайтовый символ. Чтобы указать константу расширенного символьного типа, перед символьной или строковой константой следует использовать префикс `L` .

**`signed`** и **`unsigned`** — это модификаторы, которые можно использовать с любым целочисленным типом, за исключением **`bool`** . Обратите внимание, что **`char`** , **`signed char`** и **`unsigned char`** — это три различных типа для таких механизмов, как перегрузка и шаблоны.

**`int`** Типы и **`unsigned int`** имеют размер четыре байта. Однако переносимый код не должен зависеть от размера, **`int`** так как языковой стандарт позволяет реализовать его в зависимости от реализации.

C и C++ в Visual Studio также поддерживают целочисленные типы с указанием размера. Дополнительные сведения см. в разделе [`__int8, __int16, __int32, __int64`](../cpp/int8-int16-int32-int64.md) и [ограничения целых чисел](../cpp/integer-limits.md).

Дополнительные сведения об ограничениях размеров каждого типа см. [в разделе Встроенные типы](../cpp/fundamental-types-cpp.md).

Диапазон перечисляемых типов зависит от контекста языка и указанных флажков компилятора. Дополнительные сведения см. в статьях [Объявления перечислений C](../c-language/c-enumeration-declarations.md) и [Объявления перечислений C++](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>См. также раздел

[Ключевые слова](../cpp/keywords-cpp.md)<br/>
[Встроенные типы](../cpp/fundamental-types-cpp.md)
