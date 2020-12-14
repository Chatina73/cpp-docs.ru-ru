---
description: 'Дополнительные сведения о: Ошибка компилятора C2664'
title: Ошибка компилятора C2664
ms.date: 11/04/2016
f1_keywords:
- C2664
helpviewer_keywords:
- C2664
ms.assetid: 3595d66e-cf87-4fda-a896-c0cd81f95db4
ms.openlocfilehash: cacf799288c343b267bfa9307ec88c60f81e6e50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210846"
---
# <a name="compiler-error-c2664"></a>Ошибка компилятора C2664

function: не удается преобразовать аргумент n из type1 в type2

Эта проблема преобразования параметра может возникнуть, если создается экземпляр класса и выполняется неявное преобразование в конструкторе, помеченном **`explicit`** ключевым словом. Дополнительные сведения о явных преобразованиях см. в разделе [преобразования определяемого пользователем типа](../../cpp/user-defined-type-conversions-cpp.md).

Если временный объект передается в функцию, которая принимает ссылку на объект в качестве параметра, ссылка должна быть **`const`** ссылкой.

Если функции передается параметр, не относящийся к типу, ожидаемому функцией, то с помощью соответствующего конструктора создается временный объект. Этот временный объект затем передается функции. В этом случае временный объект будет использован для инициализации ссылки. В более ранних версиях языка все ссылки могли инициализироваться временными объектами.

Чтобы устранить ошибку C2664,

- проверьте прототип нужной функции и исправьте аргумент, указанный в сообщении;

- при необходимости введите явное преобразование.

Ошибка C2664 также может возникать в случае, если класс скрывает член одного из своих базовых классов.

Дополнительные сведения см. [в разделе руководство. Преобразование System:: String в wchar_t * или char \* ](../../dotnet/how-to-convert-system-string-to-wchar-t-star-or-char-star.md).

## <a name="examples"></a>Примеры

В следующем примере показано возникновение ошибки C2664 и приводятся сведения по ее устранению.

```cpp
// C2664.cpp
// C2664
struct A {
   void f(int i) {};
};

struct B : public A {
   // To fix, uncomment the following line.
   // using A::f;
   void f(A a) {};
};

int main() {
   B b;
   int i = 1;
   b.f(i);   // B::F hides A::f Uncomment the using declaration in B.
}
```

В этом примере также показано возникновение ошибки C2664 и приводятся сведения по ее устранению.

```cpp
// C2664b.cpp
// C2664 expected
struct A {
   // To fix, uncomment the following line.
   // A(int i){}
};

void func( int, A ) {}

int main() {
   func( 1, 1 );   // No conversion from int to A.
}
```

В следующем примере показана ошибка C2664, возникающая при использовании строкового литерала для вызова `Test`, а также описаны способы ее устранения. Поскольку параметр является ссылкой `szString`, необходимо создать объект с помощью соответствующего конструктора. В результате создается временный объект, который не может быть использован для инициализации ссылки.

```cpp
// C2664c.cpp
// compile with: /EHsc
// C2664 expected
#include <iostream>
#include <string.h>
using namespace std;

class szString {
   int slen;
   char *str;

public:
   szString(const char *);
   int len() const {
      return slen;
   }
};

// Simple reference cannot bind to temp var.
void Test(szString &a) {}

// To fix, uncomment the following line.
// void Test(const szString &a) {}

szString::szString(const char * newstr) : slen(0), str(NULL) {
   slen=strlen(newstr);
   str = new char[slen + 1];
   if (str)
      strcpy_s(str, (slen + 1), newstr);
}

int main() {
   Test("hello");
}
```

Компилятор применяет стандартные требования C++ к применению **`const`** . В следующем примере возникает ошибка C2664:

```cpp
// C2664d.cpp
// C2664 expected
#include <windows.h>

void func1(LPCSTR &s)
{

}

void func2(LPSTR &s)
{
   func1(s);
}

int main()
{
   return 0;
}
```

Вот более сложная ситуация, когда возникает ошибка C2664, а также инструкции по ее устранению.

```cpp
// C2664e.cpp
// compile with: /EHsc
// C2664 expected
#define _INTL
#include <locale>
#include <iostream>

using namespace std;
#define LEN 90

int main( ) {
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));

   // To fix, delete the following line.
   char* pszNext;

   // To fix, uncomment the following line.
   // const char* pszNext;

   wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).in( state,
      pszExt, &pszExt[strlen(pszExt)], pszNext,
      pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   // See earlier comment.
      pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error) ?
                       L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;

   exit(-1);
}
```

Переменная перечисления не преобразуется в свой базовый тип, позволяющий выполнить вызов функции. Дополнительные сведения см. в разделе [Класс Enum](../../extensions/enum-class-cpp-component-extensions.md). В следующем примере показано возникновение ошибки C2664 и приводятся сведения по ее устранению.

```cpp
// C2664f.cpp
// compile with: /clr
using namespace System;
public enum class A : Char {
   None = 0,
   NonSilent = 1,
};

void Test(Char c) {}

int main() {
   A aa = A::None;
   Test(aa);   // C2664
   Test(Char(aa));   // OK - fix by using a conversion cast
}
```

Ошибка в компиляторе MIDL приводит к тому, что тип wchar_t публикуется в библиотеке типов как unsigned short. Чтобы устранить эту ошибку, добавьте в коде C++ приведение типа или определите тип как string в IDL-файле.

```
// C2664g.idl
import "prsht.idl";

[ object, uuid(8402B8F1-BF7F-4B49-92D4-C2B9DF4543E9) ]

interface IMyObj1 : IUnknown {
   HRESULT  teststr([in, string] wchar_t *wstr);
   HRESULT  testarr([in, size_is(len)] wchar_t wstr[], [in] int len);
   HRESULT  testbstr([in] BSTR bstr);
};

[  uuid(44463307-CBFC-47A6-8B4F-13CD0A83B436) ]
library myproj1 {
   [  version(1.0), uuid(D8622C12-5448-42B8-8F0E-E3AD6B8470C1) ]
   coclass CMyObj1 { interface IMyObj1; };
}
```

C2664 также создается с помощью **`wchar_t`** при переносе кода из Visual C++ 6,0 в более поздние версии. В Visual C++ 6,0 и более ранних версий **`wchar_t`** WAS был **`typedef`** для **`unsigned short`** и, следовательно, неявно преобразован в этот тип. После Visual C++ 6,0 **`wchar_t`** является собственным встроенным типом, как указано в стандарте C++, и больше не может быть неявно преобразован в **`unsigned short`** . См. раздел [/Zc: wchar_t (wchar_t является собственным типом)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

В следующем примере показано возникновение ошибки C2664 и приводятся сведения по ее устранению.

```cpp
// C2664h.cpp
#import "C2664g.tlb"
using namespace myproj1;

int main() {
   IMyObj1Ptr ptr;

   wchar_t * mybuff = 0;
   BSTR bstr = 0;
   int len;
   ptr->teststr(mybuff);
   ptr->testbstr(bstr);
   ptr->testarr(mybuff, len);   // C2664
   ptr->testarr((unsigned short *)mybuff, len);   // OK - Fix by using a cast
}
```

Ошибка C2664 также возникает, если компилятор не может вывести аргументы шаблона.

```cpp
// C2664i.cpp
#include <stdio.h>
template <class T, int iType=0>
class CTypedImg {
public:
   CTypedImg() {}
   void run() {}

   operator CTypedImg<T>& () {
      return *((CTypedImg<T>*)this);
    }
};

template <class t1>
void test(CTypedImg<t1>& myarg) {
   myarg.run();
}

int main() {
   CTypedImg<float,2> img;

   test((CTypedImg<float>&)img);   // OK
   test<float>(img);   // OK
   test(img);   // C2664 - qualify as above to fix
}
```
