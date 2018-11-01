---
title: Ошибка компилятора C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 5ff8b0bee1f79d9534841e4368fd5a5249cbb413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534853"
---
# <a name="compiler-error-c2267"></a>Ошибка компилятора C2267

«функция»: статические функции с областью видимости блока недопустимы

Локальная функция объявлена `static`. Статические функции должны иметь глобальной области.

Следующий пример приводит к возникновению ошибки C2267:

```
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```