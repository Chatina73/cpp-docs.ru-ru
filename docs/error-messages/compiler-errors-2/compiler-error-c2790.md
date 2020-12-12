---
description: 'Дополнительные сведения о: Ошибка компилятора C2790'
title: Ошибка компилятора C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: 0913b87f40e7f4ad2ecccb333e67bb0d76b4afde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297809"
---
# <a name="compiler-error-c2790"></a>Ошибка компилятора C2790

"Super": это ключевое слово можно использовать только в теле функции члена класса

Это сообщение об ошибке появляется, если пользователь когда-либо пытается использовать ключевое слово [Super](../../cpp/super.md) вне контекста функции-члена.

Следующий пример приводит к возникновению ошибки C2790:

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
