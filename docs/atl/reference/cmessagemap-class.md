---
title: Класс CMessageMap
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: 617b7b4592c96625b44fbe5c2b93da971a423128
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293177"
---
# <a name="cmessagemap-class"></a>Класс CMessageMap

Этот класс позволяет схемы сообщений объекта, к которому будет обращаться другим объектом.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|Получает доступ к схеме сообщений в `CMessageMap`-производного класса.|

## <a name="remarks"></a>Примечания

`CMessageMap` — Это абстрактный базовый класс, позволяющий объекта сообщения сопоставляется осуществляться другим объектом. Чтобы предоставлять его схемы сообщений объекта, его класс должен быть производным от `CMessageMap`.

Использует ATL `CMessageMap` содержится поддержка windows и цепочки карты динамического сообщения. Например, любого класса, содержащего [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) объект должен быть производным от `CMessageMap`. Следующий код взят из [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) образца. Через [CComControl](../../atl/reference/ccomcontrol-class.md), `CAtlEdit` автоматически класс является производным от `CMessageMap`.

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

Так как окно автономной `m_EditCtrl`, будет использовать схему сообщений в содержащего класса `CAtlEdit` является производным от `CMessageMap`.

Дополнительные сведения о схемах сообщений см. в разделе [схемы сообщений](../../atl/message-maps-atl.md) в статье «Классы окон ATL».

## <a name="requirements"></a>Требования

**Заголовок:** atlwin.h

##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage

Получает доступ к схеме сообщений определяется *dwMsgMapID* в `CMessageMap`-производного класса.

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>Параметры

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

*dwMsgMapID*<br/>
[in] Идентификатор схемы сообщений, который будет обрабатывать сообщения. Сопоставление сообщений по умолчанию, объявленные с [BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map), определяется по 0. Альтернативную схему сообщений, объявленных с [ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map), идентифицируемый `msgMapID`.

### <a name="return-value"></a>Возвращаемое значение

Значение TRUE, если сообщение обработано полностью; в противном случае — значение FALSE.

### <a name="remarks"></a>Примечания

Вызывается в процедуру [CContainedWindow](../../atl/reference/ccontainedwindowt-class.md) объекта или объекта, динамически цепочки в схеме сообщений.

## <a name="see-also"></a>См. также

[Класс CDynamicChain](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
