---
description: 'Дополнительные сведения о: Кваиткурсор Class'
title: Класс Кваиткурсор
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 5d2323e3be78154c6a9d3ded55ab9e1a951d78b7
ms.sourcegitcommit: 6183207b11575d7b44ebd7c18918e916a0d8c63d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/06/2021
ms.locfileid: "97951504"
---
# <a name="cwaitcursor-class"></a>Класс Кваиткурсор

Предоставляет односторонний способ отображения курсора ожидания (который обычно отображается как песочные часы) при выполнении длительной операции.

## <a name="syntax"></a>Синтаксис

```
class CWaitCursor
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Кваиткурсор:: Кваиткурсор](#cwaitcursor)|Конструирует `CWaitCursor` объект и отображает курсор ожидания.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[Кваиткурсор:: RESTORE](#restore)|Восстанавливает курсор ожидания после его изменения.|

## <a name="remarks"></a>Комментарии

`CWaitCursor` не имеет базового класса.

Для работы с хорошей практикой программирования Windows необходимо, чтобы при выполнении операции, которая занимает значительное время, отображался курсор ожидания.

Чтобы отобразить курсор ожидания, просто определите `CWaitCursor` переменную перед кодом, выполняющим длительную операцию. Конструктор объекта автоматически вызывает отображение курсора ожидания.

Когда объект выходит из области действия (в конце блока, в котором `CWaitCursor` объявлен объект), его деструктор устанавливает курсор на предыдущий курсор. Иными словами, объект выполняет необходимую очистку автоматически.

> [!NOTE]
> Поскольку конструкторы и деструкторы работают, `CWaitCursor` объекты всегда объявляются как локальные переменные — они никогда не объявляются как глобальные переменные и не выделяются с помощью **`new`** .

При выполнении операции, которая может вызвать изменение курсора, например отображение окна сообщения или диалогового окна, вызовите функцию-член [RESTORE](#restore) , чтобы восстановить курсор ожидания. Можно вызывать, `Restore` даже если в данный момент отображается курсор ожидания.

Еще один способ отобразить курсор ожидания — использовать сочетание [от CCmdTarget:: бегинваиткурсор](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [от CCmdTarget:: ендваиткурсор](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)и, возможно, [от CCmdTarget:: рестореваиткурсор](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Однако `CWaitCursor` проще использовать, так как при выполнении длительной операции не нужно устанавливать курсор на предыдущий курсор.

> [!NOTE]
> MFC устанавливает и восстанавливает курсор с помощью виртуальной функции [CWinApp::D оваиткурсор](../../mfc/reference/cwinapp-class.md#dowaitcursor) . Эту функцию можно переопределить, чтобы обеспечить пользовательское поведение.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`CWaitCursor`

## <a name="requirements"></a>Требования

**Заголовок:** afxwin.h

## <a name="example"></a>Пример

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a> Кваиткурсор:: Кваиткурсор

Чтобы отобразить курсор ожидания, просто объявите `CWaitCursor` объект перед кодом, выполняющим длительную операцию.

```
CWaitCursor();
```

### <a name="remarks"></a>Комментарии

Конструктор автоматически вызывает отображение курсора ожидания.

Когда объект выходит из области действия (в конце блока, в котором `CWaitCursor` объявлен объект), его деструктор устанавливает курсор на предыдущий курсор. Иными словами, объект выполняет необходимую очистку автоматически.

Можно воспользоваться преимуществами того факта, что деструктор вызывается в конце блока (который может предшествовать концу функции), чтобы активировать курсор ожидания только в части функции. Этот метод показан во втором примере ниже.

> [!NOTE]
> Поскольку конструкторы и деструкторы работают, `CWaitCursor` объекты всегда объявляются как локальные переменные — они никогда не объявляются как глобальные переменные и не выделяются с помощью **`new`** .

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a> Кваиткурсор:: RESTORE

Чтобы восстановить курсор ожидания, вызовите эту функцию после выполнения операции, например отображения окна сообщения или диалогового окна, которое может изменить курсор ожидания на другой курсор.

```cpp
void Restore();
```

### <a name="remarks"></a>Комментарии

Можно вызывать, `Restore` даже если в данный момент отображается курсор ожидания.

Если необходимо восстановить курсор ожидания в функции, отличной от той, в которой `CWaitCursor` объявлен объект, можно вызвать [от CCmdTarget:: рестореваиткурсор](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>См. также раздел

[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[От CCmdTarget:: Бегинваиткурсор](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[От CCmdTarget:: Ендваиткурсор](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[От CCmdTarget:: Рестореваиткурсор](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::D Оваиткурсор](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[Изменение указателя мыши для окна в MFC с помощью Visual C++](/troubleshoot/cpp/change-mouse-pointer-window-mfc)
