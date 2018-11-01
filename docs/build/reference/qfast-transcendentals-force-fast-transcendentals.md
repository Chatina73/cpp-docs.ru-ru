---
title: /Qfast_transcendentals (принудительное использование быстрых трансцендентных функций)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 512e658cf546e77bff6d58465932d2f830541521
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666132"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (принудительное использование быстрых трансцендентных функций)

Создает встроенный код для трансцендентных функций.

## <a name="syntax"></a>Синтаксис

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Примечания

Этот параметр компилятора заставляет трансцендентных функций для преобразования в встроенного кода для повышения быстродействия. Этот параметр действует только в том случае, когда используется вместе с **/fp: except** или **/fp: точное**. Создание встроенного кода для трансцендентных функций уже поведение по умолчанию в разделе **/fp:fast**.

Этот параметр несовместим с **/fp: strict**. См. в разделе [/fp (определение поведения с плавающей запятой)](../../build/reference/fp-specify-floating-point-behavior.md) Дополнительные сведения о точке параметры компилятора.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Откройте папку **C/C++** .

1. Выберите страницу свойств **Командная строка** .

1. Введите параметр компилятора в поле **Дополнительные параметры** .

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры /Q (низкоуровневые операции)](../../build/reference/q-options-low-level-operations.md)<br/>
[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)