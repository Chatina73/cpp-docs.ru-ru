---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 4) C4245'
title: Предупреждение компилятора (уровень 4) C4245
ms.date: 11/04/2016
f1_keywords:
- C4245
helpviewer_keywords:
- C4245
ms.assetid: 85083d53-9cc2-4d12-b58c-6dad28f15cbe
ms.openlocfilehash: 8e75c82ca775881d3ac2771a19f0f68b789e1940
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341702"
---
# <a name="compiler-warning-level-4-c4245"></a>Предупреждение компилятора (уровень 4) C4245

> "*Преобразование*": преобразование из "*тип1*" в "*тип2*", несоответствие со знаком и без знака

Предпринята попытка преобразования **`signed const`** типа с отрицательным значением в **`unsigned`** тип.

Следующий пример приводит к возникновению ошибки C4245:

```cpp
// C4245.cpp
// compile with: /W4 /c
const int i = -1;
unsigned int j = i; // C4245

const int k = 1;
unsigned int l = k; // okay

int m = -1;
unsigned int n = m; // okay

void Test(size_t i) {}

int main() {
   Test( -19 );   // C4245
}
```
