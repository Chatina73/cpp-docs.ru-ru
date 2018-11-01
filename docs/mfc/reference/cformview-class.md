---
title: Класс CFormView
ms.date: 11/04/2016
f1_keywords:
- CFormView
- AFXEXT/CFormView
- AFXEXT/CFormView::CFormView
- AFXEXT/CFormView::IsInitDlgCompleted
helpviewer_keywords:
- CFormView [MFC], CFormView
- CFormView [MFC], IsInitDlgCompleted
ms.assetid: a99ec313-36f0-4f28-9d2b-de11de14ac19
ms.openlocfilehash: 37ae7ca2efeb579cba388e22cf0fe450a068e721
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651962"
---
# <a name="cformview-class"></a>Класс CFormView

Базовый класс, используемый для представлений формы.

## <a name="syntax"></a>Синтаксис

```
class CFormView : public CScrollView
```

## <a name="members"></a>Участники

### <a name="protected-constructors"></a>Защищенные конструкторы

|Имя|Описание|
|----------|-----------------|
|[CFormView::CFormView](#cformview)|Создает объект `CFormView`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CFormView::IsInitDlgCompleted](#isinitdlgcompleted)|Используется для синхронизации во время инициализации.|

## <a name="remarks"></a>Примечания

По сути, представление формы — это представление, содержащее элементы управления. Эти элементы управления располагаются на основе ресурса шаблона диалогового окна. Используйте `CFormView`, если вы хотите задействовать формы в своем приложении. Эти представления поддерживают прокрутку, при необходимости, с помощью [CScrollView](../../mfc/reference/cscrollview-class.md) функциональные возможности.

Когда вы будете [Создание приложения на основе форм](../../mfc/reference/creating-a-forms-based-mfc-application.md), класс представления может быть основан на `CFormView`, делая приложение на основе форм.

Вы также можете вставить новые [разделы с описанием форм](../../mfc/form-views-mfc.md) в документ представление-приложения. Даже если ваше приложение изначально не поддерживает формы, при вставке новой формы Visual C++ обеспечит их поддержку.

Приложения на основе форм рекомендуется создавать с помощью мастера приложений MFC и команды Add Class. Если вам нужно создать приложение на основе форм без использования этих методов, см. в разделе [Создание приложения на основе форм](../../mfc/reference/creating-a-forms-based-mfc-application.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

`CFormView`

## <a name="requirements"></a>Требования

**Заголовок:** afxext.h

##  <a name="cformview"></a>  CFormView::CFormView

Создает объект `CFormView`.

```
CFormView(LPCTSTR lpszTemplateName);
CFormView(UINT nIDTemplate);
```

### <a name="parameters"></a>Параметры

*lpszTemplateName*<br/>
Содержащий заканчивающуюся нулем строку, которая является именем ресурса шаблона диалогового окна.

*nIDTemplate*<br/>
Содержит идентификатор ресурса шаблона диалогового окна.

### <a name="remarks"></a>Примечания

При создании объекта типа производным от `CFormView`, вызвать один из конструкторов для создания объекта view и определения ресурса диалогового окна, на котором основано представление. Вы можете определить ресурс, либо по имени (pass строку в качестве аргумента в конструктор), либо по его Идентификатору (pass целое число без знака в качестве аргумента).

Представление формы окна и дочерние элементы управления не создаются до `CWnd::Create` вызывается. `CWnd::Create` вызывается платформой как часть документа и представления процесс создания, которое определяется с помощью шаблона документа.

> [!NOTE]
>  Производный класс *необходимо* предоставить собственный конструктор. В конструкторе, вызвать конструктор `CFormView::CFormView`, имя ресурса или идентификатор в качестве аргумента, как показано в предыдущем Общие сведения о классе.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDocView#90](../../mfc/codesnippet/cpp/cformview-class_1.h)]

[!code-cpp[NVC_MFCDocView#91](../../mfc/codesnippet/cpp/cformview-class_2.cpp)]

##  <a name="isinitdlgcompleted"></a>  CFormView::IsInitDlgCompleted

Используется MFC, чтобы убедиться, что инициализация завершена до выполнения других операций.

```
BOOL IsInitDlgCompleted() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если инициализация для этого диалогового окна была завершена.

## <a name="see-also"></a>См. также

[Пример MFC: SNAPVW](../../visual-cpp-samples.md)<br/>
[Пример MFC: VIEWEX](../../visual-cpp-samples.md)<br/>
[Класс CScrollView](../../mfc/reference/cscrollview-class.md)<br/>
[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Класс CDialog](../../mfc/reference/cdialog-class.md)<br/>
[Класс CScrollView](../../mfc/reference/cscrollview-class.md)
