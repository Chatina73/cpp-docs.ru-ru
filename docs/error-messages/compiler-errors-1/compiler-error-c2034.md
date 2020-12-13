---
description: 'Дополнительные сведения о: Ошибка компилятора C2034'
title: Ошибка компилятора C2034
ms.date: 11/04/2016
f1_keywords:
- C2034
helpviewer_keywords:
- C2034
ms.assetid: 953d70fa-bde9-4ce6-a55d-741e7bc63ff4
ms.openlocfilehash: cbc3f8788e495a95b1eb5fb848322815b6f78d57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175421"
---
# <a name="compiler-error-c2034"></a>Ошибка компилятора C2034

"идентификатор": тип битового поля слишком мал для числа битов

Число битов в объявлении битового поля превышает размер базового типа.

Следующий пример приводит к возникновению ошибки C2034:

```cpp
// C2034.cpp
struct A {
   char test : 9;   // C2034, char has 8 bits
};
```

Возможное решение:

```cpp
// C2034b.cpp
// compile with: /c
struct A {
   char test : 8;
};
```
