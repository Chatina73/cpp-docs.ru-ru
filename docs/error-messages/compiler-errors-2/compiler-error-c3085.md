---
title: Ошибка компилятора C3085
ms.date: 11/04/2016
f1_keywords:
- C3085
helpviewer_keywords:
- C3085
ms.assetid: 1ac40bf2-f63e-439e-8921-47e6dadc8354
ms.openlocfilehash: 9e174d4f8e50864dd7b33b58786cce03d50c2295
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558383"
---
# <a name="compiler-error-c3085"></a>Ошибка компилятора C3085

"конструктор": конструктор не может быть "ключевое слово"

Конструктор был объявлен неправильно. Дополнительные сведения см. в разделе [Override Specifiers](../../windows/override-specifiers-cpp-component-extensions.md) .

## <a name="example"></a>Пример

В следующем примере возникает ошибка C3085.

```
// C3085.cpp
// compile with: /c /clr
ref struct S {
   S() abstract;   // C3085
   S(S%) abstract;   // C3085
};

ref struct T {
   T() sealed {}   // C3085
   T(T%) sealed {}   // C3085
};
```