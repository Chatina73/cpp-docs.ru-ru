---
description: 'Дополнительные сведения о: Ошибка компилятора C2678'
title: Ошибка компилятора C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: 9314d3d0201e38c2ce13b48f59356e04e0925a3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220868"
---
# <a name="compiler-error-c2678"></a>Ошибка компилятора C2678

бинарный operator: не определен оператор, принимающий левый операнд типа type (или приемлемое преобразование отсутствует)

Чтобы использовать этот оператор, необходимо перегрузить его для указанного типа или определить преобразование в тип, для которого определен оператор.

Ошибка C2678 может возникать, если левый операнд квалифицирован как константный, однако оператор определен для принятия неконстантного аргумента.

## <a name="examples"></a>Примеры

В следующем примере показано возникновение ошибки C2678 и приводятся сведения по ее устранению.

```cpp
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

Ошибка C2678 также может возникать, если не закрепить собственный член до вызова для него функции-члена.

В следующем примере показано возникновение ошибки C2678 и приводятся сведения по ее устранению.

```cpp
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
