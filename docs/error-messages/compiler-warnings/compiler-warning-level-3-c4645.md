---
title: Предупреждение компилятора (уровень 3) C4645
ms.date: 11/04/2016
f1_keywords:
- C4645
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
ms.openlocfilehash: a3e5c834a3f14b9a125176dcddd5bcc355cf1faa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401648"
---
# <a name="compiler-warning-level-3-c4645"></a>Предупреждение компилятора (уровень 3) C4645

функция, объявленная с атрибутом __declspec(noreturn) имеет оператор return

A [return](../../cpp/return-statement-in-program-termination-cpp.md) найден в функции, помеченной модификатором [noreturn](../../cpp/noreturn.md) `__declspec` . Оператор `return` был пропущен.

Следующий пример приводит к возникновению ошибки C4645.

```
// C4645.cpp
// compile with:  /W3
void __declspec(noreturn) func() {
   return;   // C4645, delete this line to resolve
}

int main() {
}
```