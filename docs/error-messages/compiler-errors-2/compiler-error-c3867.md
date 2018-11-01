---
title: Ошибка компилятора C3867
ms.date: 11/04/2016
f1_keywords:
- C3867
helpviewer_keywords:
- C3867
ms.assetid: bc5de03f-e01a-4407-88c3-2c63f0016a1e
ms.openlocfilehash: 9308e238c86c7b8a957720228a823688fac289d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571201"
---
# <a name="compiler-error-c3867"></a>Ошибка компилятора C3867

func: в вызове функции отсутствует список аргументов; используйте "&func" для создания указателя на член

Вы попытались получить адрес функции-члена без указания полного имени класса и оператора взятия адреса функции-члена.

Эта ошибка также может возникать в результате действий по обеспечению совместимости компилятора с Visual C++ 2005: расширенным соответствием указателя на элемент. Код, скомпилированный в версии до Visual C++ 2005, будет выдавать ошибку C3867.

## <a name="example"></a>Пример

Ошибка C3867 может быть вызвана компилятором с неправильно предложенным разрешением. По возможности используйте наиболее производный класс.

В следующем примере показано возникновение ошибки C3867 и приводятся сведения по ее устранению.

```
// C3867_1.cpp
// compile with: /c
struct Base {
protected:
   void Test() {}
};

class Derived : public Base {
   virtual void Bar();
};

void Derived::Bar() {
   void (Base::*p1)() = Test;   // C3867
   &Derived::Test;   // OK
}
```

## <a name="example"></a>Пример

В следующем примере показано возникновение ошибки C3867 и приводятся сведения по ее устранению.

```
// C3867_2.cpp
#include<stdio.h>

struct S {
   char *func() {
      return "message";
   }
};

class X {
public:
   void f() {}
};

int main() {
   X::f;   // C3867

   // OK
   X * myX = new X;
   myX->f();

   S s;
   printf_s("test %s", s.func);   // C3867
   printf_s("test %s", s.func());   // OK
}
```

## <a name="example"></a>Пример

В следующем примере показано возникновение ошибки C3867 и приводятся сведения по ее устранению.

```
// C3867_3.cpp
class X {
public:
   void mf(){}
};

int main() {
   void (X::*pmf)() = X::mf;   // C3867

   // try the following line instead
   void (X::*pmf2)() = &X::mf;
}
```

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3867:

```
// C3867_4.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b1;
      b1.p = f;   // C3867
   }
};
```

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3867:

```
// C3867_5.cpp
// compile with: /EHsc
#include <iostream>

class Testpm {
public:
   void m_func1() {
      std::cout << m_num << "\tm_func1\n";
    }

   int m_num;
   typedef void (Testpm::*pmfn1)();
   void func(Testpm* p);
};

void Testpm::func(Testpm* p) {
   pmfn1 s = m_func1;   // C3867
   pmfn1 s2 = &Testpm::m_func1;   // OK
   (p->*s2)();
}

int main() {
   Testpm *pTestpm = new Testpm;
   pTestpm->m_num = 10;

   pTestpm->func(pTestpm);
}
```