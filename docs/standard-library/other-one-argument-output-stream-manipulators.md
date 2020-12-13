---
description: 'Дополнительные сведения: другие манипуляторы потока вывода One-Argument'
title: Прочие манипуляторы потока вывода с одним аргументом
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, one-argument manipulators
ms.assetid: e381dee8-6b16-4cef-805a-4a6a1d2b696b
ms.openlocfilehash: 3ad50216375de1ca5e2d9fe41b206aa01a8c8e80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342261"
---
# <a name="other-one-argument-output-stream-manipulators"></a>Прочие манипуляторы потока вывода с одним аргументом

В следующем примере используется класс `money` , который является **`long`** типом. Манипулятор `setpic` присоединяет строку форматирования "рисунок" к классу, который может использоваться перегруженным оператором вставки в поток класса `money`. Строка изображения сохраняется как статическая переменная в классе `money`, а не как член данных класса потока, поэтому не нужно производить новый класс потока вывода.

## <a name="example"></a>Пример

```cpp
// one_arg_output.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

typedef char* charp;

class money
{
private:
    long value;
    static char *szCurrentPic;
public:
    money( long val ) { value = val; }
    friend ostream& operator << ( ostream& os, money m ) {
        // A more complete function would merge the picture
        // with the value rather than simply appending it
        os << m.value << '[' << money::szCurrentPic << ']';
        return os;
    }
    static void setpic( char* szPic ) {
        money::szCurrentPic = new char[strlen( szPic ) + 1];
        strcpy_s( money::szCurrentPic, strlen( szPic ) + 1, szPic );
    }
};

char *money::szCurrentPic;  // Static pointer to picture

void fb( ios_base& os, char * somename )
{
   money::setpic(somename);
/*
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
*/
}

_Smanip<charp>
   __cdecl setpic(char * somename)
   {
   return (_Smanip<charp>(&fb, somename));
   }

int main( )
{
    money amt = (long)35235.22;
    cout << setiosflags( ios::fixed );
    cout << setpic( "###,###,###.##" ) << "amount = " << amt << endl;
}
```

## <a name="see-also"></a>См. также раздел

[Пользовательские манипуляторы с аргументами](../standard-library/custom-manipulators-with-arguments.md)
