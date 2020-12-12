---
description: Дополнительные сведения см. в статье списки аргументов переменных (...) (C++/CLI)
title: Списки аргументов переменных (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: fec05a2ce397a0991a4bfd0a5aeb6a8b16d986ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176851"
---
# <a name="variable-argument-lists--ccli"></a>Списки аргументов переменных (...) (C++/CLI)

В этом примере показано, как можно использовать синтаксис `...` в C++/CLI для реализации функций с переменным числом аргументов.

> [!NOTE]
> Этот раздел относится к C++/CLI. Сведения об использовании `...` в стандартном коде ISO C++ см. в разделе [шаблоны Variadic](../cpp/ellipses-and-variadic-templates.md) и многоточия, а также аргументы по умолчанию в [постфиксных выражениях](../cpp/postfix-expressions.md).

Параметр, который использует `...`, должен быть последним параметром в списке.

## <a name="example"></a>Пример

### <a name="code"></a>Код

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>Пример кода

В следующем примере показано, как из C# вызвать функцию Visual C++, которая принимает переменное число аргументов.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Функция `f` может быть вызвана, например, из C# или Visual Basic, как если бы она была функцией, которая может принимать переменное число аргументов.

В C# аргумент, передаваемый параметру `ParamArray`, может быть вызван переменным числом аргументов. Рассмотрим приведенный ниже пример кода в C#.

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Вызов `f` в Visual C++ может передать инициализированный массив или массив переменной длины.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>См. также

[Массивы](arrays-cpp-component-extensions.md)
