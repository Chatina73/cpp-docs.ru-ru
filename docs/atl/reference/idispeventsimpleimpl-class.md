---
title: Класс IDispEventSimpleImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
ms.openlocfilehash: 1578518b8918f59b1da54f474e82cf899f3c76f6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275377"
---
# <a name="idispeventsimpleimpl-class"></a>Класс IDispEventSimpleImpl

Этот класс предоставляет реализацию `IDispatch` методы без получения сведений о типе из библиотеки типов.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
template <UINT nID, class T, const IID* pdiid>
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```

#### <a name="parameters"></a>Параметры

*nID*<br/>
Уникальный идентификатор для исходного объекта. Когда `IDispEventSimpleImpl` является базовым классом для составного элемента управления, используйте идентификатор ресурса для нужного элемента управления в контейнере для этого параметра. В других случаях используйте произвольное целое положительное число.

*T*<br/>
Класс пользователя, который является производным от `IDispEventSimpleImpl`.

*pdiid*<br/>
Указатель на идентификатор IID disp-интерфейс событий, реализованные этим классом.

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[IDispEventSimpleImpl::Advise](#advise)|Устанавливает соединение с источником события по умолчанию.|
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Устанавливает соединение с источником события.|
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Разрывает соединение с источником события.|
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Возвращает E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Возвращает E_NOTIMPL.|
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Возвращает E_NOTIMPL.|
|[IDispEventSimpleImpl::Invoke](#invoke)|Вызывает обработчики событий указанного в описании события карты в качестве приемника.|
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Разрывает соединение с источником события по умолчанию.|

## <a name="remarks"></a>Примечания

`IDispEventSimpleImpl` предоставляет способ реализации диспетчерский интерфейс событий без необходимости указать код реализации для каждого метода и события в этом интерфейсе. `IDispEventSimpleImpl` предоставляет реализацию `IDispatch` методы. Необходимо предоставлять реализации для событий, что вы заинтересованы в обработке.

`IDispEventSimpleImpl` работает совместно с картой приемника событий в классе события соответствующим функциям обработки. Чтобы использовать этот класс:

- Добавить [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) макрос для карты приемника событий для каждого события для каждого объекта, который необходимо обработать.

- Передавать сведения о типе для каждого события, передав указатель на [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) структуру как параметр для каждой записи. На x86 платформы, `_ATL_FUNC_INFO.cc` значение должно быть CC_CDECL с функцией обратного вызова, вызвав метод __stdcall.

- Вызовите [DispEventAdvise](#dispeventadvise) для установления соединения между исходным объектом и базовый класс.

- Вызовите [DispEventUnadvise](#dispeventunadvise) Чтобы разорвать подключение.

Должен быть производным от `IDispEventSimpleImpl` (с помощью уникальное значение для *nID*) для каждого объекта, для которого требуется для обработки событий. Можно повторно использовать базовый класс, unadvising от одного исходного объекта, затем о том, с объектом другого источника, но максимальное число объектов источника, которые могут обрабатываться одновременно в одном объекте ограничивается число `IDispEventSimpleImpl` базовых классов.

`IDispEventSimplImpl` предоставляет те же функции, что [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), за исключением, что он не получает сведения о типе об интерфейсе из библиотеки типов. Мастер создает код на основе только `IDispEventImpl`, но вы можете использовать `IDispEventSimpleImpl` , добавив код вручную. Используйте `IDispEventSimpleImpl` при не имеют библиотеку типов, описывающие интерфейса событий или хотите избежать издержек, связанных с использованием библиотеки типов.

> [!NOTE]
> `IDispEventImpl` и `IDispEventSimpleImpl` предоставляют свою собственную реализацию `IUnknown::QueryInterface` включение каждого `IDispEventImpl` или `IDispEventSimpleImpl` базового класса в качестве отдельного удостоверения COM по-прежнему предоставляя прямой доступ к членам класса в основной COM-объект.

Реализация CE ATL ActiveX событий приемники только поддерживает возвращаемого значения типа HRESULT или void из методов обработчика событий; Возвращаемое значение не поддерживается, и его поведение не определено.

Дополнительные сведения см. в разделе [поддержка IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`_IDispEvent`

`_IDispEventLocator`

`IDispEventSimpleImpl`

## <a name="requirements"></a>Требования

**Заголовок:** atlcom.h

##  <a name="advise"></a>  IDispEventSimpleImpl::Advise

Вызовите этот метод для установления соединения с источником события, представленного *pUnk*.

```
HRESULT Advise(IUnknown* pUnk);
```

### <a name="parameters"></a>Параметры

*pUnk*<br/>
[in] Указатель на `IUnknown` интерфейс объекта источника события.

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK или любое значение HRESULT ошибки.

### <a name="remarks"></a>Примечания

После того как соединение установлено, событие, возникающее из *pUnk* будут направляться на обработчики в вашем классе посредством карты приемника событий.

> [!NOTE]
>  Если класс является производным из нескольких `IDispEventSimpleImpl` классов, необходимо будет устранить неоднозначность вызова этого метода с областью, вызов с определенного базового класса, которые вас интересуют.

`Advise` Устанавливает соединение с источником события по умолчанию, он получает IID источника события по умолчанию объекта определяется [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise

Вызовите этот метод для установления соединения с источником события, представленного *pUnk*.

```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Параметры

*pUnk*<br/>
[in] Указатель на `IUnknown` интерфейс объекта источника события.

*piid*<br/>
Указатель на идентификатор IID объект источника события.

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK или любое значение HRESULT ошибки.

### <a name="remarks"></a>Примечания

Как следствие, событие, возникающее из *pUnk* будут направляться на обработчики в вашем классе посредством карты приемника событий.

> [!NOTE]
>  Если класс является производным из нескольких `IDispEventSimpleImpl` классов, необходимо будет устранить неоднозначность вызова этого метода с областью, вызов с определенного базового класса, которые вас интересуют.

`DispEventAdvise` Устанавливает соединение с источником события, указанного в `pdiid`.

##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise

Разрывает соединение с источником события, представленного *pUnk*.

```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```

### <a name="parameters"></a>Параметры

*pUnk*<br/>
[in] Указатель на `IUnknown` интерфейс объекта источника события.

*piid*<br/>
Указатель на идентификатор IID объект источника события.

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK или любое значение HRESULT ошибки.

### <a name="remarks"></a>Примечания

Когда соединение является разорванным, события больше не направляются в функции обработчика, в карте приемника событий.

> [!NOTE]
>  Если класс является производным из нескольких `IDispEventSimpleImpl` классов, необходимо будет устранить неоднозначность вызова этого метода с областью, вызов с определенного базового класса, которые вас интересуют.

`DispEventAdvise` разрывает соединение, которое было установлено с источником события, указанного в `pdiid`.

##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames

Эта реализация `IDispatch::GetIDsOfNames` возвращает E_NOTIMPL.

```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::GetIdsOfNames расширенное](/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) в Windows SDK.

##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo

Эта реализация `IDispatch::GetTypeInfo` возвращает E_NOTIMPL.

```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::GetTypeInfo](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) в Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount

Эта реализация `IDispatch::GetTypeInfoCount` возвращает E_NOTIMPL.

```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) в Windows SDK.

##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke

Эта реализация `IDispatch::Invoke` вызывает обработчики событий указанного в описании события карты в качестве приемника.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::Invoke](/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke).

##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise

Разрывает соединение с источником события, представленного *pUnk*.

```
HRESULT Unadvise(IUnknown* pUnk);
```

### <a name="parameters"></a>Параметры

*pUnk*<br/>
[in] Указатель на `IUnknown` интерфейс объекта источника события.

### <a name="return-value"></a>Возвращаемое значение

Значение S_OK или любое значение HRESULT ошибки.

### <a name="remarks"></a>Примечания

Когда соединение является разорванным, события больше не направляются в функции обработчика, в карте приемника событий.

> [!NOTE]
>  Если класс является производным из нескольких `IDispEventSimpleImpl` классов, необходимо будет устранить неоднозначность вызова этого метода с областью, вызов с определенного базового класса, которые вас интересуют.

`Unadvise` прерывает подключение, которое было установлено с источником события по умолчанию, указанное в `pdiid`.

`Unavise` разрывы соединения с источником события по умолчанию, он получает IID источника события по умолчанию объекта определяется [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).

## <a name="see-also"></a>См. также

[Структура _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)<br/>
[Класс IDispatchImpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Класс IDispEventImpl](../../atl/reference/idispeventimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
