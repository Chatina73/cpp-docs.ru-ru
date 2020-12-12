---
description: 'Дополнительные сведения: структура AFX_GLOBAL_DATA'
title: AFX_GLOBAL_DATA - структура
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::InitD2D
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: 3f7bb7bfeb4e5985d558211450755972c0f55812
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322857"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA - структура

Структура `AFX_GLOBAL_DATA` содержит поля и методы, используемые для управления платформой или настройки внешнего вида и поведения приложения.

## <a name="syntax"></a>Синтаксис

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Создает структуру `AFX_GLOBAL_DATA` .|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Деструктор.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Освобождает ресурсы, выделенные платформой, например кисти, шрифты и библиотеки DLL.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Создает преобразование вращения, осуществляющее поворот на указанный угол вокруг указанной точки.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Рисует фон родительского объекта элемента управления в заданной области.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Рисует заданный текст в визуальном стиле указанной темы.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Удаляет заданную пару тегов XML из указанного буфера.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Получает текущий цвет из указанного элемента пользовательского интерфейса.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Получает указатель на интерфейс `ID2D1Factory` , хранящийся в глобальных данных. Если интерфейс не инициализирован, он создается с параметрами по умолчанию.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Извлекает стандартный курсор в виде руки, идентификатор которого равен `IDC_HAND`.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Создает и сохраняет в глобальных данных указатель на интерфейс ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Создает и сохраняет в глобальных данных указатель на интерфейс ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Получает метрики, связанные с неклиентской областью несвернутого окна.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Определяет положения автоматически скрываемых панелей оболочки.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Получает высоту символов текста в текущем шрифте.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Получает указатель на интерфейс `IWICImagingFactory` , хранящийся в глобальных данных. Если интерфейс не инициализирован, он создается с параметрами по умолчанию.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Получает указатель на интерфейс `IDWriteFactory` , хранящийся в глобальных данных. Если интерфейс не инициализирован, он создается с параметрами по умолчанию.|
|[AFX_GLOBAL_DATA::InitD2D](#initd2d)|Инициализирует фабрики `D2D`, `DirectWrite`и `WIC` . Данный метод следует вызывать до инициализации основного окна.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Указывает, поддерживаются ли стандартные 32-разрядные значки.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Определяет, был ли инициализирован `D2D` .|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Предоставляет простой способ для вызова метода [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) Windows.|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Указывает, отображаются ли сейчас изображения с высокой контрастностью.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Определяет текущее состояние для анимации меню рабочего стола и функций автоматического скрытия панели задач.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Регистрирует указанный класс окна MFC.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Освобождает интерфейсы, полученные через методы GetITaskbarList и GetITaskbarList3.|
|[AFX_GLOBAL_DATA::Resume](#resume)|Повторно инициализирует внутренние указатели функции, которые обращаются к методам, поддерживающим [темы и стили оформления](/windows/win32/Controls/visual-styles-overview)Windows.|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Предоставляет простой способ для вызова метода [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) Windows.|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Создает указанный логический шрифт.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Создает и инициализирует объект элемента оболочки из имени синтаксического анализа.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Повторно инициализирует логические шрифты, используемые платформой.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Инициализирует цвета, глубину цвета, кисти, перья и изображения, используемые платформой.|

### <a name="protected-methods"></a>Защищенные методы

|Имя|Описание|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Включает или отключает поддержку Microsoft Active Accessibility. Active Accessibility предлагает надежные методы для предоставления информации об элементах пользовательского интерфейса.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Указывает, включена ли поддержка Microsoft Active Accessibility.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Указывает, поддерживает ли операционная система многослойные окна.|

### <a name="data-members"></a>Элементы данных

|Имя|Описание|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Указывает, поддерживает ли текущая операционная система альфа-смешение.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Указывает, выполняется ли приложение в ОС Windows 7 или более поздней версии.|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Задает цвет градиента для активного заголовка. Обычно используется для закрепляемых панелей.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Задает цвет градиента для неактивного заголовка. Обычно используется для закрепляемых панелей.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Указывает, использует ли платформа стандартные 32-разрядные цветные значки или значки более низкого разрешения.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Указывает, используется ли системный шрифт для меню, панелей инструментов и лент.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Сохраняет дескриптор курсора в виде ладони.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Сохраняет дескриптор для курсора растяжения по горизонтали.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Сохраняет дескриптор для курсора растяжения по вертикали.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Сохраняет дескриптор для значка средства.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Указывает смещение от самой левой автоматически скрываемой панели инструментов до левой части панели стыковки.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Указывает интервал между автоматически скрываемыми панелями инструментов.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Указывает толщину кадра перетаскивания, который используется для взаимодействия в закрепленном состоянии.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Указывает толщину кадра перетаскивания, который используется для взаимодействия в плавающем состоянии.|

### <a name="remarks"></a>Комментарии

Большинство данных в структуре `AFX_GLOBAL_DATA` инициализируется при запуске приложения.

### <a name="inheritance-hierarchy"></a>Иерархия наследования

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Требования

**Заголовок:** afxglobals.h

## <a name="afx_global_databisosalphablendingsupport"></a><a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA:: Бисосалфаблендингсуппорт

Указывает, поддерживает ли операционная система альфа-смешение.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Комментарии

Значение TRUE указывает, что альфа-смешение поддерживается; в противном случае — значение FALSE.

## <a name="afx_global_datacleanup"></a><a name="cleanup"></a> AFX_GLOBAL_DATA:: CleanUp

Освобождает ресурсы, выделенные платформой, например кисти, шрифты и библиотеки DLL.

```cpp
void CleanUp();
```

## <a name="afx_global_datad2d1makerotatematrix"></a><a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D 2D1MakeRotateMatrix

Создает преобразование вращения, осуществляющее поворот на указанный угол вокруг указанной точки.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Параметры

*под*<br/>
Угол поворота по часовой стрелке в градусах.

*Center*<br/>
Точка, о которой нужно повернуть.

*таблицу*<br/>
При возврате из этого метода содержит новое преобразование поворота. Для этого параметра необходимо выделить хранилище.

### <a name="return-value"></a>Возвращаемое значение

Возвращает S_OK в случае успеха или значение ошибки в противном случае.

## <a name="afx_global_datadrawparentbackground"></a><a name="drawparentbackground"></a> AFX_GLOBAL_DATA::D Равпарентбаккграунд

Рисует фон родительского объекта элемента управления в заданной области.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Параметры

*Приводится*<br/>
окне Указатель на окно элемента управления.

*Хозяин*<br/>
окне Указатель на контекст устройства.

*лпрект*<br/>
окне Указатель на прямоугольник, ограничивающий область для рисования. Значение по умолчанию — NULL.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

## <a name="afx_global_datadrawtextonglass"></a><a name="drawtextonglass"></a> AFX_GLOBAL_DATA::D Равтекстонгласс

Рисует заданный текст в визуальном стиле указанной темы.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Параметры

*хсеме*<br/>
окне Указатель на данные темы окна или значение NULL. Платформа использует указанную тему для отрисовки текста, если этот параметр не имеет значение NULL и темы поддерживаются. В противном случае платформа не использует тему для рисования текста.

Используйте метод [опенсемедата](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) для создания хсеме.

*Хозяин*<br/>
окне Указатель на контекст устройства.

*ипартид*<br/>
окне Элемент управления, имеющий нужный внешний вид текста. Дополнительные сведения см. в столбце "Части" в таблице [Части и состояния](/windows/win32/controls/parts-and-states). Если это значение равно 0, текст рисуется с помощью шрифта по умолчанию или шрифта, выбранного в контексте устройства.

*истатеид*<br/>
окне Состояние элемента управления с требуемым внешним видом текста. Дополнительные сведения см. в столбце "Состояния" в таблице [Части и состояния](/windows/win32/controls/parts-and-states).

*стртекст*<br/>
окне Текст для рисования.

*rect*<br/>
окне Граница области, в которой рисуется указанный текст.

*dwFlags*<br/>
окне Побитовое сочетание (или) флагов, определяющих внешний вид указанного текста.

Если параметр *хсеме* имеет значение `NULL` или если темы не поддерживаются и не включены, параметр *нформат* метода [CDC::D равтекст](../../mfc/reference/cdc-class.md#drawtext) описывает допустимые флаги. Если темы поддерживаются, параметр *dwFlags* метода [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) описывает допустимые флаги.

*нгловсизе*<br/>
окне Размер эффект свечения, который рисуется на фоне перед рисованием указанного текста. Значение по умолчанию — 0.

*clrText*<br/>
окне Цвет, в котором рисуется указанный текст. Значением по умолчанию является цвет по умолчанию.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если тема используется для рисования указанного текста; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Тема определяет визуальный стиль приложения. Тема не используется для отрисовки текста, если параметр *хсеме* имеет значение null или если метод [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) не поддерживается, или если [Диспетчер окон рабочего стола](/windows/win32/dwm/dwm-overview) (DWM) отключена.

## <a name="afx_global_dataenableaccessibilitysupport"></a><a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA:: Енаблеакцессибилитисуппорт

Включает или отключает поддержку Microsoft Active Accessibility.

```cpp
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Параметры

*bEnable*<br/>
окне Значение TRUE, чтобы включить поддержку специальных возможностей; Значение FALSE, чтобы отключить поддержку специальных возможностей. Значение по умолчанию — TRUE.

### <a name="remarks"></a>Комментарии

Active Accessibility — это технология на основе COM, которая улучшает работу программ и операционной системы Windows вместе с продуктами вспомогательных технологий. Он предоставляет надежные методы для предоставления сведений об элементах пользовательского интерфейса. Однако теперь доступна более новая модель доступности, называемая Microsoft UI Automation. Сравнение двух технологий см. в разделе [Модель автоматизации пользовательского интерфейса и Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Используйте метод [AFX_GLOBAL_DATA:: исакцессибилитисуппорт](#isaccessibilitysupport) , чтобы определить, включена ли поддержка Microsoft Active Accessibility.

## <a name="afx_global_dataexcludetag"></a><a name="excludetag"></a> AFX_GLOBAL_DATA:: Ексклудетаг

Удаляет заданную пару тегов XML из указанного буфера.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Параметры

*стрбуффер*<br/>
окне Буфер текста.

*лпсзтаг*<br/>
окне Имя пары открывающих и закрывающих XML-тегов.

*стртаг*<br/>
заполняет При возврате из этого метода параметр *стртаг* содержит текст между открывающим и ЗАКРЫВАЮЩИМ XML-тегами, которые именуются с помощью параметра *лпсзтаг* . Все начальные и конечные пробелы удаляются из результата.

*бисчарслист*<br/>
окне Значение TRUE, чтобы преобразовать символы для escape-символов в параметре *стртаг* в фактические escape-символы; Значение FALSE, чтобы не выполнять преобразование. Значение по умолчанию — FALSE. Дополнительные сведения см. в подразделе "Примечания".

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Пара XML-тегов состоит из именованных открывающих и закрывающих тегов, которые указывают начало и конец выполнения текста в указанном буфере. Параметр *стрбуффер* задает буфер, а параметр *лпсзтаг* указывает имя XML-тегов.

Используйте символы в следующей таблице для кодирования набора escape-символов в указанном буфере. Укажите значение TRUE для параметра *бисчарслист* , чтобы преобразовать символы в параметре *стртаг* в фактические escape-символы. В следующей таблице используется макрос [_T ()](../../c-runtime-library/data-type-mappings.md) для указания строк символов и escape-символов.

|Символ|Escape-символ|
|------------|----------------------|
|_T (" \\ \t")|_T ("\t")|
|_T (" \\ \n")|_T ("\n")|
|_T (" \\ \r")|_T ("\r")|
|_T (" \\ \b")|_T ("\b")|
|_T ("LT")|_T (" \< ")|
|_T ("GT")|_T (">")|
|_T ("AMP")|_T ("&")|

## <a name="afx_global_datagetcolor"></a><a name="getcolor"></a> AFX_GLOBAL_DATA:: "Color"

Получает текущий цвет из указанного элемента пользовательского интерфейса.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Параметры

*нколор*<br/>
окне Значение типа, указывающее элемент пользовательского интерфейса, цвет которого извлекается. Список допустимых значений см. в описании параметра *ниндекс* метода [жетсисколор](/windows/win32/api/winuser/nf-winuser-getsyscolor) .

### <a name="return-value"></a>Возвращаемое значение

Значение цвета RGB указанного элемента пользовательского интерфейса. Дополнительные сведения см. в подразделе "Примечания".

### <a name="remarks"></a>Комментарии

Если параметр *нколор* выходит за пределы диапазона, возвращаемое значение равно нулю. Поскольку ноль также является допустимым значением RGB, нельзя использовать этот метод, чтобы определить, поддерживается ли системный цвет текущей операционной системой. Вместо этого используйте метод [жетсисколорбруш](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) , который возвращает значение null, если цвет не поддерживается.

## <a name="afx_global_datagetdirect2dfactory"></a><a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA:: GetDirect2dFactory

Возвращает указатель на интерфейс ID2D1Factory, хранящийся в глобальных данных. Если интерфейс не инициализирован, он создается с параметрами по умолчанию.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на интерфейс ID2D1Factory в случае, если создание фабрики завершается успешно, или значение NULL, если создание завершается ошибкой, или текущая система операций не поддерживает D2D.

## <a name="afx_global_datagethandcursor"></a><a name="gethandcursor"></a> AFX_GLOBAL_DATA:: Жесандкурсор

Извлекает стандартный курсор, напоминающий руки, чей идентификатор IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель курсора в виде руки.

## <a name="afx_global_datagetnonclientmetrics"></a><a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA:: Жетнонклиентметрикс

Получает метрики, связанные с неклиентской областью несвернутого окна.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Параметры

*контактные*<br/>
[вход, выход] Структура [нонклиентметрикс](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) , содержащая масштабируемые метрики, связанные с неклиентской областью неуменьшенного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод завершился с ошибкой; в противном случае — значение FALSE.

## <a name="afx_global_datagettextheight"></a><a name="gettextheight"></a> AFX_GLOBAL_DATA:: Жеттекссеигхт

Получает высоту символов текста в текущем шрифте.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Параметры

*бхорз*<br/>
окне Значение TRUE, чтобы получить высоту символов, когда текст выполняется горизонтально; Значение FALSE, чтобы получить высоту символов, если текст выполняется вертикально. Значение по умолчанию — TRUE.

### <a name="return-value"></a>Возвращаемое значение

Высота текущего шрифта, измеряемая от его Ascend до его нижнего края.

## <a name="afx_global_datagetwicfactory"></a><a name="getwicfactory"></a> AFX_GLOBAL_DATA:: Жетвикфактори

Возвращает указатель на интерфейс IWICImagingFactory, хранящийся в глобальных данных. Если интерфейс не инициализирован, он создается с параметрами по умолчанию.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на интерфейс IWICImagingFactory в случае, если создание фабрики завершается успешно, или значение NULL, если создание завершается ошибкой или текущая система операций не поддерживает WIC.

## <a name="afx_global_datagetwritefactory"></a><a name="getwritefactory"></a> AFX_GLOBAL_DATA:: Жетвритефактори

Возвращает указатель на интерфейс Идвритефактори, хранящийся в глобальных данных. Если интерфейс не инициализирован, он создается с параметрами по умолчанию.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на интерфейс Идвритефактори в случае, если создание фабрики завершается успешно, или значение NULL, если создание завершается ошибкой или текущая система операций не поддерживает DirectWrite.

## <a name="afx_global_datainitd2d"></a><a name="initd2d"></a> AFX_GLOBAL_DATA:: InitD2D

Инициализирует фабрики D2D, DirectWrite и WIC. Данный метод следует вызывать до инициализации основного окна.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Параметры

*d2dFactoryType*<br/>
Потоковая модель фабрики D2D и ресурсов, которые она создает.

*вритефакторитипе*<br/>
Значение типа, указывающее, будет ли объект фабрики записи общим или изолированным.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение TRUE, если фабрики были интилализрд, и FALSE — в противном случае

## <a name="afx_global_datais32biticons"></a><a name="is32biticons"></a> AFX_GLOBAL_DATA:: Is32BitIcons

Указывает, поддерживаются ли стандартные 32-разрядные значки.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если поддерживаются стандартные 32-разрядные значки; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Этот метод возвращает значение TRUE, если платформа поддерживает 32-разрядные встроенные значки, и, если операционная система поддерживает 16 бит на пиксель или более, и если изображения не отображаются в высокой контрастности.

## <a name="afx_global_dataisaccessibilitysupport"></a><a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA:: Исакцессибилитисуппорт

Указывает, включена ли поддержка Microsoft Active Accessibility.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если включена поддержка специальных возможностей; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Microsoft Active Accessibility было предыдущим решением для обеспечения доступности приложений. Автоматизация пользовательского интерфейса Майкрософт — это новая модель специальных возможностей для Microsoft Windows, которая предназначена для удовлетворения потребностей программных продуктов и средств автоматизированного тестирования.

Используйте метод [AFX_GLOBAL_DATA:: енаблеакцессибилитисуппорт](#enableaccessibilitysupport) , чтобы включить или отключить поддержку Active Accessibility.

## <a name="afx_global_dataisd2dinitialized"></a><a name="isd2dinitialized"></a> AFX_GLOBAL_DATA:: IsD2DInitialized

Определяет, инициализирован ли D2D

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если был инициализирован D2D; в противном случае — FALSE.

## <a name="afx_global_dataisdwmcompositionenabled"></a><a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA:: Исдвмкомпоситионенаблед

Предоставляет простой способ для вызова метода [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) Windows.

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если композиция [Диспетчер окон рабочего стола](/windows/win32/dwm/dwm-overview) (DWM) включена; в противном случае — значение FALSE.

## <a name="afx_global_dataishighcontrastmode"></a><a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA:: Ишигхконтрастмоде

Указывает, отображаются ли сейчас изображения с высокой контрастностью.

```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если изображения в данный момент отображаются в режиме высокой контрастности (черный или белый); в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

В режиме «черновая контрастность» края, направленные на свет, являются белыми, а фон — черным. В режиме высокой контрастности края, направленные на свет, являются черными, а фон — белым.

## <a name="afx_global_dataiswindowslayersupportavailable"></a><a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA:: Исвиндовслайерсуппортаваилабле

Указывает, поддерживает ли операционная система многослойные окна.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если многослойные окна поддерживаются; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Если многоуровневые окна поддерживаются, то в маркерах *смарт-закрепления* используются многоуровневые окна.

## <a name="afx_global_datam_busebuiltin32biticons"></a><a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA:: m_bUseBuiltIn32BitIcons

Указывает, использует ли платформа стандартные 32-разрядные цветные значки или значки более низкого разрешения.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Комментарии

Значение TRUE указывает, что платформа использует 32-разрядные цветные значки; Значение FALSE задает значки с низким разрешением. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`Конструктор инициализирует этот элемент ЗНАЧЕНИЕМ true.

Этот элемент должен быть задан при запуске приложения.

## <a name="afx_global_datam_busesystemfont"></a><a name="m_busesystemfont"></a> AFX_GLOBAL_DATA:: m_bUseSystemFont

Указывает, используется ли системный шрифт для меню, панелей инструментов и лент.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Комментарии

Значение TRUE указывает, что используется системный шрифт; в противном случае — значение FALSE. `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`Конструктор инициализирует этот элемент ЗНАЧЕНИЕМ false.

Тестирование этого элемента не является единственным способом определить используемый шрифт для платформы. `AFX_GLOBAL_DATA::UpdateFonts`Метод также проверяет значения по умолчанию и альтернативные шрифты, чтобы определить, какие визуальные стили доступны для применения к меню, панелям инструментов и лентам.

## <a name="afx_global_datam_hcurhand"></a><a name="m_hcurhand"></a> AFX_GLOBAL_DATA:: m_hcurHand

Сохраняет дескриптор курсора в виде ладони.

```
HCURSOR m_hcurHand;
```

## <a name="afx_global_datam_hcurstretch"></a><a name="m_hcurstretch"></a> AFX_GLOBAL_DATA:: m_hcurStretch

Сохраняет дескриптор для курсора растяжения по горизонтали.

```
HCURSOR m_hcurStretch;
```

## <a name="afx_global_datam_hcurstretchvert"></a><a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA:: m_hcurStretchVert

Сохраняет дескриптор для курсора растяжения по вертикали.

```
HCURSOR m_hcurStretchVert;
```

## <a name="afx_global_datam_hicontool"></a><a name="m_hicontool"></a> AFX_GLOBAL_DATA:: m_hiconTool

Сохраняет дескриптор для значка средства.

```
HICON m_hiconTool;
```

## <a name="afx_global_datam_nautohidetoolbarmargin"></a><a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA:: m_nAutoHideToolBarMargin

Задает смещение от самой левой панели инструментов автоскрытия к левой стороне панели закрепления.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Комментарии

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`Конструктор инициализирует этот элемент до 4 пикселей.

## <a name="afx_global_datam_nautohidetoolbarspacing"></a><a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA:: m_nAutoHideToolBarSpacing

Указывает интервал между автоматически скрываемыми панелями инструментов.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Комментарии

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`Конструктор инициализирует этот элемент до 14 пикселей.

## <a name="afx_global_datam_ndragframethicknessdock"></a><a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA:: m_nDragFrameThicknessDock

Задает толщину рамки перетаскивания, используемой для указания закрепленного состояния.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Комментарии

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`Конструктор инициализирует этот элемент до 3 пикселей.

## <a name="afx_global_datam_ndragframethicknessfloat"></a><a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA:: m_nDragFrameThicknessFloat

Задает толщину рамки перетаскивания, используемой для обозначения плавающего состояния.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Комментарии

`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`Конструктор инициализирует этот элемент до 4 пикселей.

## <a name="afx_global_dataonsettingchange"></a><a name="onsettingchange"></a> AFX_GLOBAL_DATA:: Онсеттингчанже

Определяет текущее состояние для анимации меню рабочего стола и функций автоматического скрытия панели задач.

```cpp
void OnSettingChange();
```

### <a name="remarks"></a>Комментарии

Этот метод задает для переменных платформы состояние определенных атрибутов рабочего стола пользователя. Этот метод определяет текущее состояние анимации меню, затухания меню и функции автоскрытия панели задач.

## <a name="afx_global_dataregisterwindowclass"></a><a name="registerwindowclass"></a> AFX_GLOBAL_DATA:: Регистервиндовкласс

Регистрирует указанный класс окна MFC.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Параметры

*лпсзкласснамепрефикс*<br/>
окне Имя регистрируемого класса окна.

### <a name="return-value"></a>Возвращаемое значение

Полное имя зарегистрированного класса, если этот метод завершился с ошибкой; в противном случае — [исключение ресурса](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Комментарии

Возвращаемое значение представляет собой список с разделителями-двоеточиями строки параметра *лпсзкласснамепрефикс* , а также шестнадцатеричное текстовое представление дескрипторов текущего экземпляра приложения. курсор приложения, который является курсором со стрелкой, идентификатор которого IDC_ARROW; и кисть фона. Дополнительные сведения о регистрации классов окон MFC см. в разделе [афксрегистеркласс](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="afx_global_dataresume"></a><a name="resume"></a> AFX_GLOBAL_DATA:: Resume

Повторно инициализирует внутренние указатели функции, которые обращаются к методам, поддерживающим темы и стили оформления Windows.

```
BOOL Resume();
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод завершился с ошибкой; в противном случае — значение FALSE. В режиме отладки этот метод утверждает, если этот метод завершился неудачно.

### <a name="remarks"></a>Комментарии

Этот метод вызывается, когда платформа получает сообщение [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) .

## <a name="afx_global_datasetlayeredattrib"></a><a name="setlayeredattrib"></a> AFX_GLOBAL_DATA:: Сетлайередаттриб

Предоставляет простой способ для вызова метода [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) Windows.

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Параметры

*HWND*<br/>
окне Обработчик для многоуровневого окна.

*кркэй*<br/>
окне Ключ цвета прозрачности, используемый [Диспетчер окон рабочего стола](/windows/win32/dwm/dwm-overview) для создания многоуровневого окна.

*балфа*<br/>
окне Альфа-значение, которое используется для описания прозрачности многоуровневого окна.

*dwFlags*<br/>
окне Побитовое сочетание (или) флагов, которые указывают, какие параметры метода следует использовать. Укажите LWA_COLORKEY, чтобы использовать параметр *кркэй* в качестве цвета прозрачности. Укажите LWA_ALPHA, чтобы использовать параметр *балфа* для определения прозрачности многоуровневого окна.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод завершился с ошибкой; в противном случае — значение FALSE.

## <a name="afx_global_datasetmenufont"></a><a name="setmenufont"></a> AFX_GLOBAL_DATA:: Сетменуфонт

Создает указанный логический шрифт.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Параметры

*лплогфонт*<br/>
окне Указатель на структуру, содержащую атрибуты шрифта.

*бхорз*<br/>
окне Значение TRUE, чтобы указать, что текст выполняется горизонтально; Значение FALSE, чтобы указать, что текст выполняется по вертикали.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод завершился с ошибкой; в противном случае — значение FALSE. В режиме отладки этот метод утверждает, если этот метод завершился неудачно.

### <a name="remarks"></a>Комментарии

Этот метод создает горизонтальный обычный шрифт, подчеркнутый шрифт и полужирный шрифт, используемый в пунктах меню по умолчанию. При необходимости этот метод создает обычный вертикальный шрифт. Дополнительные сведения о логических шрифтах см. в разделе [кфонт:: CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="afx_global_dataupdatefonts"></a><a name="updatefonts"></a> AFX_GLOBAL_DATA:: Упдатефонтс

Повторно инициализирует логические шрифты, используемые платформой.

```cpp
void UpdateFonts();
```

### <a name="remarks"></a>Комментарии

Дополнительные сведения о логических шрифтах см. в разделе `CFont::CreateFontIndirect` .

## <a name="afx_global_dataupdatesyscolors"></a><a name="updatesyscolors"></a> AFX_GLOBAL_DATA:: Упдатесисколорс

Инициализирует цвета, глубину цвета, кисти, перья и изображения, используемые платформой.

```cpp
void UpdateSysColors();
```

## <a name="afx_global_databiswindows7"></a><a name="biswindows7"></a> AFX_GLOBAL_DATA:: bIsWindows7

Указывает, выполняется ли приложение в Windows 7 или более поздней версии.

```
BOOL bIsWindows7;
```

## <a name="afx_global_dataclractivecaptiongradient"></a><a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA:: Клрактивекаптионградиент

Задает цвет градиента для активного заголовка. Обычно используется для закрепляемых панелей.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="afx_global_dataclrinactivecaptiongradient"></a><a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA:: Клринактивекаптионградиент

Задает цвет градиента для неактивного заголовка. Обычно используется для закрепляемых панелей.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="afx_global_datagetitaskbarlist"></a><a name="getitaskbarlist"></a> AFX_GLOBAL_DATA:: Жетитаскбарлист

Создает и сохраняет в глобальных данных указатель на `ITaskBarList` интерфейс.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на `ITaskbarList` интерфейс при успешности создания объекта списка задач. Значение NULL, если создание завершается ошибкой или если текущая операционная система меньше Windows 7.

## <a name="afx_global_datagetitaskbarlist3"></a><a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA:: GetITaskbarList3

Создает и сохраняет в глобальных данных указатель на `ITaskBarList3` интерфейс.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на `ITaskbarList3` интерфейс при успешности создания объекта списка задач. Значение NULL, если создание завершается ошибкой или если текущая операционная система меньше Windows 7.

## <a name="afx_global_datagetshellautohidebars"></a><a name="getshellautohidebars"></a> AFX_GLOBAL_DATA:: Жетшеллаутохидебарс

Определяет положения автоматически скрываемых панелей оболочки.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Возвращаемое значение

Целочисленное значение с закодированными флагами, задающих позиции автоматически скрытых полос. Он может сочетать следующие значения: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="afx_global_datareleasetaskbarrefs"></a><a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA:: Релеасетаскбаррефс

Освобождает интерфейсы, полученные с `GetITaskbarList` помощью `GetITaskbarList3` методов и.

```cpp
void ReleaseTaskBarRefs();
```

## <a name="afx_global_datashellcreateitemfromparsingname"></a><a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA:: Шеллкреатеитемфромпарсингнаме

Создает и инициализирует объект элемента оболочки из имени синтаксического анализа.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Параметры

*псзпас*<br/>
окне Указатель на отображаемое имя.

*пбк*<br/>
Указатель на контекст привязки, управляющий операцией синтаксического анализа.

*riid*<br/>
Ссылка на идентификатор интерфейса.

*ппв*<br/>
заполняет При возврате этой функции содержит указатель интерфейса, запрошенный в *riid*. Как правило, это `IShellItem` или `IShellItem2` .

### <a name="return-value"></a>Возвращаемое значение

Возвращает S_OK в случае успеха. значение ошибки в противном случае.

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../hierarchy-chart.md)<br/>
[Структуры, стили, обратные вызовы и схемы сообщений](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Части и состояния](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Диспетчер окон рабочего стола](/windows/win32/dwm/dwm-overview)<br/>
[Включение и контроль композиции DWM](/windows/win32/dwm/composition-ovw)<br/>
[Модель автоматизации пользовательского интерфейса и Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[Функция Жетсисколор](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[жетсисколорбруш](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[Структура НОНКЛИЕНТМЕТРИКС](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
