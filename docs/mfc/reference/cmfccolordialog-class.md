---
title: Класс CMFCColorDialog
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: d94c223ed1e0b236ae8565d13a9f2c9652b6eb84
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270323"
---
# <a name="cmfccolordialog-class"></a>Класс CMFCColorDialog

`CMFCColorDialog` Класс представляет диалоговое окно выбора цвета.

## <a name="syntax"></a>Синтаксис

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание:|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|Создает объект `CMFCColorDialog`.|
|`CMFCColorDialog::~CMFCColorDialog`|Деструктор.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|Возвращает текущий выбранный цвет.|
|[CMFCColorDialog::GetPalette](#getpalette)|Возвращает цветовую палитру.|
|`CMFCColorDialog::PreTranslateMessage`|Преобразует сообщения окна перед их диспетчеризацией в [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) и [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) функции Windows. Синтаксис и Дополнительные сведения см. в разделе [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Переопределяет `CDialogEx::PreTranslateMessage`.)|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|Является производным палитры из системной палитры.|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|Задает текущий выбранный цвет.|
|[CMFCColorDialog::SetNewColor](#setnewcolor)|Задает цвет, наиболее эквивалентно указанное значение RGB.|
|[CMFCColorDialog::SetPageOne](#setpageone)|Выбирает значение RGB для первой страницы свойств.|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|Выбирает значение RGB для второй страницы свойств.|

### <a name="protected-data-members"></a>Защищенные члены данных

|Имя|Описание:|
|----------|-----------------|
|`m_bIsMyPalette`|Значение TRUE, если диалоговое окно выбора цвета использует свою собственную цветовую палитру, или значение FALSE, если в диалоговом окне используются палитру, которая указана в `CMFCColorDialog` конструктор.|
|`m_bPickerMode`|Значение TRUE, а пользователь выбирает цвет в диалоговом окне выбора; в противном случае — значение FALSE.|
|`m_btnColorSelect`|Кнопка цвета, выбранный пользователем.|
|`m_CurrentColor`|Выбранный цвет.|
|`m_hcurPicker`|Курсор, который используется для выбора цвета.|
|`m_NewColor`|Потенциальным выбранного цвета, который может быть без возможности восстановления выбранные или вернуть исходное значение цвета.|
|`m_pColourSheetOne`|Указатель на первую страницу свойств, свойств, выделение цветом.|
|`m_pColourSheetTwo`|Указатель на вторую страницу свойств, свойств, выделение цветом.|
|`m_pPalette`|Текущий логическую палитру.|
|`m_pPropSheet`|Указатель на окно свойств диалоговое окно выбора цвета.|
|`m_wndColors`|Объект управления средства выбора цвета.|
|`m_wndStaticPlaceHolder`|Статический элемент управления, — это заполнитель для страницы свойств средства выбора цвета.|

## <a name="remarks"></a>Примечания

Диалоговое окно выбора цвета отображается как свойств двух страниц. На первой странице выберите стандартный цвет из палитры системы; на второй странице выберите пользовательский цвет.

Можно создать `CMFCColorDialog` объект в стеке, а затем вызвать `DoModal`, передав в качестве параметра цвет `CMFCColorDialog` конструктор. Диалоговое окно выбора цвета затем создает несколько [класс CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md) объектов для обработки каждого цветовую палитру.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>Пример

Следующий пример демонстрирует настройку цвета диалоговое окно с помощью различных методов в `CMFCColorDialog` класса. В примере показано, как задать текущего и нового цвета диалогового окна и настройке компонентов красного, зеленого и синего цвета, выбранного на страницах свойств два цвета диалогового окна. Этот пример является частью [пример новых элементов управления](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>Требования

**Заголовок:** afxcolordialog.h

##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog

Создает объект `CMFCColorDialog`.

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>Параметры

*clrInit*<br/>
[in] Выбранный цвет по умолчанию. Если значение не указано, по умолчанию используется RGB(0,0,0) (черный).

*dwFlags*<br/>
[in] Зарезервировано.

*pParentWnd*<br/>
[in] Указатель на окно родительский объект или владельца диалогового окна.

*hPal*<br/>
[in] Дескриптор палитры.

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Примечания

##  <a name="getcolor"></a>  CMFCColorDialog::GetColor

Получает цвет, который пользователь выбирает в диалоговом окне цвет.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Возвращаемое значение

Объект [COLORREF](/windows/desktop/gdi/colorref) значение, содержащее данные RGB для цвета, выбранного в диалоговом окне цвет.

### <a name="remarks"></a>Примечания

Вызывайте эту функцию после вызова метода `DoModal` метод.

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

Возвращает цветовую палитру, которая доступна в диалоговом окне текущий цвет.

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на `CPalette` объект, который был указан в `CMFCColorDialog` конструктор.

### <a name="remarks"></a>Примечания

Цветовую палитру палитра цветов, которые может выбрать пользователь.

##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette

Является производным палитры из системной палитры.

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor

Задает текущий цвет диалогового окна.

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>Параметры

*rgb*<br/>
[in] Значение цвета RGB

### <a name="remarks"></a>Примечания

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

Задает текущий цвет цвет в палитре текущего, наиболее подходящий.

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>Параметры

*rgb*<br/>
[in] Объект [COLORREF](/windows/desktop/gdi/colorref) , указывающее цвета RGB.

### <a name="remarks"></a>Примечания

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

Явно указывает компонентов красного, зеленого и синего цвета, выбранные на первой странице свойство цвета диалогового окна.

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Параметры

*R*<br/>
[in] Указывает красный компонент RGB-значение.

*G*<br/>
[in] Задает компонент прокрутки на зеленый значения RGB.

*B*<br/>
[in] Задает компонент прокрутки на синий значения RGB.

### <a name="remarks"></a>Примечания

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

Явно указывает красного, зеленого и синего компонентов цвета, выбранного на второй странице свойств цвета диалогового окна.

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>Параметры

*R*<br/>
[in] Указывает красный компонент RGB-значение

*G*<br/>
[in] Задает зеленый компонент значения RGB

*B*<br/>
[in] Задает синий компонент RGB-значение

### <a name="remarks"></a>Примечания

## <a name="see-also"></a>См. также

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)
