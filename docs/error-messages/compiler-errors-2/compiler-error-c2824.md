---
description: 'Дополнительные сведения о: Ошибка компилятора C2824'
title: Ошибка компилятора C2824
ms.date: 11/04/2016
f1_keywords:
- C2824
helpviewer_keywords:
- C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
ms.openlocfilehash: cb6f7f86647a465cb0b525bc0da8f2d452661af8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194687"
---
# <a name="compiler-error-c2824"></a>Ошибка компилятора C2824

возвращаемый тип для оператора New должен быть "void *"

При использовании указателей, отличных от, перегрузки оператора `new` должны возвращать `void *` .

Следующий пример приводит к возникновению ошибки C2824:

```cpp
// C2824.cpp
// compile with: /c
class   A {
   A* operator new(size_t i, char *m);   // C2824
   // try the following line instead
   // void* operator new(size_t i, char *m);
};
```
