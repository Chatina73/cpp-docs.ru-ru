---
description: Дополнительные сведения см. в статье сравнение среда выполнения с параллелизмом с другими моделями параллелизма
title: Сравнение среды выполнения с параллелизмом с другими моделями параллелизма
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, compared to other models
ms.assetid: d8b9a1f4-f15f-43c3-a5b4-c0991edf9c86
ms.openlocfilehash: 3259d24d4eb3d5b4af9731b97c343d4dd01ea6e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97271483"
---
# <a name="comparing-the-concurrency-runtime-to-other-concurrency-models"></a>Сравнение среды выполнения с параллелизмом с другими моделями параллелизма

В этом документе описываются различия между функциями и моделями программирования среды выполнения с параллелизмом и других технологий. Разобравшись, чем преимущества среды выполнения с параллелизмом отличаются от преимуществ других моделей программирования, вы сможете выбрать ту технологию, которая лучше всего соответствует требованиям ваших приложений.

Если сейчас вы используете другую модель программирования, например пул потоков Windows или OpenMP, существуют ситуации, в которых может оказаться выгодным перейти на среду выполнения с параллелизмом. Например, в разделе [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md) описано, когда может быть выгодна миграция из OpenMP в среду выполнения с параллелизмом. Тем не менее, если вы удовлетворены производительностью приложений и текущим уровнем поддержки отладки, миграция не требуется.

Функции и преимущества среды выполнения с параллелизмом можно использовать, чтобы дополнить возможности существующего приложения, использующего другую модель параллелизма. Среда выполнения с параллелизмом не гарантирует балансировку нагрузки, когда несколько планировщиков заданий конкурируют за одни и те же вычислительные ресурсы. Однако если рабочие нагрузки не накладываются, этот эффект проявляется в минимальной степени.

## <a name="sections"></a><a name="top"></a> Священ

- [Сравнение планирования по приоритетам с координированным планированием](#models)

- [Сравнение среды выполнения с параллелизмом с Windows API](#winapi)

- [Сравнение среды выполнения с параллелизмом с OpenMP](#openmp)

## <a name="comparing-preemptive-scheduling-to-cooperative-scheduling"></a><a name="models"></a> Сравнение планирования с вытеснением до совместного планирования

Модель планирования по приоритетам и модель координированного планирования — это два распространенных способа позволить нескольким задачам совместно использовать вычислительные ресурсы, например процессоры или аппаратные потоки.

### <a name="preemptive-and-cooperative-scheduling"></a>Планирование по приоритетам и координированное планирование

*Планирование по приоритетам* — это основанный на приоритетах механизм циклического перебора, который предоставляет каждой задаче монопольный доступ к вычислительному ресурсу на заданный период, а затем переключается на другую задачу. Планирование по приоритетам используется в многозадачных операционных системах, таких как Windows. *Совместное планирование* — это механизм, который предоставляет каждой задаче эксклюзивный доступ к вычислительному ресурсу до тех пор, пока задача не завершится, или пока задача не выдаст доступ к ресурсу. Среда выполнения с параллелизмом использует координированное планирование вместе с приоритетным планировщиком операционной системы, чтобы максимально эффективно использовать ресурсы для обработки.

### <a name="differences-between-preemptive-and-cooperative-schedulers"></a>Различия между приоритетным и координированным планировщиком

Приоритетные планировщики стремятся предоставить нескольким потокам равный доступ к вычислительным ресурсам, чтобы обеспечить обработку каждого потока. На компьютерах с большим объемом вычислительных ресурсов проще реализовать равноправный доступ, однако сложнее обеспечить эффективное использование ресурсов.

Приоритетный планировщик в режиме ядра требует, чтобы при принятии решений планирования код приложения полагался на операционную систему. И наоборот, координированный планировщик в пользовательском режиме позволяет коду приложения принимать собственные решения планирования. Поскольку координированное планирование позволяет приложению принимать множество решений по планированию, это уменьшает временные затраты, связанные с синхронизацией в режиме ядра. Координированный планировщик обычно уступает принятие решений по планированию ядру операционной системы, когда нет другой работы, которую нужно спланировать. Координированный планировщик также уступает планировщику операционной системы, если имеется операция блокировки, которая передана ядру, но не передана планировщику в пользовательском режиме.

### <a name="cooperative-scheduling-and-efficiency"></a>Координированное планирование и эффективность

Для приоритетного планировщика вся работа, имеющая один и тот же уровень приоритета, равнозначна. Обычно приоритетный планировщик планирует потоки в порядке их создания. Кроме того, приоритетный планировщик предоставляет каждому потоку отрезок времени по принципу циклического перебора, основываясь на приоритете потока. Хотя этот механизм обеспечивает равноправность (обработка каждого потока продвигается вперед), отчасти это достигается за счет эффективности. Например, многие алгоритмы с большим объемом вычислений не требуют равноправность. Вместо этого очень важно обеспечить минимальное общее время, затрачиваемое на завершение связанных задач. Координированное планирование позволяет приложению планировать работу более эффективно. Например, рассмотрим приложение с большим числом потоков. Планирование потоков, не использующих ресурсы совместно, для параллельного выполнения позволяет сократить временные затраты на синхронизацию и тем самым повысить эффективность. Еще одним эффективным способом планирования задач является запуск конвейеров задач (где каждая последующая задача обрабатывает выходные данные предыдущей) на одном процессоре, чтобы входные данные каждого этапа конвейера были уже загружены в кэш памяти.

### <a name="using-preemptive-and-cooperative-scheduling-together"></a>Совместное использование планирования по приоритетам и координированного планирования

Координированное планирование не позволяет решить все проблемы, связанные с планированием. Например, задачи, которые не уступают управление другим задачам по принципу равноправности, могут потреблять все доступные вычислительные ресурсы и препятствовать выполнению других задач. Среда выполнения с параллелизмом использует преимущества координированного планирования, чтобы дополнить гарантии равноправности планирования по приоритетам. По умолчанию среда выполнения с параллелизмом использует координированный планировщик, реализующий алгоритм переноса нагрузки для эффективного распределения вычислительных ресурсов. Однако планировщик среды выполнения с параллелизмом также полагается на приоритетный планировщик операционной системы для равномерного распределения ресурсов между приложениями. В приложениях можно также создать пользовательские планировщики и их политики, чтобы осуществлять точный контроль над выполнением потока.

[[Top](#top)]

## <a name="comparing-the-concurrency-runtime-to-the-windows-api"></a><a name="winapi"></a> Сравнение среда выполнения с параллелизмом с API Windows

Программный интерфейс Microsoft Windows, который обычно называют Windows API (ранее назывался Win32), предоставляет модель программирования, позволяющую использовать параллелизм в приложениях. Среда выполнения с параллелизмом использует Windows API для предоставления дополнительных моделей программирования, которые не доступны из базовой операционной системы.

Среда выполнения с параллелизмом использует потоковую модель Windows API для выполнения параллельной работы. Кроме того, она использует механизмы локальной памяти потока и управления памятью Windows API. В Windows 7 и Windows Server 2008 R2 она использует поддержку Windows API для планируемых пользователями потоков и компьютеров, имеющих более 64 аппаратных потоков. Среда выполнения с параллелизмом расширяет модель Windows API, предоставляя координированный планировщик задач и алгоритм переноса нагрузки для оптимизации использования вычислительных ресурсов, а также разрешая использовать несколько экземпляров планировщика одновременно.

### <a name="programming-languages"></a>Языки программирования

Windows API использует язык программирования C для предоставления модели программирования. Среда выполнения с параллелизмом предоставляет интерфейс программирования C++, который использует новейшие функции языка C++. Например, лямбда-функции предоставляют исчерпывающий типобезопасный механизм для определения параллельных рабочих функций. Дополнительные сведения о новейших функциях языка C++, используемых в среде выполнения с параллелизмом, см. в [этом обзоре](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="threads-and-thread-pools"></a>Потоки и пулы потоков

Центральным механизмом параллелизма в Windows AP является поток. Обычно для создания потоков используется функция [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread). Хотя потоки относительно легко создавать и использовать, операционная система выделяет значительный объем времени и ресурсов для управления ими. Кроме того, хотя каждому потоку гарантируется то же время выполнения, что и любому другому потоку с таким же уровнем приоритета, связанные с ним временные затраты требуют создания достаточно крупных задач. Для более мелких или детальных задач издержки, связанные с параллелизмом, могут перевесить преимущества параллельного выполнения задач.

Пулы потоков являются одним из способов снизить затраты на управление потоками. Пользовательские пулы потоков и реализация пула потоков, представленная в Windows API, позволяют эффективно выполнять небольшие рабочие элементы в параллельном режиме. Пул потоков Windows обрабатывает рабочие элементы в очереди в порядке поступления (FIFO). Все рабочие элементы запускаются в порядке добавления в пул.

Среда выполнения с параллелизмом реализует алгоритм переноса нагрузки для расширения механизма планирования FIFO. Алгоритм перемещает задачи, обработка которых еще не начата, в потоки, где рабочие элементы заканчиваются. Хотя алгоритм переноса нагрузки может равномерно распределять рабочую нагрузку, он также может переупорядочивать рабочие элементы. В результате рабочий элемент может запускаться не в том порядке, в котором он был отправлен. Это полезно при рекурсивных алгоритмах, где выше вероятность совместного использования данных более новыми задачами, а не более старыми. Обеспечение первоначального выполнения новых элементов снижает число промахов кэша и, возможно, число ошибок страниц.

С точки зрения операционной системы перенос нагрузки не является равноправным. Однако если приложение реализует алгоритм или задачу для параллельного выполнения, равноправность подзадач не всегда имеет значение. Действительно важно то, насколько быстро завершается задача в общем случае. Для других алгоритмов FIFO является подходящей стратегией планирования.

### <a name="behavior-on-various-operating-systems"></a>Поведение в различных операционных системах

В Windows XP и Windows Vista приложения, использующие среду выполнения с параллелизмом, ведут себя точно так же, за исключением того, что в Windows Vista наблюдается повышение производительности кучи.

В Windows 7 и Windows Server 2008 R2 операционная система дополнительно поддерживает параллелизм и масштабируемость. Например, эти операционные системы поддерживают компьютеры, имеющие более 64 аппаратных потоков. Чтобы воспользоваться преимуществами этих новых функций, необходимо изменить существующее приложение, использующее Windows API. Однако приложение, использующее среду выполнения с параллелизмом, применяет эти возможности автоматически и не требует изменений.

[base.user-mode_scheduling](/windows/win32/procthread/user-mode-scheduling)

[[Top](#top)]

## <a name="comparing-the-concurrency-runtime-to-openmp"></a><a name="openmp"></a> Сравнение среда выполнения с параллелизмом с OpenMP

Среда выполнения с параллелизмом позволяет использовать самые разные модели программирования. Эти модели могут перекрываться с моделями других библиотек или дополнять их. В этом разделе среда выполнения с параллелизмом сравнивается с [OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp).

Модель программирования OpenMP определяется открытым стандартом и обладает четко определенными привязками к языкам программирования Fortran и C/C++. OpenMP версий 2.0 и 2.5 хорошо подходит для параллельных алгоритмов, которые являются итеративными, то есть выполняют параллельные итерации по массиву данных. OpenMP работает наиболее эффективно при предопределенной степени параллелизма и соответствующем уровне доступных ресурсов в системе. Модель OpenMP особенно хорошо подходит для высокопроизводительных вычислений, где очень крупные вычислительные задачи распределяются по вычислительным ресурсам на одном компьютере. В этом случае аппаратная среда известна, и разработчик может рассчитывать на монопольный доступ к вычислительным ресурсам при выполнении алгоритма.

Однако другие, менее ограниченные вычислительные среды, могут показывать не такие высокие результаты при использовании с OpenMP. Например, с помощью OpenMP сложнее реализовать рекурсивные задачи (например, алгоритм быстрой сортировки или поиск в дереве данных). Среда выполнения с параллелизмом дополняет возможности OpenMP, предоставляя [библиотеку параллельных шаблонов](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) и [библиотеку асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md). В отличие от OpenMP среда выполнения с параллелизмом предоставляет динамический планировщик, адаптирующийся к доступным ресурсам и корректирующий уровень параллелизма при изменении рабочей нагрузки.

Многие функции в среде выполнения с параллелизмом можно расширить. Кроме того, можно объединять существующие функции для создания новых. Поскольку модель OpenMP основывается на директивах компилятора, ее не так легко расширять.

Дополнительные сведения о сравнении среды выполнения с параллелизмом с OpenMP и о миграции существующего кода OpenMP для использования среды выполнения с параллелизмом см. в разделе [Migrating from OpenMP to the Concurrency Runtime](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md).

[[Top](#top)]

## <a name="see-also"></a>См. также раздел

[Среда выполнения с параллелизмом](../../parallel/concrt/concurrency-runtime.md)<br/>
[Обзор](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Библиотека параллельных шаблонов](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[библиотеку асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[OpenMP](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md#openmp)
