---
title: Сводка по обработке событий ATL
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
ms.assetid: e8b47ef0-0bdc-47ff-9dd6-34df11dde9a2
ms.openlocfilehash: 0e3a47719e3160170ed1bfa64b315415ddc7a1c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252152"
---
# <a name="atl-event-handling-summary"></a>Сводка по обработке событий ATL

Как правило обработка событий COM — это относительно простой процесс. Существует три основных этапа:

- Реализация событий интерфейса для объекта.

- Уведомить источник события, объект хочет получать события.

- Когда объект больше не нужно получать события негативной рекомендации источника события.

## <a name="implementing-the-interface"></a>Реализация интерфейса

Существует четыре основных способа реализации интерфейса с помощью ATL.

|Являются производными от|Подходит для типа интерфейса|Необходимо реализовать все методы *|Требуется библиотеку типов во время выполнения|
|-----------------|---------------------------------|---------------------------------------------|-----------------------------------------|
|Интерфейс|Vtable|Да|Нет|
|[IDispatchImpl](../atl/reference/idispatchimpl-class.md)|Dual|Да|Да|
|[IDispEventImpl](../atl/reference/idispeventimpl-class.md)|Disp-интерфейс|Нет|Да|
|[IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Disp-интерфейс|Нет|Нет|

\* При использовании вспомогательных классов ATL, никогда не требуется реализовывать `IUnknown` или `IDispatch` методы вручную.

## <a name="advising-and-unadvising-the-event-source"></a>О том и Unadvising источника события

Существует три основных способа спроса и unadvising источник событий, с использованием ATL.

|Уведомить функции|Негативной рекомендации функции|Наиболее подходящий для использования с|Требуется отслеживать файл cookie|Комментарии|
|---------------------|-----------------------|--------------------------------|---------------------------------------------|--------------|
|[AtlAdvise](reference/connection-point-global-functions.md#atladvise), [CComPtrBase::Advise](../atl/reference/ccomptrbase-class.md#advise)|[AtlUnadvise](reference/connection-point-global-functions.md#atlunadvise)|Vtable или сдвоенные интерфейсы|Да|`AtlAdvise` — это глобальная функция ATL. `CComPtrBase::Advise` используется [CComPtr](../atl/reference/ccomptr-class.md) и [CComQIPtr](../atl/reference/ccomqiptr-class.md).|
|[IDispEventSimpleImpl::DispEventAdvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventadvise)|[IDispEventSimpleImpl::DispEventUnadvise](../atl/reference/idispeventsimpleimpl-class.md#dispeventunadvise)|[IDispEventImpl](../atl/reference/idispeventimpl-class.md) или [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md)|Нет|Меньше параметров, чем `AtlAdvise` , так как большую часть работы выполняет базовый класс.|
|[CComCompositeControl::AdviseSinkMap(TRUE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|[CComCompositeControl::AdviseSinkMap(FALSE)](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)|Элементы управления ActiveX в составных элементов управления|Нет|`CComCompositeControl::AdviseSinkMap` будет указано, что все записи событий приемника карты. Ту же функцию не рекомендуйте записи. Этот метод вызывается автоматически `CComCompositeControl` класса.|
|[CAxDialogImpl::AdviseSinkMap(TRUE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|[CAxDialogImpl::AdviseSinkMap(FALSE)](../atl/reference/caxdialogimpl-class.md#advisesinkmap)|Элементы управления ActiveX в диалоговое окно|Нет|`CAxDialogImpl::AdviseSinkMap` будет указано и дает негативную рекомендацию все элементы управления ActiveX в ресурс диалогового окна. Это выполняется автоматически для вас.|

## <a name="see-also"></a>См. также

[Обработка событий](../atl/event-handling-and-atl.md)<br/>
[Поддержка IDispEventImpl](../atl/supporting-idispeventimpl.md)
