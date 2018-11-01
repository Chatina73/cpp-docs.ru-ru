---
title: Ошибка компилятора C3266
ms.date: 11/04/2016
f1_keywords:
- C3266
helpviewer_keywords:
- C3266
ms.assetid: 7375c099-acb7-42f6-898d-57cfefa010b8
ms.openlocfilehash: d93056116ebf2f4646dc34f848b073fe6401b9db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475170"
---
# <a name="compiler-error-c3266"></a>Ошибка компилятора C3266

"класс": список параметров конструктора класса должен иметь тип "void"

Конструкторы классов, программируемых с использованием параметра /clr, не могут принимать параметры.

Следующий пример приводит к возникновению ошибки C3266:

```
// C3266.cpp
// compile with: /clr

ref class X {
   static X(int i) { // C3266
   // try the following line instead
   // static X() {
   }
};

int main() {
}
```
