---
description: 'Дополнительные сведения о: Ошибка компилятора C2381'
title: Ошибка компилятора C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: ccaed8e5fc637ffb7e5cd2a33a00ddb5cf7c102b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282184"
---
# <a name="compiler-error-c2381"></a>Ошибка компилятора C2381

"функция": переопределение; __declspec (noreturn) отличается

Функция объявлена, а затем определена, но определение использовало модификатор [noreturn](../../cpp/noreturn.md) **`__declspec`** . Использование `noreturn` создает переопределение функции; объявление и определение необходимо согласовать с использованием `noreturn` .

Следующий пример приводит к возникновению ошибки C2381:

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
