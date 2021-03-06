---
description: 'Дополнительные сведения о: Ошибка компилятора C2494'
title: Ошибка компилятора C2494
ms.date: 11/04/2016
f1_keywords:
- C2494
helpviewer_keywords:
- C2494
ms.assetid: 5dfd07ab-351d-49c9-b54e-f0a104776ab8
ms.openlocfilehash: 4842ad7360b4d8a943ee118cb56d79b694232c84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283658"
---
# <a name="compiler-error-c2494"></a>Ошибка компилятора C2494

> "*ключевое слово*" нельзя вызывать из выражения фильтра или блока __finally/финалли

Нельзя использовать *ключевое слово* в **`__finally`** **`finally`** блоке или.

Следующий пример приводит к возникновению ошибки C2494:

```cpp
// C2494.cpp
#include <malloc.h>

int main() {
   __try {}
   __except ( _alloca(100), 1 ) {}   // C2494
   __try {}
   __finally {
      _alloca(100);   // C2494
   }
}
```

C2494 также может возникать при использовании **/CLR**.

```cpp
// C2494b.cpp
// compile with: /clr
#include <malloc.h>

int main() {
   char * buf;
   try {}
   catch (char * buf2) {}
   finally {
      _alloca(100);   // C2494
   }
}
```
