---
title: Ошибка компилятора C3054
ms.date: 11/04/2016
f1_keywords:
- C3054
helpviewer_keywords:
- C3054
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
ms.openlocfilehash: c45a59f136b989190a46fd9fbe00fdd0e4b89527
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470137"
---
# <a name="compiler-error-c3054"></a>Ошибка компилятора C3054

Директива #pragma omp parallel в настоящее время не поддерживается в универсальном классе или функции

Дополнительные сведения см. в разделе [универсальные шаблоны](../../windows/generics-cpp-component-extensions.md) и [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3054:

```
// C3054.cpp
// compile with: /openmp /clr /c
#include <omp.h>

ref struct MyBaseClass {
   // Delete the following 7 lines to resolve.
   generic <class ItemType>
   void Test(ItemType i) {   // C3054
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }

   // OK
   void Test2() {
      #pragma omp parallel num_threads(4)
      {
         int i = omp_get_thread_num();
      }
   }
};
```