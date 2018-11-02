---
title: Диалоговое окно "Параметры направляющих" (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- DLUs (dialog units)
- Dialog Editor [C++], snap to guides
- grid spacing
- guides, settings
- dialog units (DLUs)
- layout grid in Dialog Editor
- snap to guides (Dialog editor)
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
ms.assetid: 55381e1c-146a-4fa7-b1b3-b1492817615f
ms.openlocfilehash: 2f83acddf0f56225f74961ef31988a5938685b67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483620"
---
# <a name="guide-settings-dialog-box-c"></a>Диалоговое окно "Параметры направляющих" (C++)

## <a name="layout-guides"></a>Направляющие разметки

Параметры для направляющих макета.

### <a name="none"></a>Нет

Скрывает макета.

### <a name="rulers-and-guides"></a>Линейки и направляющие

Если этот параметр включен, добавляет линейки средство «layout»; направляющие можно поместить в линейки. В руководствах по умолчанию – это поля, которые можно перемещать путем перетаскивания. Щелкните линейки, чтобы разместить структуру. Элементы управления «привязка» к описаниям при перемещении элементов управления через или рядом с ними. Элементы управления также перемещаются вместе с руководством, присоединенная к нему. Когда элемент управления прикрепляется к структуре на каждой стороне и направляющая перемещается, размер.

### <a name="grid"></a>Grid

Создание сетки макета. Новые элементы управления автоматически будет соответствовать сетки.

## <a name="grid-spacing"></a>шаг сетки

Параметры для шаг сетки в единицах диалогового (окна DLU).

### <a name="width-dlus"></a>Ширина: DLU

Задает ширину сетки макета в единицах диалогового окна. Горизонтальная Единица диалогового окна — среднюю ширину деления четыре на шрифт диалогового окна.

### <a name="height-dlus"></a>Высота: DLU

Задает высоту сетки макета в единицах диалогового окна. Вертикальная Единица диалогового окна — это средняя высота шрифта диалогового деленная на восемь.

Сведения о добавлении ресурсов в управляемые проекты см. в разделе [ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework*. Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделе [Создание файлов ресурсов для приложений рабочего стола](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Сведения о глобализации и локализации ресурсов в управляемых приложениях, см. в разделе [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Требования

Win32

## <a name="see-also"></a>См. также

[Изменение сетки макета](../windows/modifying-the-layout-grid.md)<br/>
[Состояния редактора диалоговых окон (направляющие и сетки)](../windows/dialog-editor-states-guides-and-grids.md)