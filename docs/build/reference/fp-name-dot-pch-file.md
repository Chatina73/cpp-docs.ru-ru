---
title: /Fp (имя PCH-файла)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: 95506e17dff47e51cb7a3d83b629880f63422d26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270996"
---
# <a name="fp-name-pch-file"></a>/Fp (имя PCH-файла)

Предоставляет путь для предкомпилированного заголовка, вместо того чтобы использовать имя пути по умолчанию.

## <a name="syntax"></a>Синтаксис

> **/ Fp**<em>pathname</em>

## <a name="remarks"></a>Примечания

Этот параметр используется с [/Yc (создать предкомпилированный заголовочный файл)](yc-create-precompiled-header-file.md) или [/Yu (использование файла предкомпилированного заголовка)](yu-use-precompiled-header-file.md) имя пути для предкомпилированного заголовка, вместо того чтобы использовать имя пути по умолчанию. Можно также использовать **/FP** с **/Yc** позволяет указать использование файла предкомпилированного заголовка, который отличается от **/Yc**<em>filename</em> аргумент и из базового имени исходного файла.

Если вы не укажете расширение как часть имени пути, предполагается расширение PCH. Если задан каталог без имени файла, имя файла по умолчанию — VC*x*0.pch, где *x* – основная используемая версия Visual C++.

Можно также использовать **/FP** с параметром **/Yu**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Откройте папку **C/C++** .

1. Нажмите кнопку **предкомпилированные заголовки** страницу свойств.

1. Изменить **файла предкомпилированного заголовка** свойство.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.

## <a name="example"></a>Пример

Если вы хотите создать файл предкомпилированного заголовка для отладочной версии программы и файлы заголовков и исходного кода при компиляции, такие как можно указать команду:

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>Пример

Следующая команда задает использование файла предкомпилированного заголовка с именем MYPCH.pch. Компилятор предполагает, что исходный код в PROG.cpp скомпилированные через MYAPP.h и что предварительно скомпилированный код содержится в файле MYPCH.pch. Он использует содержимое файла MYPCH.pch и компилирует остаток PROG.cpp для создания OBJ-файл. Выходные данные этого примера является файл с именем PROG.exe.

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>См. также

[Параметры выходного файла (/F)](output-file-f-options.md)<br/>
[Параметры компилятора MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора MSVC](compiler-command-line-syntax.md)<br/>
[Указание пути](specifying-the-pathname.md)
