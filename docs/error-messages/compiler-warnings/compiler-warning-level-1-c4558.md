---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4558'
title: Предупреждение компилятора (уровень 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: b35f127daad10d0346a8adc30e712d6de56d5805
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173679"
---
# <a name="compiler-warning-level-1-c4558"></a>Предупреждение компилятора (уровень 1) C4558

значение операнда "значение" выходит за пределы диапазона "ловербаунд-уппербаунд"

Значение, передаваемое в инструкцию языка ассемблера, выходит за пределы диапазона, указанного для параметра. Значение будет обрезано.

Следующий пример приводит к возникновению ошибки C4558:

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```
