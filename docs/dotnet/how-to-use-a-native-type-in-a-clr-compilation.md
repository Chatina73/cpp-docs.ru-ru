---
title: 'Практическое: Использование собственного типа в компиляции - clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 0079be21b474858684e1abaaeb363820764a701d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459960"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Практическое руководство. Использование собственного типа в компиляции /clr

Можно определить собственный тип в **/CLR** компиляции и любое использование этого машинного типа в сборке является допустимым. Тем не менее собственные типы, не будет использоваться в ссылочных метаданных.

Каждая сборка может содержать определение каждого собственный тип, который будет использоваться.

Дополнительные сведения см. в разделе [/clr (компиляция CLR)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Пример

В этом примере создается компонент, который определяет и использует собственный тип.

```
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

## <a name="example"></a>Пример

В этом примере определяется клиент, который использует компонент. Обратите внимание на то, что это ошибка для доступа к в собственный тип, если оно определено в единице компиляции.

```
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>См. также

[Использование взаимодействия языка C++ (неявный PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)