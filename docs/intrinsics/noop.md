---
title: __noop
ms.date: 09/02/2019
f1_keywords:
- __noop_cpp
- __noop
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
ms.openlocfilehash: 24ba85b1fbbba4491c03d5a81afae345228db3bd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217181"
---
# <a name="__noop"></a>__noop

**Блок, относящийся только к системам Microsoft**

`__noop` Встроенная функция указывает, что функцию следует игнорировать. Список аргументов анализируется, но для аргументов не создается код. Он предназначен для использования в глобальных функциях отладки, принимающих переменное число аргументов.

Компилятор преобразует `__noop` встроенное значение в 0 во время компиляции.

## <a name="example"></a>Пример

В следующем коде показано, как можно использовать `__noop`.

```cpp
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

## <a name="see-also"></a>См. также

[Встроенные функции компилятора](../intrinsics/compiler-intrinsics.md)\
[Ключевые слова](../cpp/keywords-cpp.md)
