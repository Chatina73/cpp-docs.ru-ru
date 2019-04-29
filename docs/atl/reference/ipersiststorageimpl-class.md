---
title: Класс IPersistStorageImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: 3239ed22e37ff694c9f399b05e765d63e97e99ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276150"
---
# <a name="ipersiststorageimpl-class"></a>Класс IPersistStorageImpl

Этот класс реализует [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) интерфейс.

> [!IMPORTANT]
>  Этот класс и его члены не может использоваться в приложениях, выполняемых в среде выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Параметры

*T*<br/>
Ваш класс, производный от `IPersistStorageImpl`.

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Извлекает идентификатор CLSID объекта.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Указывает, что объект освободить все объекты хранилища и перейти в режим HandsOff. Реализация ATL, возвращается значение s_ок.|
|[IPersistStorageImpl::InitNew](#initnew)|Инициализирует новое хранилище.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Проверяет, изменялся ли данные объекта с момента последнего сохранения.|
|[IPersistStorageImpl::Load](#load)|Загружает свойства объекта из указанного хранилища.|
|[IPersistStorageImpl::Save](#save)|Сохраняет свойства объекта в указанном хранилище.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Уведомляет объект, который может возвращаться в обычном режиме для записи на свой объект хранения. Реализация ATL, возвращается значение s_ок.|

## <a name="remarks"></a>Примечания

`IPersistStorageImpl` реализует [IPersistStorage](/windows/desktop/api/objidl/nn-objidl-ipersiststorage) интерфейс, который позволяет клиенту для запроса, нагрузки объекта и сохранить постоянные данные с помощью хранилища.

Реализации этого класса требуется класс `T` чтобы сделать реализацию `IPersistStreamInit` интерфейс, доступный через `QueryInterface`. Обычно это означает, что класс `T` должен быть производным от [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), предоставить запись для `IPersistStreamInit` в [COM карты](com-map-macros.md)и использовать [сопоставление свойств](property-map-macros.md) для описания класса постоянных данных.

**Связанные статьи** [учебник по ATL](../../atl/active-template-library-atl-tutorial.md), [Создание проекта ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Иерархия наследования

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Требования

**Заголовок:** atlcom.h

##  <a name="getclassid"></a>  IPersistStorageImpl::GetClassID

Извлекает идентификатор CLSID объекта.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Примечания

См. в разделе [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) в Windows SDK.

##  <a name="handsoffstorage"></a>  IPersistStorageImpl::HandsOffStorage

Указывает, что объект освободить все объекты хранилища и перейти в режим HandsOff.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение S_OK.

### <a name="remarks"></a>Примечания

См. в разделе [IPersistStorage::HandsOffStorage](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) в Windows SDK.

##  <a name="initnew"></a>  IPersistStorageImpl::InitNew

Инициализирует новое хранилище.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Примечания

Делегирует реализацию ATL [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) интерфейс.

См. в разделе [IPersistStorage:InitNew](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-initnew) в Windows SDK.

##  <a name="isdirty"></a>  IPersistStorageImpl::IsDirty

Проверяет, изменялся ли данные объекта с момента последнего сохранения.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Примечания

Делегирует реализацию ATL [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) интерфейс.

См. в разделе [IPersistStorage:IsDirty](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-isdirty) в Windows SDK.

##  <a name="load"></a>  IPersistStorageImpl::Load

Загружает свойства объекта из указанного хранилища.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Примечания

Делегирует реализацию ATL [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) интерфейс. `Load` поток с именем «Содержание» используется для извлечения данных объекта. [Сохранить](#save) метод изначально создает этот поток.

См. в разделе [IPersistStorage:Load](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-load) в Windows SDK.

##  <a name="save"></a>  IPersistStorageImpl::Save

Сохраняет свойства объекта в указанном хранилище.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Примечания

Делегирует реализацию ATL [IPersistStreamInit](/windows/desktop/api/ocidl/nn-ocidl-ipersiststreaminit) интерфейс. Когда `Save` является первым именем, он создает поток с именем «Содержание» в указанное хранилище. Этот поток используется в последующих вызовах `Save` и вызовы [нагрузки](#load).

См. в разделе [IPersistStorage:Save](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-save) в Windows SDK.

##  <a name="savecompleted"></a>  IPersistStorageImpl::SaveCompleted

Уведомляет объект, который может возвращаться в обычном режиме для записи на свой объект хранения.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение S_OK.

### <a name="remarks"></a>Примечания

См. в разделе [IPersistStorage:SaveCompleted](/windows/desktop/api/objidl/nf-objidl-ipersiststorage-savecompleted) в Windows SDK.

## <a name="see-also"></a>См. также

[Хранилищ и потоков](/windows/desktop/Stg/storages-and-streams)<br/>
[Класс IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[Класс IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)
