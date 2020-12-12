---
description: 'Дополнительные сведения о: Идбкреатекоммандимпл Class'
title: Класс IDBCreateCommandImpl
ms.date: 11/04/2016
f1_keywords:
- ATL::IDBCreateCommandImpl
- IDBCreateCommandImpl
- ATL.IDBCreateCommandImpl
- IDBCreateCommandImpl.CreateCommand
- IDBCreateCommandImpl::CreateCommand
helpviewer_keywords:
- IDBCreateCommandImpl class
- CreateCommand method
ms.assetid: eac4755e-1668-42e1-958e-a35620c385ae
ms.openlocfilehash: aaa9e84b66bd8bcb93fa418eed56a3cdadd31d6f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287350"
---
# <a name="idbcreatecommandimpl-class"></a>Класс IDBCreateCommandImpl

Предоставляет реализацию интерфейса [IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85)) .

## <a name="syntax"></a>Синтаксис

```cpp
template <class T, class CommandClass >
class ATL_NO_VTABLE IDBCreateCommandImpl
   : public IDBCreateCommand
```

### <a name="parameters"></a>Параметры

*T*<br/>
Объект сеанса, производный от `IDBCreateCommandImpl` .

*коммандкласс*<br/>
Класс команд.

## <a name="requirements"></a>Требования

**Заголовок:** atldb.h

## <a name="members"></a>Элементы

### <a name="interface-methods"></a>Методы интерфейса

| Имя | Описание |
|-|-|
|[CreateCommand](#createcommand)|Создает новую команду.|

## <a name="remarks"></a>Комментарии

Необязательный интерфейс объекта Session для получения новой команды.

## <a name="idbcreatecommandimplcreatecommand"></a><a name="createcommand"></a> Идбкреатекоммандимпл:: CreateCommand

Создает новую команду и возвращает запрошенный интерфейс.

### <a name="syntax"></a>Синтаксис

```cpp
STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,
   REFIID riid,
   IUnknown ** ppvCommand);
```

#### <a name="parameters"></a>Параметры

См. раздел [IDBCreateCommand:: CreateCommand](/previous-versions/windows/desktop/ms709772(v=vs.85)) в *справочнике программиста OLE DB*.

Некоторые параметры соответствуют *OLE DB ссылочным параметрам программиста* с разными именами, которые описаны в `IDBCreateCommand::CreateCommand` :

|OLE DB параметры шаблона|*OLE DB ссылочные параметры программиста*|
|--------------------------------|------------------------------------------------|
|*ппвкомманд*|*ппкомманд*|

## <a name="see-also"></a>См. также раздел

[Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
