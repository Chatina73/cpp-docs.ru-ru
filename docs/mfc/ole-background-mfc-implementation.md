---
description: 'Дополнительные сведения о: OLE Background: реализация MFC'
title: Поддержка OLE. Реализация MFC
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: 81b62fc1ff704a8a0f34bfd1ac864142720b3864
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343546"
---
# <a name="ole-background-mfc-implementation"></a>Поддержка OLE. Реализация MFC

Из-за размера и сложности необработанного API OLE, обращение непосредственно к написанию приложений OLE может занять много времени. Целью реализации библиотека Microsoft Foundation Class OLE является сокращение объема работы, которую необходимо выполнить для написания полнофункциональных приложений, поддерживающих технологию OLE.

В этой статье объясняются части интерфейса API OLE, которые не были реализованы в MFC. В обсуждении также объясняется, как реализовано сопоставление с разделом OLE Windows SDK.

## <a name="portions-of-ole-not-implemented-by-the-class-library"></a><a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> Части OLE, не реализованные библиотекой классов

Некоторые интерфейсы и функции OLE не предоставляются напрямую библиотекой MFC. Если вы хотите использовать эти функции, можно напрямую вызвать OLE API.

Интерфейс IMoniker `IMoniker` . интерфейс реализуется библиотекой классов (например, `COleServerItem` классом), но ранее не был предоставлен программисту. Дополнительные сведения об этом интерфейсе см. в статье реализация моникера OLE в разделе OLE Windows SDK. Однако см. также Class [кмоникерфиле](reference/cmonikerfile-class.md) и [касинкмоникерфиле](reference/casyncmonikerfile-class.md).

Интерфейсы IUnknown и IMarshal `IUnknown` интерфейс реализуется библиотекой классов, но не предоставляется программисту. `IMarshal`Интерфейс не реализуется библиотекой классов, но используется внутренним образом. Серверы автоматизации, созданные с помощью библиотеки классов, уже имеют встроенные возможности упаковки.

Составные файлы докфилес (составные файлы) частично поддерживаются библиотекой классов. Не поддерживается ни одна из функций, которые напрямую управляют составными файлами после создания. MFC использует класс `COleFileStream` для поддержки управления потоками с помощью стандартных файловых функций. Дополнительные сведения см. в разделе [контейнеры статей: составные файлы](containers-compound-files.md).

In-Process серверы и обработчики объектов внутрипроцессный сервер и обработчики объектов позволяют реализовать визуальное редактирование данных или объекты модели COM в библиотеке динамической компоновки (DLL). Для этого можно реализовать библиотеку DLL, напрямую вызвав API OLE. Однако при создании сервера автоматизации и отсутствии пользовательского интерфейса на сервере можно использовать помощью мастера, чтобы сделать сервер сервером в процессе и полностью разместить его в библиотеке DLL. Дополнительные сведения об этих разделах см. в разделе [серверы автоматизации](automation-servers.md).

> [!TIP]
> Самый простой способ реализовать сервер автоматизации — поместить его в библиотеку DLL. MFC поддерживает этот подход.

Дополнительные сведения о том, как классы OLE Microsoft Foundation реализуют интерфейсы OLE, см. в статье Технические примечания MFC [38](tn038-mfc-ole-iunknown-implementation.md), [39](tn039-mfc-ole-automation-implementation.md)и [40](tn040-mfc-ole-in-place-resizing-and-zooming.md).

## <a name="see-also"></a>См. также раздел

[Фон OLE](ole-background.md)<br/>
[Фон OLE: стратегии реализации](ole-background-implementation-strategies.md)
