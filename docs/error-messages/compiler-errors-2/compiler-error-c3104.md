---
title: Ошибка компилятора C3104
ms.date: 11/04/2016
f1_keywords:
- C3104
helpviewer_keywords:
- C3104
ms.assetid: b5648d47-e5d3-4b45-a3c0-f46e04eae731
ms.openlocfilehash: 71a5943f65f4bd490ecb02824fef7a96741709f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540327"
---
# <a name="compiler-error-c3104"></a>Ошибка компилятора C3104

Недопустимый аргумент атрибута

Указан недопустимый аргумент для атрибута.

См. в разделе [типы параметров атрибутов](../../windows/attribute-parameter-types-cpp-component-extensions.md) Дополнительные сведения.

Эта ошибка может возникать в результате действий по обеспечению совместимости компилятора с Visual C++ 2005: при передаче управляемых массивов в настраиваемых атрибутов, тип массива больше не выводится из списка агрегатной инициализации. Компилятор теперь требует указать тип массива, а также список инициализаторов.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3104.

```
// C3104a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( {1,2,3}, param = {2.71, 3.14})]   // C3104
// try the following line instead
// [ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3104.

```
// C3104b.cpp
// compile with: /clr /c
// C3104 expected
using namespace System;

int func() {
   return 0;
}

[attribute(All)]
ref class A {
public:
   A(int) {}
};

// Delete the following 2 lines to resolve.
[A(func())]
ref class B {};

// OK
[A(0)]
ref class B {};
```
