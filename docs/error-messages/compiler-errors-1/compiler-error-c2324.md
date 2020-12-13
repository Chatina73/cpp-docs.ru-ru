---
description: 'Дополнительные сведения о: Ошибка компилятора C2324'
title: Ошибка компилятора C2324
ms.date: 11/04/2016
f1_keywords:
- C2324
helpviewer_keywords:
- C2324
ms.assetid: 215f0544-85b0-452d-825f-17a388b6a61c
ms.openlocfilehash: 25aa799e9419b0bbab32b7362b1fdd9c604a66c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344449"
---
# <a name="compiler-error-c2324"></a>Ошибка компилятора C2324

"идентификатор": не предусмотрено справа от "имя"

Деструктор вызывается с неверным идентификатором.

Следующий пример приводит к возникновению ошибки C2324:

```cpp
// C2324.cpp
class A {};
typedef A* pA_t;
int i;

int main() {
   pA_t * ppa = new pA_t;
   ppa->~i;   // C2324
   ppa->~pA_t();   // OK
}
```
