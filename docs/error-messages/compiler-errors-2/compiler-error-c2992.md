---
title: Ошибка компилятора C2992
ms.date: 11/04/2016
f1_keywords:
- C2992
helpviewer_keywords:
- C2992
ms.assetid: 01b16447-43fe-4e91-9a5a-af884a166a31
ms.openlocfilehash: c30a1d2e1c2bae92b426fdd8fa4be628c009fa02
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581926"
---
# <a name="compiler-error-c2992"></a>Ошибка компилятора C2992

"класс": список параметров типов недопустим или отсутствует

Классу предшествует ключевое слово `template` или **generic** с отсутствующими или недопустимыми параметрами.

## <a name="example"></a>Пример

При компиляции следующего примера возникнет ошибка C2992:

```
// C2992.cpp
// compile with: /c
template <class T>
struct TC1 {
   template <class U>
   struct TC2;
};

template <class T>   struct TC1<T>::TC2 {};   // C2992

// OK
template <class T>
template <class U>
struct TC1<T>::TC2 {};
// C2992 can also occur when using generics:
// C2992c.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T> ref struct GC1<T>::GC2 {};   // C2992

// OK
generic <class T>
generic <class U>
ref struct GC1<T>::GC2 {};
```