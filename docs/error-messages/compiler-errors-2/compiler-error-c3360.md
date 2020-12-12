---
description: 'Дополнительные сведения о: Ошибка компилятора C3360'
title: Ошибка компилятора C3360
ms.date: 11/04/2016
f1_keywords:
- C3360
helpviewer_keywords:
- C3360
ms.assetid: 6acf983a-dbb6-422b-b045-a34bb4ba6761
ms.openlocfilehash: d4ab0a4ffd12e5ffde46971134dfe858c491733c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150895"
---
# <a name="compiler-error-c3360"></a>Ошибка компилятора C3360

"строка": невозможно создать имя

Значение, переданное в атрибут [uuid](../../windows/attributes/uuid-cpp-attributes.md) , недопустимо.

При компиляции следующего примера возникнет ошибка C3360:

```cpp
// C3360.cpp
[ uuid("1") ]
// try this line instead
// [ uuid("12341234-1234-1234-1234-123412341234") ]
struct A   // C3360
{
};

int main()
{
}
```
