---
description: 'Дополнительные сведения о: Ошибка компилятора C2423'
title: Ошибка компилятора C2423
ms.date: 11/04/2016
f1_keywords:
- C2423
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
ms.openlocfilehash: 902a02d4bad34b3a386b95a72c8eca59dac19156
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120234"
---
# <a name="compiler-error-c2423"></a>Ошибка компилятора C2423

"число": недопустимый масштаб

Для масштабирования регистра в встроенном коде ассемблера используется число, отличное от 1, 2, 4 или 8.

Следующий пример приводит к возникновению ошибки C2423:

```cpp
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```
