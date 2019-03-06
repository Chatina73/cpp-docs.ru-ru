---
title: /Ox (Включение большинства видов оптимизации скорости)
ms.date: 10/18/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.ToolOptimization
- /Ox
- /Oxs
helpviewer_keywords:
- Ox compiler option [C++]
- fast code [C++]
- /Ox compiler option [C++]
- -Ox compiler option [C++]
ms.assetid: 3ad7c30b-c615-428c-b1d0-2e024f81c760
ms.openlocfilehash: 9f93d67a24f254dff1604c11635c9fa2da7e4557
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414542"
---
# <a name="ox-enable-most-speed-optimizations"></a>/Ox (Включение большинства видов оптимизации скорости)

**/Ox** сочетание оптимизаций, предпочитать скорость включает параметр компилятора. В некоторых версиях Visual Studio IDE и компилятора справочные сообщения, это называется *Полная оптимизация*, но **/Ox** только подмножество параметров оптимизации скорости, включаемые включает параметр компилятора **/O2**.

## <a name="syntax"></a>Синтаксис

> **/Ox**

## <a name="remarks"></a>Примечания

**/Ox** включает параметр компилятора **/O** параметров компилятора, приоритет скорости. **/Ox** параметр компилятора не включает дополнительный [/GF (исключение повторяющихся строк)](../../build/reference/gf-eliminate-duplicate-strings.md) и [/Gy (включение компоновки на уровне функций)](../../build/reference/gy-enable-function-level-linking.md) включаемые Параметры[/O1 или/O2 (минимизировать размер, максимизировать скорость)](../../build/reference/o1-o2-minimize-size-maximize-speed.md). Дополнительные параметры, примененное **/O1** и **/O2** может привести к указатели для строк или функции для общего доступа целевой адрес, что может повлиять на отладку и соответствие стандартам языка strict. **/Ox** — простой способ Включение большинства видов оптимизации без включения **/GF** и **/Gy**. Дополнительные сведения см. в разделе описания [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) и [/Gy](../../build/reference/gy-enable-function-level-linking.md) параметры.

**/Ox** параметр компилятора совпадает с помощью следующих параметров в сочетании:

- [Параметр /Ob (расширение встраиваемых функций)](../../build/reference/ob-inline-function-expansion.md), где параметр option 2 (**/Ob2**)

- [/Og (виды глобальной оптимизации)](../../build/reference/og-global-optimizations.md)

- [/Oi (создание встроенных функций)](../../build/reference/oi-generate-intrinsic-functions.md)

- [/Ot (приоритет скорости кода)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md)

- [/Oy (подавление указателей фрейма)](../../build/reference/oy-frame-pointer-omission.md)

**/Ox** является взаимоисключающим с:

- [/ O1 (минимизировать размер)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/ O2 (максимизировать скорость)](../../build/reference/o1-o2-minimize-size-maximize-speed.md)

- [/Od (отключение (отладчика))](../../build/reference/od-disable-debug.md)

Вы можете отменить смещения в сторону быстродействия **/Ox** параметр компилятора, если указать **/Oxs**, сочетающий **/Ox** параметра компилятора с [/Os (приоритет небольшого размера Код)](../../build/reference/os-ot-favor-small-code-favor-fast-code.md). Объединенные параметры предпочитать размер кода.  **/Oxs** параметр именно это аналогично указанию **/Ox** **/Os** после того как параметры отобразятся в указанном порядке.

Чтобы применить все доступные файлового уровня оптимизации для сборок выпуска, мы рекомендуем указать [/O2 (максимизировать скорость)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) вместо **/Ox**, и [/O1 (минимизировать размер)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) вместо из **/Oxs**. Для еще больше оптимизации в версии сборок, также учитывать [/GL (оптимизация всей программы)](../../build/reference/gl-whole-program-optimization.md) параметр компилятора и [/LTCG (Создание кода во время компоновки)](../../build/reference/ltcg-link-time-code-generation.md) параметр компоновщика.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. В разделе **свойства конфигурации**откройте **C/C++** и выберите **оптимизации** страницу свойств.

1. Изменить **оптимизации** свойство.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>См. также

[Параметры /O (оптимизация кода)](../../build/reference/o-options-optimize-code.md)<br/>
[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)
