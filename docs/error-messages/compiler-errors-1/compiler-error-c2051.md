---
description: 'Дополнительные сведения о: Ошибка компилятора C2051'
title: Ошибка компилятора C2051
ms.date: 11/04/2016
f1_keywords:
- C2051
helpviewer_keywords:
- C2051
ms.assetid: 81c0469a-78e2-49fa-bd76-97cdb135e3ea
ms.openlocfilehash: ceea0466ef5f285c9cf7b3aa6bdf312ec25f283e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175018"
---
# <a name="compiler-error-c2051"></a>Ошибка компилятора C2051

выражение CASE не является константой

Выражения CASE должны быть целочисленными константами.

Следующий пример приводит к возникновению ошибки C2051:

```cpp
// C2051.cpp
class X {};

int main() {
   static X x;
   int i = 0;

   switch (i) {
      case x:   // C2051 use constant expression to resolve error
         break;
      default:
         break;
   }
}
```

Возможное решение:

```cpp
// C2051b.cpp
class X {};

int main() {
   static X x;
   int i = 0;

   switch (i) {
      case 1:
         break;
      default:
         break;
   }
}
```
