---
description: 'Дополнительные сведения о: Кмфкфонтинфо Class'
title: Класс Кмфкфонтинфо
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: 0922e07f268509cd4b5552a6123d8d3465a426bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265419"
---
# <a name="cmfcfontinfo-class"></a>Класс Кмфкфонтинфо

`CMFCFontInfo`Класс описывает имя и другие атрибуты шрифта.

## <a name="syntax"></a>Синтаксис

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|`CMFCFontInfo`|Формирует объект `CMFCFontInfo`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Кмфкфонтинфо:: FullName](#getfullname)|Извлекает Объединенные имена шрифта и его набор символов (скрипт).|

### <a name="data-members"></a>Элементы данных

|Имя|Описание|
|----------|-----------------|
|[Кмфкфонтинфо:: m_nCharSet](#m_ncharset)|Значение, указывающее набор символов (скрипт), связанный со шрифтом.|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|Значение, указывающее шаг и семейство шрифта.|
|[Кмфкфонтинфо:: m_nType](#m_ntype)|Значение типа, указывающее тип шрифта.|
|[Кмфкфонтинфо:: m_strName](#m_strname)|Имя шрифта; Например, **Arial**.|
|[Кмфкфонтинфо:: m_strScript](#m_strscript)|Имя набора символов (скрипт), связанного со шрифтом.|

## <a name="remarks"></a>Комментарии

Можно присоединить `CMFCFontInfo` объект к элементу класса [класса кмфктулбарфонткомбобокс](../../mfc/reference/cmfctoolbarfontcombobox-class.md) . Вызовите метод [кмфктулбарфонткомбобокс:: жетфонтдеск](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc) , чтобы получить указатель на `CMFCFontInfo` объект.

## <a name="example"></a>Пример

В следующем примере показано, как использовать различные члены `CMFCFontInfo` класса. В примере показано, как получить `CMFCFontInfo` объект из `CMFCRibbonFontComboBox` и как получить доступ к его локальным переменным. Этот пример является частью [демонстрационного примера мсоффице 2007](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>Требования

**Заголовок:** афкстулбарфонткомбобокс. h

## <a name="cmfcfontinfocmfcfontinfo"></a><a name="cmfcfontinfo"></a> Кмфкфонтинфо:: Кмфкфонтинфо

Формирует объект `CMFCFontInfo`.

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>Параметры

*лпсзнаме*<br/>
окне Имя шрифта. Дополнительные сведения см. в описании `lfFaceName` члена структуры [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*лпсзскрипт*<br/>
окне Имя скрипта (кодировка) шрифта.

*Тип nChar*<br/>
окне Значение, указывающее кодировку (скрипт) шрифта. Дополнительные сведения см. в описании `lfCharSet` члена структуры [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*нпитчандфамили*<br/>
окне Значение, указывающее шаг и семейство шрифта. Дополнительные сведения см. в описании `lfPitchAndFamily` члена структуры [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) .

*nType*<br/>
окне Значение типа, указывающее тип шрифта. Этот параметр может быть побитовым сочетанием (или) DEVICE_FONTTYPE, RASTER_FONTTYPE и TRUETYPE_FONTTYPE.

*src*<br/>
окне Существующий `CMFCFontInfo` объект, члены которого используются для создания этого `CMFCFontInfo` объекта.

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

В этой *документации термин «кодировка» и* « *Скрипт* » используются взаимозаменяемыми. *Сценарий*, который также известен как система записи, представляет собой набор символов и правил для записи этих символов на одном или нескольких языках. Коллекция символов включает алфавит и знаки препинания, используемые в этом скрипте. Например, Латинский сценарий используется для английского языка, так как он просматривается в США, а его алфавит содержит символы от A до Z. `lfCharSet` Элемент структуры [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) задает кодировку. Например, значение ANSI_CHARSET указывает кодировку ANSI, которая включает алфавит для латиницы.

## <a name="cmfcfontinfogetfullname"></a><a name="getfullname"></a> Кмфкфонтинфо:: FullName

Извлекает Объединенные имена шрифта и его набор символов (скрипт).

```
CString GetFullName() const;
```

### <a name="return-value"></a>Возвращаемое значение

Строка, содержащая имя и скрипт шрифта.

### <a name="remarks"></a>Комментарии

Используйте этот метод, чтобы получить полное имя шрифта. Например, если шрифт имеет значение **Arial** , а сценарий шрифта имеет значение **Кирилл**, то этот метод возвращает «Arial (кириллица)».

## <a name="cmfcfontinfom_ncharset"></a><a name="m_ncharset"></a> Кмфкфонтинфо:: m_nCharSet

Значение, указывающее набор символов (скрипт), связанный со шрифтом.

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Комментарии

Дополнительные сведения см. в описании параметра *nchar* конструктора [Кмфкфонтинфо:: кмфкфонтинфо](#cmfcfontinfo) .

## <a name="cmfcfontinfom_npitchandfamily"></a><a name="m_npitchandfamily"></a> Кмфкфонтинфо:: m_nPitchAndFamily

Значение, указывающее шаг (размер точки) и семейство (например, Serif, Sans-Serif и моноширинная) шрифта.

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Комментарии

Дополнительные сведения см. в описании параметра *нпитчандфамили* конструктора [Кмфкфонтинфо:: кмфкфонтинфо](#cmfcfontinfo) .

## <a name="cmfcfontinfom_ntype"></a><a name="m_ntype"></a> Кмфкфонтинфо:: m_nType

Значение типа, указывающее тип шрифта.

```
const int m_nType;
```

### <a name="remarks"></a>Комментарии

Дополнительные сведения см. в описании параметра *nуведомления* конструктора [Кмфкфонтинфо:: кмфкфонтинфо](#cmfcfontinfo) .

## <a name="cmfcfontinfom_strname"></a><a name="m_strname"></a> Кмфкфонтинфо:: m_strName

Имя шрифта: например, **Arial**.

```
const CString m_strName;
```

### <a name="remarks"></a>Комментарии

Дополнительные сведения см. в описании параметра *лпсзнаме* конструктора [Кмфкфонтинфо:: кмфкфонтинфо](#cmfcfontinfo) .

## <a name="cmfcfontinfom_strscript"></a><a name="m_strscript"></a> Кмфкфонтинфо:: m_strScript

Имя набора символов (скрипт), связанного со шрифтом.

```
const CString m_strScript;
```

### <a name="remarks"></a>Комментарии

Дополнительные сведения см. в описании параметра *лпсзскрипт* конструктора [Кмфкфонтинфо:: кмфкфонтинфо](#cmfcfontinfo) .

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс Кмфктулбарфонткомбобокс](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[Класс Кмфктулбарфонтсизекомбобокс](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
