---
description: 'Дополнительные сведения: серверы'
title: Серверы
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: 5e9a9dd7cbb1ab237712b5ad0c84e3114a119ee3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217306"
---
# <a name="servers"></a>Серверы

Серверное приложение (или компонентное приложение) создает элементы OLE (или компоненты) для использования в приложениях-контейнерах. Серверное приложение визуального редактирования также поддерживает визуальное редактирование или активацию на месте. Другой формой OLE-сервера является [сервер автоматизации](../mfc/automation-servers.md). Некоторые серверные приложения поддерживают только создание внедренных элементов. другие поддерживают создание внедренных и связанных элементов. Некоторые поддерживают компоновку, хотя это случается редко. Все серверные приложения должны поддерживать активацию в приложениях контейнеров, когда пользователь хочет изменить элемент. Приложение может быть как контейнером, так и сервером. Иными словами, он может включать данные в свои документы и создавать данные, которые могут быть включены как элементы в документы других приложений.

Минисервер — это серверное приложение специального типа, которое может запускаться только контейнером. Примерами минисерверс являются Microsoft Draw и Microsoft Graph. Минисервер не сохраняет документы в виде файлов на диске. Вместо этого он считывает документы из и записывает их в элементы в документах, принадлежащих контейнерам. В результате минисервер поддерживает только внедрение, а не компоновку.

Полный сервер можно запустить либо как автономное приложение, либо запустить с помощью приложения-контейнера. Полный сервер может хранить документы в виде файлов на диске. Он может поддерживать только внедрение, внедрение и компоновку или только компоновку. Пользователь приложения-контейнера может создать внедренный элемент, выбрав команду Вырезать или копировать на сервере и команду вставить в контейнере. Связанный элемент создается путем выбора команды Копировать на сервере и команды вставить ссылку в контейнере. Кроме того, пользователь может создать внедренный или связанный элемент с помощью диалогового окна «Вставка объекта».

В следующей таблице перечислены характеристики различных типов серверов.

### <a name="server-characteristics"></a>Характеристики сервера

|Тип сервера|Поддерживает несколько экземпляров|Элементов на документ|Документов на экземпляр|
|--------------------|---------------------------------|------------------------|----------------------------|
|минисервер|Да|1|1|
|Полный сервер SDI|Да|1 (Если компоновка поддерживается, 1 или более)|1|
|Полный MDI-сервер|Нет (не требуется)|1 (Если компоновка поддерживается, 1 или более)|0 или больше|

Серверное приложение должно поддерживать несколько контейнеров одновременно, в случае, если для изменения внедренного или связанного элемента будет использоваться несколько контейнеров. Если сервер является приложением SDI (или минисервер с интерфейсом диалогового окна), несколько экземпляров сервера должны иметь возможность одновременного выполнения. Это позволяет отдельному экземпляру приложения работать с каждым запросом контейнера.

Если сервер является приложением MDI, он может создать новое дочернее окно MDI каждый раз, когда контейнеру потребуется изменить элемент. Таким образом, один экземпляр приложения может поддерживать несколько контейнеров.

Серверное приложение должно сообщить системным библиотекам OLE, что делать, если один экземпляр сервера уже запущен, когда другой контейнер запрашивает свои службы: следует ли запускать новый экземпляр сервера или направлять все запросы контейнеров на один экземпляр сервера.

Дополнительные сведения о серверах см. в следующих статьях:

- [Серверы: реализация сервера](../mfc/servers-implementing-a-server.md)

- [Серверы: реализация серверных документов](../mfc/servers-implementing-server-documents.md)

- [Серверы: реализация окон кадров In-Place](../mfc/servers-implementing-in-place-frame-windows.md)

- [Серверы: элементы сервера](../mfc/servers-server-items.md)

- [Серверы: User-Interface проблемы](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>См. также раздел

[OLE](../mfc/ole-in-mfc.md)<br/>
[Контейнеры](../mfc/containers.md)<br/>
[Контейнеры: дополнительные функции](../mfc/containers-advanced-features.md)<br/>
[Меню и ресурсы (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Регистрация](../mfc/registration.md)<br/>
[Серверы автоматизации](../mfc/automation-servers.md)
