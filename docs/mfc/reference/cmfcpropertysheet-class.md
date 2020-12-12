---
description: 'Дополнительные сведения о: Кмфкпропертишит Class'
title: Класс Кмфкпропертишит
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: 6dd621e02074bf247f59b20e19024f06734f7fa2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289924"
---
# <a name="cmfcpropertysheet-class"></a>Класс Кмфкпропертишит

Класс `CMFCPropertySheet` поддерживает таблицу свойств, каждая страница свойств в которой обозначается вкладкой, кнопкой панели инструментов, узлом элемента управления «Дерево» или элементом списка.

## <a name="syntax"></a>Синтаксис

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[CMFCPropertySheet::CMFCPropertySheet](#cmfcpropertysheet)|Формирует объект `CMFCPropertySheet`.|
|`CMFCPropertySheet::~CMFCPropertySheet`|Деструктор.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CMFCPropertySheet::AddPage](#addpage)|Добавляет страницу в таблицу свойств.|
|[CMFCPropertySheet::AddPageToTree](#addpagetotree)|Добавляет новую страницу свойств в элемент управления «Дерево».|
|[CMFCPropertySheet::AddTreeCategory](#addtreecategory)|Добавляет новый узел в элемент управления «Дерево».|
|[CMFCPropertySheet::EnablePageHeader](#enablepageheader)|Резервирует место в верхней части каждой страницы для отрисовки пользовательского заголовка.|
|[CMFCPropertySheet::GetHeaderHeight](#getheaderheight)|Получает высоту текущего заголовка.|
|[CMFCPropertySheet::GetLook](#getlook)|Получает значение перечисления, указывающее внешний вид текущей таблицы свойств.|
|[CMFCPropertySheet::GetNavBarWidth](#getnavbarwidth)|Получает ширину панели навигации в пикселях.|
|[CMFCPropertySheet::GetTab](#gettab)|Получает внутренний объект набора вкладок, который поддерживает текущий элемент управления «Страница свойств».|
|`CMFCPropertySheet::GetThisClass`|Используется платформой для получения указателя на объект [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) , связанный с этим типом класса.|
|[CMFCPropertySheet::InitNavigationControl](#initnavigationcontrol)|Инициализирует появление текущего элемента управления «Страница свойств».|
|[CMFCPropertySheet::OnActivatePage](#onactivatepage)|Вызывается платформой при включении страницы свойств.|
|[CMFCPropertySheet::OnDrawPageHeader](#ondrawpageheader)|Вызывается платформой для отрисовки пользовательского заголовка страницы свойств.|
|`CMFCPropertySheet::OnInitDialog`|Обрабатывает сообщение [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) . (Переопределяет [CPropertySheet:: онинитдиалог](../../mfc/reference/cpropertysheet-class.md#oninitdialog).)|
|[CMFCPropertySheet::OnRemoveTreePage](#onremovetreepage)|Вызывается платформой для удаления страницы свойств из элемента управления «Дерево».|
|`CMFCPropertySheet::PreTranslateMessage`|Преобразует сообщения окна до их отправки в функции Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) и [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Переопределяет `CPropertySheet::PreTranslateMessage`.)|
|[CMFCPropertySheet::RemoveCategory](#removecategory)|Удаляет узел из элемента управления «Дерево».|
|[CMFCPropertySheet::RemovePage](#removepage)|Удаляет страницу свойств из таблицы свойств.|
|[CMFCPropertySheet::SetIconsList](#seticonslist)|Указывает список изображений, используемых в элементе управления навигации панели Outlook.|
|[CMFCPropertySheet::SetLook](#setlook)|Задает внешний вид таблицы свойств.|

## <a name="remarks"></a>Комментарии

Класс `CMFCPropertySheet` представляет таблицы свойств, также называемые диалоговыми окнами с вкладками. Класс `CMFCPropertySheet` может отображать страницу свойств различными способами.

Чтобы использовать класс `CMFCPropertySheet` в приложении, выполните следующие действия.

1. Создайте класс из класса `CMFCPropertySheet` и дайте ему имя, например CMyPropertySheet.

1. Создайте объект [кмфкпропертипаже](../../mfc/reference/cmfcpropertypage-class.md) для каждой страницы свойств.

1. Вызовите метод [кмфкпропертишит:: сетлук](#setlook) в конструкторе кмипропертишит. Параметр этого метода указывает, что страницы свойств должны отображаться как вкладки вдоль верхней или левой стороны таблицы свойств, как вкладки в стиле таблицы свойств Microsoft OneNote свойств, как кнопки в элементе управления «Панель инструментов» Microsoft Outlook, как узлы дерева или как список элементов с левой стороны таблицы свойств.

1. При создании страницы свойств в стиле панели инструментов Microsoft Outlook вызовите метод [кмфкпропертишит:: сетиконслист](#seticonslist) , чтобы связать список изображений со страницами свойств.

1. Вызовите метод [кмфкпропертишит:: addPage](#addpage) для каждой страницы свойств.

1. Создайте элемент управления `CMFCPropertySheet` и вызовите его метод `DoModal`.

## <a name="illustrations"></a>Рисунки

На следующем рисунке показана таблица свойств в стиле встроенной панели инструментов Microsoft Outlook. Панель инструментов Outlook отображается с левой стороны таблицы свойств.

![Элементы управления цветов CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_color.png "Элементы управления цветов CMFCPropertySheet")

На следующем рисунке показана страница свойств, содержащая объект [класса кмфкпропертигридктрл](../../mfc/reference/cmfcpropertygridctrl-class.md) . Этот объект является таблицей свойств в стиле стандартной страницы свойств общих элементов управления.

![Элементы управления свойств и списков CMFCPropertySheet](../../mfc/reference/media/cmfcpropertysheet_list.png "Элементы управления свойств и списков CMFCPropertySheet")

На следующем рисунке показана таблица свойств в стиле элемента управления «Дерево».

![Дерево свойств](../../mfc/reference/media/proptree.png "Дерево свойств")

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** афкспропертишит. h

## <a name="cmfcpropertysheetaddpage"></a><a name="addpage"></a> Кмфкпропертишит:: AddPage

Добавляет страницу в таблицу свойств.

```cpp
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Параметры

*ппаже*<br/>
окне Указатель на объект страницы. Значение этого параметра не может быть равно NULL.

### <a name="remarks"></a>Комментарии

Этот метод добавляет указанную страницу свойств в качестве крайней правой вкладки на странице свойств. Поэтому используйте этот метод для добавления страниц в порядке слева направо.

Если страница свойств имеет стиль Microsoft Outlook, платформа отображает список кнопок навигации в левой части страницы свойств. После того как этот метод добавляет страницу свойств, он добавляет соответствующую кнопку в список. Чтобы отобразить страницу свойств, щелкните соответствующую ей кнопку. Дополнительные сведения о стилях страниц свойств см. в разделе [кмфкпропертишит:: сетлук](#setlook).

## <a name="cmfcpropertysheetaddpagetotree"></a><a name="addpagetotree"></a> Кмфкпропертишит:: Аддпажетотри

Добавляет новую страницу свойств в элемент управления «Дерево».

```cpp
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>Параметры

*пкатегори*<br/>
окне Указатель на родительский узел дерева или значение NULL, чтобы связать указанную страницу с узлом верхнего уровня. Чтобы получить этот указатель, вызовите метод [кмфкпропертишит:: аддтрикатегори](#addtreecategory) .

*ппаже*<br/>
окне Указатель на объект страницы свойств.

*никоннум*<br/>
окне Отсчитываемый от нуля индекс значка или значение-1, если значок не используется. Значок отображается рядом со страницей свойств элемент управления деревом, если страница не выбрана. Значение по умолчанию — -1.

*нселиконнум*<br/>
окне Отсчитываемый от нуля индекс значка или значение-1, если значок не используется. Значок отображается рядом со страницей свойств элемент управления деревом при выборе этой страницы. Значение по умолчанию — -1.

### <a name="remarks"></a>Комментарии

Этот метод добавляет страницу свойств в качестве листа элемента управления "дерево". Чтобы добавить страницу свойств, создайте `CMFCPropertySheet` объект, вызовите метод [кмфкпропертишит:: сетлук](#setlook) с параметром *Look* , имеющим значение `CMFCPropertySheet::PropSheetLook_Tree` , а затем используйте этот метод для добавления страницы свойств.

## <a name="cmfcpropertysheetaddtreecategory"></a><a name="addtreecategory"></a> Кмфкпропертишит:: Аддтрикатегори

Добавляет новый узел в элемент управления «Дерево».

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>Параметры

*лпсзлабел*<br/>
окне Имя узла.

*никоннум*<br/>
окне Отсчитываемый от нуля индекс значка или значение-1, если значок не используется. Значок отображается рядом со страницей свойств элемент управления деревом, если страница не выбрана. Значение по умолчанию — -1.

*нселектедиконнум*<br/>
окне Отсчитываемый от нуля индекс значка или значение-1, если значок не используется. Значок отображается рядом со страницей свойств элемент управления деревом при выборе этой страницы. Значение по умолчанию — -1.

*ппаренткатегори*<br/>
окне Указатель на родительский узел дерева или значение NULL, чтобы связать указанную страницу с узлом верхнего уровня. Задайте этот параметр с помощью метода [кмфкпропертишит:: аддтрикатегори](#addtreecategory) .

### <a name="return-value"></a>Возвращаемое значение

Указатель на новый узел в элементе управления "дерево".

### <a name="remarks"></a>Комментарии

Этот метод используется для добавления нового узла, который также называется категорией, в древовидный элемент управления. Чтобы добавить узел, создайте `CMFCPropertySheet` объект, вызовите метод [кмфкпропертишит:: сетлук](#setlook) с параметром *Look* , имеющим значение `CMFCPropertySheet::PropSheetLook_Tree` , а затем используйте этот метод для добавления узла.

Используйте возвращаемое значение этого метода в последующих вызовах [кмфкпропертишит:: аддпажетотри](#addpagetotree) и [Кмфкпропертишит:: аддтрикатегори](#addtreecategory).

## <a name="cmfcpropertysheetcmfcpropertysheet"></a><a name="cmfcpropertysheet"></a> Кмфкпропертишит:: Кмфкпропертишит

Формирует объект `CMFCPropertySheet`.

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>Параметры

*псзкаптион*<br/>
окне Строка, содержащая заголовок страницы свойств. Не может быть NULL.

*нидкаптион*<br/>
окне Идентификатор ресурса, содержащий заголовок страницы свойств.

*ппарентвнд*<br/>
окне Указатель на родительское окно страницы свойств или значение NULL, если родительское окно является главным окном приложения. Значение по умолчанию — NULL.

*иселектпаже*<br/>
окне Отсчитываемый от нуля индекс верхней страницы свойств. Значение по умолчанию — 0.

### <a name="remarks"></a>Комментарии

Дополнительные сведения см. в разделе Параметры для конструктора [CPropertySheet:: CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet) .

## <a name="cmfcpropertysheetenablepageheader"></a><a name="enablepageheader"></a> Кмфкпропертишит:: Енаблепажехеадер

Резервирует место в верхней части каждой страницы для отрисовки пользовательского заголовка.

```cpp
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>Параметры

*нхеадерхеигхт*<br/>
окне Высота заголовка в пикселях.

### <a name="remarks"></a>Комментарии

Чтобы использовать значение параметра *нхеадерхеигхт* для рисования пользовательского заголовка, переопределите метод [Кмфкпропертишит:: ондравпажехеадер](#ondrawpageheader) .

## <a name="cmfcpropertysheetgetheaderheight"></a><a name="getheaderheight"></a> Кмфкпропертишит:: Жесеадерхеигхт

Получает высоту текущего заголовка.

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>Возвращаемое значение

Высота заголовка в пикселях.

### <a name="remarks"></a>Комментарии

Перед вызовом этого метода вызовите метод [кмфкпропертишит:: енаблепажехеадер](#enablepageheader) .

## <a name="cmfcpropertysheetgetlook"></a><a name="getlook"></a> Кмфкпропертишит:: Look

Получает значение перечисления, указывающее внешний вид текущей таблицы свойств.

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>Возвращаемое значение

Одно из значений перечисления, определяющее внешний вид страницы свойств. Список возможных значений см. в таблице перечисления в разделе "Примечания" раздела [кмфкпропертишит:: сетлук](#setlook).

## <a name="cmfcpropertysheetgetnavbarwidth"></a><a name="getnavbarwidth"></a> Кмфкпропертишит:: Жетнавбарвидс

Получает ширину панели навигации.

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ширина панели навигации в пикселях.

## <a name="cmfcpropertysheetgettab"></a><a name="gettab"></a> Кмфкпропертишит:: Жеттаб

Получает внутренний объект набора вкладок, который поддерживает текущий элемент управления «Страница свойств».

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>Возвращаемое значение

Внутренний управляющий объект вкладки.

### <a name="remarks"></a>Комментарии

Можно задать страницу свойств таким образом, чтобы она появилась в разных стилях, таких как древовидный элемент управления, список кнопок навигации или набор страниц с вкладками.

Перед вызовом этого метода вызовите метод [кмфкпропертишит:: сетлук](#setlook) , чтобы задать внешний вид элемента управления страницы свойств. Затем вызовите метод [кмфкпропертишит:: инитнавигатионконтрол](#initnavigationcontrol) , чтобы инициализировать внутренний управляющий объект вкладки. Этот метод используется для получения объекта элемента управления Tab и последующего использования этого объекта для работы с вкладками на странице свойств.

Этот метод утверждается в режиме отладки, если элемент управления "страница свойств" не установлен в стиле Microsoft OneNote.

## <a name="cmfcpropertysheetinitnavigationcontrol"></a><a name="initnavigationcontrol"></a> Кмфкпропертишит:: Инитнавигатионконтрол

Инициализирует появление текущего элемента управления «Страница свойств».

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на окно элемента управления страницы свойств.

### <a name="remarks"></a>Комментарии

Элемент управления "страница свойств" может находиться в нескольких разных формах, например в наборе страниц с вкладками, в элементе управления "дерево" или в списке кнопок навигации. Используйте метод [кмфкпропертишит:: сетлук](#setlook) , чтобы указать внешний вид элемента управления страницы свойств.

## <a name="cmfcpropertysheetonactivatepage"></a><a name="onactivatepage"></a> Кмфкпропертишит:: Онактиватепаже

Вызывается платформой при включении страницы свойств.

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Параметры

*ппаже*<br/>
окне Указатель на объект страницы свойств, представляющий страницу "включенные свойства".

### <a name="remarks"></a>Комментарии

По умолчанию этот метод обеспечивает прокрутку страницы свойств Enabled на представление. Если стиль текущей страницы свойств содержит панель Microsoft Outlook, этот метод устанавливает соответствующую кнопку Outlook в состояние checked.

## <a name="cmfcpropertysheetondrawpageheader"></a><a name="ondrawpageheader"></a> Кмфкпропертишит:: Ондравпажехеадер

Вызывается платформой для отрисовки заголовка настраиваемой страницы свойств.

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>Параметры

*Хозяин*<br/>
окне Указатель на контекст устройства.

*нпаже*<br/>
окне Номер страницы свойств, начинающийся с нуля.

*рексеадер*<br/>
окне Ограничивающий прямоугольник, указывающий, где следует нарисовать заголовок.

### <a name="remarks"></a>Комментарии

По умолчанию этот метод не выполняет никаких действий. При переопределении этого метода вызовите метод [кмфкпропертишит:: енаблепажехеадер](#enablepageheader) , прежде чем платформа вызовет этот метод.

## <a name="cmfcpropertysheetonremovetreepage"></a><a name="onremovetreepage"></a> Кмфкпропертишит:: Онремоветрипаже

Вызывается платформой для удаления страницы свойств из элемента управления «Дерево».

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Параметры

*ппаже*<br/>
окне Указатель на объект страницы свойств, представляющий удаляемую страницу свойств.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

## <a name="cmfcpropertysheetremovecategory"></a><a name="removecategory"></a> Кмфкпропертишит:: Ремовекатегори

Удаляет узел из элемента управления «Дерево».

```cpp
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>Параметры

*пкатегори*<br/>
окне Указатель на категорию (узел), которую нужно удалить.

### <a name="remarks"></a>Комментарии

Этот метод используется для удаления узла, который также называется категорией, из элемента управления "дерево". Используйте метод [кмфкпропертишит:: аддтрикатегори](#addtreecategory) , чтобы добавить узел в элемент управления "дерево".

## <a name="cmfcpropertysheetremovepage"></a><a name="removepage"></a> Кмфкпропертишит:: RemovePage

Удаляет страницу свойств из таблицы свойств.

```cpp
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Параметры

*ппаже*<br/>
окне Указатель на объект страницы свойств, представляющий удаляемую страницу свойств. Не может быть NULL.

*нпаже*<br/>
окне Отсчитываемый от нуля индекс удаляемой страницы.

### <a name="remarks"></a>Комментарии

Этот метод удаляет указанную страницу свойств и уничтожает связанное окно. Объект страницы свойств, заданный параметром *ппаже* , не уничтожается до закрытия окна [кмфкпропертишит](../../mfc/reference/cmfcpropertysheet-class.md) .

## <a name="cmfcpropertysheetseticonslist"></a><a name="seticonslist"></a> Кмфкпропертишит:: Сетиконслист

Указывает список изображений, используемых в элементе управления навигации панели Outlook.

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>Параметры

*уиимажелистресид*<br/>
окне Идентификатор ресурса для списка изображений.

*/CX*<br/>
окне Ширина (в пикселях) значков в списке изображений.

*клртранспарент*<br/>
окне Цвет прозрачного изображения. Части изображения, имеющие этот цвет, будут прозрачными. Значением по умолчанию является пурпурный цвет, RGB (255, 0255).

*хиконс*<br/>
окне Маркер существующего списка изображений.

### <a name="return-value"></a>Возвращаемое значение

В первом синтаксисе перегрузки метода — TRUE, если этот метод успешно выполнен; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Если страница свойств имеет стиль Microsoft Outlook, платформа отображает список кнопок навигации, называемый элементом управления панели Outlook, в левой части страницы свойств. Используйте этот метод, чтобы задать список изображений, используемый элементом управления "панель Outlook".

Дополнительные сведения о методах, поддерживающих этот метод, см. в разделе [CImageList:: Create](../../mfc/reference/cimagelist-class.md#create) и [CImageList:: Add](../../mfc/reference/cimagelist-class.md#add). Дополнительные сведения о том, как задать стиль страницы свойств, см. в разделе [кмфкпропертишит:: сетлук](#setlook).

## <a name="cmfcpropertysheetsetlook"></a><a name="setlook"></a> Кмфкпропертишит:: Сетлук

Задает внешний вид таблицы свойств.

```cpp
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>Параметры

*взглян*<br/>
окне Одно из значений перечисления, определяющее внешний вид страницы свойств. Стилем по умолчанию для страницы свойств является `CMFCPropertySheet::PropSheetLook_Tabs` . Дополнительные сведения см. в таблице в подразделе «Примечания» этого раздела.

*ннавконтролвидс*<br/>
окне Ширина элемента управления навигацией в пикселях. По умолчанию используется значение 100.

### <a name="remarks"></a>Комментарии

Чтобы отобразить страницу свойств в стиле, отличном от значения по умолчанию, вызовите этот метод перед созданием окна страницы свойств.

В следующей таблице перечислены значения перечисления, которые можно указать в параметре *вида* .

|Значение|Описание|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|Параметры Отображает вкладку для каждой страницы свойств. Вкладки отображаются в верхней части страницы свойств и помещаются в стек, если количество вкладок больше, чем в одной строке.|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|Отображает список кнопок навигации в стиле панели Microsoft Outlook, расположенном в левой части страницы свойств. Каждая кнопка в списке соответствует странице свойств. Платформа отображает стрелки прокрутки, если имеется больше кнопок, чем помещается в видимую область списка.|
|`CMFCPropertySheet::PropSheetLook_Tree`|Отображает элемент управления "дерево" в левой части страницы свойств. Каждый родительский или дочерний узел элемента управления "дерево" соответствует странице свойств. Платформа отображает стрелки прокрутки, если количество узлов больше, чем помещается в видимую область элемента управления "дерево".|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|Отображает вкладку в стиле Microsoft OneNote для каждой страницы свойств. Платформа отображает вкладки в верхней части страницы свойств и стрелки прокрутки, если больше вкладок, чем помещается в одной строке.|
|`CMFCPropertySheet::PropSheetLook_List`|Отображает список в левой части страницы свойств. Каждый элемент списка соответствует странице свойств. Платформа отображает стрелки прокрутки, если количество элементов списка больше, чем помещается в видимую область списка.|

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс Кмфкпропертипаже](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[Класс CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)
