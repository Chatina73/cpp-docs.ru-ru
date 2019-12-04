---
title: Ошибка компилятора C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: 39a57aa7b85b9f8a8aae0b93e2b346584edef8de
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756244"
---
# <a name="compiler-error-c3421"></a>Ошибка компилятора C3421

"тип": невозможно вызвать метод завершения для данного класса, поскольку он либо недоступен, либо не существует

Метод завершения является неявно закрытым, поэтому его нельзя вызвать за пределами включающего типа.

Дополнительные сведения см. [в разделе Деструкторы и методы завершения в статье инструкции: определение и использование классов и структур (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3421:

```cpp
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```
