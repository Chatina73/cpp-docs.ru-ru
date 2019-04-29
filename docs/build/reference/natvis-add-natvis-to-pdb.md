---
title: / NATVIS (Добавление файла Natvis в PDB-ФАЙЛ)
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: e758a49b41a17d805b752947cd1944087c8ff852
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320621"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (Добавление файла Natvis в PDB-ФАЙЛ)

> / NATVIS:*имя файла*

## <a name="parameters"></a>Параметры

*filename*<br/>
Natvis-файл для добавления в PDB-файл. Он внедряет визуализация отладчика в файле Natvis в PDB-ФАЙЛ.

## <a name="remarks"></a>Примечания

Параметр /NATVIS внедряет визуализация отладчика, определенный в natvis-файла *filename* в PDB-файл, созданный с помощью LINK. Это позволяет отладчику отображать визуализации, независимо от natvis-файл. Можно использовать несколько вариантов /NATVIS для внедрения более одного файла Natvis в файл PDB.

LINK игнорирует /NATVIS, когда PDB-файл не создается с помощью [/DEBUG](debug-generate-debug-info.md) параметр. Сведения о создании и использовании natvis-файлы, см. в разделе [Создание настраиваемых представлений собственных объектов в отладчике Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств компилятора и собранной задать C++ в Visual Studio](../working-with-project-properties.md).

1. Выберите **командной строки** страницы свойств в **компоновщика** папки.

1. Добавьте параметр /NATVIS **Дополнительные параметры** текстовое поле.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- Этот параметр не поддерживает программный эквивалент.

## <a name="see-also"></a>См. также

[Справочник по компоновщику MSVC](linking.md)<br/>
[Параметры компоновщика MSVC](linker-options.md)
