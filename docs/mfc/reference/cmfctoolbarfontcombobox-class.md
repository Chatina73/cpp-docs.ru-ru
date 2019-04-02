---
title: Класс CMFCToolBarFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 89767a3ed6880703c3c754700ea5669c0cc183e5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779200"
---
# <a name="cmfctoolbarfontcombobox-class"></a>Класс CMFCToolBarFontComboBox

Кнопка панели инструментов, которая содержит поле со списком, позволяющий пользователю выбрать шрифт из списка системных шрифтов.

## <a name="syntax"></a>Синтаксис

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>Участники

### <a name="protected-constructors"></a>Защищенные конструкторы

|name|Описание|
|----------|-----------------|
|[CMFCToolBarFontComboBox::CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|Создает объект `CMFCToolBarFontComboBox`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|Возвращает указатель на `CMFCFontInfo` объект для указанного индекса в поле со списком.|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|Выбирает шрифт в поле со списком шрифта в соответствии с, либо имя шрифта или префикс и набор символов шрифта.|

### <a name="data-members"></a>Элементы данных

[CMFCToolBarFontComboBox::m_nFontHeight](#m_nfontheight)<br/>
Высота символов в поле со списком шрифта.

## <a name="remarks"></a>Примечания

Чтобы добавить кнопку поле со списком шрифтов на панель инструментов, выполните следующие действия:

1. Зарезервируйте идентификатор фиктивный ресурс для кнопки в панели инструментов к родительскому ресурсу.

1. Создать `CMFCToolBarFontComboBox` объекта.

1. В обработчике сообщений, который обрабатывает сообщение AFX_WM_RESETTOOLBAR, заменить исходный кнопку "Создать поле" поле со списком с помощью [CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

1. Синхронизировать шрифта, выбранного в поле со списком с помощью шрифта в документе с помощью [CMFCToolBarFontComboBox::SetFont](#setfont) метод.

Чтобы синхронизировать шрифта документа с помощью шрифта, выбранного в поле со списком, используйте [CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc) метод для получения атрибутов выбранного шрифта и использовать эти атрибуты для создания [ Класс CFont](../../mfc/reference/cfont-class.md) объекта.

Кнопка поле со списком шрифта вызывает функцию Win32 [EnumFontFamiliesEx](/windows/desktop/api/wingdi/nf-wingdi-enumfontfamiliesexa) для определения шрифтов экрана и принтера, доступных в системе.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** afxtoolbarfontcombobox.h

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

Создает [CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md) объекта.

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>Параметры

*uiID*<br/>
[in] Идентификатор команды поля со списком.

*iImage*<br/>
[in] Отсчитываемый от нуля индекс изображения панели инструментов. Образ находится в [класс CMFCToolBarImages](../../mfc/reference/cmfctoolbarimages-class.md) объекта, [класс CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md) класс поддерживает.

*nFontType*<br/>
[in] Типы шрифтов, которые содержит поля со списком. Этот параметр может быть собой комбинацию (логическое OR) из следующих значений:

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
[in] Если задано DEFAULT_CHARSET, поле со списком содержит все уникальность имен шрифтов во всех наборах символов. (При наличии двух шрифтов с одинаковым именем, поле со списком содержит один из них.) Если задано значение допустимым символом, поле со списком содержит только шрифты в набор знаков. См. в разделе [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) список возможных символов задает.

*dwStyle*<br/>
[in] Стиль поля со списком. (см. в разделе [поле со списком стилей](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles))

*iWidth*<br/>
[in] Ширина в пикселях элемента управления.

*nPitchAndFamily*<br/>
[in] Если задано DEFAULT_PITCH, поле со списком содержит шрифты, независимо от того, тона. Если значение FIXED_PITCH или VARIABLE_PITCH, поле со списком содержит только шрифты с этим типом тона. Фильтрация на основе семейства шрифтов в настоящее время не поддерживается.

*pLstFontsExternal*<br/>
[out] Указатель на [класс CObList](../../mfc/reference/coblist-class.md) объект, который хранит доступные шрифты.

### <a name="remarks"></a>Примечания

Как правило `CMFCToolBarFontComboBox` объектов сохранить список доступных шрифтов в одну общую `CObList` объекта. Если использовать вторую перегрузку конструктора и указать допустимый указатель на *pLstFontsExternal*, в котором `CMFCToolBarFontComboBox` объекта вместо заполнит `CObList` , *pLstFontsExternal* Указывает на доступные шрифты.

### <a name="example"></a>Пример

В следующем примере демонстрируется создание `CMFCToolBarFontComboBox` объекта. Этот фрагмент кода входит в состав [примера Word Pad](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

Возвращает указатель на `CMFCFontInfo` объект для указанного индекса в поле со списком.

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>Параметры

*iIndex*<br/>
[in] Указывает отсчитываемый от нуля индекс элемента поля со списком.

### <a name="return-value"></a>Возвращаемое значение

Указатель на объект `CMFCFontInfo` . Если *iIndex* не содержит допустимый элемент индекса, возвращаемое значение равно NULL.

##  <a name="m_nfontheight"></a>  CMFCToolBarFontComboBox::m_nFontHeight

Указывает высоту в пикселях символов в поле со списком шрифта, если поле со списком имеет владельца, стиль рисования.

```
static int m_nFontHeight
```

### <a name="remarks"></a>Примечания

Если `m_nFontHeight` переменной равно 0, высота рассчитывается автоматически в соответствии с шрифт по умолчанию в поле со списком. Высота относится и восхождение символов превышает базовые показатели и спуск символов под базовых показателей.

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

Выбирает шрифт в поле со списком шрифта в соответствии с имя шрифта и символ набора, указываются в параметрах.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>Параметры

*lpszName*<br/>
[in] Задает имя шрифта или префикс.

*nCharSet*<br/>
[in] Указывает кодировку.

*bExact*<br/>
[in] Указывает, является ли *lpszName* содержит имя шрифта или префикс шрифта.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если шрифт был выбран успешно; в противном случае 0.

### <a name="remarks"></a>Примечания

Если *bExact* имеет значение TRUE, этот метод выбирает шрифт, который точно соответствует имени, которая была указана как *lpszName*. Если *bExact* имеет значение FALSE, этот метод, выбирает шрифт, который начинается с текста, согласно *lpszName* и использует набор символов, которая была указана как *nCharSet*. Если *nCharSet* задается для DEFAULT_CHARSET, будет набор символов, игнорируются и только *lpszName* будет использоваться для выбора шрифта.

## <a name="see-also"></a>См. также

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)<br/>
[Класс CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Класс CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[Класс CMFCFontInfo](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Пошаговое руководство: Размещение элементов управления на панели инструментов](../../mfc/walkthrough-putting-controls-on-toolbars.md)
