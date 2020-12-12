---
description: 'Дополнительные сведения о: Ошибка компилятора C2027'
title: Ошибка компилятора C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 131362f2caa8da80865a9601d87cfe3a5e7ab3b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175551"
---
# <a name="compiler-error-c2027"></a>Ошибка компилятора C2027

Использование неопределенного типа "тип"

Тип нельзя использовать, пока не будет определен. Чтобы устранить эту ошибку, убедитесь, что тип определен полностью, прежде чем ссылаться на него.

## <a name="examples"></a>Примеры

Следующий пример приводит к возникновению ошибки C2027.

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

Можно объявить указатель на объявленный, но неопределенный тип. Но C++ не допускает ссылку на неопределенный тип.

Следующий пример приводит к возникновению ошибки C2027.

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
