---
title: Управление памятью. Изменяемые блоки памяти
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: 499e2d4a99152e08f50159c4c952eb882c9fd425
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481150"
---
# <a name="memory-management-resizable-memory-blocks"></a>Управление памятью. Изменяемые блоки памяти

**Новый** и **удалить** операторы, описанные в статье [управление памятью: примеры](../mfc/memory-management-examples.md), хорошо подходят для выделение и освобождение блоков фиксированного размера памяти и объекты. В некоторых случаях приложение может потребовать изменяемые блоки памяти. Необходимо использовать стандартные функции библиотеки времени выполнения C [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), и [бесплатный](../c-runtime-library/reference/free.md) для управления изменяемые блоки памяти в куче.

> [!IMPORTANT]
>  Смешивание **новый** и **удалить** операторы с функциями переменного размера выделения памяти на одного блока памяти приведет к повреждение памяти в отладочной версии MFC. Не следует использовать **realloc** на блок памяти, выделенной с помощью **новый**. Аналогичным образом, не следует выделить блок памяти с **новый** оператор и удалите его, используя **бесплатный**, или использовать **удалить** оператора в блок памяти, выделенной с помощью **malloc**.

## <a name="see-also"></a>См. также

[Управление памятью. Выделение кучи](../mfc/memory-management-heap-allocation.md)

