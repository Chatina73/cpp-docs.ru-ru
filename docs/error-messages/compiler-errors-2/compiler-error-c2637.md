---
title: Ошибка компилятора C2637
ms.date: 11/04/2016
f1_keywords:
- C2637
helpviewer_keywords:
- C2637
ms.assetid: 58d94447-eb96-4d8f-a690-dd78d322462e
ms.openlocfilehash: a17bd95cf1727d058e0cbd9e3dfb93c500da9fb5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758259"
---
# <a name="compiler-error-c2637"></a>Ошибка компилятора C2637

"идентификатор": невозможно изменить указатели на элементы данных

Указатель на элемент данных не может иметь соглашение о вызовах. Чтобы устранить эту проблему, удалите соглашение о вызовах или объявите указатель на функцию-член.

Следующий пример приводит к возникновению ошибки C2637:

```cpp
// C2637.cpp
// compile with: /c
struct S {};
int __stdcall S::*pms1;   // C2637

// OK
int S::*pms2;
int (__stdcall S::*pms3)(...);
```
