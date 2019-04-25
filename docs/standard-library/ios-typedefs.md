---
title: Определения типов &lt;ios&gt;
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 1f0ff93c22263ca4b35377b5d9af089816e8895a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159266"
---
# <a name="ltiosgt-typedefs"></a>Определения типов &lt;ios&gt;

||||
|-|-|-|
|[ios](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|

## <a name="ios"></a>  ios

Поддерживает класс ios из старой библиотеки iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Примечания

Тип является синонимом класса шаблона [basic_ios](../standard-library/basic-ios-class.md), специализированного для элементов типа **char** с признаками символа по умолчанию.

## <a name="streamoff"></a>  streamoff

Поддерживает внутренние операции.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Примечания

Тип — целое число со знаком, описывающее объект, который может хранить смещение в байтах, участвующее в различных операциях размещения потока. Его представление имеет по крайней мере 32 бита значения. Оно не обязательно достаточно велико для представления произвольных позиций внутри потока. Значение `streamoff(-1)` обычно указывает на ошибочное смещение.

## <a name="streampos"></a>  streampos

Содержит текущее положение указателя буфера или указателя файла.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Примечания

Тип является синонимом для [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

### <a name="example"></a>Пример

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a>  streamsize

Указывает размер потока.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Примечания

Тип — целое число со знаком, описывающее объект, который может хранить количество элементов, участвующих в различных операциях размещения потока. Его представление имеет по крайней мере 16 битов значения. Оно не обязательно достаточно велико для представления произвольных позиций внутри потока.

### <a name="example"></a>Пример

После компиляции и запуска следующей программы рассмотрим файл Test.txt, чтобы увидеть влияние параметра `streamsize`.

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## <a name="wios"></a>  wios

Поддерживает класс wios из старой библиотеки iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Примечания

Тип является синонимом класса шаблона [basic_ios](../standard-library/basic-ios-class.md), специализированного для элементов типа **wchar_t** с признаками символа по умолчанию.

## <a name="wstreampos"></a>  wstreampos

Содержит текущее положение указателя буфера или указателя файла.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Примечания

Тип является синонимом для [fpos](../standard-library/fpos-class.md)< `mbstate_t`>.

### <a name="example"></a>Пример

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="see-also"></a>См. также

[\<ios>](../standard-library/ios.md)<br/>
