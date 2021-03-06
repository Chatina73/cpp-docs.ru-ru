---
description: 'Дополнительные сведения: планировщик задач (среда выполнения с параллелизмом)'
title: Планировщик задач (среда выполнения с параллелизмом)
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
ms.openlocfilehash: db52b6714f5bdb96cb33aeea1bce1d92f5d5d4a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271386"
---
# <a name="task-scheduler-concurrency-runtime"></a>Планировщик задач (среда выполнения с параллелизмом)

Подразделы в этом разделе документации описывают важные возможности планировщика заданий исполняющей среды с параллелизмом. Планировщик задач удобно использовать, когда нужно оптимизировать производительность существующего кода, использующего среду выполнения с параллелизмом.

> [!IMPORTANT]
> Планировщик задач недоступен из приложения для универсальная платформа Windows (UWP). Дополнительные сведения см. [в статье Создание асинхронных операций в C++ для приложений UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).
>
> В Visual Studio 2015 и более поздних версиях класс [Concurrency:: Task](../../parallel/concrt/reference/task-class.md) и связанные типы в из ppltasks. h используют Windows ThreadPool в качестве своего планировщика. Этот раздел больше не относится к типам, определенным в файле ppltasks.h. Параллельные алгоритмы, например parallel_for, продолжают по умолчанию использовать планировщик среды выполнения с параллелизмом.

> [!TIP]
> Среда выполнения с параллелизмом предоставляет планировщик по умолчанию, и таким образом не требуется создавать планировщик в приложении. Поскольку планировщик задач помогает точно настроить производительность приложений, рекомендуется начать с [библиотеки параллельных шаблонов (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) или [библиотеки асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md) , если вы не знакомы с среда выполнения с параллелизмом.

Планировщик задач планирует и координирует задачи во время выполнения. *Задача* — это единица работы, которая выполняет определенное задание. Обычно задача выполняется параллельно с другими задачами. В качестве примеров задач можно назвать работу, выполняемую элементами группы задач, параллельными алгоритмами и асинхронными агентами.

Планировщик задач осуществляет управление сведениями, связанными с эффективным планированием задач на компьютерах с большим объемом вычислительных ресурсов. Планировщик задач также использует новейшие возможности базовой операционной системы. Таким образом, приложения, использующие среду выполнения с параллелизмом, автоматически масштабируются и совершенствуются на оборудовании с расширенными возможностями.

[Сравнение с другими моделями параллелизма](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) описывает различия между механизмами планирования с вытеснением и совместной работой. Планировщик задач использует координированное планирование и алгоритм перехвата работы вместе с планировщиком с приоритетами операционной системы, чтобы максимально эффективно использовать ресурсы для обработки.

Среда выполнения с параллелизмом предоставляет планировщик по умолчанию, поэтому нет необходимости управлять деталями инфраструктуры. Поэтому планировщик задач обычно не используется напрямую. Однако для удовлетворения качественных требований приложения вы можете с помощью планировщика задач предоставить собственную политику планирования или связать планировщики с конкретными задачами. Например, предположим, что имеется подпрограмма параллельной сортировки, которая не может использовать более четырех процессоров. *Политики планировщика* можно использовать для создания планировщика, который создает не более четырех параллельных задач. Выполнение подпрограммы сортировки в данном планировщике позволит другим активным планировщикам использовать все остающиеся вычислительные ресурсы.

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Экземпляры планировщика](../../parallel/concrt/scheduler-instances.md)|В этом разделе описываются экземпляры планировщиков и использование классов `concurrency::Scheduler` и `concurrency::CurrentScheduler` для управления ими. Используйте экземпляры планировщика, когда требуется связать явные политики планирования с определенными типами рабочих нагрузок.|
|[Политики планировщика](../../parallel/concrt/scheduler-policies.md)|В этом разделе описывается роль политик планировщика. Используйте политики планировщика, если нужно управлять стратегией, которую планировщик применяет при управлении задачами.|
|[Планирование групп](../../parallel/concrt/schedule-groups.md)|В этом разделе описывается роль групп расписаний. Используйте группы расписаний, когда требуется высокая степень локальности связанных задач, например если группу связанных задач лучше выполнять в одном узле процессора.|
|[Упрощенные задачи](../../parallel/concrt/lightweight-tasks.md)|В этом разделе описывается роль упрощенных задач. Упрощенные задачи полезны при адаптации существующего кода к использованию функциональных возможностей планирования среды выполнения с параллелизмом.|
|[Контексты](../../parallel/concrt/contexts.md)|В этом разделе описывается роль контекстов, функция `concurrency::wait` и класс `concurrency::Context`. Используйте эту функциональность, если необходимо управлять блокированием, разблокированием и выдачей контекстов или если требуется разрешить превышение лимита в приложении.|
|[Функции управления памятью](../../parallel/concrt/memory-management-functions.md)|В этом разделе описываются функции `concurrency::Alloc` и `concurrency::Free`. Эти функции могут улучшить производительность памяти путем выделения и освобождения памяти в параллельном режиме.|
|[Сравнение с другими моделями параллелизма](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|В этом разделе описываются различия между механизмами приоритетного планирования и координированного планирования.|
|[Библиотека параллельных шаблонов](../../parallel/concrt/parallel-patterns-library-ppl.md)|В этом разделе описывается использование различных параллельных шаблонов, таких как параллельные алгоритмы, в ваших приложениях.|
|[библиотеку асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md)|В этом разделе описывается использование асинхронных агентов в ваших приложениях.|
|[Среда выполнения с параллелизмом](../../parallel/concrt/concurrency-runtime.md)|Описывает среду выполнения с параллелизмом, которая упрощает процесс параллельного программирования и содержит ссылки на соответствующие разделы.|
