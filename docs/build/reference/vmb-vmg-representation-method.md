---
description: Дополнительные сведения о:/VMB,/vmg (метод представления)
title: /vmb, /vmg (метод представления)
ms.date: 04/12/2021
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.openlocfilehash: 54bff3787684906b6a932470abbfe8fb60e54cc1
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577163"
---
# <a name="vmb-vmg-representation-method"></a>`/vmb`, `/vmg` (Метод представления)

Выберите метод, используемый компилятором для представления указателей на члены класса.

## <a name="syntax"></a>Синтаксис

> **`/vmb`**\
> **`/vmg`**

### <a name="options"></a>Параметры

**`/vmb`** поведение компилятора по умолчанию. Его поведение аналогично `#pragma pointers_to_members(best_case)` . Он не требует и не гарантирует полные типы. Для полных типов используется лучшее представление между отдельными, несколькими или виртуальными наследованиями на основе наследования типа класса. Для неполных типов используется наибольшее общее представление.

**`/vmg`** позволяет указать поведение компилятора в сочетании с [ `/vmm` , `/vms` , `/vmv` (представление общего назначения)](./vmm-vms-vmv-general-purpose-representation.md) для объявления указателя на член класса перед определением класса. Это может возникнуть при определении членов в двух разных классах, ссылающихся друг на друга. Для таких взаимно ссылающихся классов необходимо ссылаться на один класс до его определения.

## <a name="remarks"></a>Замечания

Можно также использовать [`#pragma pointers_to_members`](../../preprocessor/pointers-to-members.md) [Ключевые слова или наследование](../../cpp/inheritance-keywords.md) в коде для указания представления указателя.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите страницу свойств **Свойства конфигурации**  >  **C/C++**  >  **Командная строка** .

1. В поле **Дополнительные параметры** введите параметр компилятора.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора КОМПИЛЯТОРОМ MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md)
