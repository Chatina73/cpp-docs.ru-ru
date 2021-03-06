---
description: 'Дополнительные сведения о: Control classes'
title: Классы элементов управления
ms.date: 11/04/2016
f1_keywords:
- vc.classes.control
helpviewer_keywords:
- static display controls [MFC]
- control classes [MFC]
- buttons, MFC control classes
- controls [MFC], MFC control classes
- controls [MFC]
- list boxes [MFC], MFC control classes
- control classes [MFC], MFC
- text, controls for input [MFC]
- user input [MFC], MFC control classes
ms.assetid: f9876606-9f5b-44cb-9135-213298d1df8f
ms.openlocfilehash: eb0bee6d865867a052b5f49408bdaa1b70da343f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310126"
---
# <a name="control-classes"></a>Классы элементов управления

Классы элементов управления инкапсулируют разнообразные стандартные элементы управления Windows, начиная от статических текстовых элементов управления до элементов управления "дерево". Кроме того, MFC предоставляет несколько новых элементов управления, включая кнопки с точечными рисунками и панели элементов управления.

Элементы управления, имена классов которых оканчиваются на "**CTRL**", появились в Windows 95 и Windows NT версии 3,51.

## <a name="static-display-controls"></a>Статические элементы управления отображением

[CStatic](reference/cstatic-class.md)<br/>
Окно со статическим отображением. Статические элементы управления используются для добавления меток, полей или разделения других элементов управления в диалоговом окне или окне. Они также могут отображать графические изображения, а не текстовые или поля.

## <a name="text-controls"></a>Текстовые элементы управления

[CEdit](reference/cedit-class.md)<br/>
Окно элемента управления для редактирования текста. Элементы управления "поле ввода" используются для приема текстового ввода пользователем.

[CIPAddressCtrl](reference/cipaddressctrl-class.md)<br/>
Поддерживает поле редактирования для управления IP-адресом.

[CRichEditCtrl](reference/cricheditctrl-class.md)<br/>
Элемент управления, в котором пользователь может вводить и редактировать текст. В отличие от элемента управления, инкапсулированного в `CEdit` , форматированный элемент управления "поле ввода" поддерживает форматирование символов и абзацев и объекты OLE.

## <a name="controls-that-represent-numbers"></a>Элементы управления, представляющие числа

[CSliderCtrl](reference/csliderctrl-class.md)<br/>
Элемент управления, содержащий ползунок, который перемещается пользователем для выбора значения или набора значений.

[CSpinButtonCtrl](reference/cspinbuttonctrl-class.md)<br/>
Пара кнопок со стрелками, которую пользователь может щелкнуть для увеличения или уменьшения значения.

[CProgressCtrl](reference/cprogressctrl-class.md)<br/>
Отображает прямоугольник, который постепенно заполняется слева направо, чтобы указать ход выполнения операции.

[CScrollBar](reference/cscrollbar-class.md)<br/>
Окно элемента управления полосы прокрутки. Класс предоставляет функциональные возможности полосы прокрутки для использования в качестве элемента управления в диалоговом окне или окне, с помощью которого пользователь может указать расположение в пределах диапазона.

## <a name="buttons"></a>Кнопки

[CButton](reference/cbutton-class.md)<br/>
Окно элемента управления "Кнопка". Класс предоставляет программный интерфейс для кнопки отправки, флажка или переключателя в диалоговом окне или окне.

[CBitmapButton](reference/cbitmapbutton-class.md)<br/>
Кнопка с точечным рисунком, а не текстовым заголовком.

## <a name="lists"></a>Списки

[CListBox](reference/clistbox-class.md)<br/>
Окно элемента управления "список". В окне списка отображается список элементов, которые пользователь может просматривать и выбирать.

[CDragListBox](reference/cdraglistbox-class.md)<br/>
Предоставляет функциональные возможности окна списка Windows; позволяет пользователю перемещать элементы списка, такие как имена файлов и строковые литералы, в поле со списком. Списки с такой возможностью удобно использовать для списка элементов в порядке, отличном от алфавитного, например для включения путей или файлов в проект.

[CComboBox](reference/ccombobox-class.md)<br/>
Окно элемента управления "поле со списком". Поле со списком содержит элемент управления Edit (Правка) и поле со списком.

[CComboBoxEx](reference/ccomboboxex-class.md)<br/>
Расширяет элемент управления "поле со списком", предоставляя поддержку списков изображений.

[CCheckListBox](reference/cchecklistbox-class.md)<br/>
Отображает список элементов с флажками, которые пользователь может проверить или очистить, рядом с каждым элементом.

[CListCtrl](reference/clistctrl-class.md)<br/>
Отображает коллекцию элементов, каждая из которых состоит из значка и метки, аналогично правой панели проводника.

[CTreeCtrl](reference/ctreectrl-class.md)<br/>
Отображает иерархический список значков и меток, упорядоченный таким же образом, как и левая панель проводника.

## <a name="toolbars-and-status-bars"></a>Панели инструментов и строки состояния

[CToolBarCtrl](reference/ctoolbarctrl-class.md)<br/>
Предоставляет функциональные возможности стандартного элемента управления "панель инструментов" Windows. Большинство программ MFC используют [CToolBar](reference/ctoolbar-class.md) вместо этого класса.

[CStatusBarCtrl](reference/cstatusbarctrl-class.md)<br/>
Горизонтальное окно, обычно разделенное на области, в которых приложение может отображать сведения о состоянии. Большинство программ MFC используют [CStatusBar](reference/cstatusbar-class.md) вместо этого класса.

## <a name="miscellaneous-controls"></a>Прочие элементы управления

[CAnimateCtrl](reference/canimatectrl-class.md)<br/>
Отображает простой видеоролик.

[CToolTipCtrl](reference/ctooltipctrl-class.md)<br/>
Небольшое всплывающее окно, в котором отображается одна строка текста, описывающая назначение инструмента в приложении.

[CDateTimeCtrl](reference/cdatetimectrl-class.md)<br/>
Поддерживает либо расширенный элемент управления "Правка", либо простой элемент управления "интерфейс календаря", позволяющий пользователю выбрать конкретное значение даты или времени.

[CHeaderCtrl](reference/cheaderctrl-class.md)<br/>
Отображает заголовки или метки для столбцов.

[CMonthCalCtrl](reference/cmonthcalctrl-class.md)<br/>
Поддерживает простой элемент управления "интерфейс календаря", позволяющий пользователю выбрать дату.

[CTabCtrl](reference/ctabctrl-class.md)<br/>
Элемент управления с вкладками, на которых пользователь может щелкнуть, аналогичный разделителям в записной книжке.

[CHotKeyCtrl](reference/chotkeyctrl-class.md)<br/>
Позволяет пользователю создать сочетание клавиш, которое пользователь может нажать для быстрого выполнения действия.

[CLinkCtrl](reference/clinkctrl-class.md)<br/>
Отображает помеченный текст и запускает соответствующие приложения, когда пользователь щелкает внедренную ссылку.

[CHtmlEditCtrl](reference/chtmleditctrl-class.md)<br/>
Предоставляет функциональные возможности элемента управления ActiveX WebBrowser в окне MFC.

## <a name="related-classes"></a>Связанные классы

[CImageList](reference/cimagelist-class.md)<br/>
Предоставляет функциональные возможности списка образов Windows. Списки изображений используются с элементами управления "список" и "дерево". Они также могут использоваться для хранения и архивации набора точечных рисунков одинакового размера.

[CCtrlView](reference/cctrlview-class.md)<br/>
Базовый класс для всех представлений, связанных с элементами управления Windows. Ниже описаны представления, основанные на элементах управления.

[CEditView](reference/ceditview-class.md)<br/>
Представление, содержащее стандартный элемент управления "поле ввода" Windows.

[CRichEditView](reference/cricheditview-class.md)<br/>
Представление, содержащее элемент управления Rich Edit в Windows.

[CListView](reference/clistview-class.md)<br/>
Представление, содержащее элемент управления "список" Windows.

[CTreeView](reference/ctreeview-class.md)<br/>
Представление, содержащее элемент управления "дерево" Windows.

## <a name="see-also"></a>См. также раздел

[Общие сведения о классах](class-library-overview.md)
