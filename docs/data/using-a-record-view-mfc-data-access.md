---
title: Использование представления записей (доступ к данным MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- record views, customizing default code
ms.assetid: 91f2828f-0666-4273-ae28-e4703fd98521
ms.openlocfilehash: 9d64fc26e1c78bad0431bc9b10dd5117c4866159
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152921"
---
# <a name="using-a-record-view--mfc-data-access"></a>Использование представления записей (доступ к данным MFC)

В этом разделе объясняется, как настроить код по умолчанию для представлений записей, создаваемых мастером для вас. Как правило, требуется ограничить выбор записей с помощью [фильтра](../data/odbc/recordset-filtering-records-odbc.md) или [параметры](../data/odbc/recordset-parameterizing-a-recordset-odbc.md), возможно [сортировки](../data/odbc/recordset-sorting-records-odbc.md) записи, настроить инструкцию SQL.

С помощью `CRecordView` — это во многом так же, как [CFormView](../mfc/reference/cformview-class.md). Основной подход заключается в использовании представления записей для отображения и возможно, обновления записей одного определенного набора записей. Кроме этого, может возникнуть необходимость использования других наборов записей, как описано в [представления записей: Заполнение списка из второго набора записей](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

## <a name="see-also"></a>См. также

[Представления записей (доступ к данным MFC)](../data/record-views-mfc-data-access.md)<br/>
[Список драйверов ODBC](../data/odbc/odbc-driver-list.md)