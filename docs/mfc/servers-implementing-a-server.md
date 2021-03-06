---
description: 'Дополнительные сведения о: серверы: реализация сервера'
title: Серверы. Реализация сервера
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 3ced10f88ce062ab571841610ba4b000571835b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217384"
---
# <a name="servers-implementing-a-server"></a>Серверы. Реализация сервера

В этой статье описывается код, создаваемый мастером приложений MFC для серверного приложения визуального редактирования. Если мастер приложений не используется, в этой статье перечислены области, в которых необходимо написать код для реализации серверного приложения.

Если вы используете мастер приложений для создания нового серверного приложения, он предоставляет значительный объем серверного кода. При добавлении функциональных возможностей сервера визуального редактирования в существующее приложение необходимо дублировать код, предоставленный мастером приложений, прежде чем добавлять остальную часть необходимого серверного кода.

Серверный код, предоставляемый мастером приложений, попадает в несколько категорий:

- Определение ресурсов сервера:

  - Ресурс меню, используемый, когда сервер редактирует внедренный элемент в отдельном окне.

  - Ресурсы меню и панели инструментов, используемые при наличии активного сервера.

  Дополнительные сведения об этих ресурсах см. в разделе [меню и ресурсы: дополнения сервера](../mfc/menus-and-resources-server-additions.md).

- Определение класса элемента, производного от `COleServerItem` . Дополнительные сведения об элементах сервера см. в разделе [серверы: серверные элементы](../mfc/servers-server-items.md).

- Изменение базового класса класса Document на `COleServerDoc` . Дополнительные сведения см. в разделе [серверы: реализация серверных документов](../mfc/servers-implementing-server-documents.md).

- Определение класса фреймового окна, производного от `COleIPFrameWnd` . Дополнительные сведения см. в разделе [Servers: реализация In-Place фреймовых окон](../mfc/servers-implementing-in-place-frame-windows.md).

- Создание записи для серверного приложения в базе данных регистрации Windows и регистрация нового экземпляра сервера в системе OLE. Сведения об этом разделе см. в разделе [Регистрация](../mfc/registration.md).

- Инициализация и запуск серверного приложения. Сведения об этом разделе см. в разделе [Регистрация](../mfc/registration.md).

Дополнительные сведения см. в разделе [COleServerItem](../mfc/reference/coleserveritem-class.md), [колесервердок](../mfc/reference/coleserverdoc-class.md)и [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) в *справочнике по библиотеке классов*.

## <a name="see-also"></a>См. также раздел

[Серверы](../mfc/servers.md)<br/>
[Контейнеры](../mfc/containers.md)<br/>
[Меню и ресурсы (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Регистрация](../mfc/registration.md)
