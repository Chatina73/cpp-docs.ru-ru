---
description: 'Дополнительные сведения о: Ошибка компилятора C3206'
title: Ошибка компилятора C3206
ms.date: 11/04/2016
f1_keywords:
- C3206
helpviewer_keywords:
- C3206
ms.assetid: d62995b5-e349-4418-bbe8-8a5e776ca7b0
ms.openlocfilehash: ea4ded5daebe0f002a3d0363fba125c2c02f332b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174017"
---
# <a name="compiler-error-c3206"></a>Ошибка компилятора C3206

"функция": недопустимый аргумент типа для "параметр", отсутствует список аргументов типа для типа класса "имя_типа"

Функция-шаблон определена как принимающая аргумент типа шаблона. Однако передан аргумент шаблона template.

Следующий пример приводит к возникновению ошибки C3206:

```cpp
// C3206.cpp
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S>();   // C3206
   // try the following line instead
   // f<S<int> >();
}
```

Возможное решение:

```cpp
// C3206b.cpp
// compile with: /c
template <class T>
void f() {}

template <class T>
struct S {};

void f1() {
   f<S<int> >();
}
```

Ошибка C3206 также может возникнуть при использовании универсальных шаблонов.

```cpp
// C3206c.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS>();   // C3206
}
```

Возможное решение:

```cpp
// C3206d.cpp
// compile with: /clr
generic <class GT1>
void gf() {}

generic <class T>
value struct GS {};

int main() {
   gf<GS<int> >();
}
```

Шаблон класса недопустим в качестве аргумента типа шаблона. Следующий пример вызывает исключение C3206:

```cpp
// C3206e.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T<int> t;
}

int main() {
   func<S>();   // C3206 S is not a type.
}
```

Возможное решение:

```cpp
// C3206f.cpp
template <class T>
struct S {};

template <class T>
void func() {   // takes a type
   T t;
}

int main() {
   func<S<int> >();
}
```

Если требуется параметр шаблона шаблона, необходимо заключить функцию в класс шаблона, который принимает параметр шаблона шаблона:

```cpp
// C3206g.cpp
template <class T>
struct S {};

template<template<class> class TT>
struct X {
   static void func() {
      TT<int> t1;
      TT<char> t2;
   }
};

int main() {
   X<S>::func();
}
```
