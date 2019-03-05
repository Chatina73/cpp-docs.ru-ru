---
title: Отраженные идентификаторы сообщений окон
ms.date: 11/04/2016
f1_keywords:
- OCM_CTLCOLORBTN
- OCM_PARENTNOTIFY
- OCM_VKEYTOITEM
- OCM_CTLCOLORSTATIC
- OCM_HSCROLL
- OCM_CHARTOITEM
- OCM_DRAWITEM
- OCM_MEASUREITEM
- OCM_COMPAREITEM
- OCM_COMMAND
- OCM_NOTIFY
- OCM_CTLCOLORMSGBOX
- OCM_DELETEITEM
- OCM_CTLCOLORLISTBOX
- OCM_CTLCOLORDLG
- OCM_CTLCOLOREDIT
- OCM_CTLCOLORSCROLLBAR
- OCM_VSCROLL
- OCM_CTLCOLOR
helpviewer_keywords:
- OCM_HSCROLL message [MFC]
- OCM_PARENTNOTIFY message [MFC]
- messages, reflected
- reflected messages, window message Ids
- OCM_CTLCOLORDLG message [MFC]
- OCM_COMMAND message [MFC]
- OCM_CTLCOLORMSGBOX message [MFC]
- OCM_COMPAREITEM message [MFC]
- OCM_DRAWITEM message [MFC]
- OCM_VSCROLL message [MFC]
- OCM_CTLCOLOREDIT message [MFC]
- OCM_VKEYTOITEM message [MFC]
- OCM_CHARTOITEM message [MFC]
- OCM_CTLCOLORBTN message [MFC]
- OCM_CTLCOLORSTATIC message [MFC]
- OCM_MEASUREITEM message [MFC]
- OCM_CTLCOLOR message [MFC]
- OCM_CTLCOLORSCROLLBAR message [MFC]
- OCM_ messages
- OCM_DELETEITEM message [MFC]
- OCM_CTLCOLORLISTBOX message [MFC]
- OCM_NOTIFY message [MFC]
- reflected messages
ms.assetid: 3417ff51-ff9f-458c-bff4-17c200f00d96
ms.openlocfilehash: 2f6aea30fbf86865b5d42ea8da364685010c95c0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302095"
---
# <a name="reflected-window-message-ids"></a>Отраженные идентификаторы сообщений окон

Подкласс быстрый способ создания элемента управления ActiveX или другие специализированного элемента управления является окном. Дополнительные сведения см. в разделе [элементы управления MFC ActiveX: Создание подкласса элемента управления Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

Чтобы предотвратить получение окно сообщения, отправленные элемент управления Windows, контейнера элемента управления [COleControl](../mfc/reference/colecontrol-class.md) создает окно «рефлектор» для перехвата определенных сообщений окна и отправить их обратно в элемент управления. Элемент управления, в его процедуре окна, затем может обрабатывать эти отраженные сообщения, выполнив действия, соответствующие для элемента управления ActiveX.

Ниже приведены сообщения, которые могут быть перехвачены и соответствующие сообщения, отправляемые в окне reflector.

|Сообщение, отправленное с помощью элемента управления|Сообщение, отражаемый для элемента управления|
|---------------------------------|--------------------------------------|
|[WM_COMMAND](/windows/desktop/menurc/wm-command)|OCM_COMMAND|
|[WM_CTLCOLORBTN](/windows/desktop/Controls/wm-ctlcolorbtn)|OCM_CTLCOLORBTN|
|[WM_CTLCOLOREDIT](/windows/desktop/Controls/wm-ctlcoloredit)|OCM_CTLCOLOREDIT|
|[WM_CTLCOLORDLG](/windows/desktop/dlgbox/wm-ctlcolordlg)|OCM_CTLCOLORDLG|
|[WM_CTLCOLORLISTBOX](/windows/desktop/Controls/wm-ctlcolorlistbox)|OCM_CTLCOLORLISTBOX|
|[WM_CTLCOLORSCROLLBAR](/windows/desktop/Controls/wm-ctlcolorscrollbar)|OCM_CTLCOLORSCROLLBAR|
|[WM_CTLCOLORSTATIC](/windows/desktop/Controls/wm-ctlcolorstatic)|OCM_CTLCOLORSTATIC|
|[WM_DRAWITEM](/windows/desktop/Controls/wm-drawitem)|OCM_DRAWITEM|
|[WM_MEASUREITEM](/windows/desktop/Controls/wm-measureitem)|OCM_MEASUREITEM|
|[WM_DELETEITEM](/windows/desktop/Controls/wm-deleteitem)|OCM_DELETEITEM|
|[WM_VKEYTOITEM](/windows/desktop/Controls/wm-vkeytoitem)|OCM_VKEYTOITEM|
|[WM_CHARTOITEM](/windows/desktop/Controls/wm-chartoitem)|OCM_CHARTOITEM|
|[WM_COMPAREITEM](/windows/desktop/Controls/wm-compareitem)|OCM_COMPAREITEM|
|[WM_HSCROLL](/windows/desktop/Controls/wm-hscroll)|OCM_HSCROLL|
|[WM_VSCROLL](/windows/desktop/Controls/wm-vscroll)|OCM_VSCROLL|
|[WM_PARENTNOTIFY](/previous-versions/windows/desktop/inputmsg/wm-parentnotify)|OCM_PARENTNOTIFY|
|[WM_NOTIFY](/windows/desktop/controls/wm-notify)|OCM_NOTIFY|

> [!NOTE]
>  Если элемент управления работает в системе Win32, существует несколько видов WM_CTLCOLOR\* она может получать сообщения. Дополнительные сведения см. в разделе WM_CTLCOLORBTN, WM_CTLCOLORDLG, WM_CTLCOLOREDIT, которые, WM_CTLCOLORLISTBOX, WM_CTLCOLORMSGBOX, WM_CTLCOLORSCROLLBAR, WM_CTLCOLORSTATIC.

## <a name="see-also"></a>См. также

[Элементы ActiveX в MFC. Создание подкласса элемента управления Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)<br/>
[TN062: Отражение сообщений для элементов управления Windows](../mfc/tn062-message-reflection-for-windows-controls.md)
