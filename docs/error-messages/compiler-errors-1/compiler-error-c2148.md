---
description: 'Дополнительные сведения о: Ошибка компилятора C2148'
title: Ошибка компилятора C2148
ms.date: 11/04/2016
f1_keywords:
- C2148
helpviewer_keywords:
- C2148
ms.assetid: e510c2c9-7b57-4ce8-be03-ba363e2cc5d9
ms.openlocfilehash: 253d3d491a17002ab885649c010190833c59f687
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97235363"
---
# <a name="compiler-error-c2148"></a>Ошибка компилятора C2148

Общий размер массива не должен превышать 0x7fffffff байт

Массив превышает ограничение. Уменьшите размер массива.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C2148:

```cpp
// C2148.cpp
#include <stdio.h>
#include <stdlib.h>

int main( ) {
   char MyArray[0x7ffffffff];   // C2148
   char * MyArray2 = (char *)malloc(0x7fffffff);

   if (MyArray2)
      printf_s("It worked!");
   else
      printf_s("It didn't work.");
}
```
