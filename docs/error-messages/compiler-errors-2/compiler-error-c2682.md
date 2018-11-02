---
title: Ошибка компилятора C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 8a9ec2f59f362df284e9bd5cd8df6ae986d59d77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439420"
---
# <a name="compiler-error-c2682"></a>Ошибка компилятора C2682

нельзя использовать "оператор приведения" для преобразования из «тип1» в «тип2»

Оператор приведения предпринял попытку преобразования между двумя несовместимыми типами. Например, нельзя использовать [dynamic_cast](../../cpp/dynamic-cast-operator.md) оператор преобразования указатель на ссылку. `dynamic_cast` Оператор не может использоваться для снятия квалификаторов. Все квалификаторы типов должны совпадать.

Можно использовать `const_cast` оператор удаления атрибутов, таких как `const`, `volatile`, или `__unaligned`.

Следующий пример приводит к возникновению ошибки C2682:

```
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

Следующий пример приводит к возникновению ошибки C2682:

```
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```