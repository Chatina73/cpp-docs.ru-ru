---
description: 'Дополнительные сведения: управляемые, неуправляемые директивы pragma'
title: Директивы pragma managed, unmanaged
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 10f632b009c9922f67f4321acc862142d895e7ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333389"
---
# <a name="managed-unmanaged-pragmas"></a>Директивы pragma managed, unmanaged

Включите управление на уровне функций для компиляции функций как управляемых или неуправляемых.

## <a name="syntax"></a>Синтаксис

> **управляемые #pragma**\
> **неуправляемый #pragma**\
> **управляемый #pragma (** [ **Push,** ] { **On**  |  **Off** } **)**\
> **управляемый #pragma (POP)**

## <a name="remarks"></a>Комментарии

Параметр компилятора [/CLR](../build/reference/clr-common-language-runtime-compilation.md) обеспечивает управление на уровне модуля для компиляции функций как управляемых, так и неуправляемых.

Для собственной платформы будет скомпилирована неуправляемая функция. Выполнение этой части программы будет передано в собственную платформу средой CLR.

При использовании параметра `/clr` по умолчанию функции компилируются как управляемые.

При применении этих директив pragma выполните следующие действия.

- Добавьте директиву pragma перед функцией, но не внутри тела функции.

- Добавьте директиву pragma после операторов `#include`. Не используйте эти директивы pragma перед `#include` инструкциями.

Компилятор игнорирует **управляемые** и **неуправляемые** директивы pragma, если `/clr` в компиляции не используется.

При создании экземпляра функции-шаблона состояние директивы pragma при определении шаблона определяет, является ли он управляемым или неуправляемым.

Дополнительные сведения см. в разделе [Инициализация смешанных сборок](../dotnet/initialization-of-mixed-assemblies.md).

## <a name="example"></a>Пример

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>См. также раздел

[Директивы pragma и ключевое слово __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
