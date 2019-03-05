---
title: Класс CDynamicChain
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4b68198c17d7bd030b88bc78ad4de1367c914703
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299158"
---
# <a name="cdynamicchain-class"></a>Класс CDynamicChain

Этот класс предоставляет методы, поддержки динамической цепочки схемы сообщений.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
class CDynamicChain
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|Конструктор.|
|[CDynamicChain:: ~ CDynamicChain](#dtor)|Деструктор|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание:|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|Направляет сообщение Windows для схемы сообщений другим объектом.|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|Удаляет запись сопоставления сообщения из коллекции.|
|[CDynamicChain::SetChainEntry](#setchainentry)|Добавляет запись сопоставления сообщений в коллекцию или изменяет существующую запись.|

## <a name="remarks"></a>Примечания

`CDynamicChain` Управляет коллекцией схемы сообщений, включение Windows сообщение направляется во время выполнения, в схеме сообщений другим объектом.

Чтобы добавить поддержку динамической цепочки для схем сообщений, сделайте следующее:

- Наследование класса из `CDynamicChain`. В схеме сообщений, укажите [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) макрос цепочку в схеме сообщений другим объектом по умолчанию.

- Каждый класс, требуется цепочку сертификатов до из [CMessageMap](../../atl/reference/cmessagemap-class.md). `CMessageMap` позволяет объекту предоставлять его схемы сообщений к другим объектам.

- Вызовите `CDynamicChain::SetChainEntry` определить, какие объекта и сопоставление сообщений, вы хотите цепочки.

Например предположим, что ваш класс определяется следующим образом:

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

Затем клиент вызывает `CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

где `chainedObj` — цепного объект и является экземпляром класса, производного от `CMessageMap`. Теперь если `myCtl` получает сообщение, которое не обрабатывается `OnPaint` или `OnSetFocus`, процедура окна направляет сообщение `chainedObj`в схеме сообщений по умолчанию.

Дополнительные сведения о цепочках map сообщения, см. в разделе [схемы сообщений](../../atl/message-maps-atl.md) в статье «Классы окон ATL».

## <a name="requirements"></a>Требования

**Заголовок:** atlwin.h

##  <a name="callchain"></a>  CDynamicChain::CallChain

Направляет сообщение Windows, схему сообщений другим объектом.

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>Параметры

*dwChainID*<br/>
[in] Уникальный идентификатор, связанный с объектом цепочки и схему сообщений.

*hWnd*<br/>
[in] Дескриптор окна, принимающего сообщение.

*uMsg*<br/>
[in] Сообщение, отправленное окну.

*wParam*<br/>
[in] Дополнительные сведения, относящиеся к сообщению.

*lParam*<br/>
[in] Дополнительные сведения, относящиеся к сообщению.

*lResult*<br/>
[out] Результат обработки сообщения.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если оно полностью обрабатывается; в противном случае — значение FALSE.

### <a name="remarks"></a>Примечания

Для вызова процедуры окна `CallChain`, необходимо указать [CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic) макрос в схему сообщения. Например, см. в разделе [CDynamicChain](../../atl/reference/cdynamicchain-class.md) Обзор.

`CallChain` требуется предыдущего вызова [SetChainEntry](#setchainentry) связываемый *dwChainID* значение с помощью объекта и схему сообщений.

##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain

Конструктор.

```
CDynamicChain();
```

##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain

Деструктор

```
~CDynamicChain();
```

### <a name="remarks"></a>Примечания

Освобождает все выделенные ресурсы.

##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry

Удаляет указанное сообщение карты из коллекции.

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>Параметры

*dwChainID*<br/>
[in] Уникальный идентификатор, связанный с объектом цепочки и схему сообщений. Изначально вы определите это значение путем вызова [SetChainEntry](#setchainentry).

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если в схеме сообщений был успешно удален из коллекции. В противном случае — значение FALSE.

##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry

Карта указанное сообщение добавляется в коллекцию.

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>Параметры

*dwChainID*<br/>
[in] Уникальный идентификатор, связанный с объектом цепочки и схему сообщений.

*pObject*<br/>
[in] Указатель на объект цепочки объявление схемы сообщений. Этот объект должен быть производным от [CMessageMap](../../atl/reference/cmessagemap-class.md).

*dwMsgMapID*<br/>
[in] Идентификатор схемы сообщений в цепочке объекта. Значение по умолчанию — 0, который определяет схему сообщений по умолчанию, объявленные с [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map). Чтобы указать альтернативную схему сообщений, объявленные с [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), передайте `msgMapID`.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если в схеме сообщений успешно добавлен в коллекцию. В противном случае — значение FALSE.

### <a name="remarks"></a>Примечания

Если *dwChainID* значение уже существует в коллекции, его связанный объект и схему сообщений заменяются *pObject* и *dwMsgMapID*, соответственно. В противном случае добавляется новая запись.

## <a name="see-also"></a>См. также

[Класс CWindowImpl](../../atl/reference/cwindowimpl-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
