---
description: Дополнительные сведения см. в статье как предоставить рабочие функции классам Call и transformer.
title: Практическое руководство. Предоставление рабочих функций классам call и transformer
ms.date: 11/04/2016
helpviewer_keywords:
- call class, example
- using the transformer class [Concurrency Runtime]
- using the call class [Concurrency Runtime]
ms.assetid: df715ce4-8507-41ca-b204-636d11707a73
ms.openlocfilehash: 05def4dcc8357e73a8606fbc4ce741eebb647d37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197365"
---
# <a name="how-to-provide-work-functions-to-the-call-and-transformer-classes"></a>Практическое руководство. Предоставление рабочих функций классам call и transformer

В этом разделе показано несколько способов предоставления рабочих функций классам [Concurrency:: Call](../../parallel/concrt/reference/call-class.md) и [Concurrency:: transformer](../../parallel/concrt/reference/transformer-class.md) .

В первом примере показано, как передать лямбда-выражение `call` объекту. Во втором примере показано, как передать объект функции в `call` объект. В третьем примере показано, как привязать метод класса к `call` объекту.

Для иллюстрации каждый пример в этом разделе использует `call` класс. Пример использования `transformer` класса см. в разделе [как использовать преобразователь в конвейере данных](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

## <a name="example-call-class"></a>Пример. вызов класса

В следующем примере показан распространенный способ использования `call` класса. В этом примере лямбда-функция передается в `call` конструктор.

[!code-cpp[concrt-call-lambda#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_1.cpp)]

В этом примере формируются следующие данные:

```Output
13 squared is 169.
```

## <a name="example-call-class-with-function-object"></a>Пример: вызов класса с объектом функции

Следующий пример похож на предыдущий, за исключением того, что он использует `call` класс вместе с объектом функции (функтор).

[!code-cpp[concrt-call-functor#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_2.cpp)]

## <a name="example-functions-to-bind-call-object"></a>Пример: функции для привязки объекта вызова

Следующий пример похож на предыдущий, за исключением того, что он использует функции [std:: bind1st](../../standard-library/functional-functions.md#bind1st) и [std:: mem_fun](../../standard-library/functional-functions.md#mem_fun) для привязки `call` объекта к методу класса.

Используйте этот метод, если необходимо привязать `call` объект или `transformer` к конкретному методу класса, а не к оператору вызова `operator()` функции.

[!code-cpp[concrt-call-method#1](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_3.cpp)]

Можно также присвоить результат `bind1st` функции объекту [std:: Function](../../standard-library/function-class.md) или использовать **`auto`** ключевое слово, как показано в следующем примере.

[!code-cpp[concrt-call-method#2](../../parallel/concrt/codesnippet/cpp/how-to-provide-work-functions-to-the-call-and-transformer-classes_4.cpp)]

## <a name="compiling-the-code"></a>Компиляция кода

Скопируйте пример кода и вставьте его в проект Visual Studio или вставьте в файл с именем, `call.cpp` а затем выполните следующую команду в окне командной строки Visual Studio.

> **cl.exe/EHsc Call. cpp**

## <a name="see-also"></a>См. также раздел

[библиотеку асинхронных агентов](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Асинхронные блоки сообщений](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Как использовать преобразователь в конвейере данных](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
[Класс Call](../../parallel/concrt/reference/call-class.md)<br/>
[Класс transformer](../../parallel/concrt/reference/transformer-class.md)
