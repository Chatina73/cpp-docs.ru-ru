---
title: Ошибка компилятора C2662
ms.date: 11/04/2016
f1_keywords:
- C2662
helpviewer_keywords:
- C2662
ms.assetid: e172c2a4-f29e-4034-8232-e7dc6f83689f
ms.openlocfilehash: fefd523ca3b9a3406afc307150322f9d431aa730
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360355"
---
# <a name="compiler-error-c2662"></a>Ошибка компилятора C2662

«функция»: невозможно преобразовать указатель «this» из «типа1» в «тип2»

Компилятору не удалось преобразовать `this` указатель из `type1` для `type2`.

Эта ошибка может быть вызвана путем вызова отличный от`const` функции-члена `const` объекта.  Возможные решения:

- Удалить `const` из объявления объекта.

- Добавление `const` на функцию-член.

Следующий пример приводит к возникновению ошибки C2662:

```
// C2662.cpp
class C {
public:
   void func1();
   void func2() const{}
} const c;

int main() {
   c.func1();   // C2662
   c.func2();   // OK
}
```

При компиляции с параметром **/CLR**, невозможно вызвать функцию на `const` или `volatile` управляемого типа с указанием. Нельзя объявлять постоянная функция-член управляемого класса, поэтому нельзя вызывать методы для объектов, управляемых const.

```
// C2662_b.cpp
// compile with: /c /clr
ref struct M {
   property M^ Type {
      M^ get() { return this; }
   }

   void operator=(const M %m) {
      M ^ prop = m.Type;   // C2662
   }
};

ref struct N {
   property N^ Type {
      N^ get() { return this; }
   }

   void operator=(N % n) {
      N ^ prop = n.Type;   // OK
   }
};
```

Следующий пример приводит к возникновению ошибки C2662:

```
// C2662_c.cpp
// compile with: /c
// C2662 expected
typedef int ISXVD;
typedef unsigned char BYTE;

class LXBASE {
protected:
    BYTE *m_rgb;
};

class LXISXVD:LXBASE {
public:
   // Delete the following line to resolve.
   ISXVD *PMin() { return (ISXVD *)m_rgb; }

   ISXVD *PMin2() const { return (ISXVD *)m_rgb; };   // OK
};

void F(const LXISXVD *plxisxvd, int iDim) {
   ISXVD isxvd;
   // Delete the following line to resolve.
   isxvd = plxisxvd->PMin()[iDim];

   isxvd = plxisxvd->PMin2()[iDim];
}
```