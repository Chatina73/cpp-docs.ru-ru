---
title: Реализация сдвоенного интерфейса (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- IDispatchImpl class, implementing dual interfaces
- dual interfaces, implementing
ms.assetid: d1da3633-b445-4dcd-8a0a-3efdafada3ea
ms.openlocfilehash: ecd6a0cc90ca4175c4ae898f2e9aa8bf00508a3e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287340"
---
# <a name="implementing-a-dual-interface"></a>Реализация сдвоенного интерфейса

Вы можете реализовать сдвоенного интерфейса с помощью [IDispatchImpl](../atl/reference/idispatchimpl-class.md) класс, который предоставляет реализацию по умолчанию `IDispatch` методы в сдвоенный интерфейс. Дополнительные сведения см. в разделе [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

Чтобы использовать этот класс:

- Определите ваш сдвоенного интерфейса в библиотеке типов.

- Создайте класс, производный от специализации `IDispatchImpl` (передать сведения о библиотеке интерфейс и тип как аргументы шаблонов).

- Добавить запись (или записи) в сопоставление COM для предоставления сдвоенный интерфейс, через `QueryInterface`.

- Реализация vtable частью интерфейса в классе.

- Убедитесь, что библиотеки типов, содержащей определение интерфейса для объектов во время выполнения.

## <a name="atl-simple-object-wizard"></a>Мастер простых объектов ATL

Если вы хотите создать новый интерфейс и новый класс для его реализации, можно использовать [диалоговое окно Добавление класса ATL](../ide/add-class-dialog-box.md), а затем [мастер простых объектов ATL](../atl/reference/atl-simple-object-wizard.md).

## <a name="implement-interface-wizard"></a>Мастер реализации интерфейсов

Если у вас есть существующий интерфейс, можно использовать [мастер реализации интерфейса](../atl/reference/adding-a-new-interface-in-an-atl-project.md) Добавление необходимые базового класса, записей сопоставления COM и реализации каркас метода к существующему классу.

> [!NOTE]
>  Может потребоваться изменить созданный базовый класс, таким образом, чтобы основной и дополнительный номера версии библиотеки типов, передаются как аргументы шаблонов для вашей `IDispatchImpl` базового класса. Мастер реализации интерфейса не проверяет номер версии библиотеки типов.

## <a name="implementing-idispatch"></a>Реализация интерфейса IDispatch

Можно использовать `IDispatchImpl` базовый класс для предоставления реализации disp-интерфейсом, просто указав соответствующую запись в карту COM (с помощью [COM_INTERFACE_ENTRY2](reference/com-interface-entry-macros.md#com_interface_entry2) или [COM_INTERFACE_ENTRY_IID](reference/com-interface-entry-macros.md#com_interface_entry_iid) макрос) до тех пор, пока у вас есть библиотеку типов, описывающий соответствующий сдвоенный интерфейс. Довольно часто для реализации `IDispatch` интерфейса таким образом, например. Мастер простых объектов ATL и оба предполагается, что вы планируете реализовать мастера реализации интерфейса `IDispatch` таким образом, поэтому они добавит соответствующую запись на карту.

> [!NOTE]
>  Предлагает ATL [IDispEventImpl](../atl/reference/idispeventimpl-class.md) и [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) классы для реализации диспетчерских без необходимости библиотеку типов, содержащие определение совместимых сдвоенный интерфейс.

## <a name="see-also"></a>См. также

[Сдвоенные интерфейсы и ATL](../atl/dual-interfaces-and-atl.md)
