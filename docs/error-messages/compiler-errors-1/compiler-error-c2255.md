---
title: Ошибка компилятора C2255
ms.date: 11/04/2016
f1_keywords:
- C2255
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
ms.openlocfilehash: 2cb2fd5a673fd44e2b06f8675cfc3ae8e418c290
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87208750"
---
# <a name="compiler-error-c2255"></a>Ошибка компилятора C2255

"элемент": не допускается вне определения класса

Например, функция, не являющийся членом, объявляется **`friend`** .

При компиляции следующего примера возникнет ошибка C2255:

```cpp
// C2255.cpp
// compile with: /c
class A {
private:
   void func1();
   friend void func2();
};

friend void func1() {}   // C2255
void func2(){}
```
