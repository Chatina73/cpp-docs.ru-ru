---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 4) C4913'
title: Предупреждение компилятора (уровень 4) C4913
ms.date: 11/04/2016
f1_keywords:
- C4913
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
ms.openlocfilehash: f47c72bfbc714e8834ba27a604b8f6a58203628f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97330453"
---
# <a name="compiler-warning-level-4-c4913"></a>Предупреждение компилятора (уровень 4) C4913

**пользовательский двоичный оператор "," существует, но ни одной перегрузке не удалось преобразовать все операнды, по умолчанию использован встроенный двоичный оператор ","**

Вызов встроенного оператора "запятая" произошел в программе, которая также имела перегруженный оператор "запятая"; преобразование, на которое вы, возможно, рассчитывали, не произошло.

В следующем примере возникает ошибка C4913.

```cpp
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```
