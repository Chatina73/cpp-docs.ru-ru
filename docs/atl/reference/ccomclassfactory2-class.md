---
title: Класс CComClassFactory2
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: b3b14fa59765aa72a1142e0eef41aa84abea35de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259694"
---
# <a name="ccomclassfactory2-class"></a>Класс CComClassFactory2

Этот класс реализует [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) интерфейс.

## <a name="syntax"></a>Синтаксис

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Параметры

*лицензии*<br/>
Класс, реализующий следующие статические функции:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Создает объект для указанного идентификатора CLSID.|
|[CComClassFactory2::CreateInstanceLic](#createinstancelic)|Лицензионный ключ создает объект с заданным идентификатором CLSID.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Извлекает сведения, описывающие возможности лицензирования фабрики класса.|
|[CComClassFactory2::LockServer](#lockserver)|Блокирует фабрики класса в памяти.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Создает и возвращает лицензионный ключ.|

## <a name="remarks"></a>Примечания

`CComClassFactory2` реализует [IClassFactory2](/windows/desktop/api/ocidl/nn-ocidl-iclassfactory2) интерфейс, который представляет собой расширение из [IClassFactory](/windows/desktop/api/unknwnbase/nn-unknwnbase-iclassfactory). `IClassFactory2` Создание элементов управления объекта через лицензию. Класс фабрики выполнение лицензированного компьютера можно предоставить ключ лицензии времени выполнения. Этот ключ лицензии позволяет приложению создавать экземпляры объектов, если лицензия весь компьютер не существует.

Объекты ATL обычно получить фабрику класса путем наследования от [CComCoClass](../../atl/reference/ccomcoclass-class.md). Этот класс включает макрос [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), который объявляет [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) как фабрики класса по умолчанию. Чтобы использовать `CComClassFactory2`, укажите [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) макроса в определении класса объекта. Пример:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`, для параметра-шаблона `CComClassFactory2`, необходимо реализовать статические функции `VerifyLicenseKey`, `GetLicenseKey`, и `IsLicenseValid`. Ниже приведен пример класса простой лицензии:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2` наследует от `CComClassFactory2Base` и *лицензии*. `CComClassFactory2Base`, в свою очередь, является производным от `IClassFactory2` и `CComObjectRootEx< CComGlobalsThreadModel >`.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`CComObjectRootBase`

`license`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Требования

**Заголовок:** atlcom.h

##  <a name="createinstance"></a>  CComClassFactory2::CreateInstance

Создает объект для указанного идентификатора CLSID и получает указатель интерфейса на этот объект.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Параметры

*pUnkOuter*<br/>
[in] Если объект создается как часть агрегата, затем *pUnkOuter* должен быть внешняя Неизвестная строка. В противном случае *pUnkOuter* должен иметь значение NULL.

*riid*<br/>
[in] Идентификатор IID запрошенного интерфейса. Если *pUnkOuter* отлично от NULL, *riid* должно быть `IID_IUnknown`.

*ppvObj*<br/>
[out] Указатель на указатель интерфейса, идентифицируемый *riid*. Если объект не поддерживает этот интерфейс *ppvObj* имеет значение NULL.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Примечания

Необходимо полностью лицензировать компьютера. Если лицензия весь компьютер не существует, вызов [CreateInstanceLic](#createinstancelic).

##  <a name="createinstancelic"></a>  CComClassFactory2::CreateInstanceLic

Аналогичную [CreateInstance](#createinstance), за исключением того, что `CreateInstanceLic` требуется лицензионный ключ.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>Параметры

*pUnkOuter*<br/>
[in] Если объект создается как часть агрегата, затем *pUnkOuter* должен быть внешняя Неизвестная строка. В противном случае *pUnkOuter* должен иметь значение NULL.

*pUnkReserved*<br/>
[in] Не используется. Должен иметь значение NULL.

*riid*<br/>
[in] Идентификатор IID запрошенного интерфейса. Если *pUnkOuter* отлично от NULL, *riid* должно быть `IID_IUnknown`.

*bstrKey*<br/>
[in] Во время выполнения лицензионный ключ, ранее полученный из вызова `RequestLicKey`. Этот ключ необходим для создания объекта.

*ppvObject*<br/>
[out] Указатель на указатель интерфейса, заданный параметром *riid*. Если объект не поддерживает этот интерфейс *ppvObject* имеет значение NULL.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Примечания

Вы можете получить ключа лицензии с помощью [RequestLicKey](#requestlickey). Чтобы создать объект на машине без лицензии, необходимо вызвать `CreateInstanceLic`.

##  <a name="getlicinfo"></a>  CComClassFactory2::GetLicInfo

Заполняет [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) структуры со сведениями, описывающими фабрики класса рамках лицензионных возможности.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Параметры

*pLicInfo*<br/>
[out] Указатель на `LICINFO` структуры.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Примечания

`fRuntimeKeyAvail` Член этой структуры указывает, учитывая лицензионный ключ, фабрика классов разрешает ли создавать на машине нелицензированного объекты. *FLicVerified* элемент указывает, существует ли лицензия весь компьютер.

##  <a name="lockserver"></a>  CComClassFactory2::LockServer

Увеличивает и уменьшает счетчик блокировки модуля путем вызова `_Module::Lock` и `_Module::Unlock`, соответственно.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Параметры

*fLock*<br/>
[in] Если значение равно TRUE, увеличивается счетчик блокировок; в противном случае уменьшается количество блокировок.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Примечания

`_Module` ссылается на глобальный экземпляр [CComModule](../../atl/reference/ccommodule-class.md) или класс, производный от него.

Вызов `LockServer` позволяет клиенту, чтоб фабрику класса для создания нескольких объектов можно быстро.

##  <a name="requestlickey"></a>  CComClassFactory2::RequestLicKey

Создает и возвращает лицензионный ключ, при условии, что `fRuntimeKeyAvail` членом [LICINFO](/windows/desktop/api/ocidl/ns-ocidl-taglicinfo) структура имеет значение TRUE.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Параметры

*dwReserved*<br/>
[in] Не используется. Должен равняться нулю.

*pbstrKey*<br/>
[out] Указатель на лицензионный ключ.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Примечания

Лицензионный ключ необходим для вызова метода [CreateInstanceLic](#createinstancelic) для создания объекта на машине без лицензии. Если `fRuntimeKeyAvail` имеет значение FALSE, то объекты могут создаваться только на полностью лицензированную компьютере.

Вызовите [GetLicInfo](#getlicinfo) для извлечения значения `fRuntimeKeyAvail`.

## <a name="see-also"></a>См. также

[Класс CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[Класс CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[Класс CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
