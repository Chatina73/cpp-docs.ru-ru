---
description: Дополнительные сведения о функциях управления памятью
title: Функции управления памятью
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: d75778f99294c1a177ac204bb0fb96c3ee84422c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205542"
---
# <a name="memory-management-functions"></a>Функции управления памятью

В этом документе описываются функции управления памятью, предоставляемые среда выполнения с параллелизмом, позволяющие одновременно распределять и освобождать память.

> [!TIP]
> Среда выполнения с параллелизмом предоставляет планировщик по умолчанию, и таким образом не требуется создавать планировщик в приложении. Поскольку планировщик задач помогает точно настроить производительность приложений, рекомендуется начать с [библиотеки параллельных шаблонов (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) или [библиотеки асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md) , если вы не знакомы с среда выполнения с параллелизмом.

Среда выполнения с параллелизмом предоставляет две функции управления памятью, оптимизированные для одновременного выделения и освобождения блоков памяти. Функция [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) выделяет блок памяти, используя указанный размер. Функция [Concurrency:: Free](reference/concurrency-namespace-functions.md#free) освобождает память, выделенную `Alloc` .

> [!NOTE]
> `Alloc`Функции и `Free` зависят друг от друга. Используйте `Free` функцию только для освобождения памяти, выделенной с помощью `Alloc` функции. Кроме того, при использовании `Alloc` функции для выделения памяти используйте только `Free` функцию для освобождения этой памяти.

Используйте `Alloc` функции и `Free` при выделении и освобождении фиксированного набора размеров выделения из разных потоков или задач. Среда выполнения с параллелизмом кэширует память, выделенную ей из кучи среды выполнения C. Среда выполнения с параллелизмом содержит отдельный кэш памяти для каждого выполняющегося потока; Таким образом, среда выполнения управляет памятью без использования блокировок или барьеров памяти. Приложение имеет больше преимуществ `Alloc` функций и, `Free` когда доступ к кэшу памяти осуществляется чаще. Например, поток, который часто вызывает как, так `Alloc` и `Free` более выгоднее, чем поток, который в основном вызывает `Alloc` или `Free` .

> [!NOTE]
> Если вы используете эти функции управления памятью и ваше приложение использует много памяти, приложение может ввести условие нехватки памяти быстрее, чем вы ждете. Поскольку блоки памяти, кэшированные одним потоком, недоступны для любого другого потока, в случае, если один поток удерживает много памяти, эта память недоступна.

## <a name="example"></a>Пример

Пример использования `Alloc` `Free` функций и для повышения производительности памяти см. в разделе [как использовать Alloc и Free для повышения производительности памяти](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>См. также раздел

[Планировщик заданий](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Как использовать Alloc и Free для повышения производительности памяти](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
