---
title: Пошаговые руководства по среде выполнения с параллелизмом
ms.date: 11/04/2016
helpviewer_keywords:
- walkthroughs [Concurrency Runtime]
- Concurrency Runtime, walkthroughs
ms.assetid: 7374c5e9-54eb-44bf-9ed9-5e190cfd290b
ms.openlocfilehash: f26ff3ba35539b24e4c670935212069a34b942a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511089"
---
# <a name="concurrency-runtime-walkthroughs"></a>Пошаговые руководства по среде выполнения с параллелизмом

Разделы на основе сценариев, в этом разделе показано, как использовать многие функции среды выполнения с параллелизмом.

## <a name="in-this-section"></a>В этом разделе

[Пошаговое руководство. Подключение с использованием задач и HTTP-запросов XML](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Демонстрируется использование [IXMLHTTPRequest2](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2) и [IXMLHTTPRequest2Callback](/previous-versions/windows/desktop/api/msxml6/nn-msxml6-ixmlhttprequest2callback) интерфейсы вместе с задачами отправки запросов HTTP GET и POST для веб-службы в приложении универсальной платформы Windows (UWP).

[Пошаговое руководство. Создание приложения на основе агента](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
В этой статье описывается создание базового приложения на основе агентов.

[Пошаговое руководство. Создание агента потоков данных](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
В этой статье демонстрируется создание приложения на основе агента в потоке данных, а не на основе потока управления.

[Пошаговое руководство. Создание сети обработки изображений](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
Показано, как создавать сеть асинхронных блоков сообщений, выполняющих обработку изображений.

[Пошаговое руководство. Реализация фьючерсов](../../parallel/concrt/walkthrough-implementing-futures.md)<br/>
Показано, как асинхронно вычислять значения для последующего использования.

[Пошаговое руководство. Использование класса join для предотвращения взаимоблокировки](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)<br/>
Использует примере проблемы обедающих философов показано использование [concurrency::join](../../parallel/concrt/reference/join-class.md) класс для недопущения взаимоблокировок в приложении.

[Пошаговое руководство. Удаление задач из потока пользовательского интерфейса](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
Показано, как повысить производительность приложения MFC, рисующего фрактал Мандельброта.

[Пошаговое руководство. Использование среды выполнения с параллелизмом в приложениях с поддержкой модели COM](../../parallel/concrt/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application.md)<br/>
В этой статье демонстрируется использование среды выполнения с параллелизмом в приложении, которое использует компонент модели объектов (COM).

[Пошаговое руководство. Адаптация существующего кода для использования упрощенных задач](../../parallel/concrt/walkthrough-adapting-existing-code-to-use-lightweight-tasks.md)<br/>
Показано, как адаптировать имеющийся код, использующее Windows API для создания и выполнения потока используется упрощенная задача.

[Пошаговое руководство. Создание пользовательского блока сообщений](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md)<br/>
Описывает, как создать пользовательский тип блока сообщений, сортирующий входящие сообщения по приоритету.

## <a name="related-sections"></a>Связанные разделы

[Среда выполнения с параллелизмом](../../parallel/concrt/concurrency-runtime.md)<br/>
Представляет платформой параллельного программирования для Visual C++.

