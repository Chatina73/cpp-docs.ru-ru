---
description: 'Дополнительные сведения о: Ошибка компилятора C2042'
title: Ошибка компилятора C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 3dd4ae7471997e518c854d570b4a2e3aa4ec3856
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175213"
---
# <a name="compiler-error-c2042"></a>Ошибка компилятора C2042

зарезервированные слова signed и unsigned являются взаимоисключающими

Ключевые слова **`signed`** и **`unsigned`** используются в одном объявлении.

Следующий пример приводит к возникновению ошибки C2042:

```cpp
// C2042.cpp
unsigned signed int i;   // C2042
```

Возможное решение:

```cpp
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```
