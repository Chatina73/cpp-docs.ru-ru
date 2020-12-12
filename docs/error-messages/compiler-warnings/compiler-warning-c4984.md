---
description: 'Дополнительные сведения о: предупреждение компилятора C4984'
title: Предупреждение компилятора C4984
ms.date: 08/19/2019
f1_keywords:
- C4984
helpviewer_keywords:
- C4984
ms.openlocfilehash: 5a6708a1063baf8fa4b5feece65eabd93df7bbeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326004"
---
# <a name="compiler-warning-c4984"></a>Предупреждение компилятора C4984

> "If constexpr" — расширение языка C++ 17

## <a name="remarks"></a>Комментарии

Компилятор обнаружил `if constexpr` выражение в коде, скомпилированном с использованием стандарта c++ 14 Standard по умолчанию. Это выражение указывается начиная с стандарта C++ 17. Если требуется совместимость с C++ 11 или C++ 14, это выражение не является переносимым.

C4984 выдается как ошибка по умолчанию, но это суппрессибле. Чтобы включить это выражение путем компиляции кода как C++ 17, используйте [/std: c++ 17 или/std: C + + Latest](../../build/reference/std-specify-language-standard-version.md). Чтобы использовать `if constexpr` выражение в коде, скомпилированном для c++ 14 в качестве расширения Майкрософт, можно подавить, отключить или изменить уровень предупреждений сообщения об ошибке. Вы можете использовать [/wd4984](../../build/reference/compiler-option-warning-level.md) , чтобы отключить C4984, или __/w__*n*__4984__ , чтобы включить его как предупреждение уровня *N* вместо ошибки. Или используйте [#pragma warning (подавлять: 4984)](../../preprocessor/warning.md) перед строкой, которая вызывает предупреждение в исходном файле.

Это предупреждение доступно в Visual Studio 2017 версии 15,3. Сведения о том, как отключить предупреждения, появившиеся в определенной версии компилятора или более поздней версии, см. в разделе [предупреждения компилятора по версиям компилятора](compiler-warnings-by-compiler-version.md).

## <a name="example"></a>Пример

Этот пример создает C4984 и демонстрирует способы его исправления:

```cpp
// C4984.cpp
// compile with: cl /EHsc C4984.cpp
#include <iostream>

int main()
{
    constexpr bool compile_time = true;
    // Uncomment the following line or use /std:c++17 to fix
    // #pragma warning(suppress:4984)
    if constexpr (compile_time)
    {
        std::cout << "compile_time is true";
    }
    else
    {
        std::cout << "compile_time is false";
    }
}
```
