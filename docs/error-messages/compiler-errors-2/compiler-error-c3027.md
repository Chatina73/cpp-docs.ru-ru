---
description: 'Дополнительные сведения о: Ошибка компилятора C3027'
title: Ошибка компилятора C3027
ms.date: 11/04/2016
f1_keywords:
- C3027
helpviewer_keywords:
- C3027
ms.assetid: 6562a5c2-2f28-4b36-91ca-2a64c0f0501a
ms.openlocfilehash: bf58cc6913c39919e8a9d5906e9cb81d9acce721
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174251"
---
# <a name="compiler-error-c3027"></a>Ошибка компилятора C3027

"предложение": требуется арифметическое выражение или выражение-указатель

Предложению, которому требуется арифметическое выражение или выражение-указатель, было передано выражение другого типа.

## <a name="example"></a>Пример

При компиляции следующего примера возникнет ошибка C3027:

```cpp
// C3027.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

struct MyStruct
{
    int x;
} m_MyStruct;

int main()
{
    int i;

    puts("Test with class MyStruct:\n");
    #pragma omp parallel for if(m_MyStruct)   // C3027
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);

    puts("Test with int:\n");
    #pragma omp parallel for if(9)   // OK
    for (i = 1; i <= 2; ++i)
        printf_s("Hello World - thread %d - iteration %d\n",
                 omp_get_thread_num(), i);
}
```
