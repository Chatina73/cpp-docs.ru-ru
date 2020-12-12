---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4533'
title: Предупреждение компилятора (уровень 1) C4533
ms.date: 11/04/2016
f1_keywords:
- C4533
helpviewer_keywords:
- C4533
ms.assetid: 359fecda-d540-46e5-b214-dbabe9ef50d2
ms.openlocfilehash: 76358a19beb5fc6d177c21d39fe9a375eb60af02
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212289"
---
# <a name="compiler-warning-level-1-c4533"></a>Предупреждение компилятора (уровень 1) C4533

Инициализация "Variable" пропускается "инструкцией"

Инструкция в программе изменила поток управления, таким, что инструкция, инициализирующая переменную, не была выполнена. Следующий пример приводит к возникновению ошибки C4533:

```cpp
// C4533.cpp
// compile with: /W1
#include <stdio.h>

struct A
{
   int m_data;
};

int main()
{
   if (1)
   {
      goto Label;
   }

   A a = { 100 };

   Label:   // C4533
      printf("\n%d", a.m_data);   // prints an uninitialized value
}
```
