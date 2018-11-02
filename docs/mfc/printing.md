---
title: Печать
ms.date: 11/04/2016
helpviewer_keywords:
- view classes [MFC], print operations
- documents [MFC], printing
- printing [MFC], from framework
- printing [MFC]
ms.assetid: be465e8d-b0c9-4fc5-9fa8-d10486064f76
ms.openlocfilehash: 88b89ee54ec6270b01859d0f0baeea0efebd9ad6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589399"
---
# <a name="printing"></a>Печать

Microsoft Windows реализует зависящих от устройства отображения. В MFC, это означает, что же вызовы рисования, в `OnDraw` функция-член класса представления, несут ответственность за рисование на экране и на других устройствах, таких как принтеры. Для предварительного просмотра печати целевое устройство – имитации печати для отображения.

##  <a name="_core_your_role_in_printing_vs.._the_framework.92.s_role"></a> Роль в печати и роль платформы

Представление класса имеет следующие обязанности:

- Сообщите платформы, сколько страниц в документе.

- При запросе на печать на указанной странице, нарисуйте этой части документа.

- Выделять и освобождать все шрифты или других графических устройств (интерфейс) ресурсы, необходимые для печати.

- При необходимости будет отправить escape-кодами. Чтобы изменить режим принтера перед печатью на данной странице, например, изменение ориентации на уровне страниц.

Ниже приведены обязанности платформы:

- Отображение **печати** диалоговое окно.

- Создание [CDC](../mfc/reference/cdc-class.md) объекта для принтера.

- Вызовите [StartDoc](../mfc/reference/cdc-class.md#startdoc) и [EndDoc](../mfc/reference/cdc-class.md#enddoc) функциями-членами `CDC` объекта.

- Раз вызвать [StartPage](../mfc/reference/cdc-class.md#startpage) функцию-член `CDC` объекта, информирования класса представления страницы следует печатать, а также вызвать [EndPage](../mfc/reference/cdc-class.md#endpage) функцию-член `CDC` объекта.

- Вызовите переопределяемые функции в представлении в нужное время.

В следующих статьях рассматриваются, как платформа поддерживает печати и предварительного просмотра:

### <a name="what-do-you-want-to-know-more-about"></a>Выберите для получения дополнительных сведений

- [По умолчанию печать по](../mfc/how-default-printing-is-done.md)

- [Многостраничные документы](../mfc/multipage-documents.md)

- [Верхние и нижние колонтитулы](../mfc/headers-and-footers.md)

- [Выделение ресурсов GDI для печати](../mfc/allocating-gdi-resources.md)

- [Предварительный просмотр печати](../mfc/print-preview-architecture.md)

## <a name="see-also"></a>См. также

[Печать и предварительный просмотр печати](../mfc/printing-and-print-preview.md)

