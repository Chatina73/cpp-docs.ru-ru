---
description: 'Дополнительные сведения о: Кклиентдк Class'
title: Класс Кклиентдк
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: 27735929734388ccb25eaf178e49d63884beed0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122464"
---
# <a name="cclientdc-class"></a>Класс Кклиентдк

Позаботится о вызове функций Windows, [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) во время создания и [релеаседк](/windows/win32/api/winuser/nf-winuser-releasedc) в момент уничтожения.

## <a name="syntax"></a>Синтаксис

```
class CClientDC : public CDC
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[Кклиентдк:: Кклиентдк](#cclientdc)|Конструирует `CClientDC` объект, подключенный к `CWnd` .|

### <a name="protected-data-members"></a>Защищенные члены данных

|Имя|Описание|
|----------|-----------------|
|[Кклиентдк:: m_hWnd](#m_hwnd)|HWND окна, для которого это `CClientDC` допустимо.|

## <a name="remarks"></a>Комментарии

Это означает, что контекст устройства, связанный с `CClientDC` объектом, является клиентской областью окна.

Дополнительные сведения о см `CClientDC` . в разделе [контексты устройств](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Требования

**Заголовок:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a> Кклиентдк:: Кклиентдк

Конструирует `CClientDC` объект, обращающийся к клиентской области [CWnd](../../mfc/reference/cwnd-class.md) , на которую указывает *приводится*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Параметры

*Приводится*<br/>
Окно, в клиентской области которого будет доступ объект контекста устройства.

### <a name="remarks"></a>Комментарии

Конструктор вызывает функцию Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Исключение (типа `CResourceException` ) создается при `GetDC` сбое вызова Windows. Контекст устройства может быть недоступен, если в Windows уже выделены все доступные контексты устройств. Приложение будет конкурировать за пять распространенных контекстов вывода, доступных в любой момент в Windows.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a> Кклиентдк:: m_hWnd

Объект `HWND` указателя, `CWnd` используемый для создания `CClientDC` объекта.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Комментарии

*m_hWnd* является защищенной переменной.

### <a name="example"></a>Пример

  См. пример для [кклиентдк:: кклиентдк](#cclientdc).

## <a name="see-also"></a>См. также раздел

[Образец MDI-формы MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC, класс](../../mfc/reference/cdc-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[CDC, класс](../../mfc/reference/cdc-class.md)
