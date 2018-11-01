---
title: Ошибка компилятора C3010
ms.date: 11/04/2016
f1_keywords:
- C3010
helpviewer_keywords:
- C3010
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
ms.openlocfilehash: c5f0d33632cb155b8365c8de421fa5eaf91421c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455501"
---
# <a name="compiler-error-c3010"></a>Ошибка компилятора C3010

"метка": переход из структурированного блока OpenMP запрещен

Код не может переходить в блок OpenMP или из этого блока.

Следующий пример приводит к возникновению ошибки C3010.

```
// C3010.c
// compile with: /openmp
int main() {
   #pragma omp parallel
   {
      #pragma omp parallel
      {
         goto lbl3;
      }
   }
   lbl3:;   // C3010
}
```