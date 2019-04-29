---
title: Ошибка компилятора C3020
ms.date: 11/04/2016
f1_keywords:
- C3020
helpviewer_keywords:
- C3020
ms.assetid: f625c7a3-afaa-4bd8-9c1b-51891b832f36
ms.openlocfilehash: 0e2d8e70dcc9b23c56a321487cd4b933a1086387
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386685"
---
# <a name="compiler-error-c3020"></a>Ошибка компилятора C3020

«var»: переменная индекса из OpenMP цикла «for» нельзя изменять в теле цикла

OpenMP `for` цикла не может изменять индекс (счетчик цикла) в теле `for` цикла.

Следующий пример приводит к возникновению ошибки C3020:

```
// C3020.cpp
// compile with: /openmp
int main() {
   int i = 0, n = 3;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i < 10; i += n)
         i *= 2;   // C3020
         // try the following line instead
         // n++;
   }
}
```

Переменная, объявленная с [lastprivate](../../parallel/openmp/reference/lastprivate.md) нельзя использовать в качестве индекса внутри распараллеленного цикла.

Следующий пример будет предоставлять C3020 для второй lastprivate, поскольку этот lastprivate активирует запись в idx_a внутри внешнего цикла for. Первый параметр lastprivate не вызывает ошибку, поскольку запись в idx_a за пределами внешнего цикла (с технической точки зрения в самом конце последней итерации). Следующий пример приводит к возникновению ошибки C3020.

```
// C3020b.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_a)   // C3020
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```

В следующем примере показано возможное решение:

```
// C3020c.cpp
// compile with: /openmp /c
float a[100][100];
int idx_a, idx_b;
void test(int first, int last)
{
   #pragma omp parallel for lastprivate(idx_a)
   for (idx_a = first; idx_a <= last; ++idx_a) {
      #pragma omp parallel for lastprivate(idx_b)
      for (idx_b = first; idx_b <= last; ++idx_b) {
         a[idx_a][idx_b] += 1.0f;
      }
   }
}
```