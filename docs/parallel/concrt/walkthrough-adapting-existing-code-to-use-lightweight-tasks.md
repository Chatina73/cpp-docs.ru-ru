---
description: Дополнительные сведения см. в разделе Пошаговое руководство. адаптация существующего кода для использования упрощенных задач
title: Пошаговое руководство. Адаптация существующего кода для использования упрощенных задач
ms.date: 04/25/2019
helpviewer_keywords:
- using lightweight tasks [Concurrency Runtime]
- lightweight tasks, using [Concurrency Runtime]
ms.assetid: 1edfe818-d274-46de-bdd3-e92967c9bbe0
ms.openlocfilehash: 1c3de0f49dc1edc3392a436bb911e005ef84bcf0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271412"
---
# <a name="walkthrough-adapting-existing-code-to-use-lightweight-tasks"></a>Пошаговое руководство. Адаптация существующего кода для использования упрощенных задач

В этом разделе показано, как адаптировать существующий код, использующий API Windows, для создания и выполнения потока для использования упрощенной задачи.

*Упрощенная задача* — это задача, запланированная непосредственно из объекта [Concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) или [Concurrency:: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) . Упрощенные задачи полезны при адаптации существующего кода к использованию функциональных возможностей планирования среды выполнения с параллелизмом.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем приступить к работе с этим пошаговым руководством, ознакомьтесь с разделом [планировщик задач](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="example"></a>Пример

В следующем примере показано типичное использование API Windows для создания и выполнения потока. В этом примере функция [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) используется для вызова в `MyThreadFunction` отдельном потоке.

### <a name="initial-code"></a>Начальный код

[!code-cpp[concrt-windows-threads#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_1.cpp)]

В этом примере формируются следующие данные:

```Output
Parameters = 50, 100
```

Ниже показано, как адаптировать пример кода, чтобы использовать среда выполнения с параллелизмом для выполнения той же задачи.

### <a name="to-adapt-the-example-to-use-a-lightweight-task"></a>Адаптация примера для использования упрощенной задачи

1. Добавьте `#include` директиву для файла заголовка ConcRT. h.

[!code-cpp[concrt-migration-lwt#2](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_2.cpp)]

1. Добавьте **`using`** директиву для `concurrency` пространства имен.

[!code-cpp[concrt-migration-lwt#3](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_3.cpp)]

1. Измените объявление, `MyThreadFunction` чтобы использовать **`__cdecl`** соглашение о вызовах и для возврата **`void`** .

[!code-cpp[concrt-migration-lwt#4](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_4.cpp)]

1. Измените структуру, включив в нее `MyData` объект [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) , который сигнализирует главному приложению о завершении задачи.

[!code-cpp[concrt-migration-lwt#5](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_5.cpp)]

1. Замените вызов на `CreateThread` вызов метода [Concurrency:: CurrentScheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask) .

[!code-cpp[concrt-migration-lwt#6](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_6.cpp)]

1. Замените вызов на `WaitForSingleObject` вызов метода [Concurrency:: Event:: wait](reference/event-class.md#wait) , чтобы дождаться завершения задачи.

[!code-cpp[concrt-migration-lwt#7](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_7.cpp)]

1. Удалите вызов `CloseHandle` .

1. Измените сигнатуру определения, чтобы она `MyThreadFunction` соответствовала шагу 3.

[!code-cpp[concrt-migration-lwt#8](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_8.cpp)]

1. В конце `MyThreadFunction` функции вызовите метод [Concurrency:: Event:: Set](reference/event-class.md#set) , чтобы сообщить главному приложению о завершении задачи.

[!code-cpp[concrt-migration-lwt#9](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_9.cpp)]

1. Удалите **`return`** оператор из `MyThreadFunction` .

### <a name="completed-code"></a>Завершенный код

В следующем завершенном примере показан код, использующий упрощенную задачу для вызова `MyThreadFunction` функции.

[!code-cpp[concrt-migration-lwt#1](../../parallel/concrt/codesnippet/cpp/walkthrough-adapting-existing-code-to-use-lightweight-tasks_10.cpp)]

## <a name="see-also"></a>См. также раздел

[Планировщик заданий](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Класс Scheduler](../../parallel/concrt/reference/scheduler-class.md)
