---
title: Класс IRowsetInfoImpl
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: 61544658f2aef4b59b2b70baa310dcc09e2740fe
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556209"
---
# <a name="irowsetinfoimpl-class"></a>Класс IRowsetInfoImpl

Предоставляет реализацию для [IRowsetInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms724541(v=vs.85)) интерфейс.

## <a name="syntax"></a>Синтаксис

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo, 
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Параметры

*T*<br/>
Ваш класс, производный от `IRowsetInfoImpl`.

*PropClass*<br/>
Класс определяемые пользователем свойства, который по умолчанию используется *T*.

## <a name="requirements"></a>Требования

**Заголовок:** altdb.h

## <a name="members"></a>Участники

### <a name="interface-methods"></a>Методы интерфейса

|||
|-|-|
|[GetProperties](#getproperties)|Возвращает текущие значения всех свойств, поддерживаемое набором строк.|
|[GetReferencedRowset](#getreferencedrowset)|Возвращает указатель интерфейса на набор строк, к которому применяется закладка.|
|[GetSpecification](#getspecification)|Возвращает указатель интерфейса объекта (команды или сеанса), создавшего этот набор строк.|

## <a name="remarks"></a>Примечания

Обязательный интерфейс наборов строк. Этот класс реализует свойства набора строк с помощью [сопоставление набора свойств](../../data/oledb/begin-propset-map.md) определен в классе вашей команды. Несмотря на то, что класса набора строк отображается для класса команды свойство задает, набор строк предоставляется вместе с свою собственную копию свойства времени выполнения при его создании с помощью команды или сеанса работы объекта.

## <a name="getproperties"></a> IRowsetInfoImpl::GetProperties

Возвращает текущие параметры для свойств в `DBPROPSET_ROWSET` группы.

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IRowsetInfo::GetProperties](https://docs.microsoft.com/previous-versions/windows/desktop/ms719611(v=vs.85)) в *справочнике программиста OLE DB*.

## <a name="getreferencedrowset"></a> IRowsetInfoImpl::GetReferencedRowset

Возвращает указатель интерфейса на набор строк, к которому применяется закладка.

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IRowsetInfo::GetReferencedRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms721145(v=vs.85)) в *справочнике программиста OLE DB*. *IOrdinal* параметр должен быть столбца закладки.

## <a name="getspecification"></a> IRowsetInfoImpl::GetSpecification

Возвращает указатель интерфейса объекта (команды или сеанса), создавшего этот набор строк.

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IRowsetInfo::GetSpecification](https://docs.microsoft.com/previous-versions/windows/desktop/ms716746(v=vs.85)) в *справочнике программиста OLE DB*.

### <a name="remarks"></a>Примечания

Этот метод используется с [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) извлекаемого свойства из объекта источника данных.

## <a name="see-also"></a>См. также

[Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)