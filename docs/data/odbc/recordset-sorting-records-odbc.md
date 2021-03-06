---
description: 'Дополнительные сведения: набор записей: Сортировка записей (ODBC)'
title: Набор записей. Сортировка записей (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: fbf2ef3c42061bac9b41550a0c44a20f68c099b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204424"
---
# <a name="recordset-sorting-records-odbc"></a>Набор записей. Сортировка записей (ODBC)

Этот раздел относится к классам ODBC библиотеки MFC.

В этом разделе объясняется, как сортировать набор записей. Можно указать один или несколько столбцов, на которых должна основываться сортировка, а также указать порядок по возрастанию или убыванию (**ASC** или **DESC**). **ASC** — значение по умолчанию) для каждого заданного столбца. Например, если указать два столбца, записи сортируются сначала по первому столбцу с именем, а затем во втором столбце с именем. Оператор SQL **ORDER BY** определяет сортировку. Когда платформа добавляет в запрос SQL набора записей предложение **ORDER BY** , предложение управляет порядком выбора.

Необходимо установить порядок сортировки набора записей после создания объекта, но перед вызовом его `Open` функции-члена (или перед вызовом `Requery` функции члена для существующего объекта Recordset, функция-член которой была `Open` вызвана ранее).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Задание порядка сортировки для объекта набора записей

1. Создайте новый объект набора записей (или подготовьте его к вызову `Requery` для существующего объекта).

1. Задайте значение элемента данных [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) объекта.

   Сортировка является строкой, завершающейся нулем. Он содержит содержимое предложения **ORDER BY** , но не ключевое слово **ORDER BY**. Например, вы можете использовать следующие службы.

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Задайте любые другие необходимые параметры, например фильтр, режим блокировки или параметры.

1. Вызовите `Open` новый объект (или `Requery` для существующего объекта).

Выбранные записи упорядочиваются указанным образом. Например, чтобы отсортировать набор записей учащихся в порядке убывания по фамилии, сначала выполните следующие действия.

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

Набор записей содержит все записи учащихся, отсортированные в убывающем порядке (от Z до A) по фамилии, а затем по имени.

> [!NOTE]
> Если вы решили переопределить строку SQL набора записей по умолчанию, передав собственную строку SQL в `Open` , не устанавливайте сортировку, если ваша пользовательская строка содержит предложение **ORDER BY** .

## <a name="see-also"></a>См. также раздел

[Набор записей (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Набор записей. Параметризация набора записей (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Набор записей. Фильтрация записей (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
