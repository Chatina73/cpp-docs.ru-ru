---
description: Дополнительные сведения см. в статье как использовать safe_cast в C++/CLI
title: Практическое руководство. Использование safe_cast в C++/CLI
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: f921371f97f967f9517121aaa163f79769781211
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97145578"
---
# <a name="how-to-use-safe_cast-in-ccli"></a>Практическое руководство. Использование safe_cast в C++/CLI

В этой статье показано, как использовать safe_cast в приложениях C++/CLI. Дополнительные сведения о safe_cast в C++/CX см. в разделе [safe_cast](../extensions/safe-cast-cpp-component-extensions.md).

## <a name="upcasting"></a>Treat

Приведение является приведением из производного типа к одному из его базовых классов. Это приведение является надежным и не требует явной нотации приведения. В следующем примере показано, как выполнить приведение, с `safe_cast` ним и без него.

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>Опуститься

Образование производных типов — это преобразование из базового класса в класс, производный от базового класса.  Такое произведение является надежным только в том случае, если объект, который обращается к среде выполнения, на самом деле обращается к производному объекту класса.  В отличие от **`static_cast`** , `safe_cast` выполняет динамическую проверку и вызывает исключение, <xref:System.InvalidCastException> Если преобразование завершается неудачей.

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safe_cast-with-user-defined-conversions"></a>safe_cast с пользовательскими преобразованиями

В следующем примере показано, как можно использовать `safe_cast` для вызова пользовательских преобразований.

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safe_cast-and-boxing-operations"></a>safe_cast и операции упаковки

### <a name="boxing"></a>Упаковка-преобразование

Упаковка определяется как пользовательское преобразование, добавленное компилятором.  Таким образом, можно использовать `safe_cast` для блочности значения в КУЧЕ CLR.

В следующем примере показана упаковка с простыми и пользовательскими типами значений.  `safe_cast`Поле переменной типа значения, которое находится в машинном стеке, чтобы его можно было присвоить переменной в куче со сборкой мусора.

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

В следующем примере показано, что упаковка имеет приоритет над определяемым пользователем преобразованием в `safe_cast` операции.

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>Распаковка-преобразование

Распаковка определяется как пользовательское преобразование, добавленное компилятором.  Таким образом, можно использовать `safe_cast` для распаковки значения в КУЧЕ CLR.

Распаковка является определяемым пользователем преобразованием, но в отличие от упаковки, распаковка должна быть явной, т. е. должна выполняться с помощью **`static_cast`** , приведение в стиле C или `safe_cast` ; распаковка не может быть выполнена неявно.

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

В следующем примере показана распаковка с типами значений и типами-примитивами.

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safe_cast-and-generic-types"></a>safe_cast и универсальные типы

В следующем примере показано, как можно использовать `safe_cast` для выполнения образования производных с универсальным типом.

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>См. также раздел

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
