---
description: 'Дополнительные сведения о: Ошибка компилятора C3749'
title: Ошибка компилятора C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 247f98214a3f2ec8a496f1da11633f53916328f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340181"
---
# <a name="compiler-error-c3749"></a>Ошибка компилятора C3749

"атрибут": настраиваемый атрибут не может использоваться внутри функции

В функции нельзя использовать настраиваемый атрибут. Дополнительные сведения о настраиваемых атрибутах см. в разделе [атрибут](../../windows/attributes/attribute.md)раздела.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3749:

```cpp
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
