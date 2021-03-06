---
description: Дополнительные сведения о ATL и свободном потоке маршалером
title: ATL и упаковщик в режиме свободного потока
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: 01fb54386b5f48c8e49cc805e047c0faf8b0c39b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166074"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL и упаковщик в режиме свободного потока

Страница атрибутов мастера простых объектов ATL предоставляет параметр, позволяющий классу объединять бесплатный потоковый маршалеру (FTM).

Мастер создает код для создания экземпляра свободного потокового маршалером в `FinalConstruct` и выпуска этого экземпляра в `FinalRelease` . COM_INTERFACE_ENTRY_AGGREGATEный макрос автоматически добавляется в карту COM, чтобы обеспечить `QueryInterface` обработку запросов для [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal) с помощью свободного потокового модуля.

Свободный потоковый маршалинг обеспечивает прямой доступ к интерфейсам объекта из любого потока в том же процессе, ускоряя вызовы между апартаментами. Этот параметр предназначен для классов, использующих модель потоков.

При использовании этого параметра классы должны принимать ответственность за потокобезопасность данных. Кроме того, объекты, которые выполняют статистическую обработку свободного потокового маршалером и должны использовать указатели интерфейса, полученные из других объектов, должны предпринимать дополнительные действия, чтобы обеспечить правильную упаковку интерфейсов. Обычно это подразумевает хранение указателей интерфейса в глобальной таблице интерфейса (GIT) и получение указателя из GIT при каждом использовании. ATL предоставляет класс [ккомгитптр](../atl/reference/ccomgitptr-class.md) , помогающий использовать указатели интерфейса, хранящиеся в Git.

## <a name="see-also"></a>См. также раздел

[Основные понятия](../atl/active-template-library-atl-concepts.md)<br/>
[кокреатефрисреадедмаршалер](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[Когда следует использовать глобальную таблицу интерфейса](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Проблемы потоковой обработки в процессе сервера](/windows/win32/com/in-process-server-threading-issues)
