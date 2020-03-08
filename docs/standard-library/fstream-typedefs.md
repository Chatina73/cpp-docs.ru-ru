---
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
ms.openlocfilehash: 3f4104b28f5becfdbf62ede16faa81e855fcac8c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2020
ms.locfileid: "78876117"
---
# <a name="ltfstreamgt-typedefs"></a>Определения типов &lt;fstream&gt;

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

Тип `basic_filebuf` специализированный для параметров шаблона **char** .

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_filebuf](../standard-library/basic-filebuf-class.md)шаблона класса, специализированного для элементов типа **char** с признаками символа по умолчанию.

## <a name="fstream"></a>  fstream

Тип `basic_fstream` специализированный для параметров шаблона **char** .

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_fstream](../standard-library/basic-fstream-class.md)шаблона класса, специализированного для элементов типа **char** с признаками символа по умолчанию.

## <a name="ifstream"></a>  ifstream

Определяет поток, который используется для последовательного чтения однобайтовых символов из файла. `ifstream` — это typedef, который специализирует шаблон класса `basic_ifstream` для **char**.

Существует также `wifstream`, typedef, который специализирует `basic_ifstream` для чтения **wchar_t** двухбайтовых символов. Дополнительные сведения см. в описании [wifstream](../standard-library/fstream-typedefs.md#wifstream).

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_ifstream](../standard-library/basic-ifstream-class.md)шаблона класса, специализированного для элементов типа Char с признаками символа по умолчанию. Пример:

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

Тип `basic_ofstream` специализированный для параметров шаблона **char** .

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_ofstream](../standard-library/basic-ofstream-class.md)шаблона класса, специализированного для элементов типа **char** с признаками символа по умолчанию.

## <a name="wfstream"></a>  wfstream

Тип `basic_fstream` специализированный для параметров шаблона **wchar_t** .

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_fstream](../standard-library/basic-fstream-class.md)шаблона класса, специализированного для элементов типа **wchar_t** с признаками символа по умолчанию.

## <a name="wifstream"></a>  wifstream

Тип `basic_ifstream` специализированный для параметров шаблона **wchar_t** .

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_ifstream](../standard-library/basic-ifstream-class.md)шаблона класса, специализированного для элементов типа **wchar_t** с признаками символа по умолчанию.

## <a name="wofstream"></a>  wofstream

Тип `basic_ofstream` специализированный для параметров шаблона **wchar_t** .

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_ofstream](../standard-library/basic-ofstream-class.md)шаблона класса, специализированного для элементов типа **wchar_t** с признаками символа по умолчанию.

## <a name="wfilebuf"></a>  wfilebuf

Тип `basic_filebuf` специализированный для параметров шаблона **wchar_t** .

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Remarks

Тип является синонимом [basic_filebuf](../standard-library/basic-filebuf-class.md)шаблона класса, специализированного для элементов типа **wchar_t** с признаками символа по умолчанию.

## <a name="see-also"></a>См. также раздел

[\<fstream>](../standard-library/fstream.md)
