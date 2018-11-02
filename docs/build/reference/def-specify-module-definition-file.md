---
title: /DEF (указание файла определения модуля)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ModuleDefinitionFile
- /def
helpviewer_keywords:
- module definition files, specifying
- DEF linker option
- -DEF linker option
- module definition files
- /DEF linker option
ms.assetid: 6497fa68-65f0-48ca-8f66-b87166fc631a
ms.openlocfilehash: 607af17a60612f69bb24708179bb453409098bde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654757"
---
# <a name="def-specify-module-definition-file"></a>/DEF (указание файла определения модуля)

```
/DEF:filename
```

## <a name="arguments"></a>Аргументы

*filename*<br/>
Имя файла определения модуля (.def) для передачи в компоновщик.

## <a name="remarks"></a>Примечания

Параметр/DEF передает файл определения модуля (.def) в компоновщик. Ссылку можно указать только один DEF-файл. Дополнительные сведения о DEF-файлы, см. в разделе [файлы определения модуля](../../build/reference/module-definition-dot-def-files.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств проекта Visual C++ параметр](../../ide/working-with-project-properties.md).

1. Нажмите кнопку **компоновщика** папки.

1. Нажмите кнопку **ввода** страницу свойств.

1. Изменить **файл определения модуля** свойство.

Чтобы указать DEF-файл в среде разработки, следует добавить его в проект, а также другие файлы и затем укажите файл, чтобы параметр/DEF.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ModuleDefinitionFile%2A>.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)