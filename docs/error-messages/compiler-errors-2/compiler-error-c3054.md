---
description: 'Дополнительные сведения о: Ошибка компилятора C3054'
title: Ошибка компилятора C3054
ms.date: 11/04/2016
f1_keywords:
- C3054
helpviewer_keywords:
- C3054
ms.assetid: 6f4b7ac5-0d12-474b-b611-76ff26ee41ac
ms.openlocfilehash: 1fb72f1aa04efb39c007bcbe9b738a1ee3f39bea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269618"
---
# <a name="compiler-error-c3054"></a>Ошибка компилятора C3054

Директива #pragma omp parallel в настоящее время не поддерживается в универсальном классе или функции

Дополнительные сведения см. в разделе [универсальные шаблоны](../../extensions/generics-cpp-component-extensions.md) и [OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3054:

```cpp
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
