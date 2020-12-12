---
description: 'Дополнительные сведения о: Ошибка компилятора C2875'
title: Ошибка компилятора C2875
ms.date: 11/04/2016
f1_keywords:
- C2875
helpviewer_keywords:
- C2875
ms.assetid: d589fc0c-08b2-4a79-bc0e-dca5eb80bdd5
ms.openlocfilehash: 8d6d4d7f985079070cde4dfe46e3619cc035126f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320516"
---
# <a name="compiler-error-c2875"></a>Ошибка компилятора C2875

Использование объявления using приводит к множественному объявлению "класс:: идентификатор"

Объявление приводит к тому, что один и тот же элемент определяется дважды.

Следующий пример приводит к возникновению ошибки C2875:

```cpp
// C2875.cpp
struct A {
   void f(int*);
};

struct B {
   void f(double*);
};

struct AB : A, B {
   using A::f;
   using A::f;   // C2875
   using B::f;
};
```
