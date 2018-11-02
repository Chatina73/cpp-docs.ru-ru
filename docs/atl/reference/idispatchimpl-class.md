---
title: Класс IDispatchImpl
ms.date: 11/04/2016
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
ms.openlocfilehash: 8be209c8fb2e9f4d1f4dda4bbd3dc9e5220243b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490445"
---
# <a name="idispatchimpl-class"></a>Класс IDispatchImpl

Предоставляет реализацию по умолчанию для `IDispatch` частью сдвоенный интерфейс.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0,
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```

#### <a name="parameters"></a>Параметры

*T*<br/>
[in] Сдвоенный интерфейс.

*piid*<br/>
[in] Указатель на идентификатор IID *T*.

*plibid*<br/>
[in] Указатель на идентификатор LIBID библиотеки типов, содержащий сведения об интерфейсе. По умолчанию передается библиотеки типов на уровне сервера.

*wMajor*<br/>
[in] Основной номер версии библиотеки типов. По умолчанию значение равно 1.

*wMinor*<br/>
[in] Дополнительный номер версии библиотеки типов. По умолчанию значение равно 0.

*tihclass*<br/>
[in] Класс, используемый для управления сведения о типе *T*. Значение по умолчанию `CComTypeInfoHolder`.

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Конструктор. Вызовы `AddRef` переменной защищенный член, который управляет сведения о типе для сдвоенный интерфейс. Деструктор вызывает `Release`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Сопоставляет набор имен соответствующему набору идентификаторов диспетчеризации.|
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Извлекает сведения о типе для сдвоенного интерфейса.|
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Определяет, доступна ли сведения о типе для сдвоенного интерфейса.|
|[IDispatchImpl::Invoke](#invoke)|Предоставляет доступ к методам и свойствам, предоставляемым сдвоенный интерфейс.|

## <a name="remarks"></a>Примечания

`IDispatchImpl` предоставляет реализацию по умолчанию для `IDispatch` частью любой сдвоенного интерфейса на объект. Сдвоенный интерфейс является производным от `IDispatch` и использует только совместимые с автоматизацией типы. Как и disp-интерфейсом сдвоенный интерфейс поддерживает раннее связывание и позднее связывание; Тем не менее сдвоенный интерфейс также поддерживает привязки vtable.

Пример типичной реализации `IDispatchImpl`.

[!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]

По умолчанию `IDispatchImpl` класс ищет сведения о типе *T* в реестре. Чтобы реализовать интерфейс как отменить регистрацию, можно использовать `IDispatchImpl` класс без доступе к реестру с помощью предопределенных номер_версии. При создании `IDispatchImpl` объект, имеющий 0xFFFF в качестве значения для *wMajor* и 0xFFFF как значение для *wMinor*, `IDispatchImpl` класс извлекает библиотеку типов из DLL-файл, а не реестр.

`IDispatchImpl` содержит статический член типа `CComTypeInfoHolder` , управляющий сведения о типе для сдвоенного интерфейса. Если у вас есть несколько объектов, которые реализуют те же два интерфейса, только один экземпляр `CComTypeInfoHolder` используется.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`T`

`IDispatchImpl`

## <a name="requirements"></a>Требования

**Заголовок:** atlcom.h

##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames

Сопоставляет набор имен соответствующему набору идентификаторов диспетчеризации.

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::GetIdsOfNames расширенное](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-getidsofnames) в Windows SDK.

##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo

Извлекает сведения о типе для сдвоенного интерфейса.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::GetTypeInfo](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfo) в Windows SDK.

##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount

Определяет, доступна ли сведения о типе для сдвоенного интерфейса.

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Примечания

См. в разделе `IDispatch::GetTypeInfoCount` в Windows SDK.

##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl

Конструктор. Вызовы `AddRef` переменной защищенный член, который управляет сведения о типе для сдвоенный интерфейс. Деструктор вызывает `Release`.

```
IDispatchImpl();
```

##  <a name="invoke"></a>  IDispatchImpl::Invoke

Предоставляет доступ к методам и свойствам, предоставляемым сдвоенный интерфейс.

```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```

### <a name="remarks"></a>Примечания

См. в разделе [IDispatch::Invoke](/previous-versions/windows/desktop/api/oaidl/nf-oaidl-idispatch-invoke) в Windows SDK.

## <a name="see-also"></a>См. также

[Общие сведения о классе](../../atl/atl-class-overview.md)
