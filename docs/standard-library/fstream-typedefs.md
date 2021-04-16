---
description: 'Дополнительные сведения о: &lt; FStream &gt; typedefs'
title: Определения типов &lt;fstream&gt;
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 678523452b70ee7da137316e500de8973872b4e5
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539733"
---
# <a name="fstream-typedefs"></a>Определения типов `<fstream>`

[`filebuf`](#filebuf)\
[`fstream`](#fstream)\
[`ifstream`](#ifstream)\
[`ofstream`](#ofstream)\
[`wfilebuf`](#wfilebuf)\
[`wfstream`](#wfstream)\
[`wifstream`](#wifstream)\
[`wofstream`](#wofstream)

## <a name="filebuf"></a><a name="filebuf"></a> `filebuf`

Тип, `basic_filebuf` специализированный для **`char`** параметров шаблона.

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_filebuf`](../standard-library/basic-filebuf-class.md) , специализированного для элементов типа **`char`** с признаками символа по умолчанию.

## <a name="fstream"></a><a name="fstream"></a> `fstream`

Тип, `basic_fstream` специализированный для **`char`** параметров шаблона.

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_fstream`](../standard-library/basic-fstream-class.md) , специализированного для элементов типа **`char`** с признаками символа по умолчанию.

## <a name="ifstream"></a><a name="ifstream"></a> `ifstream`

Определяет поток, который используется для последовательного чтения однобайтовых символов из файла. `ifstream` — Это typedef, который специализирует шаблон класса `basic_ifstream` для **`char`** .

Также существует `wifstream` Определение типа, которое специализируется `basic_ifstream` на чтении **`wchar_t`** двухбайтовых символов. Дополнительные сведения см. на веб-сайте [`wifstream`](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_ifstream`](../standard-library/basic-ifstream-class.md) , специализированного для элементов типа Char с признаками символа по умолчанию. Пример:

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a><a name="ofstream"></a> `ofstream`

Тип, `basic_ofstream` специализированный для **`char`** параметров шаблона.

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_ofstream`](../standard-library/basic-ofstream-class.md) , специализированного для элементов типа **`char`** с признаками символа по умолчанию.

## <a name="wfstream"></a><a name="wfstream"></a> `wfstream`

Тип, `basic_fstream` специализированный для **`wchar_t`** параметров шаблона.

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_fstream`](../standard-library/basic-fstream-class.md) , специализированного для элементов типа **`wchar_t`** с признаками символа по умолчанию.

## <a name="wifstream"></a><a name="wifstream"></a> `wifstream`

Тип, `basic_ifstream` специализированный для **`wchar_t`** параметров шаблона.

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_ifstream`](../standard-library/basic-ifstream-class.md) , специализированного для элементов типа **`wchar_t`** с признаками символа по умолчанию.

## <a name="wofstream"></a><a name="wofstream"></a> `wofstream`

Тип, `basic_ofstream` специализированный для **`wchar_t`** параметров шаблона.

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_ofstream`](../standard-library/basic-ofstream-class.md) , специализированного для элементов типа **`wchar_t`** с признаками символа по умолчанию.

## <a name="wfilebuf"></a><a name="wfilebuf"></a> `wfilebuf`

Тип, `basic_filebuf` специализированный для **`wchar_t`** параметров шаблона.

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Комментарии

Этот тип является синонимом для шаблона класса [`basic_filebuf`](../standard-library/basic-filebuf-class.md) , специализированного для элементов типа **`wchar_t`** с признаками символа по умолчанию.

## <a name="see-also"></a>См. также раздел

[`<fstream>`](../standard-library/fstream.md)
