---
title: Ошибка компилятора C3010
ms.date: 11/04/2016
f1_keywords:
- C3010
helpviewer_keywords:
- C3010
ms.assetid: e959d038-bba6-432a-9c0a-0470474de7d9
ms.openlocfilehash: c5f0d33632cb155b8365c8de421fa5eaf91421c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350339"
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