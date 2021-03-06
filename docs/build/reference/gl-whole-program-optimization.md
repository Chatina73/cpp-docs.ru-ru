---
description: Дополнительные сведения о:/GL (оптимизация всей программы)
title: /GL (оптимизация всей программы)
ms.date: 03/05/2021
f1_keywords:
- /GL
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.openlocfilehash: 509deaae8881c4875a9ec2ddf4d5f1ee7744a2cf
ms.sourcegitcommit: c0c9cdae79f19655e809a4979227c51bb19cff63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236554"
---
# <a name="gl-whole-program-optimization"></a>`/GL` (Оптимизация всей программы)

Включает оптимизацию всей программы.

## <a name="syntax"></a>Синтаксис

> **`/GL`**[**`-`**]

## <a name="remarks"></a>Комментарии

Оптимизация всей программы позволяет компилятору выполнять оптимизацию со сведениями обо всех модулях в программе. Без оптимизации всей программы оптимизации выполняются на уровне каждого модуля (компилируемого объекта).

Оптимизация всей программы отключена по умолчанию и должна быть явно включена. Однако можно также явно отключить его с помощью **`/GL-`** .

Используя сведения обо всех модулях, компилятор может:

- Оптимизируйте использование регистров в границах функций.

- Лучше отслеживать изменения глобальных данных, что позволяет сократить количество загрузок и магазинов.

- Следите за возможным набором элементов, измененных разыменованием указателя, уменьшая требуемые нагрузки и хранилища.

- Встраивание функции в модуль, даже если функция определена в другом модуле.

*`.obj`* файлы, созданные с помощью, **`/GL`** не используются программами компоновщика, такими как [`EDITBIN`](editbin-reference.md) и [`DUMPBIN`](dumpbin-reference.md) .

При компиляции программы с помощью **`/GL`** и [`/c`](c-compile-without-linking.md) следует использовать параметр компоновщика/LTCG для создания выходного файла.

[`/ZI`](z7-zi-zi-debug-information-format.md) не может использоваться с **`/GL`**

Формат файлов, создаваемых **`/GL`** в текущей версии, часто не читается в более поздних версиях Visual Studio и наборе инструментов компилятором MSVC. Если вы не готовы поставлять копии *`.lib`* файла для всех версий Visual Studio, которые вы планируете использовать, сейчас и в будущем, не доставлять файл, состоящие *`.lib`* из *`.obj`* файлов, созданных **`/GL`** . Дополнительные сведения см. [в разделе ограничения на двоичную совместимость](../../porting/binary-compat-2015-2017.md#restrictions).

*`.obj`* файлы, созданные **`/GL`** и предварительно скомпилированные файлы заголовков, не должны использоваться для сборки *`.lib`* файла, если только этот *`.lib`* файл не связан с тем компьютером, на котором был создан **`/GL`** *`.obj`* файл. Сведения из *`.obj`* файла предкомпилированного заголовка файла необходимы во время компоновки.

Дополнительные сведения о оптимизациях, доступных в, и об ограничениях оптимизации всей программы см. в разделе [`/LTCG`](ltcg-link-time-code-generation.md) .  **`/GL`** также делает доступной оптимизацию профиль. При компиляции для оптимизации с профилем и при необходимости сортировки функций в профильной оптимизации необходимо выполнить компиляцию с помощью [`/Gy`](gy-enable-function-level-linking.md) или параметр компилятора, который подразумевает/Ги.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

Дополнительные сведения об указании **`/GL`** в среде разработки см. в разделе [ `/LTCG` (создание кода во время компоновки)](ltcg-link-time-code-generation.md) .

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора КОМПИЛЯТОРОМ MSVC](compiler-options.md)\
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md)
