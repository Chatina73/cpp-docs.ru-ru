---
title: Ошибка компилятора C3342
ms.date: 11/04/2016
f1_keywords:
- C3342
helpviewer_keywords:
- C3342
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
ms.openlocfilehash: 511271db9651e4274f7e0838917c5aac639eae2c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753462"
---
# <a name="compiler-error-c3342"></a>Ошибка компилятора C3342

"атрибут": неоднозначный атрибут

Компилятор обнаружил несколько определений атрибута.

Атрибут определен несколько раз.

Для получения дополнительной информации см. [User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3342:

```cpp
// C3342.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Reflection;

[AttributeUsage(AttributeTargets::All)]
public ref class XAttribute : public  Attribute {};

[AttributeUsage(AttributeTargets::All)]
public ref class X : public Attribute {};

[X]   // C3342 could refer to X or XAttribute
// try the following line instead
// [XAttribute]
public ref class Class4 {};
```
