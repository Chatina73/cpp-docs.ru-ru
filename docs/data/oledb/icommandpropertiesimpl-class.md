---
description: 'Дополнительные сведения о: ICommandPropertiesImpl Class'
title: Класс ICommandPropertiesImpl
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: bf6a6f9a3ddd43a61671a85a791d63958f63c3e3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317573"
---
# <a name="icommandpropertiesimpl-class"></a>Класс ICommandPropertiesImpl

Предоставляет реализацию интерфейса [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) .

## <a name="syntax"></a>Синтаксис

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Параметры

*T*<br/>
Ваш класс, производный от

*пропкласс*<br/>
Класс свойств.

## <a name="requirements"></a>Требования

**Заголовок:** atldb.h

## <a name="members"></a>Элементы

### <a name="interface-methods"></a>Методы интерфейса

| Имя | Описание |
|-|-|
|[GetProperties](#getproperties)|Возвращает список свойств в группе свойств набора строк, запрашиваемых в данный момент для набора строк.|
|[SetProperties](#setproperties)|Задает свойства в группе свойств набора строк.|

## <a name="remarks"></a>Комментарии

Это обязательно для команд. Реализация обеспечивается статической функцией, определенной [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map) макросом.

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a> Свойства ICommandPropertiesImpl:: Properties

Возвращает все запрошенные наборы свойств с помощью схемы свойств команды.

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Параметры

См. раздел [ICommandProperties:: Properties](/previous-versions/windows/desktop/ms723119(v=vs.85)) в *справочнике программиста OLE DB*.

### <a name="remarks"></a>Комментарии

См. раздел [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map).

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a> ICommandPropertiesImpl:: SetProperties

Задает свойства для объекта команды.

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Параметры

См. раздел [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) в *справочнике программиста OLE DB*.

## <a name="see-also"></a>См. также раздел

[Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
