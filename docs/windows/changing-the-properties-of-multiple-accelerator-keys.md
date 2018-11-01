---
title: Изменение свойств для нескольких сочетаний клавиш (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], property changing
- accelerator tables [C++], changing properties
ms.assetid: b55c9bd6-b430-48bb-b942-0e6f21d7abf9
ms.openlocfilehash: 00c2bed34d70fa13161cbaa8968d967664c8bb0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50669005"
---
# <a name="changing-the-properties-of-multiple-accelerator-keys-c"></a>Изменение свойств для нескольких сочетаний клавиш (C++)

### <a name="to-change-the-properties-of-multiple-accelerator-keys"></a>Изменение свойств для нескольких сочетаний клавиш

1. Откройте таблицу сочетаний клавиш, дважды щелкнув его значок в [представление ресурсов](../windows/resource-view-window.md).

   > [!NOTE]
   > Если в проекте еще нет RC-файла, см. раздел [Создание нового файла описания ресурсов](../windows/how-to-create-a-resource-script-file.md).

2. Выберите сочетания клавиш, которые вы хотите изменить, удерживая нажатой **Ctrl** ключа, щелкните каждый из них.

3. Перейдите к [окно "Свойства"](/visualstudio/ide/reference/properties-window) и введите значения, все сочетаний для совместного использования.

   > [!NOTE]
   > Каждое значение модификатора отображается как логическое свойство в **свойства** окна. При изменении [модификатор](../windows/accelerator-modifier-property.md) значение в **свойства** окно, в таблице сочетаний клавиш рассматривает Модификатор new как дополнение к ранее использовавшимся модификаторам. Из-за этого, если вы зададите значения любой модификатор, необходимо будет задать все из них, чтобы убедиться, что каждый ускоритель использует же **модификатор** параметры.

Сведения о добавлении ресурсов в управляемые проекты см. в разделе [ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework*. Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделе [Создание файлов ресурсов для приложений рабочего стола](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Сведения о глобализации и локализации ресурсов в управляемых приложениях, см. в разделе [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Требования

Win32

## <a name="see-also"></a>См. также

[Редактирование в таблицах сочетаний клавиш](../windows/editing-accelerator-tables.md)<br/>
[Редактор сочетаний клавиш](../windows/accelerator-editor.md)