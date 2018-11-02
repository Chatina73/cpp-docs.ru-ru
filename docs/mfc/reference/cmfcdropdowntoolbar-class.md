---
title: Класс CMFCDropDownToolBar
ms.date: 10/188/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: ccbdd69baea104f306cfdca69efb46985ee97b91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582004"
---
# <a name="cmfcdropdowntoolbar-class"></a>Класс CMFCDropDownToolBar

Панель инструментов, которая появляется, когда пользователь нажимает и удерживает кнопку верхнего уровня панели инструментов.

   Для получения дополнительных сведений см. в разделе исходном коде, расположенном в **VC\\atlmfc\\src\\mfc** папке установки Visual Studio.
## <a name="syntax"></a>Синтаксис

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|(Переопределяет `CPane::AllowShowOnPaneMenu`.)|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(Переопределяет [CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap).)|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(Переопределяет [CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar).)|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|(Переопределяет `CMFCToolBar::OnSendCommand`.)|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(Переопределяет [CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md).|

### <a name="remarks"></a>Примечания

Объект `CMFCDropDownToolBar` объект объединяет внешний вид панели инструментов с поведением во всплывающем меню. Когда пользователь нажимает и удерживает кнопку раскрывающегося списка на панели инструментов (см. в разделе [класс CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)), появляется панель инструментов раскрывающегося списка, и пользователь может выбрать кнопку из раскрывающегося списка на панели инструментов, прокрутив список к нему и отпуская кнопку мыши кнопка. После того как пользователь выберет кнопки в раскрывающемся списке панели инструментов, этой кнопки отображается как текущей кнопки на панели элементов верхнего уровня.

Нельзя настроить или закрепленной панели инструментов выберите в раскрывающемся, и он не имеет состояния перемещаемой.

На следующем рисунке показано `CMFCDropDownToolBar` объекта:

![Пример cmfcdropdowntoolbar](../../mfc/reference/media/cmfcdropdown.png "cmfcdropdown")

Создании `CMFCDropDownToolBar` объект так же, как и обычные инструментов (см. в разделе [класс CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)).

Вставляемый раскрывающегося списка на панели инструментов в родительской панели инструментов:

1. Зарезервируйте идентификатор фиктивный ресурс для кнопки в панели инструментов к родительскому ресурсу.

2. Создание `CMFCDropDownToolBarButton` , содержащий раскрывающегося списка на панели инструментов (Дополнительные сведения см. в разделе [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton)).

3. Заменить фиктивные кнопку с `CMFCDropDownToolBarButton` объекта с помощью [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Дополнительные сведения о кнопки панели инструментов, см. в разделе [Пошаговое руководство: размещение элементов управления на панели инструментов](../../mfc/walkthrough-putting-controls-on-toolbars.md). Пример того, панель инструментов раскрывающегося списка см. в разделе примера проекта VisualStudioDemo.

## <a name="example"></a>Пример

Следующий пример демонстрирует, как использовать `Create` метод в `CMFCDropDownToolBar` класса. Этот фрагмент кода является частью [Visual Studio демонстрационного](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** afxdropdowntoolbar.h

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Примечания

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

Загружает изображения значков панели инструментов из ресурсов приложения.

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>Параметры

*uiResID*<br/>
[in] Идентификатор ресурса точечного рисунка, который относится к изображениям значка панели инструментов.

*uiColdResID*<br/>
[in] Идентификатор ресурса точечного рисунка, который относится к изображениям "холодных" панели инструментов.

*uiMenuResID*<br/>
[in] Идентификатор ресурса точечного рисунка, который относится к обычным изображениям значков меню.

*Заблокировано*<br/>
[in] Значение TRUE для закрепления панели инструментов; в противном случае — значение FALSE.

*uiDisabledResID*<br/>
[in] Идентификатор ресурса точечного рисунка, который относится к изображениям отключенные панели инструментов.

*uiMenuDisabledResID*<br/>
[in] Идентификатор ресурса точечного рисунка, который относится к отключенным изображениям значков меню.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если метод выполнен успешно; в противном случае — 0.

### <a name="remarks"></a>Примечания

Метод [CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) вызывает этот метод, чтобы загрузить изображения, связанные с панелью инструментов. Переопределите этот метод для выполнения пользовательской загрузки графических ресурсов.

Вызовите метод `LoadBitmapEx` , чтобы загрузить дополнительные изображения после создания панели инструментов.

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>Параметры

[in] *uiResID*<br/>

[in] *uiColdResID*<br/>

[in] *uiMenuResID*<br/>

[in] *BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Примечания

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Параметры

[in] *nFlags*<br/>

[in] *точки*<br/>

### <a name="remarks"></a>Примечания

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>Параметры

[in] *nFlags*<br/>

[in] *точки*<br/>

### <a name="remarks"></a>Примечания

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>Параметры

[in] *pButton*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Примечания

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>Параметры

[in] *pTarget*<br/>

[in] *bDisableIfNoHndler*<br/>

### <a name="remarks"></a>Примечания

## <a name="see-also"></a>См. также

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Класс CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[Пошаговое руководство. Размещение элементов управления на панели инструментов](../../mfc/walkthrough-putting-controls-on-toolbars.md)

