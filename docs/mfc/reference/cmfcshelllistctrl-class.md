---
description: 'Дополнительные сведения о: Кмфкшелллистктрл Class'
title: Класс Кмфкшелллистктрл
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: b5efc8f336c5958ad7a7f510c7f2b69e83ca6bca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339687"
---
# <a name="cmfcshelllistctrl-class"></a>Класс Кмфкшелллистктрл

`CMFCShellListCtrl`Класс предоставляет функциональные возможности элемента управления "список" Windows и расширяет его, включая возможность отображать список элементов оболочки.

## <a name="syntax"></a>Синтаксис

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>Члены

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Кмфкшелллистктрл::D Исплайфолдер](#displayfolder)|Отображает список элементов, содержащихся в указанной папке.|
|[Кмфкшелллистктрл::D Исплайпарентфолдер](#displayparentfolder)|Отображает список элементов, содержащихся в папке, которая является родительской по отношению к отображаемой в данный момент папке.|
|[Кмфкшелллистктрл:: Енаблешеллконтекстмену](#enableshellcontextmenu)|Включает или отключает контекстное меню.|
|[Кмфкшелллистктрл:: Жеткуррентфолдер](#getcurrentfolder)|Извлекает путь к текущей папке.|
|[Кмфкшелллистктрл:: Жеткуррентфолдернаме](#getcurrentfoldername)|Возвращает имя текущей папки.|
|[Кмфкшелллистктрл:: Жеткуррентитемидлист](#getcurrentitemidlist)|Возвращает ПИДЛ текущего элемента управления "список".|
|[Кмфкшелллистктрл:: Жеткуррентшеллфолдер](#getcurrentshellfolder)|Возвращает указатель на текущую папку оболочки.|
|[Кмфкшелллистктрл:: Жетитемпас](#getitempath)|Возвращает текстовый путь к элементу.|
|[Кмфкшелллистктрл:: ItemType](#getitemtypes)|Возвращает типы элементов оболочки, отображаемые элементом управления "список".|
|[Кмфкшелллистктрл:: Настольная](#isdesktop)|Проверяет, является ли текущая выбранная папка папкой рабочего стола.|
|[Кмфкшелллистктрл:: Онкомпареитемс](#oncompareitems)|Платформа вызывает этот метод при сравнении двух элементов. (Переопределяет [кмфклистктрл:: онкомпареитемс](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).)|
|[Кмфкшелллистктрл:: Онформатфиледате](#onformatfiledate)|Вызывается, когда платформа получает файловую дату, отображаемую элементом управления "список".|
|[Кмфкшелллистктрл:: Онформатфилесизе](#onformatfilesize)|Вызывается, когда платформа преобразует размер файла элемента управления "список".|
|[Кмфкшелллистктрл:: Онжетитемикон](#ongetitemicon)|Вызывается, когда платформа получает значок элемента управления "список".|
|[Кмфкшелллистктрл:: Онжетитемтекст](#ongetitemtext)|Вызывается, когда платформа преобразует текст элемента элемента управления "список".|
|[Кмфкшелллистктрл:: Онсетколумнс](#onsetcolumns)|Вызывается платформой, когда задаются имена столбцов.|
|[Кмфкшелллистктрл:: Refresh](#refresh)|Обновляет и перерисовывает элемент управления "список".|
|[Кмфкшелллистктрл:: Сетитемтипес](#setitemtypes)|Задает тип элементов, отображаемых элементом управления "список".|

## <a name="remarks"></a>Комментарии

`CMFCShellListCtrl`Класс расширяет функциональные возможности [класса кмфклистктрл](../../mfc/reference/cmfclistctrl-class.md) , позволяя программе выводить список элементов оболочки Windows. Используемый формат отображения аналогичен представлению в виде списка для окна обозревателя.

Объект [кмфкшеллтриктрл](../../mfc/reference/cmfcshelltreectrl-class.md) может быть связан с `CMFCShellListCtrl` объектом для создания полного окна проводника. Затем, выбрав элемент в, `CMFCShellTreeCtrl` `CMFCShellListCtrl` объект будет вычислять содержимое выбранного элемента.

## <a name="example"></a>Пример

В следующем примере демонстрируется создание объекта `CMFCShellListCtrl` класса и отображение родительской папки в отображаемой в данный момент папке. Этот фрагмент кода является частью [примера обозревателя](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>Требования

**Заголовок:** афксшелллистктрл. h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a> Кмфкшелллистктрл::D Исплайфолдер

Отображает список элементов, содержащихся в указанной папке.

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>Параметры

*лпсзпас*<br/>
окне Строка, содержащая путь к папке.

*лпитеминфо*<br/>
окне Указатель на `LPAFX_SHELLITEMINFO` структуру, описывающую отображаемую папку.

### <a name="return-value"></a>Возвращаемое значение

S_OK в случае успеха; В противном случае E_FAIL.

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a> Кмфкшелллистктрл::D Исплайпарентфолдер

Обновляет объект [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) для отображения родительской папки в отображаемой в данный момент папке.

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>Возвращаемое значение

S_OK в случае успеха; В противном случае E_FAIL.

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a> Кмфкшелллистктрл:: Енаблешеллконтекстмену

Включает контекстное меню.

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Параметры

*bEnable*<br/>
окне Логическое значение, указывающее, включает ли платформа контекстное меню.

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a> Кмфкшелллистктрл:: Жеткуррентфолдер

Извлекает путь к выбранной папке в объекте [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>Параметры

*strPath*<br/>
заполняет Ссылка на строковый параметр, в котором метод записывает путь.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение в случае успешного выполнения. В противном случае — 0.

### <a name="remarks"></a>Комментарии

Этот метод завершается ошибкой, если в не выбрана папка `CMFCShellListCtrl` .

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a> Кмфкшелллистктрл:: Жеткуррентфолдернаме

Извлекает имя выбранной в данный момент папки в объекте [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>Параметры

*strName*<br/>
заполняет Ссылка на строковый параметр, в котором метод записывает имя.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение в случае успешного выполнения. В противном случае — 0.

### <a name="remarks"></a>Комментарии

Этот метод завершается ошибкой, если в не выбрана папка `CMFCShellListCtrl` .

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a> Кмфкшелллистктрл:: Жеткуррентитемидлист

Возвращает ПИДЛ текущего выбранного элемента.

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>Возвращаемое значение

ПИДЛ текущего элемента.

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a> Кмфкшелллистктрл:: Жеткуррентшеллфолдер

Возвращает указатель на текущий выбранный элемент в объекте [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на [интерфейс ишеллфолдер](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder) для выбранного объекта.

### <a name="remarks"></a>Комментарии

Этот метод возвращает значение NULL, если в данный момент ни один объект не выбран.

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a> Кмфкшелллистктрл:: Жетитемпас

Извлекает путь к элементу.

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>Параметры

*strPath*<br/>
заполняет Ссылка на строку, которая получает путь.

*iItem*<br/>
окне Индекс элемента списка.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE в случае успешного выполнения. В противном случае — значение FALSE.

### <a name="remarks"></a>Комментарии

Индекс, предоставляемый *Член iItem* , основан на элементах, которые в настоящее время отображаются объектом [класса кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a> Кмфкшелллистктрл:: ItemType

Возвращает тип элементов, отображаемых объектом [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение [шконтф](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf) , содержащее тип элементов, перечисленных в `CMFCShellListCtrl` .

### <a name="remarks"></a>Комментарии

Чтобы задать тип элементов, перечисленных в `CMFCShellListCtrl` , вызовите [кмфкшелллистктрл:: сетитемтипес](#setitemtypes).

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a> Кмфкшелллистктрл:: Настольная

Определяет, является ли папка, отображаемая в объекте [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) , папкой рабочего стола.

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если отображаемая папка является папкой рабочего стола; В противном случае — значение FALSE.

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a> Кмфкшелллистктрл:: Онкомпареитемс

Дополнительные сведения см. в исходном коде, расположенном в папке **VC \\ атлмфк \\ src \\ MFC** в установке Visual Studio.

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>Параметры

окне *lParam1*<br/>
окне *lParam2*<br/>
окне *иколумн*<br/>

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Комментарии

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a> Кмфкшелллистктрл:: Онформатфиледате

Платформа вызывает этот метод, когда он должен преобразовать дату, связанную с объектом, в строку.

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>Параметры

*тмфиле*<br/>
окне Дата, связанная с файлом.

*str*<br/>
заполняет Строка, содержащая отформатированную дату файла.

### <a name="remarks"></a>Комментарии

Когда объект [класса кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) отображает дату, связанную с файлом, она должна преобразовать эту дату в строковый формат. `CMFCShellListCtrl`Использует этот метод для выполнения преобразования. По умолчанию этот метод использует текущий языковой стандарт для форматирования даты в строку.

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a> Кмфкшелллистктрл:: Онформатфилесизе

Платформа вызывает этот метод при преобразовании размера объекта в строку.

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>Параметры

*лфилесизе*<br/>
окне Размер файла, который будет отображаться в платформе.

*str*<br/>
заполняет Строка, содержащая отформатированный размер файла.

### <a name="remarks"></a>Комментарии

Когда объекту [класса кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) требуется отобразить размер файла, он должен преобразовать размер файла в строковый формат. `CMFCShellListCtrl`Использует этот метод для выполнения преобразования. По умолчанию этот метод преобразует размер файла из байтов в килобайты, а затем использует текущий языковой стандарт для форматирования размера в строку.

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a> Кмфкшелллистктрл:: Онжетитемикон

Платформа вызывает этот метод для получения значка, связанного с элементом списка оболочки.

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Параметры

*iItem*<br/>
окне Индекс элемента.

*питем*<br/>
окне Параметр LPAFX_SHELLITEMINFO, описывающий элемент.

### <a name="return-value"></a>Возвращаемое значение

Индекс изображения значка в случае успеха; значение-1, если функция завершается ошибкой.

### <a name="remarks"></a>Комментарии

Индекс изображения значка основан на списке образов системы.

По умолчанию этот метод использует параметр *питем* . Значение *Член iItem* не используется в реализации по умолчанию. *Член iItem* можно использовать для реализации пользовательского поведения.

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a> Кмфкшелллистктрл:: Онжетитемтекст

Платформа вызывает этот метод, когда он должен получить текст элемента оболочки.

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>Параметры

*iItem*<br/>
окне Индекс элемента.

*иколумн*<br/>
окне Интересующий столбец.

*питем*<br/>
окне Параметр LPAFX_SHELLITEMINFO, описывающий элемент.

### <a name="return-value"></a>Возвращаемое значение

Значение типа `CString` , содержащее текст, связанный с элементом.

### <a name="remarks"></a>Комментарии

Каждый элемент в `CMFCShellListCtrl` объекте может содержать текст в одном или нескольких столбцах. Когда платформа вызывает этот метод, он указывает столбец, в котором он заинтересован. При вызове этой функции вручную необходимо также указать интересующий вас столбец.

По умолчанию этот метод использует параметр *питем* , чтобы определить, какой элемент обрабатывать. Значение *Член iItem* не используется в реализации по умолчанию.

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a> Кмфкшелллистктрл:: Онсетколумнс

Платформа вызывает этот метод, когда задаются имена столбцов.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Комментарии

По умолчанию платформа создает четыре столбца в `CMFCShellListCtrl` объекте. Имена этих столбцов: **имя**, **Размер**, **тип** и **изменено**. Этот метод можно переопределить для настройки количества столбцов и их имен.

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a> Кмфкшелллистктрл:: Refresh

Обновляет и перерисовывает объект [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>Возвращаемое значение

`S_OK` в случае успеха. в противном случае — значение ошибки.

### <a name="remarks"></a>Комментарии

Вызовите этот метод, чтобы обновить список элементов, отображаемых `CMFCShellListCtrl` объектом.

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a> Кмфкшелллистктрл:: Сетитемтипес

Задает тип элементов, перечисленных в объекте [кмфкшелллистктрл](../../mfc/reference/cmfcshelllistctrl-class.md) .

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>Параметры

*нтипес*<br/>
окне Список типов элементов, `CMFCShellListCtrl` поддерживаемых объектом.

### <a name="remarks"></a>Комментарии

Дополнительные сведения о списке типов элементов см. в разделе [шконтф](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf).

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс Кмфклистктрл](../../mfc/reference/cmfclistctrl-class.md)<br/>
[Класс Кмфкшеллтриктрл](../../mfc/reference/cmfcshelltreectrl-class.md)
