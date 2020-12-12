---
description: 'Дополнительные сведения: поддержка уведомлений'
title: Поддержка уведомлений
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [C++], OLE DB consumers
- events [C++], notifications in OLE DB
- OLE DB consumers, notifications
- rowsets, event notifications
- OLE DB provider templates, notifications
- OLE DB providers, notifications
ms.assetid: 76e875fd-2bfd-4e4e-9f43-dbe5a3fa7382
ms.openlocfilehash: 3f03ded9b900a8691c256e6cde8eaf1a2f4fb5cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316678"
---
# <a name="supporting-notifications"></a>Поддержка уведомлений

## <a name="implementing-connection-point-interfaces-on-the-provider-and-consumer"></a>Реализация интерфейсов точек подключения в поставщике и потребителе

Для реализации уведомлений класс поставщика должен наследовать от [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md) и [IConnectionPointContainer](../../atl/reference/iconnectionpointcontainerimpl-class.md).

`IRowsetNotifyCP` реализует сайт поставщика для интерфейса точки подключения [IRowsetNotify клиента](/previous-versions/windows/desktop/ms712959(v=vs.85)). `IRowsetNotifyCP` реализует широковещательные функции для уведомления прослушивателей точки подключения об `IID_IRowsetNotify` изменениях содержимого набора строк.

Также необходимо реализовать и зарегистрироваться `IRowsetNotify` на потребителе (также известном как приемник) с помощью [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) , чтобы потребитель мог управлять уведомлениями. Сведения о реализации интерфейса точки подключения на потребителе см. в разделе [Получение уведомлений](../../data/oledb/receiving-notifications.md).

Кроме того, класс должен иметь карту, которая определяет запись точки подключения следующим образом:

```cpp
BEGIN_CONNECTION_POINT_MAP
   CONNECTIONPOINT_ENTRY (IID_IRowsetNotify)
END_CONNECTION_POINT_MAP
```

## <a name="adding-irowsetnotify"></a>Добавление IRowsetNotify клиента

Чтобы добавить `IRowsetNotify` , необходимо добавить `IConnectionPointContainerImpl<rowset-name>` и `IRowsetNotifyCP<rowset-name>` в цепочку наследования.

Например, вот цепочка наследования для `RUpdateRowset` в [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV):

> [!NOTE]
> Пример кода может отличаться от указанного здесь. Его следует рассматривать как более актуальную версию.

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)

class RUpdateRowset :
public CRowsetImpl< RUpdateRowset, CAgentMan, CUpdateCommand,
         CAtlArray< CAgentMan, CAtlArray<CAgentMan>>, CSimpleRow,
         IRowsetScrollImpl< RUpdateRowset, IRowsetScroll >>,
      public IRowsetUpdateImpl< RUpdateRowset, CAgentMan >,
      public IConnectionPointContainerImpl<RUpdateRowset>,
      public IRowsetNotifyCP<RUpdateRowset>
```

### <a name="setting-com-map-entries"></a>Настройка записей схемы COM

Кроме того, необходимо добавить следующий объект в карту COM в наборе строк:

```cpp
COM_INTERFACE_ENTRY(IConnectionPointContainer)
COM_INTERFACE_ENTRY_IMPL(IConnectionPointContainer)
```

Эти макросы позволяют любому пользователю, обращающимся к `QueryInterface` контейнеру точки подключения (основание `IRowsetNotify` ), найти запрошенный интерфейс у вашего поставщика. Пример использования точек подключения см. в разделе пример и учебник по МНОГОУГОЛЬНИКам ATL.

### <a name="setting-connection-point-map-entries"></a>Настройка записей карт точек подключения

Также необходимо добавить карту точек подключения. Оно должно иметь приблизительно следующий вид:

```cpp
BEGIN_CONNECTION_POINT_MAP(rowset-name)
     CONNECTION_POINT_ENTRY(_uuidof(IRowsetNotify))
END_CONNECTION_POINT_MAP()
```

Эта карта точек подключения позволяет компоненту, который ищет `IRowsetNotify` интерфейс, найти его в поставщике.

### <a name="setting-properties"></a>Установка свойств

Кроме того, необходимо добавить следующие свойства в поставщик. Необходимо только добавить свойства на основе поддерживаемых интерфейсов.

|Свойство|Добавить, если поддерживается|
|--------------|------------------------|
|DBPROP_IConnectionPointContainer|Всегда|
|DBPROP_NOTIFICATIONGRANULARITY|Всегда|
|DBPROP_NOTIFICATIONPHASES|Всегда|
|DBPROP_NOTIFYCOLUMNSET|`IRowsetChange`|
|DBPROP_NOTIFYROWDELETE|`IRowsetChange`|
|DBPROP_NOTIFYROWINSERT|`IRowsetChange`|
|DBPROP_NOTIFYROWSETFETCHPOSITIONCHANGE|Всегда|
|DBPROP_NOTIFYROWFIRSTCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWSETRELEASE|Всегда|
|DBPROP_NOTIFYROWUNDOCHANGE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDODELETE|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUNDOINSERT|`IRowsetUpdate`|
|DBPROP_NOTIFYROWUPDATE|`IRowsetUpdate`|

Большая часть реализации уведомлений уже внедрена в шаблоны поставщика OLE DB. Если не добавить `IRowsetNotifyCP` в цепочку наследования, компилятор удаляет весь этот код из потока компиляции, тем самым уменьшая размер кода.

## <a name="see-also"></a>См. также раздел

[Дополнительные методы поставщика](../../data/oledb/advanced-provider-techniques.md)
