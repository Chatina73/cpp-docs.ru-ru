---
title: Классы контейнера OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 87db824e5ab4daec15870b245ea8341be7442109
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292566"
---
# <a name="ole-container-classes"></a>Классы контейнера OLE

Эти классы используются приложением-контейнером. Оба `COleLinkingDoc` и `COleDocument` управления наборами `COleClientItem` объектов. Вместо того чтобы наследование класса документов от `CDocument`, вы будете сделайте его производным от `COleLinkingDoc` или `COleDocument`, в зависимости от того, поддержка для ссылки на объекты, внедренные в документ.

Используйте `COleClientItem` объект для представления каждого элемента OLE в документе, который внедрен из другого документа или ссылку на другой документ.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Поддерживает вложение активного документа.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Используется для реализации составных документов, а также поддержка основной контейнер. Выступает в качестве контейнера для классов, производным от `CDocItem`. Этот класс используется как базовый класс для контейнера, документы и является базовым классом для `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Класс, производный от `COleDocument` , предоставляет инфраструктуру для связывания. Необходимо создать производный классы документов для приложения-контейнеры от этого класса, а не из `COleDocument` при необходимости для поддержки ссылки на внедренные объекты.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Поддерживает список клиентских элементов управления OLE, которые в элементе управления форматированным редактированием. Используется с [CRichEditView](../mfc/reference/cricheditview-class.md) и [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Абстрактный базовый класс для `COleClientItem` и `COleServerItem`. Объекты классов, производные от `CDocItem` представляют частей документов.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Класс элемента клиента, представляющий клиентского подключения для внедренного или связанного элемента OLE. Производные элементы клиента от этого класса.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Предоставляет клиентский доступ к объект OLE, элементов, хранящихся в элементе управления "rich edit" при использовании с `CRichEditView` и `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Исключение, полученный в результате ошибки во время обработки OLE. Этот класс используется, контейнеры и серверы.

## <a name="see-also"></a>См. также

[Общие сведения о классе](../mfc/class-library-overview.md)
