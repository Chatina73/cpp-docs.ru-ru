---
description: 'Дополнительные сведения о: Кмфктулбаркомбобоксбуттон Class'
title: Класс Кмфктулбаркомбобоксбуттон
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: aa28d1b125a5e1baf56a9e6e10812e7e6e56312f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97163916"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>Класс Кмфктулбаркомбобоксбуттон

Кнопка на панели инструментов, содержащая элемент управления "поле со списком" ( [класс CComboBox](../../mfc/reference/ccombobox-class.md)).

## <a name="syntax"></a>Синтаксис

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Кмфктулбаркомбобоксбуттон:: Кмфктулбаркомбобоксбуттон](#cmfctoolbarcomboboxbutton)|Создает документ `CMFCToolBarComboBoxButton`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Кмфктулбаркомбобоксбуттон:: AddItem](#additem)|Добавляет элемент в конец списка полей со списком.|
|[Кмфктулбаркомбобоксбуттон:: Аддсортедитем](#addsorteditem)|Добавляет элемент в список полей со списком. Порядок элементов в списке указывается в `Compare` .|
|[Кмфктулбаркомбобоксбуттон:: Compare](#compare)|Сравнивает два элемента. Вызывается для сортировки элементов, которые `AddSortedItems` добавляются в список полей со списком.|
|[Кмфктулбаркомбобоксбуттон:: Креатидит](#createedit)|Создает новый элемент управления "поле ввода" для кнопки со списком.|
|[Кмфктулбаркомбобоксбуттон::D Елетеитем](#deleteitem)|Удаляет элемент из списка полей со списком.|
|[Кмфктулбаркомбобоксбуттон:: FindItem](#finditem)|Возвращает индекс элемента, содержащего указанную строку.|
|[Кмфктулбаркомбобоксбуттон:: Жетбикмд](#getbycmd)|Возвращает указатель на кнопку поля со списком с указанным ИДЕНТИФИКАТОРом команды.|
|[Кмфктулбаркомбобоксбуттон:: падающее поле](#getcombobox)|Возвращает указатель на элемент управления "поле со списком", встроенный в поле со списком.|
|[Кмфктулбаркомбобоксбуттон:: NOCOUNT](#getcount)|Возвращает число элементов в списке полей со списком.|
|[Кмфктулбаркомбобоксбуттон:: Жеткаунталл](#getcountall)|Находит кнопку поля со списком с указанным ИДЕНТИФИКАТОРом команды. Возвращает число элементов в списке в поле со списком этой кнопки.|
|[Кмфктулбаркомбобоксбуттон:: рекурсивно](#getcursel)|Возвращает индекс выбранного элемента в списке поля со списком.|
|[Кмфктулбаркомбобоксбуттон:: Жеткурселалл](#getcurselall)|Находит кнопку поля со списком с указанным ИДЕНТИФИКАТОРом команды и возвращает индекс выбранного элемента в списке поля со списком этой кнопки.|
|[Кмфктулбаркомбобоксбуттон:: Жетедитктрл](#geteditctrl)|Возвращает указатель на элемент управления "поле ввода", внедренный в кнопку со списком.|
|[Кмфктулбаркомбобоксбуттон:: DataItem](#getitem)|Возвращает строку, связанную с указанным индексом в списке полей со списком.|
|[Кмфктулбаркомбобоксбуттон:: Жетитемалл](#getitemall)|Находит кнопку поля со списком, которая содержит указанный идентификатор команды, и возвращает строку, связанную с индексом, в списке поля со списком этой кнопки.|
|[Кмфктулбаркомбобоксбуттон:: Жетитемдата](#getitemdata)|Возвращает 32-разрядное значение, связанное с указанным индексом в списке полей со списком.|
|[Кмфктулбаркомбобоксбуттон:: Жетитемдатаалл](#getitemdataall)|Находит кнопку поля со списком, которая содержит указанный идентификатор команды, и возвращает 32-разрядное значение, связанное с индексом, в списке поля со списком этой кнопки.|
|[Кмфктулбаркомбобоксбуттон:: Жетитемдатаптралл](#getitemdataptrall)|Находит кнопку поля со списком с указанным ИДЕНТИФИКАТОРом команды. Извлекает 32-разрядное значение, связанное с индексом в списке полей со списком этой кнопки, и возвращает 32-разрядное значение в виде указателя.|
|[Кмфктулбаркомбобоксбуттон:: GetText](#gettext)|Возвращает текст из элемента управления "поле ввода" поля со списком.|
|[Кмфктулбаркомбобоксбуттон:: Жеттексталл](#gettextall)|Находит кнопку поля со списком с указанным ИДЕНТИФИКАТОРом команды и возвращает текст из элемента управления редактирования этой кнопки.|
|[Кмфктулбаркомбобоксбуттон:: Исцентерверт](#iscentervert)|Определяет, будут ли кнопки поля со списком в приложении центрированы или выровнены по верхней части панели инструментов.|
|[Кмфктулбаркомбобоксбуттон:: Исфлатмоде](#isflatmode)|Определяет, имеют ли кнопки поля со списком неструктурированный вид.|
|[Кмфктулбаркомбобоксбуттон:: Ремовеаллитемс](#removeallitems)|Удаляет все элементы из списка и элемент управления изменением поля со списком.|
|[Кмфктулбаркомбобоксбуттон:: Селектитем](#selectitem)|Выбирает элемент в поле со списком в соответствии с его индексом, 32-битным значением или строкой и уведомляет элемент управления "поле со списком" о выделенном фрагменте.|
|[Кмфктулбаркомбобоксбуттон:: Селектитемалл](#selectitemall)|Находит кнопку поля со списком с указанным ИДЕНТИФИКАТОРом команды. Вызывает метод `SelectItem` для выбора элемента в поле со списком этой кнопки в соответствии со строкой, индексом или 32-битным значением.|
|[Кмфктулбаркомбобоксбуттон:: Сетцентерверт](#setcentervert)|Указывает, будут ли кнопки поля со списком в приложении центрированы вертикально или выровнены по верхней части панели инструментов.|
|[Кмфктулбаркомбобоксбуттон:: Сетдропдовнхеигхт](#setdropdownheight)|Задает высоту раскрывающегося списка.|
|[Кмфктулбаркомбобоксбуттон:: Сетфлатмоде](#setflatmode)|Указывает, имеют ли кнопки поля со списком неструктурированный вид.|

## <a name="remarks"></a>Комментарии

Чтобы добавить кнопку поля со списком на панель инструментов, выполните следующие действия.

1. Зарезервируйте идентификатор фиктивного ресурса для кнопки на родительском ресурсе панели инструментов.

2. Создайте `CMFCToolBarComboBoxButton` объект.

3. В обработчике сообщений, обрабатывающем сообщение AFX_WM_RESETTOOLBAR, замените фиктивную кнопку на новое поле со списком, используя [CMFCToolBar:: реплацебуттон](../../mfc/reference/cmfctoolbar-class.md#replacebutton).

Дополнительные сведения см. [в разделе Пошаговое руководство. размещение элементов управления на панелях инструментов](../../mfc/walkthrough-putting-controls-on-toolbars.md). Пример кнопки на панели инструментов для поля со списком см. в примере проекта Висуалстудиодемо.

## <a name="example"></a>Пример

В приведенном ниже примере демонстрируется использование различных методов класса `CMFCToolBarComboBoxButton` . В этом примере показано, как включить поля «Правка» и «поле со списком», установить вертикальное расположение кнопок поля со списком в приложении, установить высоту списка при его отправке, задать внешний вид кнопок поля со списком в приложении и задать текст в поле редактирования кнопки поля со списком. Этот фрагмент кода является частью [демонстрационного примера Visual Studio](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[кмфктулбаркомбобоксбуттон](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** афкстулбаркомбобоксбуттон. h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a> Кмфктулбаркомбобоксбуттон:: AddItem

Добавляет уникальный элемент в список.

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Параметры

*лпсзитем*<br/>
окне Текст элемента, добавляемого в список.

*двдата*<br/>
окне Данные, связанные с элементом, добавляемым в список.

### <a name="return-value"></a>Возвращаемое значение

Индекс последнего элемента в списке.

### <a name="remarks"></a>Комментарии

Не используйте этот метод при сортировке стиля списка.

Если текст элемента уже содержится в списке, новые данные сохраняются с существующим элементом. При поиске элемента учитывается регистр.

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a> Кмфктулбаркомбобоксбуттон:: Аддсортедитем

Добавляет элемент в список в порядке, определенном методом [Compare](#compare) .

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Параметры

*лпсзитем*<br/>
окне Текст элемента, добавляемого в список.

*двдата*<br/>
окне Данные, связанные с элементом, добавляемым в список.

### <a name="return-value"></a>Возвращаемое значение

Индекс элемента, который был добавлен в список.

### <a name="remarks"></a>Комментарии

Эта функция используется для добавления элементов в список в определенном порядке.

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a> Кмфктулбаркомбобоксбуттон:: Канбестретчед

Указывает, может ли измениться размер кнопки поля со списком.

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение TRUE.

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a> Кмфктулбаркомбобоксбуттон:: Кмфктулбаркомбобоксбуттон

Конструирует объект [кмфктулбаркомбобоксбуттон](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) .

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>Параметры

*uiID*<br/>
окне Идентификатор команды новой кнопки.

*иимаже*<br/>
окне Индекс изображения, связанного с кнопкой "создать".

*двстиле*<br/>
окне Стиль кнопки "создать".

*ивидс*<br/>
окне Ширина (в пикселях) кнопки "создать".

### <a name="remarks"></a>Комментарии

Ширина по умолчанию — 150 пикселей.

Список стилей кнопок панели инструментов см. в разделе [стили элементов управления ToolBar](../../mfc/reference/toolbar-control-styles.md) .

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a> Кмфктулбаркомбобоксбуттон:: Клеардата

Удаляет определяемые пользователем данные.

```
virtual void ClearData();
```

### <a name="remarks"></a>Комментарии

По умолчанию этот метод не выполняет никаких действий. Переопределите этот метод в производном классе, если хотите удалить все определяемые пользователем данные.

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a> Кмфктулбаркомбобоксбуттон:: Compare

Сравнивает две строки.

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>Параметры

*lpszItem1*<br/>
окне Первая сравниваемая строка.

*lpszItem2*<br/>
окне Вторая сравниваемая строка.

### <a name="return-value"></a>Возвращаемое значение

Значение, указывающее лексикографическим порядком связь с учетом регистра между строками. В следующем списке указаны возможные значения.

|Значение|Описание|
|-----------|-----------------|
|\<0|Первая строка меньше, чем вторая.|
|0|Первая строка равна второму.|
|> 0|Первая строка больше, чем вторая.|

### <a name="remarks"></a>Комментарии

Переопределите этот метод, чтобы изменить порядок сортировки элементов в списке.

При сравнении учитывается регистр.

Этот метод вызывается только из метода [аддсортедитем](#addsorteditem) .

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a> Кмфктулбаркомбобоксбуттон:: CopyFrom

Копирует состояние указанного `CMFCToolBarComboBoxButton` объекта в текущий объект.

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>Параметры

*src*<br/>
окне Исходный `CMFCToolBarComboBoxButton` объект.

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a> Кмфктулбаркомбобоксбуттон:: Креатекомбо

Создает новое поле со списком для кнопки поля со списком.

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>Параметры

*пвндпарент*<br/>
окне Указатель на родительское окно кнопки.

*rect*<br/>
окне Ограничивающий прямоугольник поля со списком.

### <a name="return-value"></a>Возвращаемое значение

Указатель на новое поле со списком, если метод был успешным; в противном случае значение NULL.

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a> Кмфктулбаркомбобоксбуттон:: Креатидит

Создает новое поле ввода для кнопки поля со списком.

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>Параметры

*пвндпарент*<br/>
окне Указатель на родительское окно кнопки.

*rect*<br/>
окне Ограничивающий прямоугольник нового поля ввода.

*дведитстиле*<br/>
окне Стиль элемента управления для нового поля ввода.

### <a name="return-value"></a>Возвращаемое значение

Указатель на новое поле ввода, если метод был успешным; в противном случае значение NULL.

### <a name="remarks"></a>Комментарии

Платформа вызывает этот метод при создании нового поля ввода для кнопки со списком. Переопределите этот метод, чтобы изменить способ создания [кмфктулбаркомбобокседит](../../mfc/reference/cmfctoolbarcomboboxedit-class.md) .

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a> Кмфктулбаркомбобоксбуттон::D Елетеитем

Удаляет указанный элемент из списка.

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Параметры

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс удаляемого элемента.

*двдата*<br/>
окне Данные, связанные с удаляемым элементом.

*lpszText*<br/>
окне Текст удаляемого элемента. Если имеется несколько элементов с одинаковым текстом, первый элемент удаляется.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если элемент был найден и успешно удален; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a> Кмфктулбаркомбобоксбуттон::D Упликатедата

Дублирует определяемые пользователем данные.

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Комментарии

По умолчанию этот метод не выполняет никаких действий. Переопределите этот метод в производном классе, если нужно скопировать какие-либо пользовательские данные.

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a> Кмфктулбаркомбобоксбуттон:: Енаблевиндов

Включает или отключает поля "Изменить" и "поле со списком".

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Параметры

*bEnable*<br/>
окне Значение TRUE, чтобы включить поля "Изменить" и "поле со списком"; Значение FALSE, чтобы отключить поля "Изменить" и "поле со списком".

### <a name="remarks"></a>Комментарии

При отключении элементы управления не могут стать активными и не могут принимать данные, вводимые пользователем.

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a> Кмфктулбаркомбобоксбуттон:: Експорттоменубуттон

Копирует строку из таблицы строк приложения в указанное меню с помощью кнопки поля со списком Идентификатор команды.

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>Параметры

*менубуттон*<br/>
заполняет Ссылка на кнопку меню.

### <a name="return-value"></a>Возвращаемое значение

Всегда TRUE.

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a> Кмфктулбаркомбобоксбуттон:: FindItem

Возвращает индекс первого элемента в списке, содержащего указанную строку.

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Параметры

*lpszText*<br/>
окне Текст, для которого необходимо выполнить поиск в списке.

### <a name="return-value"></a>Возвращаемое значение

Индекс элемента; или CB_ERR, если элемент не найден.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a> Кмфктулбаркомбобоксбуттон:: Жетбикмд

Возвращает указатель на кнопку поля со списком, имеющий указанный идентификатор команды.

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды для поля со списком.

*бисфокус*<br/>
окне Значение TRUE для поиска только кнопок с упором; Значение FALSE для поиска всех кнопок.

### <a name="return-value"></a>Возвращаемое значение

Указатель на кнопку поля со списком; или значение NULL, если кнопка не найдена.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a> Кмфктулбаркомбобоксбуттон:: падающее поле

Возвращает указатель на поле со списком в кнопке со списком.

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на объект [класса CComboBox](../../mfc/reference/ccombobox-class.md) , если метод был успешным; в противном случае — NULL.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a> Кмфктулбаркомбобоксбуттон:: Жетконтекстменуид

Возвращает идентификатор ресурса контекстного меню для кнопки поля со списком.

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>Возвращаемое значение

Идентификатор ресурса контекстного меню.

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a> Кмфктулбаркомбобоксбуттон:: NOCOUNT

Возвращает количество элементов в списке.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Возвращаемое значение

Число элементов в списке.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a> Кмфктулбаркомбобоксбуттон:: Жеткаунталл

Возвращает число элементов в списке кнопки поля со списком, имеющей указанный идентификатор команды.

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды для поля со списком.

### <a name="return-value"></a>Возвращаемое значение

Число элементов в списке; в противном случае CB_ERR, если не найдена кнопка поля со списком.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a> Кмфктулбаркомбобоксбуттон:: рекурсивно

Возвращает индекс выбранного в данный момент элемента в списке.

```
int GetCurSel() const;
```

### <a name="return-value"></a>Возвращаемое значение

Индекс текущего выбранного элемента в списке; или CB_ERR, если элемент не выбран.

### <a name="remarks"></a>Комментарии

Индекс в списке отсчитывается от нуля.

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a> Кмфктулбаркомбобоксбуттон:: Жеткурселалл

Возвращает индекс текущего выбранного элемента в списке кнопки поля со списком, имеющей указанный идентификатор команды.

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды для поля со списком.

### <a name="return-value"></a>Возвращаемое значение

Индекс текущего выбранного элемента в списке; в противном случае CB_ERR, если элемент не выбран или не найдена кнопка поля со списком.

### <a name="remarks"></a>Комментарии

Индекс в списке отсчитывается от нуля.

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a> Кмфктулбаркомбобоксбуттон:: Жетедитктрл

Возвращает указатель на поле ввода в поле со списком.

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на поле ввода, если метод был успешным; в противном случае значение NULL.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a> Кмфктулбаркомбобоксбуттон:: "HWND"

Возвращает маркер окна для поля со списком.

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>Возвращаемое значение

Обработчик окна или значение NULL, если поле со списком не связано с объектом окна.

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a> Кмфктулбаркомбобоксбуттон:: DataItem

Возвращает строку, связанную с элементом по указанному индексу в поле со списком.

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>Параметры

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Указатель на строку, связанную с элементом; в противном случае значение NULL, если параметр индекса является недопустимым, или если параметр индекса имеет значение-1 и в поле со списком не выбран элемент.

### <a name="remarks"></a>Комментарии

Параметр индекса-1 возвращает строку выбранного в данный момент элемента.

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a> Кмфктулбаркомбобоксбуттон:: Жетитемалл

Возвращает строку, связанную с элементом по указанному индексу в поле со списком кнопки поля со списком, имеющей указанный идентификатор команды.

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды для поля со списком.

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Указатель на строку элемента, если метод был успешным; в противном случае значение NULL, если индекс недопустим, кнопка поля со списком не найдена или если индекс равен-1 и в поле со списком не выбран элемент.

### <a name="remarks"></a>Комментарии

Значение индекса, равное-1, возвращает строку выбранного в данный момент элемента.

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a> Кмфктулбаркомбобоксбуттон:: Жетитемдата

Возвращает данные, связанные с элементом по указанному индексу в поле со списком.

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>Параметры

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Данные, связанные с элементом; или 0, если элемент не существует.

### <a name="remarks"></a>Комментарии

Параметр индекса-1 возвращает данные, связанные с текущим выбранным элементом.

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a> Кмфктулбаркомбобоксбуттон:: Жетитемдатаалл

Возвращает данные, связанные с элементом по указанному индексу в поле со списком кнопки поля со списком, имеющей конкретный идентификатор команды.

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды для поля со списком.

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Данные, связанные с элементом, если метод был успешным; в противном случае значение 0, если указанный индекс является недопустимым, или CB_ERR, если не найдена кнопка поля со списком.

### <a name="remarks"></a>Комментарии

Параметр индекса-1 возвращает данные, связанные с текущим выбранным элементом.

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a> Кмфктулбаркомбобоксбуттон:: Жетитемдатаптралл

Возвращает данные, связанные с элементом по указанному индексу в поле со списком кнопки поля со списком, имеющей конкретный идентификатор команды. Эти данные возвращаются в виде указателя.

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды для поля со списком.

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Указатель, связанный с элементом, если метод был успешным; в противном случае — значение-1, если возникает ошибка, или NULL, если кнопка со списком не найдена.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a> Кмфктулбаркомбобоксбуттон:: @ Prompt

Возвращает строку запроса для кнопки поля со списком.

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>Возвращаемое значение

Строка запроса.

### <a name="remarks"></a>Комментарии

Этот метод в настоящее время не реализован.

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a> Кмфктулбаркомбобоксбуттон:: GetText

Возвращает текст в поле ввода.

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>Возвращаемое значение

Текст в поле ввода.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a> Кмфктулбаркомбобоксбуттон:: Жеттексталл

Получает текст в поле ввода кнопки поля со списком, имеющей указанный идентификатор команды.

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды определенного поля со списком.

### <a name="return-value"></a>Возвращаемое значение

Текст в поле ввода, если метод был успешным; в противном случае значение NULL.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a> Кмфктулбаркомбобоксбуттон:: Хасфокус

Указывает, находится ли фокус в поле со списком в данный момент.

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если поле со списком в данный момент имеет фокус; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Этот метод также возвращает значение TRUE, если любое дочернее окно поля со списком в данный момент имеет фокус.

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a> Кмфктулбаркомбобоксбуттон:: Исцентерверт

Возвращает вертикальное расположение кнопок со списком в приложении.

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если кнопки центрируются по центру; Значение FALSE, если кнопки вычисляются сверху.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a> Кмфктулбаркомбобоксбуттон:: Исфлатмоде

Возвращает внешний вид кнопок со списком в приложении в плоском стиле.

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если кнопки имеют плоский стиль; в противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Неструктурированный стиль по умолчанию для кнопок со списком имеет значение FALSE.

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a> Кмфктулбаркомбобоксбуттон:: Исовнероф

Указывает, связан ли указанный маркер с кнопкой поля со списком или с одним из его дочерних элементов.

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>Параметры

*HWND*<br/>
окне Обработчик окна.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если маркер ассокатед с кнопкой поля со списком или одним из его дочерних элементов. в противном случае — значение FALSE.

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a> Кмфктулбаркомбобоксбуттон:: Исриббонбуттон

Указывает, расположена ли кнопка поля со списком на панели ленты.

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>Возвращаемое значение

Всегда значение FALSE.

### <a name="remarks"></a>Remarks

По умолчанию этот метод всегда возвращает значение FALSE, означающее, что кнопка со списком никогда не отображается на панели ленты.

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a> Кмфктулбаркомбобоксбуттон:: Исвиндоввисибле

Возвращает состояние видимости кнопки поля со списком.

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>Возвращаемое значение

Состояние видимости кнопки поля со списком.

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a> Кмфктулбаркомбобоксбуттон:: Нотификомманд

Указывает, обрабатывает ли кнопка поля со списком сообщение.

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>Параметры

*инотификоде*<br/>
окне Сообщение уведомления, связанное с командой.

### <a name="return-value"></a>Возвращаемое значение

Обрабатывает ли кнопка поля со списком сообщение.

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a> Кмфктулбаркомбобоксбуттон:: Онаддтокустомизепаже

Вызывается структурой при добавлении кнопки в диалоговое окно " **Настройка** ".

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a> Кмфктулбаркомбобоксбуттон:: Онкалкулатесизе

Вызывается платформой для вычисления размера кнопки.

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>Параметры

*Хозяин*<br/>
окне Контекст устройства, на котором отображается кнопка со списком.

*сизедефаулт*<br/>
окне Размер по умолчанию кнопки поля со списком.

*бхорз*<br/>
окне Состояние закрепления родительской панели инструментов. Значение TRUE, если панель инструментов закреплена по горизонтали и FALSE, если панель инструментов закреплена по вертикали.

### <a name="return-value"></a>Возвращаемое значение

`SIZE`Структура, содержащая размеры кнопки поля со списком в пикселях.

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a> Кмфктулбаркомбобоксбуттон:: Ончанжепарентвнд

Вызывается структурой при вставке кнопки поля со списком в новую панель инструментов.

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>Параметры

*пвндпарент*<br/>
окне Указатель на новую родительскую панель инструментов.

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a> Кмфктулбаркомбобоксбуттон:: OnClick

Вызывается структурой при нажатии пользователем кнопки со списком.

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>Параметры

*Приводится*<br/>
окне Указатель на родительское окно кнопки поля со списком.

*бделай*<br/>
окне Зарезервировано для использования в производном классе.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если метод обрабатывает событие; в противном случае — значение FALSE.

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a> Кмфктулбаркомбобоксбуттон:: Онктлколор

Вызывается структурой, когда пользователь изменяет цвет родительской панели инструментов, устанавливая цвет кнопки поля со списком.

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>Параметры

*Хозяин*<br/>
окне Контекст устройства, на котором отображается кнопка со списком.

*нктлколор*<br/>
[in] Не используется.

### <a name="return-value"></a>Возвращаемое значение

Дескриптор кисти, используемой платформой для рисования фона кнопки поля со списком.

### <a name="remarks"></a>Комментарии

Этот метод также задает цвет текста кнопки поля со списком.

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a> Кмфктулбаркомбобоксбуттон:: OnDraw

Вызывается платформой для рисования кнопки поля со списком с использованием указанных стилей и параметров.

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>Параметры

*Хозяин*<br/>
окне Контекст устройства, на котором отображается кнопка.

*rect*<br/>
окне Ограничивающий прямоугольник кнопки.

*пимажес*<br/>
окне Коллекция изображений, связанных с кнопкой.

*бхорз*<br/>
окне Состояние закрепления родительской панели инструментов. Значение TRUE, если панель инструментов закреплена по горизонтали и FALSE, если панель инструментов закреплена по вертикали.

*бкустомиземоде*<br/>
окне Находится ли приложение в режиме настройки.

*бхигхлигхт*<br/>
окне Указывает, следует ли нарисовать выделенную кнопку поля со списком.

*бдравбордер*<br/>
окне Следует ли нарисовать кнопку поля со списком с границей.

*бграйдисабледбуттонс*<br/>
окне Значение TRUE для рисования затененных отключенных кнопок; Значение FALSE, чтобы использовать коллекцию отключенных изображений.

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a> Кмфктулбаркомбобоксбуттон:: Ондравонкустомизелист

Вызывается платформой для рисования кнопки со списком в области **команд** диалогового окна **Настройка** .

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>Параметры

*Хозяин*<br/>
окне Контекст устройства, на котором отображается кнопка со списком.

*rect*<br/>
окне Ограничивающий прямоугольник кнопки поля со списком.

*бселектед*<br/>
окне Значение TRUE, если выбрана кнопка поля со списком. в противном случае — значение FALSE.

### <a name="return-value"></a>Возвращаемое значение

Ширина (в пикселях) кнопки поля со списком.

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a> Кмфктулбаркомбобоксбуттон:: Онглобалфонтсчанжед

Вызывается платформой для установки шрифта кнопки поля со списком при изменении шрифта приложения.

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a> Кмфктулбаркомбобоксбуттон:: OnMove

Вызывается платформой для изменения положения кнопки поля со списком при перемещении родительской панели инструментов.

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a> Кмфктулбаркомбобоксбуттон:: onShow

Вызывается структурой при скрытии или отображении кнопки поля со списком.

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>Параметры

*bShow*<br/>
окне Указывает, следует ли скрывать или отображать кнопку в поле со списком.

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a> Кмфктулбаркомбобоксбуттон:: OnSize

Вызывается платформой для изменения размера кнопки поля со списком при изменении размера родительской панели инструментов.

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>Параметры

*исизе*<br/>
окне Новая ширина кнопки поля со списком.

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a> Кмфктулбаркомбобоксбуттон:: Онупдатетултип

Вызывается платформой, когда пользователь изменяет подсказку для кнопки поля со списком.

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>Параметры

*пвндпарент*<br/>
окне Указатель на родительское окно для кнопки поля со списком.

*ибуттониндекс*<br/>
окне Идентификатор кнопки поля со списком.

*вндтултип*<br/>
окне Всплывающая подсказка, связываемая с кнопкой поля со списком.

*str*<br/>
окне Текст подсказки.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если метод обрабатывает событие; в противном случае — значение FALSE.

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a> Кмфктулбаркомбобоксбуттон:: Ремовеаллитемс

Удаляет все элементы из полей списка и редактирования.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Комментарии

Удаляет все элементы из списка и элементы управления поля со списком.

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a> Кмфктулбаркомбобоксбуттон:: Селектитем

Выбирает элемент в списке.

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Параметры

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке.

*бнотифи*<br/>
окне Значение TRUE для уведомления кнопки поля со списком в выделенном фрагменте; в противном случае — FALSE.

*двдата*<br/>
окне Данные, связанные с элементом в списке.

*lpszText*<br/>
окне Текст элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если метод выполнен успешно; в противном случае — FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a> Кмфктулбаркомбобоксбуттон:: Селектитемалл

Выбирает элемент в списке кнопки поля со списком, имеющей указанный идентификатор команды.

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>Параметры

*уикмд*<br/>
окне Идентификатор команды поля со списком, содержащей список.

*ииндекс*<br/>
окне Отсчитываемый от нуля индекс элемента в списке. Значение-1 удаляет все текущие выбранные элементы из списка и очищает поле ввода.

*двдата*<br/>
окне Данные элемента в списке.

*lpszText*<br/>
окне Текст элемента в списке.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если метод выполнен успешно; в противном случае — FALSE.

### <a name="remarks"></a>Комментарии

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a> Кмфктулбаркомбобоксбуттон:: Serialize

Считывает этот объект из архива или записывает его в архив.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Параметры

*ar*<br/>
[вход, выход] `CArchive` Сериализуемый объект.

### <a name="remarks"></a>Комментарии

Параметры `CArchive` объекта определяют, производит ли этот метод чтение или запись в архив.

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a> Кмфктулбаркомбобоксбуттон:: Сетаккдата

Заполняет указанный объект с `CAccessibilityData` помощью данных о специальных возможностях поля со списком.

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>Параметры

*ппарент*<br/>
окне Родительское окно кнопки поля со списком.

*data*<br/>
заполняет `CAccessibilityData` Объект, который получает данные о специальных возможностях из поля со списком.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если метод выполнен успешно; в противном случае — FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a> Кмфктулбаркомбобоксбуттон:: Сетцентерверт

Задает вертикальное расположение кнопок поля со списком в приложении.

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>Параметры

*бцентерверт*<br/>
окне Значение TRUE, чтобы центрировать кнопку поля со списком на панели инструментов. Значение FALSE, чтобы согласовать кнопку поля со списком с верхней границей панели инструментов.

### <a name="remarks"></a>Комментарии

По умолчанию кнопки в поле со списком вычисляются по верхнему краю.

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a> Кмфктулбаркомбобоксбуттон:: Сетконтекстменуид

Задает идентификатор ресурса контекстного меню для кнопки поля со списком.

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>Параметры

*уиресид*<br/>
окне Идентификатор ресурса контекстного меню.

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a> Кмфктулбаркомбобоксбуттон:: Сетдропдовнхеигхт

Задает высоту поля со списком при его перетаскивании.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Параметры

*нхеигхт*<br/>
окне Высота (в пикселях) поля со списком.

### <a name="remarks"></a>Комментарии

Высота по умолчанию — 150 пикселей.

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a> Кмфктулбаркомбобоксбуттон:: Сетфлатмоде

Задает внешний вид кнопок со списком в приложении плоского стиля.

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>Параметры

*бфлат*<br/>
окне Значение TRUE для плоского внешнего вида; в противном случае — FALSE.

### <a name="remarks"></a>Комментарии

Неструктурированный стиль по умолчанию для кнопок со списком имеет значение FALSE.

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a> Кмфктулбаркомбобоксбуттон:: SetStyle

Задает указанный стиль для кнопки поля со списком и перерисовывает элемент управления, если он не отключен.

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>Параметры

*nStyle*<br/>
окне Побитовое сочетание (или) стилей панелей инструментов.

### <a name="remarks"></a>Комментарии

Список стилей кнопок панели инструментов см. в разделе [стили элементов управления ToolBar](../../mfc/reference/toolbar-control-styles.md) .

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a> Кмфктулбаркомбобоксбуттон:: SetText

Задает текст в поле ввода кнопки поля со списком.

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Параметры

*lpszText*<br/>
окне Указатель на строку, содержащую текст для поля ввода.

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[Класс CComboBox](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar:: Реплацебуттон](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[Пошаговое руководство. размещение элементов управления на панелях инструментов](../../mfc/walkthrough-putting-controls-on-toolbars.md)
