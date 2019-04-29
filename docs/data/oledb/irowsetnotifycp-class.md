---
title: Класс IRowsetNotifyCP
ms.date: 11/04/2016
f1_keywords:
- IRowsetNotifyCP
- Fire_OnFieldChange
- ATL::IRowsetNotifyCP::Fire_OnFieldChange
- ATL.IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnFieldChange
- IRowsetNotifyCP::Fire_OnFieldChange
- IRowsetNotifyCP.Fire_OnRowChange
- ATL.IRowsetNotifyCP.Fire_OnRowChange
- Fire_OnRowChange
- ATL::IRowsetNotifyCP::Fire_OnRowChange
- IRowsetNotifyCP::Fire_OnRowChange
- Fire_OnRowsetChange
- IRowsetNotifyCP::Fire_OnRowsetChange
- IRowsetNotifyCP.Fire_OnRowsetChange
- ATL::IRowsetNotifyCP::Fire_OnRowsetChange
- ATL.IRowsetNotifyCP.Fire_OnRowsetChange
helpviewer_keywords:
- IRowsetNotifyCP class
- Fire_OnFieldChange method
- Fire_OnRowChange method
- Fire_OnRowsetChange method
ms.assetid: ccef402b-94a0-4c2e-9a13-7e854ef82390
ms.openlocfilehash: a3ab63206ce7ac53ff996ecf1bb64bdaa0b79fcb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390741"
---
# <a name="irowsetnotifycp-class"></a>Класс IRowsetNotifyCP

Реализует поставщик сайта для точки подключения интерфейса [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)).

## <a name="syntax"></a>Синтаксис

```cpp
template <class T, class ReentrantEventSync = CComSharedMutex>
class IRowsetNotifyCP :
   public IConnectionPointImpl<
      T,
      piid = &__uuidof(IRowsetNotify),
      CComDynamicUnkArray DynamicUnkArray>,
   public ReentrantEventSync
```

### <a name="parameters"></a>Параметры

*T*<br/>
Класс, производный от `IRowsetNotifyCP`.

*ReentrantEventSync*<br/>
Класс mutex, поддерживающий повторного входа (по умолчанию используется `CComSharedMutex`). Мьютекс — объект синхронизации, позволяющий один поток взаимно исключают друг друга доступ к ресурсу.

*piid*<br/>
Указатель на интерфейс идентификатор (`IID*`) для `IRowsetNotify` интерфейса точки подключения. Значение по умолчанию — `&__uuidof(IRowsetNotify)`.

*DynamicUnkArray*<br/>
Массив объектов типа [CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md), которая представляет динамический массив `IUnknown` указатели на клиенте приемник интерфейсов.

## <a name="requirements"></a>Требования

**Заголовок:** atldb.h

## <a name="members"></a>Участники

### <a name="methods"></a>Методы

|||
|-|-|
|[Fire_OnFieldChange](#onfieldchange)|Уведомляет объект-получатель изменения значения столбца.|
|[Fire_OnRowChange](#onrowchange)|Уведомляет объект-получатель изменений, влияющих на строки.|
|[Fire_OnRowsetChange](#onrowsetchange)|Уведомляет объект-получатель изменений, влияющих на весь набор строк.|

## <a name="remarks"></a>Примечания

`IRowsetNotifyCP` реализует широковещательных функции для в точке подключения `IID_IRowsetNotify` об изменениях содержимого набора строк.

Обратите внимание, что необходимо также реализовать и зарегистрировать `IRowsetNotify` на объекте-получателе (также называется «приемник») с помощью [IRowsetNotifyImpl](../../data/oledb/irowsetnotifyimpl-class.md) потребитель может обрабатывать уведомления. См. в разделе [получение уведомлений](../../data/oledb/receiving-notifications.md) о реализации интерфейса точки подключения на объекте-получателе.

Подробные сведения о реализации уведомлений см. в разделе «Поддержка уведомления» в [Создание поставщика с возможностью записи](../../data/oledb/creating-an-updatable-provider.md).

## <a name="onfieldchange"></a> IRowsetNotifyCP::Fire_OnFieldChange

Осуществляет широковещательную передачу [OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) событие для уведомления пользователей об изменении значения столбца.

### <a name="syntax"></a>Синтаксис

```cpp
HRESULT Fire_OnFieldChange(IRowset* pRowset,
   HROW hRow,
   DBORDINAL cColumns,
   DBORDINAL* rgColumns,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IRowsetNotify::OnFieldChange](/previous-versions/windows/desktop/ms715961(v=vs.85)) в *справочнике программиста OLE DB*.

## <a name="onrowchange"></a> IRowsetNotifyCP::Fire_OnRowChange

Осуществляет широковещательную передачу [OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) событий все прослушиватели в точке подключения `IID_IRowsetNotify` для уведомления потребителей изменений, влияющих на строки.

### <a name="syntax"></a>Синтаксис

```cpp
HRESULT Fire_OnRowChange(IRowset* pRowset,
   DBCOUNTITEM cRows,
   const HROW rghRows[],
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IRowsetNotify::OnRowChange](/previous-versions/windows/desktop/ms722694(v=vs.85)) в *справочнике программиста OLE DB*.

## <a name="onrowsetchange"></a> IRowsetNotifyCP::Fire_OnRowsetChange

Осуществляет широковещательную передачу [OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) событий все прослушиватели в точке подключения `IID_IRowsetNotify` для уведомления потребителей изменений, влияющих на весь набор строк.

### <a name="syntax"></a>Синтаксис

```cpp
HRESULT Fire_OnRowsetChange(IRowset* pRowset,
   DBREASON eReason,
   DBEVENTPHASE ePhase,
   BOOL fCantDeny);
```

#### <a name="parameters"></a>Параметры

См. в разделе [IRowsetNotify::OnRowsetChange](/previous-versions/windows/desktop/ms722669(v=vs.85)) в *справочнике программиста OLE DB*.

## <a name="see-also"></a>См. также

[Шаблоны поставщика OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Уведомления (COM)](/windows/desktop/com/notifications)<br/>
[BEGIN_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#begin_connection_point_map)<br/>
[END_CONNECTION_POINT_MAP](../../atl/reference/connection-point-macros.md#end_connection_point_map)<br/>
[CONNECTION_POINT_ENTRY](../../atl/reference/connection-point-macros.md#connection_point_entry)<br/>
[Создание поставщика с возможностью записи](../../data/oledb/creating-an-updatable-provider.md)