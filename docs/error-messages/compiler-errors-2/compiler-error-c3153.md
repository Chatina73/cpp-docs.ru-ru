---
title: Ошибка компилятора C3153
ms.date: 11/04/2016
f1_keywords:
- C3153
helpviewer_keywords:
- C3153
ms.assetid: d775d97e-2480-484f-81f1-88406b10f947
ms.openlocfilehash: 62b9e7499c52153183f14eae47c488da6a59b458
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610422"
---
# <a name="compiler-error-c3153"></a>Ошибка компилятора C3153

«интерфейс»: не удается создать экземпляр интерфейса

Интерфейс не может быть создан. Чтобы использовать члены интерфейса, наследуйте класс от интерфейса, реализация членов интерфейса и затем использовать элементы.

Следующий пример приводит к возникновению ошибки C3153:

```
// C3153.cpp
// compile with: /clr
interface class A {
};

int main() {
   A^ a = gcnew A;   // C3153
}
```
