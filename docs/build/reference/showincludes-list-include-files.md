---
description: Дополнительные сведения о:/showIncludes (список включаемых файлов)
title: /showIncludes (список включаемых файлов)
ms.date: 04/15/2021
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ShowIncludes
- VC.Project.VCCLCompilerTool.ShowIncludes
- /showincludes
helpviewer_keywords:
- include files
- /showIncludes compiler option [C++]
- include files, displaying in compilation
- -showIncludes compiler option [C++]
- showIncludes compiler option [C++]
ms.openlocfilehash: 3c960b7b88b9d96cde54f535bffbaf67dd3f67b6
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539251"
---
# <a name="showincludes-list-include-files"></a>`/showIncludes` (Список включаемых файлов)

Приводит к тому, что компилятор выводит список включаемых файлов. Параметр также отображает вложенные включаемые файлы, то есть файлы, включенные в включаемые файлы.

## <a name="syntax"></a>Синтаксис

> **`/showIncludes`**

## <a name="remarks"></a>Remarks

Когда компилятор переходит к включаемому файлу во время компиляции, выводится сообщение, как показано в следующем примере:

```cmd
Note: including file: d:\MyDir\include\stdio.h
```

Вложенные включаемые файлы обозначаются отступом, по одному месту на каждый уровень вложенности, как показано в следующем примере:

```cmd
Note: including file: d:\temp\1.h
Note: including file:  d:\temp\2.h
```

В этом случае *`2.h`* был добавлен из в *`1.h`* , что привело к отступу.

**`/showIncludes`** Параметр выдает `stderr` , а не `stdout` .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите страницу свойств свойства **конфигурации**  >  **C/C++**  >  **Дополнительно** .

1. Измените свойство **Показывать включаемые** .

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ShowIncludes%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора КОМПИЛЯТОРОМ MSVC](compiler-options.md)\
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md)
