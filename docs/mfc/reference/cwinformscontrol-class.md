---
description: 'Дополнительные сведения о: Квинформсконтрол Class'
title: Класс Квинформсконтрол
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: 32daf5f1bf9efcd5d5b17d134dc8deaee7e32527
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318446"
---
# <a name="cwinformscontrol-class"></a>Класс Квинформсконтрол

Предоставляет базовую функцию для размещения элементов управления Windows Forms.

## <a name="syntax"></a>Синтаксис

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Параметры

*тманажедконтрол*<br/>
Элемент управления Windows Forms .NET Framework, отображаемый в приложении MFC.

## <a name="members"></a>Элементы

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Квинформсконтрол:: Квинформсконтрол](#cwinformscontrol)|Конструирует объект-оболочку элемента управления MFC Windows Forms.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Квинформсконтрол:: Креатеманажедконтрол](#createmanagedcontrol)|Создает элемент управления Windows Forms в контейнере MFC.|
|[Квинформсконтрол:: oncontrol](#getcontrol)|Извлекает указатель на элемент управления Windows Forms.|
|[Квинформсконтрол:: Жетконтролхандле](#getcontrolhandle)|Извлекает маркер элемента управления Windows Forms.|

### <a name="public-operators"></a>Открытые операторы

|Имя|Описание|
|----------|-----------------|
|[Квинформсконтрол:: operator —&gt;](#operator_-_gt)|Заменяет [квинформсконтрол:: oncontrol](#getcontrol) в выражениях.|
|[Квинформсконтрол:: operator Тманажедконтрол ^](#operator_tmanagedcontrol)|Приводит тип в качестве указателя на элемент управления Windows Forms.|

## <a name="remarks"></a>Комментарии

`CWinFormsControl`Класс предоставляет базовые функции для размещения элемента управления Windows Forms.

Дополнительные сведения об использовании Windows Forms см. в разделе [Использование пользовательского элемента управления формы Windows в MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Код MFC не должен кэшировать дескрипторы окна (обычно хранится в `m_hWnd` ). Некоторые свойства элемента управления Windows Forms требуется, чтобы базовый Win32 `Window` был уничтожен и создан заново с помощью `DestroyWindow` и `CreateWindow` . Реализация Windows Forms MFC обрабатывает `Destroy` `Create` события и элементов управления для обновления `m_hWnd` элемента.

> [!NOTE]
> Интеграция с MFC Windows Forms работает только в проектах, которые динамически связываются с MFC (в котором определен AFXDLL).

## <a name="requirements"></a>Требования

**Заголовок:** афксвинформс. h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a> Квинформсконтрол:: Креатеманажедконтрол

Создает элемент управления Windows Forms в контейнере MFC.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>Параметры

*птипе*<br/>
Тип данных создаваемого элемента управления. Должен быть типом [данных.](/dotnet/api/system.type)

*двстиле*<br/>
Стиль окна, применяемого к элементу управления. Укажите сочетание [стилей окна](../../mfc/reference/styles-used-by-mfc.md#window-styles). В настоящее время поддерживаются только следующие стили: WS_TABSTOP, WS_VISIBLE, WS_DISABLED и WS_GROUP.

*rect*<br/>
[Структура Rect](/windows/win32/api/windef/ns-windef-rect) , определяющая координаты левого верхнего и правого нижнего угла элемента управления (только первая перегрузка).

*нплацехолдерид*<br/>
Маркер статического элемента управления "геодержательное место", помещенный в редактор ресурсов. Вновь созданный элемент управления Windows Forms заменяет статический элемент управления, предполагая, что его положение, z-порядок и стили (только вторая перегрузка).

*ппарентвнд*<br/>
Указатель на родительское окно.

*nID*<br/>
ИДЕНТИФИКАЦИОНный номер ресурса, назначаемый только что созданному элементу управления.

*pControl*<br/>
Экземпляр элемента управления Windows Forms, который должен быть связан с объектом [квинформсконтрол](../../mfc/reference/cwinformscontrol-class.md) (только четвертая перегрузка).

### <a name="return-value"></a>Возвращаемое значение

В случае успеха возвращает ненулевое значение. В случае неудачи возвращает ноль.

### <a name="remarks"></a>Комментарии

Этот метод создает экземпляр элемента управления .NET Framework Windows Forms в контейнере MFC.

Первая перегрузка метода принимает .NET Framework типа данных *птипе* , чтобы MFC мог создать экземпляр нового объекта этого типа. *птипе* должен быть типом [данных.](/dotnet/api/system.type)

Вторая перегрузка метода создает Windows Forms элемент управления на основе `TManagedControl` параметра шаблона `CWinFormsControl` класса. Размер и расположение элемента управления основаны на `RECT` структуре, передаваемой методу. Для стилей *двстиле* имеет значение.

Третья перегрузка метода создает элемент управления Windows Forms, который заменяет статический элемент управления, уничтожая его и предполагают его положение, z-порядок и стили. Статический элемент управления служит только в качестве заполнителя для элемента управления Windows Forms. При создании элемента управления эта перегрузка объединяет стили из *двстиле* со стилями ресурсов статического элемента управления.

Четвертая перегрузка метода позволяет передавать уже созданный экземпляр Windows Forms управления *пконтрол* , который будет переноситься в MFC. Он должен иметь тот же тип, что и `TManagedControl` параметр шаблона `CWinFormsControl` класса.

Примеры использования элементов управления Windows Form см. [в разделе Использование пользовательского элемента управления формы Windows в MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) .

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a> Квинформсконтрол:: Квинформсконтрол

Конструирует объект-оболочку элемента управления MFC Windows Forms.

```
CWinFormsControl();
```

### <a name="remarks"></a>Комментарии

Экземпляр элемента управления Windows Forms создается при вызове [квинформсконтрол:: креатеманажедконтрол](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a> Квинформсконтрол:: oncontrol

Извлекает указатель на элемент управления Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на элемент управления Windows Forms.

### <a name="example"></a>Пример

  См. раздел [квинформсконтрол:: креатеманажедконтрол](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a> Квинформсконтрол:: Жетконтролхандле

Извлекает маркер элемента управления Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает маркер для элемента управления Windows Forms.

### <a name="remarks"></a>Комментарии

`GetControlHandle` — Это вспомогательный метод, возвращающий маркер окна, хранящийся в свойствах элемента управления .NET Framework. Значение обработчика окна копируется в [CWnd:: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) во время вызова [CWnd:: Attach](../../mfc/reference/cwnd-class.md#attach).

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a> Квинформсконтрол:: operator —&gt;

Заменяет [квинформсконтрол:: oncontrol](#getcontrol) в выражениях.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Комментарии

Этот оператор предоставляет удобный синтаксис, который заменяет `GetControl` выражения.

Дополнительные сведения о Windows Forms см. в разделе [Использование пользовательского элемента управления формы Windows в MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a> Квинформсконтрол:: operator Тманажедконтрол ^

Приводит тип в качестве указателя на элемент управления Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Комментарии

Этот оператор передает `CWinFormsControl<TManagedControl>` функции, которые принимают указатель на элемент управления Windows Forms.

## <a name="see-also"></a>См. также раздел

[Класс Квинформсдиалог](../../mfc/reference/cwinformsdialog-class.md)<br/>
[Класс Квинформсвиев](../../mfc/reference/cwinformsview-class.md)
