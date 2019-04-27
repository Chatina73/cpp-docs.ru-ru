---
title: Классы документов
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: a7034a99bfefe8f4c11cdf8f99dc4b0c31fac10a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219799"
---
# <a name="document-classes"></a>Классы документов

Объекты класса документа, созданные объекты шаблонов документов, управления данными приложения. Класс будет наследовать для документов из одного из этих классов.

Объекты класса документа взаимодействовать с объектами представления. Просмотр объектов представляют клиентской области окна, отображения данных документа и разрешить пользователям взаимодействовать с ним. Документов и представлений, создаваемые объект шаблона документа.

[CDocument](../mfc/reference/cdocument-class.md)<br/>
Базовый класс для конкретных документов. Являются производными класса документа или классы из `CDocument`.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Используется для реализации составных документов, а также поддержка основной контейнер. Выступает в качестве контейнера для классов, производным от [CDocItem](../mfc/reference/cdocitem-class.md). Этот класс используется как базовый класс для контейнера, документы и является базовым классом для `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Класс, производный от `COleDocument` , предоставляет инфраструктуру для связывания. Необходимо создать производный классы документов для приложения-контейнеры от этого класса, а не из `COleDocument` при необходимости для поддержки ссылки на внедренные объекты.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Поддерживает список клиентских элементов управления OLE, которые в элементе управления форматированным редактированием. Используется с [CRichEditView](../mfc/reference/cricheditview-class.md) и [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Используется как базовый класс для классов документа серверного приложения. `COleServerDoc` объекты предоставляют основная часть поддержки сервера при взаимодействии с [COleServerItem](../mfc/reference/coleserveritem-class.md) объектов. Возможность визуального редактирования обеспечивается с помощью архитектуры document/view библиотеки классов.

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
Предоставляет, с помощью [CHtmlEditView](../mfc/reference/chtmleditview-class.md), функции платформы редактирования WebBrowser HTML в контексте архитектуры представления документов MFC.

## <a name="related-classes"></a>Связанные классы

Объекты класса документа может быть постоянным — другими словами, записать свое состояние в среде хранения и их чтения. MFC предоставляет `CArchive` класса для упрощения передачи данных документа в среду хранения.

[CArchive](../mfc/reference/carchive-class.md)<br/>
Взаимодействует с [CFile](../mfc/reference/cfile-class.md) объекту реализовать постоянное хранилище объектов с помощью сериализации (см. в разделе [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

Документы также могут содержать объекты OLE. `CDocItem` является базовым классом элементов сервера и клиента.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Абстрактный базовый класс для [COleClientItem](../mfc/reference/coleclientitem-class.md) и [COleServerItem](../mfc/reference/coleserveritem-class.md). Объекты классов, производные от `CDocItem` представляют частей документов.

## <a name="see-also"></a>См. также

[Общие сведения о классе](../mfc/class-library-overview.md)
