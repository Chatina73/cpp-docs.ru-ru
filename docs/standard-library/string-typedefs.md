---
description: 'Подробнее: &lt; &gt; Определение типов строк'
title: Определения типов &lt;string&gt;
ms.date: 11/04/2016
f1_keywords:
- string/std::string
- string/std::u16string
- string/std::u32string
- string/std::wstring
ms.assetid: fdca01e9-f2f1-4b59-abda-0093d760b3cc
ms.openlocfilehash: 544d84b68b284b7da140d663b916277cc9156ab4
ms.sourcegitcommit: 6d2a4ab362b657d17ce1cb336b22b5454dc2bc7b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2021
ms.locfileid: "107721386"
---
# <a name="string-typedefs"></a>Определения типов `<string>`

[`string`](#string)\
[`u16string`](#u16string)\
[`u32string`](#u32string)\
[`wstring`](#wstring)

## <a name="string"></a><a name="string"></a> `string`

Тип, описывающий специализацию шаблона класса [`basic_string`](../standard-library/basic-string-class.md) с элементами типа **`char`** .

Другие определения типов, которые специализируется на специализации `basic_string` [`wstring`](../standard-library/string-typedefs.md#wstring) , включают, [`u16string`](../standard-library/string-typedefs.md#u16string) и [`u32string`](../standard-library/string-typedefs.md#u32string) .

```cpp
typedef basic_string<char, char_traits<char>, allocator<char>> string;
```

### <a name="remarks"></a>Замечания

Следующие объявления являются равнозначными:

```cpp
string str("");

basic_string<char> str("");
```

Список конструкторов строк см. в разделе [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) .

## <a name="u16string"></a><a name="u16string"></a> `u16string`

Тип, описывающий специализацию шаблона класса [`basic_string`](../standard-library/basic-string-class.md) с элементами типа **`char16_t`** .

Другие определения типов, которые специализируется на специализации `basic_string` [`wstring`](../standard-library/string-typedefs.md#wstring) , включают, [`string`](../standard-library/string-typedefs.md#string) и [`u32string`](../standard-library/string-typedefs.md#u32string) .

```cpp
typedef basic_string<char16_t, char_traits<char16_t>, allocator<char16_t>> u16string;
```

### <a name="remarks"></a>Замечания

Список конструкторов строк см. в разделе [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) .

## <a name="u32string"></a><a name="u32string"></a> `u32string`

Тип, описывающий специализацию шаблона класса [`basic_string`](../standard-library/basic-string-class.md) с элементами типа **`char32_t`** .

Другие определения типов, которые специализируется на специализации `basic_string` [`string`](../standard-library/string-typedefs.md#string) , включают, [`u16string`](../standard-library/string-typedefs.md#u16string) и [`wstring`](../standard-library/string-typedefs.md#wstring) .

```cpp
typedef basic_string<char32_t, char_traits<char32_t>, allocator<char32_t>> u32string;
```

### <a name="remarks"></a>Замечания

Список конструкторов строк см. в разделе [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) .

## <a name="wstring"></a><a name="wstring"></a> `wstring`

Тип, описывающий специализацию шаблона класса [`basic_string`](../standard-library/basic-string-class.md) с элементами типа **`wchar_t`** .

Другие определения типов, которые специализируется на специализации `basic_string` [`string`](../standard-library/string-typedefs.md#string) , включают, [`u16string`](../standard-library/string-typedefs.md#u16string) и [`u32string`](../standard-library/string-typedefs.md#u32string) .

```cpp
typedef basic_string<wchar_t, char_traits<wchar_t>, allocator<wchar_t>> wstring;
```

### <a name="remarks"></a>Замечания

Следующие объявления являются равнозначными:

```cpp
wstring wstr(L"");

basic_string<wchar_t> wstr(L"");
```

Список конструкторов строк см. в разделе [`basic_string::basic_string`](../standard-library/basic-string-class.md#basic_string) .

> [!NOTE]
> Размер определяется **`wchar_t`** реализацией. Если код зависит от **`wchar_t`** конкретного размера, проверьте реализацию своей платформы (например, с помощью `sizeof(wchar_t)` ). Если требуется тип символьной строки с шириной, которая гарантированно остается одинаковой на всех платформах, используйте [`string`](../standard-library/string-typedefs.md#string) , [`u16string`](../standard-library/string-typedefs.md#u16string) или [`u32string`](../standard-library/string-typedefs.md#u32string) .

## <a name="see-also"></a>См. также раздел

[`<string>`](../standard-library/string.md)
