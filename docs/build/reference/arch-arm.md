---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: bf12abd140a56b1b914156083ecbbd3e61e7285a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495586"
---
# <a name="arch-arm"></a>/arch (ARM)

Указывает архитектуру для создания кода на платформе ARM. См. также [/arch (x86)](../../build/reference/arch-x86.md) и [/arch (x64)](../../build/reference/arch-x64.md).

## <a name="syntax"></a>Синтаксис

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Аргументы

**/arch:ARMv7VE**<br/>
Включает использование инструкций расширения виртуализации ARMv7VE.

**/arch:VFPv4**<br/>
Включает использование инструкций ARM VFPv4. Если этот параметр не указан, по умолчанию используется VFPv3.

## <a name="remarks"></a>Примечания

`_M_ARM_FP` Макроса (ARM) указывает, что, если таковые имеются, **/arch** использовался параметр компилятора. Для получения дополнительной информации см. [Predefined Macros](../../preprocessor/predefined-macros.md).

При использовании [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) для компиляции, **/arch** не влияет на создание кода для управляемых функций. **/ arch** только влияет на создание кода для собственных функций.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Чтобы задать параметр компилятора /arch:ARMv7VE или /arch:VFPv4 в Visual Studio

1. Откройте **страницы свойств** диалоговое окно для проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Выберите **C/C++** папки.

1. Выберите **командной строки** страницу свойств.

1. В **Дополнительные параметры** , добавьте `/arch:ARMv7VE` или `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>См. также

[/arch (минимальная архитектура ЦПУ)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)