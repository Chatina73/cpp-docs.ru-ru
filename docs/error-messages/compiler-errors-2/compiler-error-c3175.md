---
description: 'Дополнительные сведения о: Ошибка компилятора C3175'
title: Ошибка компилятора C3175
ms.date: 11/04/2016
f1_keywords:
- C3175
helpviewer_keywords:
- C3175
ms.assetid: 3f19d513-a05a-4b6c-806f-276fe5c36b90
ms.openlocfilehash: 278d8de3d18aaa3437f4d2c0b1d8c9e3306630a6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242084"
---
# <a name="compiler-error-c3175"></a>Ошибка компилятора C3175

"функция1": невозможно вызвать метод управляемого типа из неуправляемой функции "функция2"

Неуправляемые функции не могут вызывать функции членов управляемых классов.

Следующий пример приводит к возникновению ошибки C3175:

```cpp
// C3175_2.cpp
// compile with: /clr

ref struct A {
   static void func() {
   }
};

#pragma unmanaged   // remove this line to resolve

void func2() {
   A::func();   // C3175
}

#pragma managed

int main() {
   A ^a = gcnew A;
   func2();
}
```
