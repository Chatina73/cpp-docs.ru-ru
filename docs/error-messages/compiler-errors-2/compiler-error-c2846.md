---
title: Ошибка компилятора C2846
ms.date: 11/04/2016
f1_keywords:
- C2846
helpviewer_keywords:
- C2846
ms.assetid: bc090ec2-5410-4112-9ec6-261325374375
ms.openlocfilehash: 4e1e88e538008cff03349a35e193b7bcd471b950
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62256754"
---
# <a name="compiler-error-c2846"></a>Ошибка компилятора C2846

«конструктор»: интерфейс не может иметь конструктор

Visual C++ [интерфейс](../../cpp/interface.md) не может иметь конструктор.

Следующий пример приводит к возникновению ошибки C2846:

```
// C2846.cpp
// compile with: /c
__interface C {
   C();   // C2846 constructor not allowed in an interface
};
```