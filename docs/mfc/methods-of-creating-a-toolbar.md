---
description: 'Дополнительные сведения: методы создания панели инструментов'
title: Способы создания панели инструментов
ms.date: 11/04/2016
helpviewer_keywords:
- CToolBarCtrl class [MFC], and CToolBar class [MFC]
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- toolbar controls [MFC]
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
ms.openlocfilehash: 14626f398d3ccabd002cc21be682c1a5616a0410
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203085"
---
# <a name="methods-of-creating-a-toolbar"></a>Способы создания панели инструментов

MFC предоставляет два класса для создания панелей инструментов: [CToolBar](reference/ctoolbar-class.md) и [CToolBarCtrl](reference/ctoolbarctrl-class.md) (которые создают оболочку для стандартного элемента управления Windows). `CToolBar` предоставляет все функциональные возможности общего элемента управления панели инструментов и обрабатывает многие из необходимых общих параметров и структур элементов управления. Однако итоговый исполняемый файл обычно будет больше, чем созданный с помощью `CToolBarCtrl` .

`CToolBarCtrl` обычно приводит к уменьшению исполняемого файла, и вы можете использовать его, `CToolBarCtrl` если не планируется интегрировать панель инструментов в архитектуру MFC. Если вы планируете использовать `CToolBarCtrl` и интегрировать панель инструментов в архитектуру MFC, необходимо проделать дополнительную осторожность, чтобы взаимодействовать с элементами управления панели инструментов с MFC. Это несложная связь. Однако это дополнительная работа, которая не требуется при использовании `CToolBar` .

Visual C++ предоставляет два способа использования преимуществ общего элемента управления панели инструментов.

- Создайте панель инструментов с помощью `CToolBar` , а затем вызовите [CToolBar:: жеттулбарктрл](reference/ctoolbar-class.md#gettoolbarctrl) , чтобы получить доступ к `CToolBarCtrl` функциям элементов.

- Создайте панель инструментов с помощью конструктора [CToolBarCtrl](reference/ctoolbarctrl-class.md).

Любой из методов предоставит доступ к функциям элементов управления ToolBar. При вызове `CToolBar::GetToolBarCtrl` он возвращает ссылку на `CToolBarCtrl` объект, чтобы можно было использовать любой набор функций-членов. Сведения о создании и создании панели инструментов с помощью см. в разделе [CToolBar](reference/ctoolbar-class.md) `CToolBar` .

## <a name="see-also"></a>См. также раздел

[Использование CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Элементы управления](controls-mfc.md)
