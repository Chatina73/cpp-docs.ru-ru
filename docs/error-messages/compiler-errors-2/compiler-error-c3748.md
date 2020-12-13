---
description: 'Дополнительные сведения о: Ошибка компилятора C3748'
title: Ошибка компилятора C3748
ms.date: 11/04/2016
f1_keywords:
- C3748
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
ms.openlocfilehash: f4cb51cfbb331867c18c0f892bd9527309fb4d63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340194"
---
# <a name="compiler-error-c3748"></a>Ошибка компилятора C3748

"интерфейс": управляемые интерфейсы не могут порождать события

Ключевое слово [__event](../../cpp/event.md) не может появляться внутри интерфейса.

Следующий пример приводит к возникновению ошибки C3748:

```cpp
// C3748.cpp
__interface I {
// try the following line instead
// struct I {
   __event void f();   // C3748
};

int main() {
}
```
