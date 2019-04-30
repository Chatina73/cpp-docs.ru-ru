---
title: Ошибка компилятора C2082
ms.date: 11/04/2016
f1_keywords:
- C2082
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
ms.openlocfilehash: 8bfb54dc91ef9132e3930e2c0799070f80f5cd0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338627"
---
# <a name="compiler-error-c2082"></a>Ошибка компилятора C2082

переопределение формального параметра "идентификатор"

В теле функции переопределен формальный параметр функции. Чтобы устранить эту ошибку, удалите повторное определение.

Следующий пример приводит к возникновению ошибки C2082:

```
// C2082.cpp
void func(int i) {
   int i;   // C2082
   int ii;   // OK
}
```