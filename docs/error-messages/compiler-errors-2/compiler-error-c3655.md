---
description: 'Дополнительные сведения о: Ошибка компилятора C3655'
title: Ошибка компилятора C3655
ms.date: 11/04/2016
f1_keywords:
- C3655
helpviewer_keywords:
- C3655
ms.assetid: 724919ab-2915-4b61-8794-44648e162d62
ms.openlocfilehash: aafe0d114b5981d12376b6808841c44de08ab0bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134476"
---
# <a name="compiler-error-c3655"></a>Ошибка компилятора C3655

"функция": функция уже явно переопределена

Функция может быть явно переопределена только один раз. Дополнительные сведения см. в разделе [явные переопределения](../../extensions/explicit-overrides-cpp-component-extensions.md).

Следующий пример приводит к возникновению ошибки C3655:

```cpp
// C3655.cpp
// compile with: /clr /c
public ref struct B {
   virtual void f();
   virtual void g();
};

public ref struct D : B {
   virtual void f() new sealed = B::f;
   virtual void g() new sealed = B::f;   // C3655
   // try the following line instead
   // virtual void g() new sealed = B::g;
};
```
