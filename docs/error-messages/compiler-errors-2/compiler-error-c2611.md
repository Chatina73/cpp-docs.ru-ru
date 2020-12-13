---
description: 'Дополнительные сведения о: Ошибка компилятора C2611'
title: Ошибка компилятора C2611
ms.date: 11/04/2016
f1_keywords:
- C2611
helpviewer_keywords:
- C2611
ms.assetid: 3f2d5253-f24f-4724-83d0-6b2aa6a4e551
ms.openlocfilehash: 1bcc7f1992e2a58b77319b86b534f8474cd05e90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338692"
---
# <a name="compiler-error-c2611"></a>Ошибка компилятора C2611

"токен": Недопустимый следующий "~" (ожидаемый идентификатор)

Токен не является идентификатором.

Следующий пример приводит к возникновению ошибки C2611:

```cpp
// C2611.cpp
// compile with: /c
class C {
   C::~operator int();   // C2611
   ~C();   // OK
};
```
