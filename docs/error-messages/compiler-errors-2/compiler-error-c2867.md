---
description: 'Дополнительные сведения о: Ошибка компилятора C2867'
title: Ошибка компилятора C2867
ms.date: 11/04/2016
f1_keywords:
- C2867
helpviewer_keywords:
- C2867
ms.assetid: 63be26b2-d9ab-4f3d-a8b7-981ce3e4d6b9
ms.openlocfilehash: 81ccb96e60a412a84c76ba542fab980b9210a054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333802"
---
# <a name="compiler-error-c2867"></a>Ошибка компилятора C2867

"идентификатор": не является пространством имен

**`using`** Директива применяется не к пространству имен.

Следующий пример приводит к возникновению ошибки C2867:

```cpp
// C2867.cpp
// compile with: /c
namespace N {
   class X {};
}
using namespace N::X;   // C2867
```
