---
title: Известные проблемы Аддресссанитизер
description: Техническое описание известных проблем с Аддресссанитизер для Microsoft C/C++.
ms.date: 03/02/2021
helpviewer_keywords:
- AddressSanitizer known issues
ms.openlocfilehash: 7db8b06a96eababbd6a48e337cff7155f248fb34
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471186"
---
# <a name="addresssanitizer-known-issues"></a>Известные проблемы Аддресссанитизер

> [!NOTE]
> Отправьте нам [отзыв](https://aka.ms/vsfeedback/browsecpp) о том, что вы хотели бы увидеть в будущих выпусках, и [сообщите об ошибках](https://aka.ms/feedback/report?space=62) при возникновении проблем.

## <a name="incompatible-options-and-functionality"></a><a name="incompatible-options"></a> Несовместимые параметры и функции

Эти параметры и функции несовместимы с [`/fsanitize=address`](../build/reference/fsanitize.md) , и их следует отключить или исключить.

- [`/RTC`](../build/reference/rtc-run-time-error-checks.md)Параметры несовместимы с аддресссанитизер и должны быть отключены.
- [Инкрементная компоновка](../build/reference/incremental-link-incrementally.md) не поддерживается и должна быть отключена.
- [Edit-and-Continue](/visualstudio/debugger/edit-and-continue-visual-cpp) не поддерживается и должен быть отключен.
- [Соподпрограммы](https://devblogs.microsoft.com/cppblog/category/coroutine/) несовместимы с аддресссанитизер, а возобновляемые функции исключены из инструментирования.
- [OpenMP](../build/reference/openmp-enable-openmp-2-0-support.md) не поддерживается, и его следует отключить.
- [Управляемый C++](../build/reference/clr-common-language-runtime-compilation.md) не поддерживается и должен быть отключен.
- [C++ amp](../parallel/amp/cpp-amp-overview.md) не поддерживается, и его следует отключить.
- Файлы с [особым списком вариантов](https://clang.llvm.org/docs/SanitizerSpecialCaseList.html) не поддерживаются.

## <a name="standard-library-support"></a>Поддержка стандартной библиотеки

Стандартная библиотека КОМПИЛЯТОРОМ MSVC (STL) не поддержкой для понимания Аддресссанитизер. Исключения Аддресссанитизер, возникающие в коде STL, обнаруживают истинные ошибки. Однако они не так точны, как это может быть.

В этом примере демонстрируется нехватка точности:

```cpp
// Compile with: cl /fsanitize=address /Zi
#include <vector>

int main() {   
    // Create a vector of size 10, but with a capacity of 20.    
    std::vector<int> v(10);
    v.reserve(20);

    // Currently, MSVC ASan does NOT raise an exception here.
    // While this is an out-of-bounds write to 'v', MSVC ASan
    // ensures the write is within the heap allocation size (20).
    v[10] = 1;

    // MSVC ASan DOES raise an exception here, as this write
    // is out of bounds from the heap allocation.
    v[20] = 1;
}
```

## <a name="windows-versions"></a>Версии Windows

Так как существуют зависимости с конкретными версиями Windows, поддержка сосредоточена на Windows 10. КОМПИЛЯТОРОМ MSVC Аддресссанитизер был протестирован на 10.0.14393 (RS1) и 10.0.21323 (Предварительная сборка предварительной версии). [Сообщите об ошибке](https://aka.ms/feedback/report?space=62) , если возникли проблемы.

## <a name="memory-usage"></a>Использование памяти

Среда выполнения Аддресссанитизер не освобождает память в операционной системе во время выполнения. С точки зрения ОС она может выглядеть так, как есть утечка памяти. Это решение является намеренным, поэтому не выделяйте всю требуемую память на передний план.

## <a name="addresssanitizer-runtime-dll-locations"></a>Расположения библиотек DLL среды выполнения Аддресссанитизер

*`clang_rt.asan*.dll`* Файлы среды выполнения устанавливаются рядом с компиляторами в *`%VSINSTALLDIR%\VC\Tools\MSVC\<version>\bin\<host-arch>\<target-arch>\`* . Эти расположения находятся в пути в сеансах отладки, а также в командных запросах разработчика Visual Studio. Эти файлы никогда не помещаются в *`C:\Windows\System32`* или *`C:\Windows\SysWOW64`* .

## <a name="see-also"></a>См. также раздел

[Обзор Аддресссанитизер](./asan.md)\
[Справочник по сборке и языку Аддресссанитизер](./asan-building.md)\
[Справочник по среде выполнения Аддресссанитизер](./asan-runtime.md)\
[Аддресссанитизер теневых байт](./asan-shadow-bytes.md)\
[Аддресссанитизер облачное или распределенное тестирование](./asan-offline-crash-dumps.md)\
[Интеграция отладчика Аддресссанитизер](./asan-debugger-integration.md)\
[Примеры ошибок Аддресссанитизер](./asan-error-examples.md)
