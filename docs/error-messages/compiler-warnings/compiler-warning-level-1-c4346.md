---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4346'
title: Предупреждение компилятора (уровень 1) C4346
ms.date: 11/04/2016
f1_keywords:
- C4346
helpviewer_keywords:
- C4346
ms.assetid: 68ee562d-cca9-4a2a-9a1b-14ad1a1e7396
ms.openlocfilehash: 587aaf6954bb649ab12478721fcf428ef3611329
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340013"
---
# <a name="compiler-warning-level-1-c4346"></a>Предупреждение компилятора (уровень 1) C4346

"имя": зависимое имя не является типом

Ключевое слово [TypeName](../../cpp/typename.md) требуется, если зависимое имя должно обрабатываться как тип. Для кода, который работает одинаково во всех версиях Visual C++, добавьте **`typename`** к объявлению.

Следующий пример приводит к возникновению ошибки C4346:

```cpp
// C4346.cpp
// compile with: /WX /LD
template<class T>
struct C {
   T::X* x;   // C4346
   // try the following line instead
   // typename T::X* x;
};
```

В следующих примерах показаны другие примеры, в которых **`typename`** ключевое слово является обязательным:

```cpp
// C4346b.cpp
// compile with: /LD /W1
template<class T>
const typename T::X& f(typename T::Z* p);   // Required in both places

template<class T, int N>
struct L{};

template<class T>
struct M : public L<typename T::Type, T::Value>
{   // required on type argument, not on non-type argument
   typedef typename T::X   Type;
   Type f();   // OK: "Type" is a type-specifer
   typename T::X g();   // typename required
   operator typename T::Z();   // typename required
};
```

и это,

```cpp
// C4346c.cpp
// compile with: /LD /WX
struct Y {
   typedef int Y_t;
};

template<class T>
struct A {
   typedef Y A_t;
};

template<class T>
struct B {
   typedef /*typename*/ A<T>::A_t B_t;   // C4346 typename needed here
   typedef /*typename*/ B_t::Y_t  B_t2;   // typename also needed here
};
```
