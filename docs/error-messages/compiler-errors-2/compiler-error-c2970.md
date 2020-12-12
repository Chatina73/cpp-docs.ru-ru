---
description: 'Дополнительные сведения о: Ошибка компилятора C2970'
title: Ошибка компилятора C2970
ms.date: 11/04/2016
f1_keywords:
- C2970
helpviewer_keywords:
- C2970
ms.assetid: 21d90348-20d3-438c-b278-efdbfb93a7d2
ms.openlocfilehash: 5f48cb3df9add0a285cca5af2131db174a3d0af8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281942"
---
# <a name="compiler-error-c2970"></a>Ошибка компилятора C2970

"класс": параметр шаблона "param": "arg": выражение, включающее объекты с внутренней компоновкой, не может использоваться в качестве аргумента, не являющегося типом

Нельзя использовать имя или адрес статической переменной в качестве аргумента шаблона. Класс шаблона принимает константное значение, которое может быть вычислено во время компиляции.

Следующий пример приводит к возникновению ошибки C2970:

```cpp
// C2970.cpp
// compile with: /c
static int si;
// could declare nonstatic to resolve all errors
// int si;

template <int i>
class X {};

template <int *pi>
class Y {};

X<si> anX;   // C2970 cannot use static variable in templates

// this would also work
const int i = 10;
X<i> anX2;
```
