---
description: 'Дополнительные сведения о: Кпанедивидер Class'
title: Класс Кпанедивидер
ms.date: 11/04/2016
f1_keywords:
- CPaneDivider
- AFXPANEDIVIDER/CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::CPaneDivider
- AFXPANEDIVIDER/CPaneDivider::AddPaneContainer
- AFXPANEDIVIDER/CPaneDivider::AddPane
- AFXPANEDIVIDER/CPaneDivider::AddRecentPane
- AFXPANEDIVIDER/CPaneDivider::CalcExpectedDockedRect
- AFXPANEDIVIDER/CPaneDivider::CalcFixedLayout
- AFXPANEDIVIDER/CPaneDivider::CheckVisibility
- AFXPANEDIVIDER/CPaneDivider::CreateEx
- AFXPANEDIVIDER/CPaneDivider::DoesAllowDynInsertBefore
- AFXPANEDIVIDER/CPaneDivider::DoesContainFloatingPane
- AFXPANEDIVIDER/CPaneDivider::FindPaneContainer
- AFXPANEDIVIDER/CPaneDivider::FindTabbedPane
- AFXPANEDIVIDER/CPaneDivider::GetDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::GetFirstPane
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividerStyle
- AFXPANEDIVIDER/CPaneDivider::GetRootContainerRect
- AFXPANEDIVIDER/CPaneDivider::GetWidth
- AFXPANEDIVIDER/CPaneDivider::Init
- AFXPANEDIVIDER/CPaneDivider::InsertPane
- AFXPANEDIVIDER/CPaneDivider::IsAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::IsDefault
- AFXPANEDIVIDER/CPaneDivider::IsHorizontal
- AFXPANEDIVIDER/CPaneDivider::Move
- AFXPANEDIVIDER/CPaneDivider::NotifyAboutRelease
- AFXPANEDIVIDER/CPaneDivider::OnShowPane
- AFXPANEDIVIDER/CPaneDivider::ReleaseEmptyPaneContainers
- AFXPANEDIVIDER/CPaneDivider::RemovePane
- AFXPANEDIVIDER/CPaneDivider::ReplacePane
- AFXPANEDIVIDER/CPaneDivider::RepositionPanes
- AFXPANEDIVIDER/CPaneDivider::Serialize
- AFXPANEDIVIDER/CPaneDivider::SetAutoHideMode
- AFXPANEDIVIDER/CPaneDivider::SetPaneContainerManager
- AFXPANEDIVIDER/CPaneDivider::ShowWindow
- AFXPANEDIVIDER/CPaneDivider::StoreRecentDockSiteInfo
- AFXPANEDIVIDER/CPaneDivider::StoreRecentTabRelatedInfo
- AFXPANEDIVIDER/CPaneDivider::GetPanes
- AFXPANEDIVIDER/CPaneDivider::GetPaneDividers
- AFXPANEDIVIDER/CPaneDivider::m_nDefaultWidth
- AFXPANEDIVIDER/CPaneDivider::m_pSliderRTC
helpviewer_keywords:
- CPaneDivider [MFC], CPaneDivider
- CPaneDivider [MFC], AddPaneContainer
- CPaneDivider [MFC], AddPane
- CPaneDivider [MFC], AddRecentPane
- CPaneDivider [MFC], CalcExpectedDockedRect
- CPaneDivider [MFC], CalcFixedLayout
- CPaneDivider [MFC], CheckVisibility
- CPaneDivider [MFC], CreateEx
- CPaneDivider [MFC], DoesAllowDynInsertBefore
- CPaneDivider [MFC], DoesContainFloatingPane
- CPaneDivider [MFC], FindPaneContainer
- CPaneDivider [MFC], FindTabbedPane
- CPaneDivider [MFC], GetDefaultWidth
- CPaneDivider [MFC], GetFirstPane
- CPaneDivider [MFC], GetPaneDividerStyle
- CPaneDivider [MFC], GetRootContainerRect
- CPaneDivider [MFC], GetWidth
- CPaneDivider [MFC], Init
- CPaneDivider [MFC], InsertPane
- CPaneDivider [MFC], IsAutoHideMode
- CPaneDivider [MFC], IsDefault
- CPaneDivider [MFC], IsHorizontal
- CPaneDivider [MFC], Move
- CPaneDivider [MFC], NotifyAboutRelease
- CPaneDivider [MFC], OnShowPane
- CPaneDivider [MFC], ReleaseEmptyPaneContainers
- CPaneDivider [MFC], RemovePane
- CPaneDivider [MFC], ReplacePane
- CPaneDivider [MFC], RepositionPanes
- CPaneDivider [MFC], Serialize
- CPaneDivider [MFC], SetAutoHideMode
- CPaneDivider [MFC], SetPaneContainerManager
- CPaneDivider [MFC], ShowWindow
- CPaneDivider [MFC], StoreRecentDockSiteInfo
- CPaneDivider [MFC], StoreRecentTabRelatedInfo
- CPaneDivider [MFC], GetPanes
- CPaneDivider [MFC], GetPaneDividers
- CPaneDivider [MFC], m_nDefaultWidth
- CPaneDivider [MFC], m_pSliderRTC
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
ms.openlocfilehash: 9f05b419a2eb420794fcd416f603592e4ce8bb07
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539602"
---
# <a name="cpanedivider-class"></a>Класс Кпанедивидер

Дополнительные сведения см. в исходном коде, расположенном в папке **VC \\ атлмфк \\ src \\ MFC** в установке Visual Studio.

`CPaneDivider`Класс делит две панели, делит две группы панелей или разделяет группу панелей из клиентской области окна главного фрейма.

## <a name="syntax"></a>Синтаксис

```
class CPaneDivider : public CBasePane
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Кпанедивидер:: Кпанедивидер](#cpanedivider)||

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Кпанедивидер:: Аддпанеконтаинер](#addpanecontainer)||
|[Кпанедивидер:: Аддпане](#addpane)||
|[Кпанедивидер:: Аддрецентпане](#addrecentpane)||
|[Кпанедивидер:: Калцекспектеддоккедрект](#calcexpecteddockedrect)||
|[Кпанедивидер:: Калкфикседлайаут](#calcfixedlayout)|(Переопределяет [CBasePane:: калкфикседлайаут](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[Кпанедивидер:: Чекквисибилити](#checkvisibility)||
|[Кпанедивидер:: Креатикс](#createex)|(Переопределяет [CBasePane:: креатикс](../../mfc/reference/cbasepane-class.md#createex).)|
|[Кпанедивидер::D Оесалловдининсертбефоре](#doesallowdyninsertbefore)|(Переопределяет [CBasePane::D оесалловдининсертбефоре](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[Кпанедивидер::D Оесконтаинфлоатингпане](#doescontainfloatingpane)||
|[Кпанедивидер:: Финдпанеконтаинер](#findpanecontainer)||
|[Кпанедивидер:: Финдтаббедпане](#findtabbedpane)||
|[Кпанедивидер:: Жетдефаултвидс](#getdefaultwidth)||
|[Кпанедивидер:: Жетфирстпане](#getfirstpane)||
|[Кпанедивидер:: Жетпанедивидерс](#getpanedividers)|Возвращает список разделителей областей, которые находятся в [классе кпанеконтаинер](../../mfc/reference/cpanecontainer-class.md). Этот метод должен вызываться только для разделителей панели по умолчанию.|
|[Кпанедивидер:: Жетпанедивидерстиле](#getpanedividerstyle)||
|[Кпанедивидер:: выпанели](#getpanes)|Возвращает список панелей, находящихся в [классе кпанеконтаинер](../../mfc/reference/cpanecontainer-class.md). Этот метод должен вызываться только для разделителей панели по умолчанию.|
|[Кпанедивидер:: Жетрутконтаинеррект](#getrootcontainerrect)||
|[Кпанедивидер:: Полуширинный](#getwidth)||
|[Кпанедивидер:: init](#init)||
|[Кпанедивидер:: Инсертпане](#insertpane)||
|[Кпанедивидер:: Исаутохидемоде](#isautohidemode)|(Переопределяет [CBasePane:: исаутохидемоде](../../mfc/reference/cbasepane-class.md#isautohidemode).)|
|[Кпанедивидер:: Default](#isdefault)||
|[Кпанедивидер:: по горизонтали](#ishorizontal)|(Переопределяет [CBasePane:: Horizontal](../../mfc/reference/cbasepane-class.md#ishorizontal).)|
|[Кпанедивидер:: Move](#move)||
|[Кпанедивидер:: Нотифябаутрелеасе](#notifyaboutrelease)||
|[Кпанедивидер:: Оншовпане](#onshowpane)||
|[Кпанедивидер:: Релеасимптипанеконтаинерс](#releaseemptypanecontainers)||
|[Кпанедивидер:: Ремовепане](#removepane)||
|[Кпанедивидер:: Реплацепане](#replacepane)||
|[Кпанедивидер:: Репоситионпанес](#repositionpanes)||
|[Кпанедивидер:: Serialize](#serialize)|(Переопределяет `CBasePane::Serialize`.)|
|[Кпанедивидер:: Сетаутохидемоде](#setautohidemode)||
|[Кпанедивидер:: Сетпанеконтаинерманажер](#setpanecontainermanager)||
|[Кпанедивидер:: ShowWindow](#showwindow)||
|[Кпанедивидер:: Сторерецентдоккситеинфо](#storerecentdocksiteinfo)||
|[Кпанедивидер:: Сторереценттабрелатединфо](#storerecenttabrelatedinfo)||

|Имя|Описание|
|----------|-----------------|
|[Кпанедивидер:: m_nDefaultWidth](#m_ndefaultwidth)|Задает ширину по умолчанию в пикселях всех разделителей панели в приложении.|
|[Кпанедивидер:: m_pSliderRTC](#m_psliderrtc)|Содержит указатель на сведения о классе среды выполнения для `CPaneDivider` объекта, производного от.|

## <a name="remarks"></a>Комментарии

Платформа автоматически создает `CPaneDivider` объекты при закреплении панели.

Существует два типа разделителей областей:

- разделитель панели по умолчанию создается, когда Группа панелей закрепляется сбоку главного окна фрейма. Разделитель панели по умолчанию содержит указатель на [класс CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md) и перенаправляет большинство операций в группе панелей (например, изменение размера панели или закрепление другой панели или контейнера) в диспетчере контейнеров. Каждая закрепляемая область поддерживает указатель на разделитель панели по умолчанию.

- Разделитель обычной панели просто делит две панели в контейнере. Дополнительные сведения см. в разделе [класс кпанеконтаинер](../../mfc/reference/cpanecontainer-class.md).

## <a name="example"></a>Пример

В этом примере демонстрируется получение объекта `CPaneDivider` из объекта `CWorkspaceBar`. Этот фрагмент кода является частью [демонстрационного примера вкладок MDI](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/cpp/cpanedivider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)\
└ &nbsp; [От CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [CBasePane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└ &nbsp; [Кпанедивидер](../../mfc/reference/cpanedivider-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** афкспанедивидер. h

## <a name="cpanedividersetautohidemode"></a><a name="setautohidemode"></a> Кпанедивидер:: Сетаутохидемоде

```cpp
void SetAutoHideMode(BOOL bMode);
```

### <a name="parameters"></a>Параметры

окне *бмоде*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividersetpanecontainermanager"></a><a name="setpanecontainermanager"></a> Кпанедивидер:: Сетпанеконтаинерманажер

```cpp
void SetPaneContainerManager(CPaneContainerManager* p);
```

### <a name="parameters"></a>Параметры

окне *p*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedivideraddpane"></a><a name="addpane"></a> Кпанедивидер:: Аддпане

```
virtual void AddPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Параметры

окне *пбар*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedivideraddpanecontainer"></a><a name="addpanecontainer"></a> Кпанедивидер:: Аддпанеконтаинер

```
virtual BOOL AddPaneContainer(
    CPaneContainerManager& barContainerManager,
    BOOL bOuterEdge);

virtual BOOL AddPaneContainer(
    CDockablePane* pTargetBar,
    CPaneContainerManager& barContainerManager,
    DWORD dwAlignment);
```

### <a name="parameters"></a>Параметры

окне *барконтаинерманажер*<br/>
окне *баутередже*<br/>
окне *птаржетбар*<br/>
окне *двалигнмент*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedivideraddrecentpane"></a><a name="addrecentpane"></a> Кпанедивидер:: Аддрецентпане

```
virtual CDockablePane* AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>Параметры

окне *пбар*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividercalcexpecteddockedrect"></a><a name="calcexpecteddockedrect"></a> Кпанедивидер:: Калцекспектеддоккедрект

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>Параметры

окне *пвндтодокк*<br/>
окне *птмаусе*<br/>
окне *ректресулт*<br/>
окне *бдравтаб*<br/>
окне *пптаржетбар*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividercalcfixedlayout"></a><a name="calcfixedlayout"></a> Кпанедивидер:: Калкфикседлайаут

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Параметры

окне *бстретч*<br/>
окне *бхорз*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividercheckvisibility"></a><a name="checkvisibility"></a> Кпанедивидер:: Чекквисибилити

```
virtual BOOL CheckVisibility();
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividercpanedivider"></a><a name="cpanedivider"></a> Кпанедивидер:: Кпанедивидер

```
CPaneDivider();

CPaneDivider(
    BOOL bDefaultSlider,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Параметры

окне *бдефаултслидер*<br/>
окне *ппарент*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividercreateex"></a><a name="createex"></a> Кпанедивидер:: Креатикс

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext);
```

### <a name="parameters"></a>Параметры

окне *двстиликс*<br/>
окне *двстиле*<br/>
[in] *rect*<br/>
окне *ппарентвнд*<br/>
окне *NID*<br/>
окне *пконтекст*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerdoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> Кпанедивидер::D Оесалловдининсертбефоре

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerdoescontainfloatingpane"></a><a name="doescontainfloatingpane"></a> Кпанедивидер::D Оесконтаинфлоатингпане

```
virtual BOOL DoesContainFloatingPane();
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerfindpanecontainer"></a><a name="findpanecontainer"></a> Кпанедивидер:: Финдпанеконтаинер

```
CPaneContainer* FindPaneContainer(
    CDockablePane* pBar,
    BOOL& bLeftBar);
```

### <a name="parameters"></a>Параметры

окне *пбар*<br/>
окне *блефтбар*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerfindtabbedpane"></a><a name="findtabbedpane"></a> Кпанедивидер:: Финдтаббедпане

```
CDockablePane* FindTabbedPane(UINT nID);
```

### <a name="parameters"></a>Параметры

окне *NID*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividergetdefaultwidth"></a><a name="getdefaultwidth"></a> Кпанедивидер:: Жетдефаултвидс

```
static int __stdcall GetDefaultWidth();
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividergetfirstpane"></a><a name="getfirstpane"></a> Кпанедивидер:: Жетфирстпане

```
const CBasePane* GetFirstPane() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividergetpanedividers"></a><a name="getpanedividers"></a> Кпанедивидер:: Жетпанедивидерс

Возвращает список разделителей областей, которые находятся в [классе кпанеконтаинер](../../mfc/reference/cpanecontainer-class.md). Этот метод должен вызываться только для разделителей панели по умолчанию.

```cpp
void GetPaneDividers(CObList& lstSliders);
```

### <a name="parameters"></a>Параметры

*лстслидерс*<br/>
заполняет Содержит список разделителей областей, которые находятся в контейнере панели.

### <a name="remarks"></a>Комментарии

Этот метод должен вызываться только для разделителей панели по умолчанию. Разделитель панели по умолчанию — это разделитель, который изменяет размер всего контейнера панели.

## <a name="cpanedividergetpanedividerstyle"></a><a name="getpanedividerstyle"></a> Кпанедивидер:: Жетпанедивидерстиле

```
DWORD GetPaneDividerStyle() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividergetpanes"></a><a name="getpanes"></a> Кпанедивидер:: выпанели

Возвращает список панелей, находящихся в [классе кпанеконтаинер](../../mfc/reference/cpanecontainer-class.md). Этот метод следует вызывать только для извлечения разделителей панели по умолчанию.

```cpp
void GetPanes(CObList& lstBars);
```

### <a name="parameters"></a>Параметры

*лстбарс*<br/>
заполняет Содержит список панелей, расположенных в контейнере панели.

### <a name="remarks"></a>Комментарии

Этот метод должен вызываться только для разделителей панели по умолчанию. Разделитель панели по умолчанию — это разделитель, который изменяет размер всего контейнера панели.

## <a name="cpanedividergetrootcontainerrect"></a><a name="getrootcontainerrect"></a> Кпанедивидер:: Жетрутконтаинеррект

```
CRect GetRootContainerRect();
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividergetwidth"></a><a name="getwidth"></a> Кпанедивидер:: Полуширинный

```
int GetWidth() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerinit"></a><a name="init"></a> Кпанедивидер:: init

```cpp
void Init(
    BOOL bDefaultSlider = FALSE,
    CWnd* pParent = NULL);
```

### <a name="parameters"></a>Параметры

окне *бдефаултслидер*<br/>
окне *ппарент*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerinsertpane"></a><a name="insertpane"></a> Кпанедивидер:: Инсертпане

```
virtual BOOL InsertPane(
    CDockablePane* pBarToInsert,
    CDockablePane* pTargetBar,
    DWORD dwAlignment,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>Параметры

окне *пбартоинсерт*<br/>
окне *птаржетбар*<br/>
окне *двалигнмент*<br/>
окне *лпрект*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerisautohidemode"></a><a name="isautohidemode"></a> Кпанедивидер:: Исаутохидемоде

```
BOOL IsAutoHideMode() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerisdefault"></a><a name="isdefault"></a> Кпанедивидер:: Default

```
BOOL IsDefault() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerishorizontal"></a><a name="ishorizontal"></a> Кпанедивидер:: по горизонтали

```
BOOL IsHorizontal() const;
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerm_ndefaultwidth"></a><a name="m_ndefaultwidth"></a> Кпанедивидер:: m_nDefaultWidth

Задает ширину по умолчанию (в пикселях) всех разделителей панели в приложении.

```
AFX_IMPORT_DATA static int m_nDefaultWidth;
```

## <a name="cpanedividermove"></a><a name="move"></a> Кпанедивидер:: Move

```
virtual void Move(
    CPoint& ptOffset,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>Параметры

окне *птоффсет*<br/>
окне *баджустлайаут*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerm_psliderrtc"></a><a name="m_psliderrtc"></a> Кпанедивидер:: m_pSliderRTC

Содержит указатель на сведения о классе времени выполнения для `CPaneDivider` объекта, производного от.

```
AFX_IMPORT_DATA static CRuntimeClass* m_pSliderRTC;
```

### <a name="remarks"></a>Комментарии

Задайте эту переменную-член, если вы создаете разделитель настраиваемой панели. Это позволяет платформе создавать разделитель панели при прорисовке панели.

### <a name="example"></a>Пример

В следующем примере показано, как задать `m_pSliderRTC` переменную члена:

```
class CMySplitter : public CPaneDivider
{
...
};

CPaneDivider::m_pSliderRTC = RUNTIME_CLASS(CMySpliter);
```

## <a name="cpanedividernotifyaboutrelease"></a><a name="notifyaboutrelease"></a> Кпанедивидер:: Нотифябаутрелеасе

```
virtual void NotifyAboutRelease();
```

### <a name="remarks"></a>Комментарии

## <a name="cpanedivideronshowpane"></a><a name="onshowpane"></a> Кпанедивидер:: Оншовпане

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>Параметры

окне *пбар*<br/>
окне *бшов*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerreleaseemptypanecontainers"></a><a name="releaseemptypanecontainers"></a> Кпанедивидер:: Релеасимптипанеконтаинерс

```cpp
void ReleaseEmptyPaneContainers();
```

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerremovepane"></a><a name="removepane"></a> Кпанедивидер:: Ремовепане

```
virtual void RemovePane(CDockablePane* pBar);
```

### <a name="parameters"></a>Параметры

окне *пбар*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerreplacepane"></a><a name="replacepane"></a> Кпанедивидер:: Реплацепане

```
virtual BOOL ReplacePane(
    CDockablePane* pBarToReplace,
    CDockablePane* pBarToReplaceWith);
```

### <a name="parameters"></a>Параметры

окне *пбартореплаце*<br/>
окне *пбартореплацевис*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerrepositionpanes"></a><a name="repositionpanes"></a> Кпанедивидер:: Репоситионпанес

```
virtual void RepositionPanes(
    CRect& rectNew,
    HDWP& hdwp);
```

### <a name="parameters"></a>Параметры

окне *ректнев*<br/>
окне *хдвп*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerserialize"></a><a name="serialize"></a> Кпанедивидер:: Serialize

```cpp
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Параметры

[in] *ar*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividershowwindow"></a><a name="showwindow"></a> Кпанедивидер:: ShowWindow

```cpp
void ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>Параметры

окне *нкмдшов*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerstorerecentdocksiteinfo"></a><a name="storerecentdocksiteinfo"></a> Кпанедивидер:: Сторерецентдоккситеинфо

```cpp
void StoreRecentDockSiteInfo(CDockablePane* pBar);
```

### <a name="parameters"></a>Параметры

окне *пбар*<br/>

### <a name="remarks"></a>Комментарии

## <a name="cpanedividerstorerecenttabrelatedinfo"></a><a name="storerecenttabrelatedinfo"></a> Кпанедивидер:: Сторереценттабрелатединфо

```cpp
void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>Параметры

окне *пдоккингбар*<br/>
окне *птаббедбар*<br/>

### <a name="remarks"></a>Комментарии

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CPaneContainerManager](../../mfc/reference/cpanecontainermanager-class.md)<br/>
[Класс Кпанеконтаинер](../../mfc/reference/cpanecontainer-class.md)<br/>
[Класс Кдоккингманажер](../../mfc/reference/cdockingmanager-class.md)<br/>
[Класс CBasePane](../../mfc/reference/cbasepane-class.md)
