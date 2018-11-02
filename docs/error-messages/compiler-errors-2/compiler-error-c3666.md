---
title: Ошибка компилятора C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: aba1d3dfcf620db0f1fbaf14d0fb01745ca82659
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465550"
---
# <a name="compiler-error-c3666"></a>Ошибка компилятора C3666

«конструктор»: спецификатор переопределения «ключевое слово», не допускается в конструкторе

Спецификатор переопределения был использован с помощью конструктора, и что не допускается. Дополнительные сведения см. в разделе [спецификаторы переопределения](../../windows/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3666.

```
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```