---
title: Структура MEASUREITEMSTRUCT
ms.date: 11/04/2016
f1_keywords:
- MEASUREITEMSTRUCT
helpviewer_keywords:
- MEASUREITEMSTRUCT structure [MFC]
ms.assetid: d141ace4-47cb-46b5-a81c-ad2c5e5a8501
ms.openlocfilehash: 3f541c30c484041d855807f220345d6863a780d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575065"
---
# <a name="measureitemstruct-structure"></a>Структура MEASUREITEMSTRUCT

`MEASUREITEMSTRUCT` Структура информирует о Windows из измерений рисуемый владельцем элемент управления или меню.

## <a name="syntax"></a>Синтаксис

```
typedef struct tagMEASUREITEMSTRUCT {
    UINT CtlType;
    UINT CtlID;
    UINT itemID;
    UINT itemWidth;
    UINT itemHeight;
    DWORD itemData
} MEASUREITEMSTRUCT;
```

#### <a name="parameters"></a>Параметры

*CtlType*<br/>
Содержит тип элемента управления. Ниже приведены значения для типов элементов управления.

- Поле со списком ODT_COMBOBOX пользовательской отрисовки

- ODT_LISTBOX рисуемого владельцем поле со списком

- ODT_MENU рисуемом владельце пункте меню

*CtlID*<br/>
Содержит идентификатор элемента управления для поле со списком, поле со списком или кнопки. Этот элемент не используется для меню.

*Идентификатор элемента*<br/>
Содержит идентификатор пункта меню меню или идентификатор элемента поле списка для переменной высоты со списком или списка. Этот элемент не используется для фиксированной высоты списком или поле со списком или кнопки.

*itemWidth*<br/>
Задает ширину элемента меню. Владельца пункта меню рисуемый владельцем, прежде чем она возвращает сообщение, необходимо указать этот член.

*itemHeight*<br/>
Указывает высоту отдельный элемент в поле со списком или меню. Перед возвращением из сообщения, владельцем поле со списком рисуемого владельцем поле со списком или элемента меню, необходимо заполнить этот член. Максимальная высота элемента списка — 255.

*itemData*<br/>
Для поля со списком или списка этот элемент содержит значение, которое было передано в список с помощью одной из следующих структур:

- [CComboBox::AddString](../../mfc/reference/ccombobox-class.md#addstring)

- [CComboBox::InsertString](../../mfc/reference/ccombobox-class.md#insertstring)

- [CListBox::AddString](../../mfc/reference/clistbox-class.md#addstring)

- [CListBox::InsertString](../../mfc/reference/clistbox-class.md#insertstring)

Для меню этот элемент содержит значение, которое было передано в меню с помощью одной из следующих структур:

- [CMenu::AppendMenu](../../mfc/reference/cmenu-class.md#appendmenu)

- [CMenu::InsertMenu](../../mfc/reference/cmenu-class.md#insertmenu)

- [CMenu::ModifyMenu](../../mfc/reference/cmenu-class.md#modifymenu)

Это позволяет Windows для взаимодействия с пользователем с помощью элемента управления будут обработаны правильно. Не удалось заполнить соответствующие элементы в `MEASUREITEMSTRUCT` структуры приведет к неправильной работы элемента управления.

## <a name="requirements"></a>Требования

**Заголовок:** winuser.h

## <a name="see-also"></a>См. также

[Структуры, стили, обратные вызовы и схемы сообщений](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)

