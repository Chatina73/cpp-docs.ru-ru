---
description: 'Дополнительные сведения о: Кктрлвиев Class'
title: Класс Кктрлвиев
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: b9cb3d9e32772e0d54d23acfc7606dbc45071446
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227771"
---
# <a name="cctrlview-class"></a>Класс Кктрлвиев

Адаптирует архитектуру "документ-представление" для распространенных элементов управления, поддерживаемых Windows 98 и Windows NT (версии 3.51 и более поздние).

## <a name="syntax"></a>Синтаксис

```
class CCtrlView : public CView
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Кктрлвиев:: Кктрлвиев](#cctrlview)|Формирует объект `CCtrlView`.|

### <a name="protected-methods"></a>Защищенные методы

|Имя|Описание|
|----------|-----------------|
|[Кктрлвиев:: OnDraw](#ondraw)|Вызывается платформой для рисования с использованием указанного контекста устройства.|
|[Кктрлвиев::P Рекреатевиндов](#precreatewindow)|Вызывается до создания окна Windows, присоединенного к данному объекту класса `CCtrlView`.|

### <a name="protected-data-members"></a>Защищенные члены данных

|Имя|Описание|
|----------|-----------------|
|[Кктрлвиев:: m_dwDefaultStyle](#m_dwdefaultstyle)|Содержит стиль по умолчанию для класса представления.|
|[Кктрлвиев:: m_strClass](#m_strclass)|Содержит имя класса Windows для класса представления.|

## <a name="remarks"></a>Комментарии

Класс `CCtrlView` и его производные, [CEditView](../../mfc/reference/ceditview-class.md), [CListView](../../mfc/reference/clistview-class.md), [CTreeView](../../mfc/reference/ctreeview-class.md)и [CRichEditView](../../mfc/reference/cricheditview-class.md)адаптируют архитектуру представления документов к новым общим ЭЛЕМЕНТАМ управления, поддерживаемым Windows 95/98 и Windows NT 3,51 и более поздних версий. Дополнительные сведения об архитектуре "документ-представление" см. в разделе [архитектура документов и представлений](../../mfc/document-view-architecture.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>Требования

**Заголовок:** afxwin.h

## <a name="cctrlviewcctrlview"></a><a name="cctrlview"></a> Кктрлвиев:: Кктрлвиев

Формирует объект `CCtrlView`.

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>Параметры

*лпсзкласс*<br/>
Имя класса Windows класса представления.

*двстиле*<br/>
Стиль класса представления.

### <a name="remarks"></a>Комментарии

Платформа вызывает конструктор при создании нового окна фрейма или при разбиении окна. Переопределите [CView:: онинитиалупдате](../../mfc/reference/cview-class.md#oninitialupdate) , чтобы инициализировать представление после присоединения документа. Чтобы создать объект Windows, вызовите метод [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) или [CWnd:: креатикс](../../mfc/reference/cwnd-class.md#createex) .

## <a name="cctrlviewm_strclass"></a><a name="m_strclass"></a> Кктрлвиев:: m_strClass

Содержит имя класса Windows для класса представления.

```
CString m_strClass;
```

## <a name="cctrlviewm_dwdefaultstyle"></a><a name="m_dwdefaultstyle"></a> Кктрлвиев:: m_dwDefaultStyle

Содержит стиль по умолчанию для класса представления.

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Комментарии

Этот стиль применяется при создании окна.

## <a name="cctrlviewondraw"></a><a name="ondraw"></a> Кктрлвиев:: OnDraw

Вызывается платформой для отрисовки содержимого `CCtrlView` объекта с помощью указанного контекста устройства.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Параметры

*Хозяин*<br/>
Указатель на контекст устройства, в котором происходит рисование.

### <a name="remarks"></a>Комментарии

`OnDraw` обычно вызывается для отображения экрана с передачей контекста устройства экрана, заданного *PDC*.

## <a name="cctrlviewprecreatewindow"></a><a name="precreatewindow"></a> Кктрлвиев::P Рекреатевиндов

Вызывается до создания окна Windows, присоединенного к данному объекту класса `CWnd`.

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Параметры

*сложных*<br/>
Структура [CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw) .

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если создание окна должно быть продолжено; значение 0 указывает на сбой при создании.

### <a name="remarks"></a>Комментарии

Никогда не вызывайте эту функцию напрямую.

Реализация по умолчанию этой функции проверяет наличие имени класса окна NULL и подставляет подходящее значение по умолчанию. Переопределите эту функцию-член, чтобы изменить `CREATESTRUCT` структуру перед созданием окна.

Каждый класс, производный от, `CCtrlView` добавляет свои собственные функции к переопределению `PreCreateWindow` . Эти производные от `PreCreateWindow` не задокументированы. Чтобы определить стили, подходящие для каждого класса и взаимозависимости между этими стилями, можно изучить исходный код MFC для базового класса приложения. При выборе переопределения `PreCreateWindow` можно определить, предоставляют ли стили, используемые в базовом классе приложения, необходимые функции, используя сведения, собранные из исходного кода MFC.

Дополнительные сведения об изменении стилей окна см. в разделе [изменение стилей окна, созданного с помощью MFC](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>См. также раздел

[Класс CView](../../mfc/reference/cview-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Класс CTreeView](../../mfc/reference/ctreeview-class.md)<br/>
[Класс CListView](../../mfc/reference/clistview-class.md)<br/>
[Класс CRichEditView](../../mfc/reference/cricheditview-class.md)
