---
title: Класс CMFCRibbonFontComboBox
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 643e2a519c6d96c1070990dd86d571c5b7c09f95
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57288432"
---
# <a name="cmfcribbonfontcombobox-class"></a>Класс CMFCRibbonFontComboBox

Реализует поле со списком, содержащее список шрифтов. Необходимо задать поле со списком на панели ленты.

## <a name="syntax"></a>Синтаксис

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание:|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|Деструктор.|

### <a name="protected-constructors"></a>Защищенные конструкторы

|Имя|Описание:|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|Создает и инициализирует объект `CMFCRibbonFontComboBox`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[CMFCRibbonFontComboBox::BuildFonts](#buildfonts)|Заполняет поле со списком шрифтов на ленте на основе таких заданных параметров, как тип и семейство шрифтов, а также кодировка и шаг.|
|`CMFCRibbonFontComboBox::CreateObject`|Используется платформой для создания динамического экземпляра этого типа класса.|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|Возвращает указанный набор символов.|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|Возвращает типы шрифтов, отображаемые в поле со списком. Допустимые значения: DEVICE_FONTTYPE, RASTER_FONTTYPE и TRUETYPE_FONTTYPE, а также любые их битовые комбинации.|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|Возвращает шаг и семейство шрифтов, отображаемых в поле со списком.|
|`CMFCRibbonFontComboBox::GetThisClass`|Используется инфраструктурой, чтобы получить указатель на [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) объект, связанный с этим типом класса.|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|Заполняет поле со списком шрифтов на ленте на основе таких ранее заданных параметров, как тип и семейство шрифтов, а также кодировка и шаг.|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|Выбирает указанный шрифт в поле со списком.|

## <a name="remarks"></a>Примечания

После создания `CMFCRibbonFontComboBox` объекта, добавьте его на панель ленты, вызвав метод [CMFCRibbonPanel::Add](../../mfc/reference/cmfcribbonpanel-class.md#add).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** afxRibbonComboBox.h

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

Заполняет поле со списком на ленте с помощью шрифтов.

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>Параметры

*nFontType*<br/>
[in] Указывает тип шрифта шрифтов для добавления.

*nCharSet*<br/>
[in] Указывает кодировку шрифтов для добавления.

*nPitchAndFamily*<br/>
[in] Указывает шаг и семейство шрифтов для добавления.

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

Создает и инициализирует [CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md) объекта.

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>Параметры

*nID*<br/>
[in] Идентификатор команды, команды, которая выполняется, если пользователь выбирает элемент в поле со списком.

*nFontType*<br/>
[in] Указывает, какой шрифт типы для отображения в поле со списком. Допустимые значения: DEVICE_FONTTYPE, RASTER_FONTTYPE и TRUETYPE_FONTTYPE, а также любые их битовые комбинации.

*nCharSet*<br/>
[in] Фильтрует шрифты в поле со списком для тех, которые принадлежат указанную кодировку...

*nPitchAndFamily*<br/>
[in] Указывает шаг и семейство шрифтов, отображаемых в поле со списком.

*nWidth*<br/>
[in] Задает ширину в пикселях, в поле со списком.

### <a name="remarks"></a>Примечания

Дополнительные сведения о возможных *nFontType* значения параметров, см. в разделе [EnumFontFamProc](https://msdn.microsoft.com/library/windows/desktop/dd162621) в документации по Windows SDK.

Дополнительные сведения о допустимых кодировок, которые могут быть назначены *nCharSet*и их допустимых значений, которые могут быть назначены *nPitchAndFamily*, см. в разделе [LOGFONT](/windows/desktop/api/wingdi/ns-wingdi-taglogfonta) в Документации по пакету Windows SDK.

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

Дополнительные сведения см. в исходном коде, расположенном в папке **VC\\atlmfc\\src\\mfc** каталога установки Visual Studio.

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>Параметры

[in] *iIndex*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Примечания

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

Заполняет поле со списком на ленте с шрифтами типа ранее заданного шрифта, набор символов и шаг и семейство.

```
void RebuildFonts();
```

### <a name="remarks"></a>Примечания

Можно указать тип шрифта, набор символов, и шаг и семейство шрифтов для включения в поле со списком шрифта ленты в [конструктор](#cmfcribbonfontcombobox) для этого класса или путем вызова [CMFCRibbonFontComboBox::BuildFonts](#buildfonts).

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

Выбирает указанный шрифт в поле со списком.

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>Параметры

"lpszName * имя шрифта для выбора.

*nCharSet*<br/>
Указывает кодировку для выбранного шрифта.

*bExact*<br/>
Значение TRUE, чтобы указать, что кодировка должна соответствовать при выборе шрифта; Значение FALSE, чтобы указать, что набор символов можно игнорировать при выборе шрифта.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если указанный шрифт был найден и выбран; в противном случае — нуль.

### <a name="remarks"></a>Примечания

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

Возвращает указанный набор символов.

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>Возвращаемое значение

Набор символов (см. в разделе LOGFONT документации по пакету Windows SDK).

### <a name="remarks"></a>Примечания

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

Возвращает типы шрифтов, отображаемые в поле со списком. Допустимые значения: DEVICE_FONTTYPE, RASTER_FONTTYPE и TRUETYPE_FONTTYPE, а также любые их битовые комбинации.

```
int GetFontType() const;
```

### <a name="return-value"></a>Возвращаемое значение

Типы шрифтов (см. в разделе EnumFontFamProc в документации по Windows SDK).

### <a name="remarks"></a>Примечания

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

Возвращает шаг и семейство шрифтов, отображаемых в поле со списком.

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>Возвращаемое значение

Шаг и семейство (см. в разделе LOGFONT документации по пакету Windows SDK).

### <a name="remarks"></a>Примечания

## <a name="see-also"></a>См. также

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)
