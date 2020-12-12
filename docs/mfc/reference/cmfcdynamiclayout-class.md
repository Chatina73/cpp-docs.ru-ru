---
description: 'Дополнительные сведения о: CMFCDynamicLayout Class'
title: Класс CMFCDynamicLayout
ms.date: 08/29/2019
f1_keywords:
- CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout
- AFXLAYOUT/CMFCDynamicLayout::AddItem
- AFXLAYOUT/CMFCDynamicLayout::Adjust
- AFXLAYOUT/CMFCDynamicLayout::Create
- AFXLAYOUT/CMFCDynamicLayout::GetHostWnd
- AFXLAYOUT/CMFCDynamicLayout::GetMinSize
- AFXLAYOUT/CMFCDynamicLayout::GetWindowRect
- AFXLAYOUT/CMFCDynamicLayout::HasItem
- AFXLAYOUT/CMFCDynamicLayout::IsEmpty
- AFXLAYOUT/CMFCDynamicLayout::LoadResource
- AFXLAYOUT/CMFCDynamicLayout::SetMinSize
ms.assetid: c2df2976-f049-47fc-9cf0-abe3e01948bc
ms.openlocfilehash: 56979cce8ff20224cae444dab038bae29deeb39b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293915"
---
# <a name="cmfcdynamiclayout-class"></a>Класс CMFCDynamicLayout

Определяет порядок перемещения и изменения размеров элементов управления при изменении размеров окна.

## <a name="syntax"></a>Синтаксис

```
class CMFCDynamicLayout : public CObject
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|`CMFCDynamicLayout::CMFCDynamicLayout`|Формирует объект `CMFCDynamicLayout`.|
|`CMFCDynamicLayout::~CMFCDynamicLayout`|Деструктор.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CMFCDynamicLayout::AddItem](#additem)|Добавляет в список окон, управляемых диспетчером динамического макета, дочернее окно (обычно элемент управления).|
|[CMFCDynamicLayout::Adjust](#adjust)|Добавляет в список окон, управляемых диспетчером динамического макета, дочернее окно (обычно элемент управления).|
|[CMFCDynamicLayout::Create](#create)|Хранит и проверяет главное окно.|
|[CMFCDynamicLayout::GetHostWnd](#gethostwnd)|Возвращает указатель на главное окно.|
|[CMFCDynamicLayout::GetMinSize](#getminsize)|Возвращает минимальный размер окна для макета.|
|[CMFCDynamicLayout::GetWindowRect](#getwindowrect)|Извлекает прямоугольник для текущей клиентской области окна.|
|[CMFCDynamicLayout::HasItem](#hasitem)|Проверяет, добавлялся ли дочерний элемент управления в динамический макет.|
|[CMFCDynamicLayout::IsEmpty](#isempty)|Проверяет, что в динамический макет не добавлялись дочерние окна.|
|[CMFCDynamicLayout::LoadResource](#loadresource)|Считывает динамический макет из ресурса AFX_DIALOG_LAYOUT и применяет его для главного окна.|
|статический [CMFCDynamicLayout:: мовехоризонтал](#movehorizontal)|Возвращает значение [MoveSettings](#movesettings_structure) , определяющее, сколько дочернего элемента управления перемещается горизонтально, когда пользователь изменяет свое окно размещения.|
|статический [CMFCDynamicLayout:: мовехоризонталандвертикал](#movehorizontalandvertical)|Возвращает значение [MoveSettings](#movesettings_structure) , определяющее, сколько дочернего элемента управления перемещается горизонтально, когда пользователь изменяет свое окно размещения.|
|статический [CMFCDynamicLayout:: мовеноне](#movenone)|Возвращает значение [MoveSettings](#movesettings_structure) , которое не представляет движение, вертикальное или горизонтальное, для дочернего элемента управления.|
|статический [CMFCDynamicLayout:: мовевертикал](#movevertical)|Возвращает значение [MoveSettings](#movesettings_structure) , определяющее, сколько дочернего элемента управления перемещается по вертикали, когда пользователь изменяет свое окно размещения.|
|[CMFCDynamicLayout::SetMinSize](#setminsize)|Задает минимальный размер окна для макета.|
|статический [CMFCDynamicLayout:: сизехоризонтал](#sizehorizontal)|Возвращает значение [SizeSettings](#sizesettings_structure) , определяющее размер дочернего элемента управления по горизонтали при изменении размера его окна размещения.|
|статический [CMFCDynamicLayout:: сизехоризонталандвертикал](#sizehorizontalandvertical)|Возвращает значение [SizeSettings](#sizesettings_structure) , определяющее размер дочернего элемента управления по горизонтали при изменении размера его окна размещения.|
|статический [CMFCDynamicLayout:: сизеноне](#sizenone)|Возвращает значение [SizeSettings](#sizesettings_structure) , которое не изменяет размер дочернего элемента управления.|
|статический [CMFCDynamicLayout:: сизевертикал](#sizevertical)|Возвращает значение [SizeSettings](#sizesettings_structure) , определяющее размер дочернего элемента управления, который изменяется по вертикали, когда пользователь изменяет свое окно размещения.|

## <a name="nested-types"></a>Вложенные типы

|Имя|Описание|
|----------|-----------------|
|[Структура CMFCDynamicLayout::MoveSettings](#movesettings_structure)|Инкапсулирует данные перемещения для элементов управления в динамическом макете.|
|[Структура CMFCDynamicLayout::SizeSettings](#sizesettings_structure)|Инкапсулирует данные об изменении размера элементов управления в динамическом макете.|

## <a name="remarks"></a>Комментарии

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CMFCDynamicLayout](../../mfc/reference/cmfctoolbarbutton-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** афкслайаут. h

## <a name="cmfcdynamiclayoutadditem"></a><a name="additem"></a> CMFCDynamicLayout:: AddItem

Добавляет в список окон, управляемых диспетчером динамического макета, дочернее окно (обычно элемент управления).

```
BOOL AddItem(
    HWND hwnd,
    MoveSettings moveSettings SizeSettings sizeSettings);

BOOL AddItem(
    int nID,
    MoveSettings moveSettings SizeSettings sizeSettings);
```

### <a name="parameters"></a>Параметры

*HWND*<br/>
Дескриптор добавляемого окна.

*nID*<br/>
Идентификатор добавляемого дочернего элемента управления.

*moveSettings*<br/>
Структура, описывающая перемещение элемента управления при изменении размера окна.

*sizeSettings*<br/>
Структура, описывающая изменение размера элемента управления при изменении размера окна.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если элемент был успешно добавлен; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Положение и размер дочернего элемента управления динамически меняются при изменении размера главного окна.

## <a name="cmfcdynamiclayoutadjust"></a><a name="adjust"></a> CMFCDynamicLayout:: корректировка

Добавляет в список окон, управляемых диспетчером динамического макета, дочернее окно (обычно элемент управления).

```cpp
void Adjust();
```

### <a name="remarks"></a>Комментарии

Положение и размер дочернего элемента управления динамически меняются при изменении размера главного окна.

## <a name="cmfcdynamiclayoutcreate"></a><a name="create"></a> CMFCDynamicLayout:: Create

Хранит и проверяет главное окно.

```
BOOL Create(CWnd* pHostWnd);
```

### <a name="parameters"></a>Параметры

*pHostWnd*<br/>
Указатель на главное окно.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если создание прошло успешно; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutgethostwnd"></a><a name="gethostwnd"></a> CMFCDynamicLayout:: Жесоствнд

Возвращает указатель на главное окно.

```
CWnd* GetHostWnd();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на главное окно.

### <a name="remarks"></a>Комментарии

По умолчанию положения всех дочерних элементов управления пересчитываются относительно этого окна. 

## <a name="cmfcdynamiclayoutgetminsize"></a><a name="getminsize"></a> CMFCDynamicLayout:: Жетминсизе

Возвращает минимальный размер окна для макета.

```
CSize GetMinSize();
```

### <a name="return-value"></a>Возвращаемое значение

Минимальный размер окна для макета.

### <a name="remarks"></a>Комментарии

Положение и размер дочернего элемента управления динамически меняются при изменении размера главного окна, однако существует минимальный допустимый размер для макета. Пользователь может сделать окно меньше этого значения, но тогда определенные части окна будут скрыты.

## <a name="cmfcdynamiclayoutgetwindowrect"></a><a name="getwindowrect"></a> CMFCDynamicLayout:: Жетвиндоврект

Извлекает прямоугольник для текущей клиентской области окна.

```cpp
void GetHostWndRect(CRect& rect,);
```

### <a name="parameters"></a>Параметры

*rect*<br/>
После возвращения функцией этот параметр содержит ограничивающий прямоугольник области макета. Это выходной параметр. Входное значение перезаписывается.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayouthasitem"></a><a name="hasitem"></a> CMFCDynamicLayout:: Хаситем

Проверяет, добавлялся ли дочерний элемент управления в динамический макет.

```
BOOL HasItem(HWND hwnd);
```

### <a name="parameters"></a>Параметры

*HWND*<br/>
Дескриптор окна для элемента управления.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если макет уже содержит данный элемент; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutisempty"></a><a name="isempty"></a> CMFCDynamicLayout:: IsEmpty

Проверяет, что в динамический макет не добавлялись дочерние окна.

```
BOOL IsEmpty();
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если макет не содержит элементов; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutloadresource"></a><a name="loadresource"></a> CMFCDynamicLayout:: Лоадресаурце

Считывает динамический макет из ресурса AFX_DIALOG_LAYOUT и применяет его для главного окна.

```
static BOOL LoadResource(CWnd* pHostWnd,
    LPVOID lpResource,
    DWORD dwSize);
```

### <a name="parameters"></a>Параметры

*pHostWnd*<br/>
Указатель на главное окно.

*лпресаурце*<br/>
Указатель на буфер, содержащий ресурс AFX_DIALOG_LAYOUT.

*двсизе*<br/>
Размер буфера в байтах.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если ресурс загружен и применен для главного окна; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutmovehorizontal"></a><a name="movehorizontal"></a> CMFCDynamicLayout:: Мовехоризонтал

Возвращает значение [MoveSettings](#movesettings_structure) , определяющее, сколько дочернего элемента управления перемещается горизонтально, когда пользователь изменяет свое окно размещения.

```
static MoveSettings MoveHorizontal(int nRatio);
```

### <a name="parameters"></a>Параметры

*нратио*<br/>
Определяет расстояние (в процентах), на которое дочерний элемент управления будет перемещаться по горизонтали при изменении пользователем размера главного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение [MoveSettings](#movesettings_structure) , которое инкапсулирует запрошенный коэффициент перемещения.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutmovehorizontalandvertical"></a><a name="movehorizontalandvertical"></a> CMFCDynamicLayout:: Мовехоризонталандвертикал

Возвращает значение [MoveSettings](#movesettings_structure) , определяющее, сколько дочернего элемента управления перемещается горизонтально, когда пользователь изменяет свое окно размещения.

```
static MoveSettings MoveHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Параметры

*нксратио*<br/>
Определяет расстояние (в процентах), на которое дочерний элемент управления будет перемещаться по горизонтали при изменении пользователем размера главного окна.

*ниратио*<br/>
Определяет расстояние (в процентах), на которое дочерний элемент управления будет перемещаться по вертикали при изменении пользователем размера главного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение [MoveSettings](#movesettings_structure) , которое инкапсулирует запрошенный коэффициент перемещения.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutmovenone"></a><a name="movenone"></a> CMFCDynamicLayout:: Мовеноне

Возвращает значение [MoveSettings](#movesettings_structure) , которое не представляет движение, вертикальное или горизонтальное, для дочернего элемента управления.

```
static MoveSettings MoveNone();
```

### <a name="return-value"></a>Возвращаемое значение

Значение [MoveSettings](#movesettings_structure) , которое исправляет элемент управления на месте, чтобы оно не перемещается при изменении пользователем размера главного окна.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutmovesettings-structure"></a><a name="movesettings_structure"></a> Структура CMFCDynamicLayout:: MoveSettings

Инкапсулирует данные перемещения для элементов управления в динамическом макете.

```
struct CMFCDynamicLayout::MoveSettings;
```

### <a name="remarks"></a>Комментарии

Этот класс является вложенным в `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutmovesettingsishorizontal"></a>CMFCDynamicLayout:: MoveSettings:: Horizontal

Проверяет, задано ли в данных перемещения ненулевое перемещение по горизонтали.

```
BOOL IsHorizontal() const
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если объект `MoveSettings` задает ненулевое перемещение по горизонтали.

## <a name="cmfcdynamiclayoutmovesettingsisnone"></a>CMFCDynamicLayout:: MoveSettings:: a None

Проверяет, что задано нулевое перемещение данных.

```
BOOL IsNone() const
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если объект `MoveSettings` задает нулевое перемещение.

## <a name="cmfcdynamiclayoutmovesettingsisvertical"></a>CMFCDynamicLayout:: MoveSettings:: Vertical

Проверяет, задано ли в данных перемещения ненулевое перемещение по вертикали.

```
BOOL IsVertical() const
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если объект `MoveSettings` задает ненулевое перемещение по вертикали.

## <a name="cmfcdynamiclayoutmovevertical"></a><a name="movevertical"></a> CMFCDynamicLayout:: Мовевертикал

Возвращает значение [MoveSettings](#movesettings_structure) , определяющее, сколько дочернего элемента управления перемещается по вертикали, когда пользователь изменяет свое окно размещения.

```
static MoveSettings MoveVertical(int nRatio);
```

### <a name="parameters"></a>Параметры

*нратио*<br/>
Определяет расстояние (в процентах), на которое дочерний элемент управления будет перемещаться по вертикали при изменении пользователем размера главного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение [MoveSettings](#movesettings_structure) , которое инкапсулирует запрошенный коэффициент перемещения.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutsetminsize"></a><a name="setminsize"></a> CMFCDynamicLayout:: Сетминсизе

Задает минимальный размер окна для макета.

```cpp
void SetMinSize(const CSize& size);
```

### <a name="parameters"></a>Параметры

*size*<br/>
Необходимый минимальный размер макета.

### <a name="remarks"></a>Комментарии

Положение и размер дочернего элемента управления динамически меняются при изменении размера главного окна, однако существует минимальный допустимый размер для макета. Пользователь может сделать окно меньше этого значения, но тогда определенные части окна будут скрыты.

## <a name="cmfcdynamiclayoutsizehorizontal"></a><a name="sizehorizontal"></a> CMFCDynamicLayout:: Сизехоризонтал

Возвращает значение [SizeSettings](#sizesettings_structure) , определяющее размер дочернего элемента управления по горизонтали при изменении размера его окна размещения.

```
static SizeSettings SizeHorizontal(int nRatio);
```

### <a name="parameters"></a>Параметры

*нратио*<br/>
Определяет в процентах, как будет меняться размер дочернего элемента управления по горизонтали при изменении пользователем размера главного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение [SizeSettings](#sizesettings_structure) , которое инкапсулирует требуемый коэффициент размера.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutsizehorizontalandvertical"></a><a name="sizehorizontalandvertical"></a> CMFCDynamicLayout:: Сизехоризонталандвертикал

Возвращает значение [SizeSettings](#sizesettings_structure) , определяющее размер дочернего элемента управления по горизонтали при изменении размера его окна размещения.

```
static SizeSettings SizeHorizontalAndVertical(int nXRatio int nYRatio);
```

### <a name="parameters"></a>Параметры

*нксратио*<br/>
Определяет в процентах, как будет меняться размер дочернего элемента управления по горизонтали при изменении пользователем размера главного окна.

*ниратио*<br/>
Определяет в процентах, как будет меняться размер дочернего элемента управления по вертикали при изменении пользователем размера главного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение [SizeSettings](#sizesettings_structure) , которое инкапсулирует требуемый коэффициент размера.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutsizenone"></a><a name="sizenone"></a> CMFCDynamicLayout:: Сизеноне

Возвращает значение [SizeSettings](#sizesettings_structure) , которое не изменяет размер дочернего элемента управления.

```
static SizeSettings SizeNone();
```

### <a name="return-value"></a>Возвращаемое значение

Значение [SizeSettings](#sizesettings_structure) , которое устраняет элемент управления в определенном размере, поэтому он не изменяет размер при изменении пользователем размеров главного окна.

### <a name="remarks"></a>Комментарии

## <a name="cmfcdynamiclayoutsizesettings-structure"></a><a name="sizesettings_structure"></a> Структура CMFCDynamicLayout:: SizeSettings

Инкапсулирует данные об изменении размера элементов управления в динамическом макете.

```
struct CMFCDynamicLayout::SizeSettings;
```

### <a name="remarks"></a>Комментарии

Этот класс является вложенным в `CMFCDynamicLayout`.

## <a name="cmfcdynamiclayoutsizesettingsishorizontal"></a>CMFCDynamicLayout:: SizeSettings:: Horizontal

Проверяет, задано ли в данных об изменении размера ненулевое изменение размера по горизонтали.

```
BOOL IsHorizontal() const
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если объект `SizeSettings` задает ненулевое изменение размера по горизонтали.

## <a name="cmfcdynamiclayoutsizesettingsisnone"></a>CMFCDynamicLayout:: SizeSettings:: a None

Проверяет, задано ли в данных об изменении размера нулевое изменение размера.

```
BOOL IsNone() const
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если объект `SizeSettings` задает нулевое изменение размера.

## <a name="cmfcdynamiclayoutsizesettingsisvertical"></a>CMFCDynamicLayout:: SizeSettings:: Vertical

Проверяет, задано ли в данных об изменении размера ненулевое изменение размера по вертикали.

```
BOOL IsVertical() const
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если объект `SizeSettings` задает ненулевое изменение размера по вертикали.

## <a name="cmfcdynamiclayoutsizevertical"></a><a name="sizevertical"></a> CMFCDynamicLayout:: Сизевертикал

Возвращает значение [SizeSettings](#sizesettings_structure) , определяющее размер дочернего элемента управления, который изменяется по вертикали, когда пользователь изменяет свое окно размещения.

```
static SizeSettings SizeVertical(int nRatio);
```

### <a name="parameters"></a>Параметры

*нратио*<br/>
Определяет в процентах, как будет меняться размер дочернего элемента управления по вертикали при изменении пользователем размера главного окна.

### <a name="return-value"></a>Возвращаемое значение

Значение [SizeSettings](#sizesettings_structure) , которое инкапсулирует требуемый коэффициент размера.

### <a name="remarks"></a>Комментарии

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)
