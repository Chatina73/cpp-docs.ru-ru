---
description: 'Дополнительные сведения о: Ошибка компилятора C2765'
title: Ошибка компилятора C2765
ms.date: 11/04/2016
f1_keywords:
- C2765
helpviewer_keywords:
- C2765
ms.assetid: 47ad86f3-a7e0-47ad-85ff-0f5534458cb9
ms.openlocfilehash: 496f28645dddc0ac426716cc80ee0d6760042ad7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97239549"
---
# <a name="compiler-error-c2765"></a>Ошибка компилятора C2765

"функция": явная специализация шаблона функции не может иметь аргументы по умолчанию

Аргументы по умолчанию не разрешены для явной специализации шаблона функции. Дополнительные сведения см. в разделе [явная специализация шаблонов функций](../../cpp/explicit-specialization-of-function-templates.md).

Следующий пример приводит к возникновению ошибки C2765:

```cpp
// C2765.cpp
template<class T> void f(T t) {};

template<> void f<char>(char c = 'a') {}   // C2765
// try the following line instead
// template<> void f<char>(char c) {}
```
