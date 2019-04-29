---
title: Ошибка компилятора C3642
ms.date: 11/04/2016
f1_keywords:
- C3642
helpviewer_keywords:
- C3642
ms.assetid: 429790c2-9614-4d85-b31c-687c8d8f83ff
ms.openlocfilehash: d524c49075c400caa345dd26ed681734ea0cfb94
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385625"
---
# <a name="compiler-error-c3642"></a>Ошибка компилятора C3642

«return_type/args»: невозможно вызвать функцию с соглашением вызова из машинного кода __clrcall

Функция, которая отмечена [__clrcall](../../cpp/clrcall.md) соглашение о вызовах не может вызываться из машинного (неуправляемого) кода.

*return_type/args* имя функции или тип `__clrcall` вы пытаетесь вызвать функцию.  Тип используется при вызове через указатель функции.

Чтобы вызвать управляемую функцию из собственного контекста, можно добавить функцию «оболочки», который будет вызывать `__clrcall` функции. Или можно использовать механизм маршалинга среды CLR; см. в разделе [как: Маршалинг PInvoke с помощью указателей функции](../../dotnet/how-to-marshal-function-pointers-using-pinvoke.md) Дополнительные сведения.

Следующий пример приводит к возникновению ошибки C3642:

```
// C3642.cpp
// compile with: /clr
using namespace System;
struct S {
   void Test(String ^ s) {   // CLR type in signature, implicitly __clrcall
      Console::WriteLine(s);
   }
   void Test2(char * s) {
      Test(gcnew String(s));
   }
};

#pragma unmanaged
int main() {
   S s;
   s.Test("abc");   // C3642
   s.Test2("abc");   // OK
}
```