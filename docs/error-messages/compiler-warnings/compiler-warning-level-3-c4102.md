---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 3) C4102'
title: Предупреждение компилятора (уровень 3) C4102
ms.date: 11/04/2016
f1_keywords:
- C4102
helpviewer_keywords:
- C4102
ms.assetid: 349f308a-daf3-48c6-bd53-6c38b73f8880
ms.openlocfilehash: 5cf62be66d822f67ac1715cdd140ec55e0a7af29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281435"
---
# <a name="compiler-warning-level-3-c4102"></a>Предупреждение компилятора (уровень 3) C4102

"метка": неиспользованная метка

Метка определена, но нигде не используется. Компилятор пропускает метку.

Следующий пример приводит к возникновению предупреждения C4102:

```cpp
// C4102.cpp
// compile with: /W3
int main() {
   int a;

   test:   // C4102, remove the unreferenced label to resolve

   a = 1;
}
```
