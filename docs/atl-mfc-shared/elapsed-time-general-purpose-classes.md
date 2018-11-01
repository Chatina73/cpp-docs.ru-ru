---
title: 'Затраченное время: Классы общего назначения'
ms.date: 11/04/2016
helpviewer_keywords:
- adding dates
- calculating dates and times
- dates, calculating intervals
- elapsed time, calculating
- elapsed time
- time, elapsed
- intervals, date and time
- calculations, date and time
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
ms.openlocfilehash: ebaf77b34411cd55cb3a028bcce9109613b63ed9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676756"
---
# <a name="elapsed-time-general-purpose-classes"></a>Затраченное время: Классы общего назначения

Ниже показано, как вычислить разницу между двумя `CTime` объектов и получите `CTimeSpan` результат. Используйте `CTime` и `CTimeSpan` объекты для вычисления истекшего времени, следующим образом:

   [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/cpp/elapsed-time-general-purpose-classes_1.cpp)]

После вычисления `elapsedTime`, можно использовать функции-члены `CTimeSpan` для извлечения компонентов значения затраченного времени.

