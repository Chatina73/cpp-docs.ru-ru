---
title: Среда выполнения с параллелизмом
ms.date: 07/20/2018
helpviewer_keywords:
- Concurrency Runtime, getting started
- ConcRT (see Concurrency Runtime)
- Concurrency Runtime
ms.assetid: 874bc58f-8dce-483e-a3a1-4dcc9e52ed2c
ms.openlocfilehash: fa64e2536fd1697e839f1b4921a290e1b7a30a35
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449692"
---
# <a name="concurrency-runtime"></a>Среда выполнения с параллелизмом

Исполняющая среда с параллелизмом для C++ помогает создавать надежные, масштабируемые, быстро реагирующие параллельные приложения. Она повышает уровень абстракции, чтобы пользователю не приходилось управлять подробностями инфраструктуры, связанными с параллелизмом. Ее также можно использовать для указания политик планирования, соответствующих требованиям качества обслуживания приложений. Эти ресурсы помогут вам начать работу с исполняющей средой с параллелизмом.

Справочную документацию см. в разделе [ссылку](../../parallel/concrt/reference/reference-concurrency-runtime.md).

> [!TIP]
>  Исполняющая среда с параллелизмом интенсивно использует возможности C++11 и соответствует более современному стилю программирования на C++. Чтобы узнать больше, прочитайте [возвращением в C++](../../cpp/welcome-back-to-cpp-modern-cpp.md).

## <a name="choosing-concurrency-runtime-features"></a>Выбор возможности среды выполнения с параллелизмом

|||
|-|-|
|[Обзор](../../parallel/concrt/overview-of-the-concurrency-runtime.md)|Объясняет, почему важна среда выполнения с параллелизмом и описывает ее основные компоненты.|
|[Сравнение с другими моделями параллелизма](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Показывает характеристики среды выполнения с параллелизмом в сравнении с другими моделями параллелизма, например пулом потоков Windows и OpenMP, чтобы использовать ту модель параллелизма, которая лучше всего соответствует требованиям приложения.|
|[Переход от OpenMP к среде выполнения с параллелизмом](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)|Здесь OpenMP сравнивается с исполняющей средой с параллелизмом, и предоставляются примеры способов миграции существующего кода OpenMP для использования исполняющей среды с параллелизмом.|
|[Библиотека параллельных шаблонов (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Здесь представлены общие сведения о работе с PPL, предоставляющей параллельные циклы, задачи и контейнеры.|
|[Библиотека асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md)|Здесь приводятся способы использования асинхронных агентов и функций передачи сообщений, позволяющих встроить в приложения потоки данных и обеспечить конвейерную обработку задач.|
|[Планировщик задач](../../parallel/concrt/task-scheduler-concurrency-runtime.md)|Содержит описание планировщика задач, который позволяет точно настроить производительность ваших приложений для настольных систем, использующих исполняющую среду с параллелизмом.|

## <a name="task-parallelism-in-the-ppl"></a>Параллелизм задач в PPL

|||
|-|-|
|[Параллелизм задач](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br /><br /> [Практическое руководство. Использование функции parallel_invoke для написания программы параллельной сортировки](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md)<br /><br /> [Практическое руководство. Использование функции parallel_invoke для выполнения параллельных операций](../../parallel/concrt/how-to-use-parallel-invoke-to-execute-parallel-operations.md)<br /><br /> [Практическое руководство. Создание задачи, выполняемой после задержки](../../parallel/concrt/how-to-create-a-task-that-completes-after-a-delay.md)|Содержит описание задач и групп задач, которые могут помочь в создании асинхронного кода и декомпозиции параллельной работы на меньшие части.|
|[Пошаговое руководство: Реализация Futures](../../parallel/concrt/walkthrough-implementing-futures.md)|Здесь показано, как объединить возможности исполняющей среды с параллелизмом для выполнения более объемной задачи.|
|[Пошаговое руководство: Удаление задач из потока, обрабатывающего события от пользовательского интерфейса](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)|Здесь показано, как переместить работу, выполняемую потоком ИП, в рабочий поток в приложении MFC.|
|[Рекомендации по работе с библиотекой параллельных шаблонов](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Общие рекомендации в среде выполнения с параллелизмом](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Рекомендации по работе с PPL.|

## <a name="data-parallelism-in-the-ppl"></a>Параллелизм данных в PPL

|||
|-|-|
|[Параллельные алгоритмы](../../parallel/concrt/parallel-algorithms.md)<br /><br /> [Практическое руководство. Написание цикла parallel_for](../../parallel/concrt/how-to-write-a-parallel-for-loop.md)<br /><br /> [Практическое руководство. Написание цикла parallel_for_each](../../parallel/concrt/how-to-write-a-parallel-for-each-loop.md)<br /><br /> [Практическое руководство. Параллельное выполнение операций сопоставления и редукции числа элементов](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)|Здесь приводится описание `parallel_for`, `parallel_for_each`, `parallel_invoke`и других параллельных алгоритмов. Используйте параллельные алгоритмы для решения задач *параллельных данных* , включающих коллекции данных.|
|[Параллельные контейнеры и объекты](../../parallel/concrt/parallel-containers-and-objects.md)<br /><br /> [Практическое руководство. Использование параллельных контейнеров для повышения эффективности](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br /><br /> [Практическое руководство. Использование класса combinable для повышения производительности](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br /><br /> [Практическое руководство. Использование класса combinable для комбинирования наборов](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)|Здесь приводится описание классов `combinable` , `concurrent_vector`, `concurrent_queue`, `concurrent_unordered_map`и других параллельных контейнеров. Используйте параллельные контейнеры и объекты, когда требуются контейнеры, предоставляющие потокобезопасный доступ к своим элементам.|
|[Рекомендации по работе с библиотекой параллельных шаблонов](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br /><br /> [Общие рекомендации в среде выполнения с параллелизмом](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Рекомендации по работе с PPL.|

## <a name="canceling-tasks-and-parallel-algorithms"></a>Отмена задач и параллельных алгоритмов

|||
|-|-|
|[Отмена в библиотеке параллельных шаблонов](cancellation-in-the-ppl.md)|Здесь описывается роль отмены в PPL, включая способы создания запросов отмены и реагирования на них.|
|[Практическое руководство. Использование отмены для выхода из параллельного цикла](../../parallel/concrt/how-to-use-cancellation-to-break-from-a-parallel-loop.md)<br /><br /> [Практическое руководство. Использование обработки исключений для выхода из параллельного цикла](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md)|Здесь демонстрируются два способа отмены работы с параллельными данными.|

## <a name="universal-windows-platform-apps"></a>Приложения универсальной платформы Windows

|||
|-|-|
|[Создание асинхронных операций на C++ для приложений UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md)|Здесь описываются некоторые ключевые аспекты, которые следует помнить при использовании среды выполнения с параллелизмом для создания асинхронных операций в приложении UWP.|
|[Пошаговое руководство: Подключение с использованием задач и HTTP-запросов XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)|Показано, как объединить задачи PPL с `IXMLHTTPRequest2` и `IXMLHTTPRequest2Callback` интерфейсы для отправки запросов HTTP GET и POST веб-службы в приложении UWP.|
|[Примеры приложений для среды выполнения Windows](https://code.msdn.microsoft.com/windowsapps)|Содержит загружаемые примеры кода и демонстрации приложений для Windows 8.x. Примеры на C++ используют функции исполняющей среды с параллелизмом, например задачи PPL, для обработки данных в фоновом режиме с целью сохранения пользовательского интерфейса в откликающемся состоянии.|

## <a name="dataflow-programming-in-the-asynchronous-agents-library"></a>Программирование потоков данных в библиотеке асинхронных агентов

|||
|-|-|
|[Асинхронные агенты](../../parallel/concrt/asynchronous-agents.md)<br /><br /> [Асинхронные блоки сообщений](../../parallel/concrt/asynchronous-message-blocks.md)<br /><br /> [Функции передачи сообщений](../../parallel/concrt/message-passing-functions.md)<br /><br /> [Практическое руководство. Реализация различных шаблонов "объект-источник — объект-получатель"](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br /><br /> [Практическое руководство. Предоставление рабочих функций классам call и transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br /><br /> [Практическое руководство. Использование преобразователя в конвейере данных](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br /><br /> [Практическое руководство. Выбор среди завершенных задач](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br /><br /> [Практическое руководство. Отправка сообщений через определенные интервалы](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br /><br /> [Практическое руководство. Использование фильтра блоков сообщений](../../parallel/concrt/how-to-use-a-message-block-filter.md)|Здесь описываются асинхронные агенты, блоки сообщений и функции передачи сообщений, которые являются стандартными сборочными блоками для выполнения операций с потоками данных в исполняющей среде с параллелизмом.|
|[Пошаговое руководство: Создание приложения на основе агента](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br /><br /> [Пошаговое руководство: Создание агента для обработки потоков данных](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)|Здесь демонстрируется создание простого приложения на основе агентов.|
|[Пошаговое руководство: Создание сети обработки изображений](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)|Здесь показано, как создавать сеть асинхронных блоков сообщений, выполняющих обработку изображений.|
|[Пошаговое руководство: Использование класса join для предотвращения взаимных блокировок](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)|На примере проблемы обедающих философов показано использование исполняющей среды с параллелизмом для недопущения взаимоблокировок в приложении.|
|[Пошаговое руководство: Создание пользовательского блока сообщений](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)|Здесь описано, как создать пользовательский тип блока сообщений, сортирующий входящие сообщения по приоритету.|
|[Рекомендации по работе с библиотекой асинхронных агентов](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)<br /><br /> [Общие рекомендации в среде выполнения с параллелизмом](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)|Рекомендации по работе с агентами.|

## <a name="exception-handling-and-debugging"></a>Обработка и отладка исключений

|||
|-|-|
|[Обработка исключений](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)|Здесь описана работа с исключениями в среде выполнения с параллелизмом.|
|[Средства диагностики параллельного выполнения](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Описывает способы оптимизации приложений и наиболее эффективного использования среды выполнения с параллелизмом.|

## <a name="tuning-performance"></a>Настройка производительности

|||
|-|-|
|[Средства диагностики параллельного выполнения](../../parallel/concrt/parallel-diagnostic-tools-concurrency-runtime.md)|Описывает способы оптимизации приложений и наиболее эффективного использования среды выполнения с параллелизмом.|
|[Экземпляры планировщика](../../parallel/concrt/scheduler-instances.md)<br /><br /> [Практическое руководство. Управление экземпляром планировщика](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)<br /><br /> [Политики планировщика](../../parallel/concrt/scheduler-policies.md)<br /><br /> [Практическое руководство. Задание определенных политик планировщика](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)<br /><br /> [Практическое руководство. Создание агентов, использующих определенные политики планировщика](../../parallel/concrt/how-to-create-agents-that-use-specific-scheduler-policies.md)|Здесь показаны способы управления экземплярами планировщиков и политиками планировщика. В классических приложениях политики планировщика позволяют связывать определенные правила с определенными типами рабочих нагрузок. Например, можно создать один экземпляр планировщика для выполнения некоторых задач с повышенным приоритетом потока и использовать планировщик по умолчанию для выполнения задач с обычным приоритетом потока.|
|[Группы планирования](../../parallel/concrt/schedule-groups.md)<br /><br /> [Практическое руководство. Использование групп расписаний для определения порядка выполнения](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)|Демонстрирует использование групп планирования для группировки связанных задач. Например, вам может потребоваться высокая локальность связанных задач, если эти задачи лучше выполнять в одном узле процессора.|
|[Упрощенные задачи](../../parallel/concrt/lightweight-tasks.md)|Здесь описывается полезность легковесных задач при создании работы, которая не требует распределения нагрузки или отмены, и как они также могут использоваться для адаптации существующего кода для использования с исполняющей средой с параллелизмом.|
|[Контексты](../../parallel/concrt/contexts.md)<br /><br /> [Практическое руководство. Использование класса Context для реализации семафора, поддерживающего параллельный доступ](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br /><br /> [Практическое руководство. Использование лимита подписки для устранения задержек](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)|Здесь приводятся способы управления поведением потоков, управляемых исполняющей средой с параллелизмом.|
|[Функции управления памятью](../../parallel/concrt/memory-management-functions.md)<br /><br /> [Практическое руководство. Использование функций Alloc и Free для повышения производительности операций с памятью](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)|Здесь описываются функции управления памятью, предоставляемые исполняющей средой с параллелизмом для параллельного выделения и высвобождения памяти.|

## <a name="additional-resources"></a>Дополнительные ресурсы

|||
|-|-|
|[Шаблоны асинхронного программирования и советы по Hilo (приложения Магазина Windows на C++ и XAML)](https://msdn.microsoft.com/library/windows/apps/jj160321.aspx)|Узнайте, как мы использовали среды выполнения с параллелизмом для реализации асинхронных операций в Hilo, приложении среды выполнения Windows на C++ и XAML.|
|[Блог Parallel Programming in Native Code](https://go.microsoft.com/fwlink/p/?linkid=183873)|Содержит дополнительные подробные статьи о параллельном программировании в среде выполнения с параллелизмом.|
|[Форум Parallel Computing in C++ and Native Code](https://go.microsoft.com/fwlink/p/?linkid=183874)|Позволяет участвовать в обсуждениях сообщества о среде выполнения с параллелизмом.|
|[Параллельное программирование](/dotnet/standard/parallel-programming/index)|Содержит сведения о модель параллельного программирования, который доступен в .NET Framework.|

## <a name="see-also"></a>См. также

[Ссылки](../../parallel/concrt/reference/reference-concurrency-runtime.md)
