---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4803'
title: Предупреждение компилятора (уровень 1) C4803
ms.date: 11/04/2016
f1_keywords:
- C4803
helpviewer_keywords:
- C4803
ms.assetid: 2552f3a6-c418-49f4-98a2-a929857be658
ms.openlocfilehash: 95646895133febbf03750d1b7a07d3a8141b6eff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334930"
---
# <a name="compiler-warning-level-1-c4803"></a>Предупреждение компилятора (уровень 1) C4803

"метод": метод Raise имеет другой класс хранения из этого события, "Event"

Методы событий должны иметь тот же класс хранения, что и объявление события. Компилятор корректирует методы события таким образом, чтобы классы хранения совпадали.

Это предупреждение может возникать, если имеется класс, реализующий событие из интерфейса. Компилятор не создает неявным образом метод Raise для события в интерфейсе. При реализации этого интерфейса в классе компилятор неявно создает метод Raise, и этот метод не будет виртуальным, что, следовательно, предупреждение. Дополнительные сведения о событиях см. в разделе [event](../../extensions/event-cpp-component-extensions.md).

Сведения о том, как отключить предупреждение, см. в разделе [предупреждение](../../preprocessor/warning.md) pragma.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4803.

```cpp
// C4803.cpp
// compile with: /clr /W1
using namespace System;

public delegate void Del();

ref struct E {
   Del ^ _pd1;
   event Del ^ E1 {
      void add (Del ^ pd1) {
         _pd1 = dynamic_cast<Del ^>(Delegate::Combine(_pd1, pd1));
      }

      void remove(Del^ pd1) {
         _pd1 = dynamic_cast<Del^> (Delegate::Remove(_pd1, pd1));
      }

      virtual void raise() {   // C4803 warning (remove virtual)
         if (_pd1)
            _pd1();
      }
   }

   void func() {
      Console::WriteLine("In E::func()");
   }
};

int main() {
   E ^ ep = gcnew E;
   ep->E1 += gcnew Del(ep, &E::func);
   ep->E1();
   ep->E1 -= gcnew Del(ep, &E::func);
   ep->E1();
}
```
