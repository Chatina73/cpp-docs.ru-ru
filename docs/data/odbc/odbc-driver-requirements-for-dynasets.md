---
description: 'Дополнительные сведения: требования к драйверам ODBC для динамических подмножеств данных'
title: Требования динамических подмножеств данных к драйверу ODBC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, dynasets
- drivers, for dynasets
- drivers, ODBC
- recordsets, dynasets
- dynasets
- ODBC drivers, dynasets
ms.assetid: 585cc67b-4d92-404b-9903-d769cd17badc
ms.openlocfilehash: 9e72499eb500ae79248673e73b666bf535fcdcc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161017"
---
# <a name="odbc-driver-requirements-for-dynasets"></a>Требования динамических подмножеств данных к драйверу ODBC

В классах базы данных MFC ODBC динамические наборы записей являются наборами с динамическими свойствами. они остаются синхронизированными с источником данных определенным образом. Для динамических подмножеств MFC (но не для наборов записей прямого доступа) требуется драйвер ODBC с соответствием API уровня 2. Если драйвер для [источника данных](../../data/odbc/data-source-odbc.md) соответствует набору API уровня 1, вы можете использовать как обновляемые, так и моментальные снимки только для чтения, а также наборы записей последовательного доступа, но не динамические подмножества. Однако драйвер уровня 1 может поддерживать динамические наборы данных, если он поддерживает расширенные выборки и курсоры, управляемые набором ключей.

В терминологии ODBC динамические подмножества и моментальные снимки называются курсорами. Курсор — это механизм, используемый для отслеживания его положения в наборе записей. Дополнительные сведения о требованиях к драйверам для динамических подмножеств данных см. в разделе [Динамическое подмножество](../../data/odbc/dynaset.md). Дополнительные сведения о курсорах см. в документации по [открытому подключению баз данных (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc) .

> [!NOTE]
> Для обновляемых наборов записей драйвер ODBC должен поддерживать либо позиционированные инструкции UPDATE, либо `::SQLSetPos` функцию ODBC API. Если обе поддерживаются, MFC использует `::SQLSetPos` для повышения эффективности. Кроме того, для моментальных снимков можно использовать библиотеку курсоров, которая обеспечивает необходимую поддержку обновляемых моментальных снимков (статические курсоры и инструкции позиционированного обновления).

## <a name="see-also"></a>См. также раздел

[Основы ODBC](../../data/odbc/odbc-basics.md)
