---
description: Дополнительные сведения о:/OpenMP (Включение поддержки OpenMP)
title: /OpenMP (Включение поддержки OpenMP)
ms.date: 04/01/2021
f1_keywords:
- /openmp
- /openmp:experimental
- /openmp:llvm
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- /openmp:experimental compiler option [C++]
- /openmp:llvm compiler option [C++]
- -openmp compiler option [C++]
ms.openlocfilehash: d8363b253136c7e962ef62ecb29f0e2f13cc453e
ms.sourcegitcommit: be9a1af0b9d3f1d6c2987d8744392170b8dccab0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/02/2021
ms.locfileid: "106232326"
---
# <a name="openmp-enable-openmp-support"></a>`/openmp` (Включить поддержку OpenMP)

Заставляет компилятор обрабатывать [`#pragma omp`](../../preprocessor/omp.md) директивы для поддержки OpenMP.

## <a name="syntax"></a>Синтаксис

::: moniker range=">= msvc-160"

> **`/openmp`**\
> **`/openmp:experimental`**\
> **`/openmp:llvm`**

::: moniker-end

::: moniker range="<= msvc-150"

> **`/openmp`**

::: moniker-end

## <a name="remarks"></a>Remarks

`#pragma omp` используется для указания [директив](../../parallel/openmp/reference/openmp-directives.md) и [предложений](../../parallel/openmp/reference/openmp-clauses.md). Если параметр **`/openmp`** не указан при компиляции, компилятор игнорирует предложения и директивы OpenMP. Вызовы [функций OpenMP](../../parallel/openmp/reference/openmp-functions.md) обрабатываются компилятором, даже если **`/openmp`** не указаны.

::: moniker range=">= msvc-160"

Компилятор C++ в настоящее время поддерживает стандарт OpenMP 2,0. Однако теперь Visual Studio 2019 также предлагает функции SIMD. Чтобы использовать SIMD, Скомпилируйте с помощью **`/openmp:experimental`** параметра. Этот параметр включает как обычные функции OpenMP, так и функции OpenMP SIMD, недоступные при использовании **`/openmp`** параметра.

Начиная с Visual Studio 2019 версии 16,9 можно использовать экспериментальный **`/openmp:llvm`** вариант вместо **`/openmp`** для целевой среды выполнения OpenMP LLVM. В настоящее время поддержка в рабочем коде недоступна, так как требуемые библиотеки DLL либомп не являются распространяемыми. Параметр поддерживает те же директивы OpenMP 2,0, что и **`/openmp`** . И поддерживают все директивы SIMD, поддерживаемые **`/openmp:experimental`** параметром. Он также поддерживает параллельные индексы целых чисел без знака в соответствии со стандартом OpenMP 3,0. Дополнительные сведения см. [в статье Улучшенная поддержка OpenMP для C++ в Visual Studio](https://devblogs.microsoft.com/cppblog/improved-openmp-support-for-cpp-in-visual-studio/).

В настоящее время **`/openmp:llvm`** параметр работает только в архитектуре x64. Параметр несовместим с **`/clr`** или **`/ZW`** .

::: moniker-end

Приложения, скомпилированные с помощью **`/openmp`** и, **`/clr`** могут выполняться только в одном процессе домена приложения. Несколько доменов приложений не поддерживаются. Это значит, что при запуске конструктора модуля ( `.cctor` ) он обнаруживает, компилируется ли процесс с помощью **`/openmp`** , и если приложение загружается в среду выполнения, не используемую по умолчанию. Дополнительные сведения см. в статьях [`appdomain`](../../cpp/appdomain.md) , [ `/clr` (компиляция среды CLR)](clr-common-language-runtime-compilation.md)и [Инициализация смешанных сборок](../../dotnet/initialization-of-mixed-assemblies.md).

При попытке загрузить приложение, скомпилированное с помощью **`/openmp`** и, и * *`/clr*`* в домен приложения, не заданный по умолчанию, <xref:System.TypeInitializationException> исключение создается вне отладчика, а `OpenMPWithMultipleAppdomainsException` в отладчике создается исключение.

Эти исключения также могут возникать в следующих ситуациях.

- Значение, если приложение компилируется с использованием **`/clr`** , но не **`/openmp`** и загружается в домен приложения, не заданный по умолчанию, где процесс включает приложение, скомпилированное с помощью **`/openmp`** .

- При передаче **`/clr`** приложения в служебную программу, например [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), которая загружает целевые сборки в домен приложения, не используемый по умолчанию.

Управление доступом для кода среды CLR не работает в регионах OpenMP. Если атрибут управления доступом для кода CLR применяется за пределами параллельной области, он не будет действовать в параллельной области.

Корпорация Майкрософт не рекомендует создавать **`/openmp`** приложения, допускающие частично доверенные вызывающие объекты. Не используйте <xref:System.Security.AllowPartiallyTrustedCallersAttribute> или любые атрибуты управления доступом для кода CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Разверните страницу **Свойства**  >  языка **C/C++**  >  **язык** .

1. Измените свойство **поддержки OpenMP** .

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Пример

В следующем примере показаны некоторые эффекты запуска пула потоков по сравнению с использованием пула потоков после его запуска. При условии, что 64-разрядная, одноядерная, Двухъядерный процессор, пул потоков занимает около 16 мс для запуска. После этого пул потоков будет немного излишним.

При компиляции с помощью **`/openmp`** второй вызов test2 никогда не выполняется дольше, чем при компиляции с помощью **`/openmp-`** , так как отсутствует запуск пула потоков. В миллионах итераций **`/openmp`** версия выполняется быстрее, чем **`/openmp-`** версия второго вызова test2. При 25 итерациях обе **`/openmp-`** **`/openmp`** версии регистрируются меньше, чем степень гранулярности часов.

Если в приложении имеется только один цикл и оно выполняется менее чем на 15 мс (оно корректируется на приблизительную нагрузку на компьютер), **`/openmp`** может быть неприемлемо. Если это более высокое значение, можно использовать **`/openmp`** .

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>См. также раздел

[Параметры компилятора КОМПИЛЯТОРОМ MSVC](compiler-options.md) \
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md) \
[OpenMP в MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
