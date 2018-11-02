---
title: Ошибка компилятора C3838
ms.date: 11/04/2016
f1_keywords:
- C3838
helpviewer_keywords:
- C3838
ms.assetid: d6f470c2-131a-4a8c-843a-254acd43da83
ms.openlocfilehash: c8664c9df837d44ab6e356d54ff9e35c3776778a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635231"
---
# <a name="compiler-error-c3838"></a>Ошибка компилятора C3838

нельзя явно наследоваться от «тип»

Указанный `type` не может использоваться в качестве базового класса в любом классе.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3838:

```
// C3838a.cpp
// compile with: /clr /c
public ref class B : public System::Enum {};   // C3838
```
