---
title: Класс IOpenRowsetImpl
ms.date: 11/04/2016
f1_keywords:
- IOpenRowsetImpl
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
- OpenRowset
- IOpenRowsetImpl::OpenRowset
- IOpenRowsetImpl.OpenRowset
helpviewer_keywords:
- IOpenRowsetImpl class
- CreateRowset method
- OpenRowset method
ms.assetid: d259cedc-1db4-41cf-bc9f-5030907ab486
ms.openlocfilehash: 437f78636d1fa75f5bb8e4304a347dc3b554c34d
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556267"
---
# <a name="iopenrowsetimpl-class"></a>Класс IOpenRowsetImpl

Предоставляет реализацию для `IOpenRowset` интерфейс.

## <a name="syntax"></a>Синтаксис

```cpp
template <class SessionClass>
class IOpenRowsetImpl : public IOpenRowset
```

### <a name="parameters"></a>Параметры

*SessionClass*<br/>
Ваш класс, производный от `IOpenRowsetImpl`.

## <a name="requirements"></a>Требования

**Заголовок:** atldb.h

## <a name="members"></a>Участники

### <a name="methods"></a>Методы

|||
|-|-|
|[CreateRowset](#createrowset)|Создает объект набора строк. Не вызывается непосредственно пользователем.|
|[OpenRowset](#openrowset)|Открывает и возвращает набор строк, который содержит все строки из одной базовой таблицы или индекса. (Не в ATLDB. H)|

## <a name="remarks"></a>Примечания

[IOpenRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms716946(v=vs.85)) интерфейс является обязательным для объекта сеанса. Она открывает и возвращает набор строк, который содержит все строки из одной базовой таблицы или индекса.

## <a name="createrowset"></a> IOpenRowsetImpl::CreateRowset

Создает объект набора строк. Не вызывается непосредственно пользователем. См. в разделе [IOpenRowset::OpenRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms716724(v=vs.85)) в *справочнике программиста OLE DB.*

### <a name="syntax"></a>Синтаксис

```cpp
template template <class RowsetClass>
HRESULT CreateRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   RowsetClass*& pRowsetObj);
```

#### <a name="parameters"></a>Параметры

*RowsetClass*<br/>
Член класса шаблона, представляющий пользователя класса набора строк. Как правило, создаются с помощью мастера.

*pRowsetObj*<br/>
[out] Указатель на объект набора строк. Обычно этот параметр не используется, но он может использоваться, если необходимо выполнить дополнительные действия в наборе строк перед его передачей в COM-объект. Время существования *pRowsetObj* привязана к *ppRowset*.

Другие параметры, см. в разделе [IOpenRowset::OpenRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms716724(v=vs.85)) в *Справочник программиста OLE DB по.*

## <a name="openrowset"></a> IOpenRowsetImpl::OpenRowset

Открывает и возвращает набор строк, который содержит все строки из одной базовой таблицы или индекса.

### <a name="syntax"></a>Синтаксис

```cpp
HRESULT OpenRowset(IUnknown* pUnkOuter,
   DBID* pTableID,
   DBID* pIndexID,
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IOpenRowset::OpenRowset](https://docs.microsoft.com/previous-versions/windows/desktop/ms716724(v=vs.85)) в *справочнике программиста OLE DB*.

### <a name="remarks"></a>Примечания

Этот метод не найден в ATLDB. З. Он создается с помощью мастера объекта ATL, при создании поставщика.

## <a name="see-also"></a>См. также

[Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)