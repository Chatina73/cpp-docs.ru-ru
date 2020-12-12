---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4033'
title: Предупреждение компилятора (уровень 1) C4033
ms.date: 11/04/2016
f1_keywords:
- C4033
helpviewer_keywords:
- C4033
ms.assetid: 189a9ec3-ff6d-49dd-b9b2-530b28bbb7c9
ms.openlocfilehash: 1d2455d62b3c375b0f1a863e6cfc3064f44e840a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325963"
---
# <a name="compiler-warning-level-1-c4033"></a>Предупреждение компилятора (уровень 1) C4033

Функция "функция" должна возвращать значение

Функция не возвращает значение. Возвращается неопределенное значение.

Функции, использующие **`return`** без возвращаемого значения, должны быть объявлены как тип **`void`** .

Эта ошибка для кода на языке C.

Следующий пример приводит к возникновению ошибки C4033:

```c
// C4033.c
// compile with: /W1 /LD
int test_1(int x)   // C4033 expected
{
   if (x)
   {
      return;   // C4033
   }
}
```
