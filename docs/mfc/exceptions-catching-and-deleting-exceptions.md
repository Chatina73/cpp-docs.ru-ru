---
title: Исключения. Перехват и удаление исключений
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 370062d3e17127e711f2b4356cbb133a6c1d20b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625918"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Исключения. Перехват и удаление исключений

Следующие инструкции и примеры показывают, как для перехвата и удаление исключений. Дополнительные сведения о **попробуйте**, **catch**, и **throw** ключевые слова, см. в разделе [обработка исключений C++](../cpp/cpp-exception-handling.md).

Обработчиках исключений необходимо удалить объекты исключений, которые они обрабатывают, так как не удалось удалить исключение приводит к утечке памяти каждый раз, когда этот код перехватывает исключение.

Ваш **catch** блок необходимо удалить исключение при:

- **Catch** блок вызывает исключение.

   Конечно не удаляйте исключение при появлении этого исключения еще раз:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Выполнение возвращается изнутри **catch** блока.

> [!NOTE]
>  При удалении `CException`, использовать `Delete` функция-член для удаления исключение. Не используйте **удалить** ключевое слово, так как он может завершиться ошибкой, если исключение не в куче.

#### <a name="to-catch-and-delete-exceptions"></a>Для перехвата и удаление исключений

1. Используйте **попробуйте** ключевое слово для настройки **попробуйте** блока. Выполните все инструкции программы, которые могут создавать исключение в **попробуйте** блока.

   Используйте **catch** ключевое слово для настройки **catch** блока. Поместите код обработки исключений в **catch** блока. Код в **catch** блок выполняется только в том случае, если код внутри **попробуйте** блок вызывает исключение типа, указанного в **catch** инструкции.

   Скелет показано как **попробуйте** и **catch** блоки обычно упорядочиваются:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Когда создается исключение, управление передается первой **catch** блок, объявление которого исключение соответствует типу исключения. Можно выборочно обрабатывать различные типы исключений с последующими **catch** блокирует, как показано ниже:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Дополнительные сведения см. в разделе [исключения: преобразование из макроса исключений MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>См. также

[Обработка исключений](../mfc/exception-handling-in-mfc.md)

