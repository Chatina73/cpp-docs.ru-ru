---
description: 'Дополнительные сведения: политики планировщика'
title: Политики планировщика
ms.date: 11/04/2016
helpviewer_keywords:
- scheduler policies
ms.assetid: 58fb68bd-4a57-40a8-807b-6edb6f083cd9
ms.openlocfilehash: 42b5fa951c320fcc3bab8fe5abe3bb4988e6c368
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97188018"
---
# <a name="scheduler-policies"></a>Политики планировщика

В этом документе описывается роль политик планировщика в среда выполнения с параллелизмом. *Политика планировщика* управляет стратегией, которую планировщик использует при управлении задачами. Например, рассмотрим приложение, которое требует выполнение некоторых задач с `THREAD_PRIORITY_NORMAL` и других задач с `THREAD_PRIORITY_HIGHEST`.  Можно создать два экземпляра планировщика: один задает политику `ContextPriority` как `THREAD_PRIORITY_NORMAL`, а второй определяет ту же политику как `THREAD_PRIORITY_HIGHEST`.

Использование политики планировщика позволяет разделять доступные ресурсы для обработки и назначать каждому планировщику фиксированный набор ресурсов. Например, рассмотрим параллельный алгоритм, который не масштабируется за пределы четырех процессоров. Вы можете создать политику планировщика, которая ограничивает количество одновременно используемых задач более чем четырьмя процессорами.

> [!TIP]
> Исполняющая среда с параллелизмом предоставляет планировщик по умолчанию. Поэтому не требуется создавать его в приложении. Поскольку планировщик задач помогает точно настроить производительность приложений, рекомендуется начать с [библиотеки параллельных шаблонов (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) или [библиотеки асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md) , если вы не знакомы с среда выполнения с параллелизмом.

При использовании метода [Concurrency:: CurrentScheduler:: Create](reference/currentscheduler-class.md#create), [Concurrency:: Scheduler](reference/scheduler-class.md#create):: Create или [Concurrency:: Scheduler](reference/scheduler-class.md#setdefaultschedulerpolicy) :: SetDefaultSchedulerPolicy для создания экземпляра планировщика вы предоставляете объект [Concurrency:: SchedulerPolicy](../../parallel/concrt/reference/schedulerpolicy-class.md) , содержащий коллекцию пар "ключ-значение", которые определяют поведение планировщика. `SchedulerPolicy`Конструктор принимает переменное число аргументов. Первый аргумент — это число элементов политики, которые вы собираетесь указать. Остальные аргументы — это пары "ключ-значение" для каждого элемента policy. В следующем примере создается `SchedulerPolicy` объект, который задает три элемента политики. Среда выполнения использует для незаданных ключей политики значения по умолчанию.

[!code-cpp[concrt-scheduler-policy#2](../../parallel/concrt/codesnippet/cpp/scheduler-policies_1.cpp)]

Перечисление [Concurrency::P олициелементкэй](reference/concurrency-namespace-enums.md#policyelementkey) определяет ключи политики, связанные с планировщик задач. В следующей таблице описаны ключи политики и значение по умолчанию, используемое средой выполнения для каждого из них.

| Ключ политики | Описание | Значение по умолчанию |
|--|--|--|
| `SchedulerKind` | Значение [Concurrency:: SchedulerType](reference/concurrency-namespace-enums.md#schedulertype) , указывающее тип потоков, используемых для планирования задач. | `ThreadScheduler` (используйте стандартные потоки). Это единственное допустимое значение для этого ключа. |
| `MaxConcurrency` | **`unsigned int`** Значение, указывающее максимальное количество ресурсов параллелизма, используемых планировщиком. | [concurrency::MaxExecutionResources](reference/concurrency-namespace-constants1.md#maxexecutionresources) |
| `MinConcurrency` | **`unsigned int`** Значение типа, указывающее минимальное количество ресурсов параллелизма, используемых планировщиком. | `1` |
| `TargetOversubscriptionFactor` | **`unsigned int`** Значение, указывающее, сколько потоков следует выделить каждому ресурсу обработки. | `1` |
| `LocalContextCacheSize` | **`unsigned int`** Значение, указывающее максимальное количество контекстов, которые могут быть кэшированы в локальной очереди каждого виртуального процессора. | `8` |
| `ContextStackSize` | **`unsigned int`** Значение, указывающее размер стека (в килобайтах), резервируемого для каждого контекста. | `0` (используйте размер стека по умолчанию) |
| `ContextPriority` | **`int`** Значение, указывающее приоритет потока каждого контекста. Это может быть любое значение, которое можно передать в [сетсреадприорити](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) или `INHERIT_THREAD_PRIORITY` . | `THREAD_PRIORITY_NORMAL` |
| `SchedulingProtocol` | Значение [Concurrency:: счедулингпротоколтипе](reference/concurrency-namespace-enums.md#schedulingprotocoltype) , указывающее используемый алгоритм планирования. | `EnhanceScheduleGroupLocality` |
| `DynamicProgressFeedback` | Значение параметра [Concurrency::D инамикпрогрессфидбакктипе](reference/concurrency-namespace-enums.md#dynamicprogressfeedbacktype) , указывающее, следует ли перераспределять ресурсы в соответствии со сведениями о ходе выполнения на основе статистики.<br /><br /> **Примечание** . Не задавайте эту политику, `ProgressFeedbackDisabled` так как она зарезервирована для использования средой выполнения. | `ProgressFeedbackEnabled` |

Каждый планировщик использует собственную политику при планировании задач. Политики, связанные с одним планировщиком, не влияют на поведение других планировщиков. Кроме того, политику планировщика нельзя изменить после создания `Scheduler` объекта.

> [!IMPORTANT]
> Используйте только политики планировщика для управления атрибутами потоков, создаваемых средой выполнения. Не изменяйте сходство или приоритет потоков, создаваемых средой выполнения, поскольку это может привести к неопределенному поведению.

Среда выполнения создает планировщик по умолчанию, если он не создается явным образом. Если вы хотите использовать планировщик по умолчанию в приложении, но хотите указать политику для использования, вызовите метод [Concurrency:: Scheduler:: SetDefaultSchedulerPolicy](reference/scheduler-class.md#setdefaultschedulerpolicy) перед планированием параллельной работы. Если не вызвать `Scheduler::SetDefaultSchedulerPolicy` метод, среда выполнения использует значения политики по умолчанию из таблицы.

Используйте методы [Concurrency:: CurrentScheduler:: Policy](reference/currentscheduler-class.md#getpolicy) и [Concurrency:: Scheduler::-Policy](reference/scheduler-class.md#getpolicy) , чтобы получить копию политики планировщика. Значения политики, получаемые из этих методов, могут отличаться от значений политик, указанных при создании планировщика.

## <a name="example"></a>Пример

Чтобы изучить примеры использования конкретных политик планировщика для управления поведением планировщика, см. раздел [как указать конкретные политики планировщика](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md) и [как создать агенты, использующие определенные политики планировщика](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md).

## <a name="see-also"></a>См. также раздел

[Планировщик заданий](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Как указать конкретные политики планировщика](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br/>
[Как создавать агенты, использующие определенные политики планировщика](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)
