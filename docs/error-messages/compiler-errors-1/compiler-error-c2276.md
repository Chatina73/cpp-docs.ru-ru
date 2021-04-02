---
description: 'Дополнительные сведения о: Ошибка компилятора C2276'
title: Ошибка компилятора C2276
ms.date: 03/25/2021
f1_keywords:
- C2276
helpviewer_keywords:
- C2276
ms.openlocfilehash: 85a83637e12f0900f3a6840841c7a9a8ed50deee
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099473"
---
# <a name="compiler-error-c2276"></a>Ошибка компилятора C2276

> "*оператор*": Недопустимая операция с выражением привязанной функции элемента

Компилятор обнаружил проблему с синтаксисом, используемым для создания указателя на член.

## <a name="remarks"></a>Комментарии

Ошибка `C2276` часто возникает при попытке создать указатель на член с помощью переменной экземпляра для определения члена, а не типа класса. Эта ошибка также может возникать, если вы пытаетесь вызвать функцию-член с помощью неправильного синтаксиса.

## <a name="example"></a>Пример

В этом примере показано несколько способов C2276 и способы их устранения:

```cpp
// C2276.cpp
class A {
public:
   int func(){return 0;}
} a;

int (*pf)() = &a.func;   // C2276
// pf isn't qualified by the class type, and it 
// tries to take a member address from an instance of A.
// Try the following line instead:
// int (A::*pf)() = &A::func;

class B : public A {
public:
   void mf() {
      auto x = &this -> func;   // C2276
      // try the following line instead
      // auto x = &B::func;
   }
};

int main() {
   A a3;
   auto pmf1 = &a3.func;   // C2276
   // try the following line instead
   // auto pmf1 = &A::func;
}
```
