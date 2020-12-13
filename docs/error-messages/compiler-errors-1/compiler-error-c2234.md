---
description: 'Дополнительные сведения о: Ошибка компилятора C2234'
title: Ошибка компилятора C2234
ms.date: 11/04/2016
f1_keywords:
- C2234
helpviewer_keywords:
- C2234
ms.assetid: cfa42458-c803-4717-a017-9eca1c0cbfb0
ms.openlocfilehash: a21ca3922d55ed7fe6a5b5d6a264f0d8491c6dda
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338765"
---
# <a name="compiler-error-c2234"></a>Ошибка компилятора C2234

"имя": недопустимые массивы ссылок

Поскольку указатели на ссылки не допускаются, массивы ссылок невозможны.

Следующий пример приводит к возникновению ошибки C2234:

```cpp
// C2234.cpp
int main() {
   int i = 0, j = 0, k = 0, l = 0;
   int &array[4] = {i,j,k,l};   // C2234
   int array2[4] = {i,j,k,l};   // OK
}
```
