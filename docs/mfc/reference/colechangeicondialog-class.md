---
description: 'Дополнительные сведения о: Колечанжеикондиалог Class'
title: Класс Колечанжеикондиалог
ms.date: 11/04/2016
f1_keywords:
- COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::COleChangeIconDialog
- AFXODLGS/COleChangeIconDialog::DoChangeIcon
- AFXODLGS/COleChangeIconDialog::DoModal
- AFXODLGS/COleChangeIconDialog::GetIconicMetafile
- AFXODLGS/COleChangeIconDialog::m_ci
helpviewer_keywords:
- COleChangeIconDialog [MFC], COleChangeIconDialog
- COleChangeIconDialog [MFC], DoChangeIcon
- COleChangeIconDialog [MFC], DoModal
- COleChangeIconDialog [MFC], GetIconicMetafile
- COleChangeIconDialog [MFC], m_ci
ms.assetid: 8d6e131b-ddbb-4dff-a432-f239efda8e3d
ms.openlocfilehash: 5ec6113bbcf63462380f18c4ac52abbb8706c8d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209962"
---
# <a name="colechangeicondialog-class"></a>Класс Колечанжеикондиалог

Используется для диалогового окна OLE "Изменить значок".

## <a name="syntax"></a>Синтаксис

```
class COleChangeIconDialog : public COleDialog
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Колечанжеикондиалог:: Колечанжеикондиалог](#colechangeicondialog)|Формирует объект `COleChangeIconDialog`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Колечанжеикондиалог::D Очанжеикон](#dochangeicon)|Выполняет изменение, указанное в диалоговом окне.|
|[Колечанжеикондиалог::D Омодал](#domodal)|Отображает диалоговое окно «Изменение значка OLE 2».|
|[Колечанжеикондиалог:: Жетиконикметафиле](#geticonicmetafile)|Возвращает маркер для метафайла, связанного со значком этого элемента.|

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Описание|
|----------|-----------------|
|[Колечанжеикондиалог:: m_ci](#m_ci)|Структура, которая управляет поведением диалогового окна.|

## <a name="remarks"></a>Комментарии

Создайте объект класса, `COleChangeIconDialog` Если нужно вызвать это диалоговое окно. После создания `COleChangeIconDialog` объекта можно использовать структуру [m_ci](#m_ci) для инициализации значений или состояний элементов управления в диалоговом окне. `m_ci`Структура имеет тип олеуичанжеикон. Дополнительные сведения об использовании этого класса диалогового окна см. в описании функции члена [DoModal](#domodal) .

Дополнительные сведения см. в описании структуры [олеуичанжеикон](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) в Windows SDK.

Дополнительные сведения о диалоговых окнах, связанных с OLE, см. в разделе [диалоговые окна статьи в OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COleChangeIconDialog`

## <a name="requirements"></a>Требования

**Заголовок:** афксодлгс. h

## <a name="colechangeicondialogcolechangeicondialog"></a><a name="colechangeicondialog"></a> Колечанжеикондиалог:: Колечанжеикондиалог

Эта функция конструирует только `COleChangeIconDialog` объект.

```
explicit COleChangeIconDialog(
    COleClientItem* pItem,
    DWORD dwFlags = CIF_SELECTCURRENT,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Параметры

*питем*<br/>
Указывает на элемент для преобразования.

*dwFlags*<br/>
Флаг создания, который содержит любое число следующих значений, Объединенных с помощью оператора побитового или:

- CIF_SELECTCURRENT указывает, что при вызове диалогового окна будет выбран текущий переключатель. Это значение по умолчанию.

- CIF_SELECTDEFAULT указывает, что при вызове диалогового окна будет выбран переключатель по умолчанию.

- CIF_SELECTFROMFILE указывает, что при вызове диалогового окна будет выбран переключатель из файла изначально.

- CIF_SHOWHELP Указывает, что при вызове диалогового окна появится кнопка Справка.

- CIF_USEICONEXE указывает, что значок должен быть извлечен из исполняемого файла, указанного в `szIconExe` поле [m_ci](#m_ci) вместо того, чтобы быть полученным из типа. Это полезно для внедрения или связывания файлов, отличных от OLE.

*ппарентвнд*<br/>
Указывает на родительский элемент или объект окна-владельца (типа `CWnd` ), которому принадлежит объект диалогового окна. Если значение равно NULL, то родительское окно диалогового окна будет установлено в главное окно приложения.

### <a name="remarks"></a>Комментарии

Чтобы открыть диалоговое окно, вызовите функцию [DoModal](#domodal) .

Дополнительные сведения см. в описании структуры [олеуичанжеикон](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) в Windows SDK.

## <a name="colechangeicondialogdochangeicon"></a><a name="dochangeicon"></a> Колечанжеикондиалог::D Очанжеикон

Вызовите эту функцию, чтобы изменить значок, представляющий элемент, в тот, который выбран в диалоговом окне после [DoModal](#domodal) возвращает идок.

```
BOOL DoChangeIcon(COleClientItem* pItem);
```

### <a name="parameters"></a>Параметры

*питем*<br/>
Указывает на элемент, значок которого изменяется.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если изменение выполнено успешно; в противном случае — 0.

## <a name="colechangeicondialogdomodal"></a><a name="domodal"></a> Колечанжеикондиалог::D Омодал

Эта функция вызывается для вывода диалогового окна «значок изменения OLE».

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Возвращаемое значение

Состояние завершения для диалогового окна. Одно из следующих значений:

- ИДОК, если диалоговое окно было успешно отображено.

- ИДКАНЦЕЛ, если пользователь отменил диалоговое окно.

- ИДАБОРТ, если произошла ошибка. Если возвращается ИДАБОРТ, вызовите `COleDialog::GetLastError` функцию-член, чтобы получить дополнительные сведения о типе произошедшей ошибки. Список возможных ошибок см. в описании функции [олеуичанжеикон](/windows/win32/api/oledlg/nf-oledlg-oleuichangeiconw) в Windows SDK.

### <a name="remarks"></a>Комментарии

Если требуется инициализировать различные элементы управления диалогового окна путем установки элементов структуры [m_ci](#m_ci) , следует сделать это перед вызовом метода `DoModal` , но после создания объекта диалогового окна.

Если `DoModal` ВОЗВРАЩАЕТ идок, можно вызвать другие функции, чтобы получить параметры или сведения, введенные пользователем в диалоговое окно.

## <a name="colechangeicondialoggeticonicmetafile"></a><a name="geticonicmetafile"></a> Колечанжеикондиалог:: Жетиконикметафиле

Вызовите эту функцию, чтобы получить маркер для метафайла, содержащего значок выбранного элемента.

```
HGLOBAL GetIconicMetafile() const;
```

### <a name="return-value"></a>Возвращаемое значение

Маркер для метафайла, содержащего значок нового значка, если диалоговое окно было закрыто нажатием кнопки **ОК**. в противном случае — значок, находился перед отображением диалогового окна.

## <a name="colechangeicondialogm_ci"></a><a name="m_ci"></a> Колечанжеикондиалог:: m_ci

Структура типа ОЛЕУИЧАНЖЕИКОН, используемая для управления поведением диалогового окна «Изменение значка».

```
OLEUICHANGEICON m_ci;
```

### <a name="remarks"></a>Комментарии

Члены этой структуры можно изменять напрямую или с помощью функций-членов.

Дополнительные сведения см. в описании структуры [олеуичанжеикон](/windows/win32/api/oledlg/ns-oledlg-oleuichangeiconw) в Windows SDK.

## <a name="see-also"></a>См. также раздел

[Класс Коледиалог](../../mfc/reference/coledialog-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Класс Коледиалог](../../mfc/reference/coledialog-class.md)
