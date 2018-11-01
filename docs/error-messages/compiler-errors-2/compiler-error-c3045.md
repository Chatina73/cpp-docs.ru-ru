---
title: Ошибка компилятора C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: 9beae880d840f1cd1ac73f51ebeac8883882dd92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620822"
---
# <a name="compiler-error-c3045"></a>Ошибка компилятора C3045

Ожидается составной оператор, следующий за директивой OpenMP "sections". Отсутствует "{"

Блок кода, ограниченный фигурными скобками, должен следовать за директивой [sections](../../parallel/openmp/reference/sections-openmp.md) .

Следующий пример приводит к возникновению ошибки C3045:

```
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```