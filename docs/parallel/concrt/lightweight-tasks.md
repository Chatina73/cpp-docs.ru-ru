---
description: 'Дополнительные сведения: упрощенные задачи'
title: Упрощенные задачи
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks
ms.assetid: b6dcfc7a-9fa9-4144-96a6-2845ea272017
ms.openlocfilehash: 328d556eacb2e33bdf3077b722defa81669a525c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205568"
---
# <a name="lightweight-tasks"></a>Упрощенные задачи

В этом документе описывается роль упрощенных задач в среда выполнения с параллелизмом. *Упрощенная задача* — это задача, которая планируется непосредственно из `concurrency::Scheduler` `concurrency::ScheduleGroup` объекта или. Упрощенная задача напоминает функцию, которую вы предоставляете функции Windows API [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) . Поэтому упрощенные задачи полезны при адаптации существующего кода к использованию функций планирования среда выполнения с параллелизмом. Среда выполнения с параллелизмом сам использует упрощенные задачи для планирования асинхронных агентов и отправки сообщений между асинхронными блоками сообщений.

> [!TIP]
> Среда выполнения с параллелизмом предоставляет планировщик по умолчанию, и таким образом не требуется создавать планировщик в приложении. Поскольку планировщик задач помогает точно настроить производительность приложений, рекомендуется начать с [библиотеки параллельных шаблонов (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) или [библиотеки асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md) , если вы не знакомы с среда выполнения с параллелизмом.

Упрощенные задачи наносят меньше ресурсов, чем асинхронные агенты и группы задач. Например, среда выполнения не сообщает о завершении упрощенной задачи. Кроме того, среда выполнения не перехватывает и не обрабатывает исключения, возникающие из-за упрощенной задачи. Дополнительные сведения об обработке исключений и упрощенных задачах см. в разделе [обработка исключений](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Для большинства задач рекомендуется использовать более надежные функции, такие как группы задач и параллельные алгоритмы, так как они позволяют более легко разбивать сложные задачи на более простые. Дополнительные сведения о группах задач см. в разделе [параллелизм задач](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Дополнительные сведения о параллельных алгоритмах см. в разделе [Параллельные алгоритмы](../../parallel/concrt/parallel-algorithms.md).

Чтобы создать упрощенную задачу, вызовите метод [Concurrency:: ScheduleGroup:: ScheduleTask](reference/schedulegroup-class.md#scheduletask), [Concurrency:: CurrentScheduler:: ScheduleTask](reference/currentscheduler-class.md#scheduletask)или [Concurrency:: Scheduler:: ScheduleTask](reference/scheduler-class.md#scheduletask) . Чтобы дождаться завершения упрощенной задачи, дождитесь завершения работы родительского планировщика или используйте механизм синхронизации, например объект [Concurrency:: Event](../../parallel/concrt/reference/event-class.md) .

## <a name="example"></a>Пример

Пример, демонстрирующий способ адаптации существующего кода к упрощенной задаче, см. в разделе [Пошаговое руководство. адаптация существующего кода для использования упрощенных задач](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md).

## <a name="see-also"></a>См. также раздел

[Планировщик заданий](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Пошаговое руководство. адаптация существующего кода к использованию упрощенных задач](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)
