---
description: Дополнительные сведения о:/INCREMENTAL (инкрементная компоновка)
title: /INCREMENTAL (инкрементная компоновка)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 4b115bd88bed5b012c29c3d0e61d471aa869b78a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191294"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (инкрементная компоновка)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Комментарии

Управляет тем, как компоновщик производит инкрементную компоновку.

По умолчанию компоновщик работает в инкрементном режиме. Чтобы переопределить инкрементную компоновку, используемую по умолчанию, укажите параметр /INCREMENTAL:NO.

Инкрементно связанная программа функционально эквивалентна программе, которая не является инкрементно связанной. Тем не менее, так как она подготовлена для последующих добавочных ссылок, инкрементно связываемый исполняемый файл, статическая библиотека или библиотека динамической компоновки:

- Больше, чем неинкрементная связанная программа, из-за заполнения кода и данных. Заполнение позволяет компоновщику увеличивать размер функций и данных без повторного создания файла.

- Может содержать преобразователи переходов для обработки размещения функций по новым адресам.

   > [!NOTE]
   > Чтобы убедиться, что окончательная сборка выпуска не содержит заполнение или преобразователи, свяжите программу не инкрементно.

Для инкрементной компоновки независимо от значения по умолчанию укажите ключ /INCREMENTAL. Если выбран этот параметр, компоновщик выдает предупреждение, если оно не может выполнить инкрементную компоновку, а затем связывает программу не инкрементно. Определенные параметры и ситуации переопределяют ключ /INCREMENTAL.

Большинство программ можно компоновать инкрементно. Тем не менее некоторые изменения слишком значительны, а некоторые параметры — несовместимы с инкрементной компоновкой. LINK выполняет полною компоновку, если указаны любые из следующих параметров:

- Не выбрана инкрементная компоновка (/INCREMENTAL:NO)

- Выбран параметр /OPT:REF

- Выбран параметр /OPT:ICF

- Выбран параметр /OPT:LBR

- Выбран параметр /ORDER

Параметр/INCREMENTAL подразумевается, если указан параметр [/Debug](debug-generate-debug-info.md) .

Кроме того, LINK выполняет полную компоновку, если возникает одна из следующих ситуаций:

- Отсутствует ILK-файл инкрементного состояния. (LINK создает новый ILK-файл для подготовки к последующей инкрементной компоновке.)

- Отсутствуют права записи в ILK-файл. (Ссылка игнорирует ILK-файл и ссылки без добавочных ссылок.)

- Отсутствует выходной EXE- или DLL-файл.

- Изменена отметка времени в ILK-, EXE- или DLL-файле.

- Изменен параметр LINK. Изменение большинства параметров LINK между сборками вызывают полную компоновку.

- Добавлен или пропущен объектный OBJ-файл.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите папку **Компоновщик** .

1. Выберите страницу свойств **Общие** .

1. Измените свойство **Включить инкрементную компоновку** .

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

1. См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>.

## <a name="see-also"></a>См. также раздел

[Справочник по компоновщику MSVC](linking.md)<br/>
[Параметры компоновщика MSVC](linker-options.md)
