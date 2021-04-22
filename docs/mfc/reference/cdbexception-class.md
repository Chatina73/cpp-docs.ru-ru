---
description: 'Дополнительные сведения о: Кдбексцептион Class'
title: Класс Кдбексцептион
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: 437e59058226f274962dedcda52b973eee4ea1ba
ms.sourcegitcommit: 83a396e9491fd6bdecfb48ff225ef01c959829a6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107577278"
---
# <a name="cdbexception-class"></a>Класс Кдбексцептион

Представляет условие исключения, поступающее от классов базы данных.

## <a name="syntax"></a>Синтаксис

```
class CDBException : public CException
```

## <a name="members"></a>Члены

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Описание|
|----------|-----------------|
|[Кдбексцептион:: m_nRetCode](#m_nretcode)|Содержит код возврата ODBC, имеющий тип РЕТКОДЕ.|
|[Кдбексцептион:: m_strError](#m_strerror)|Содержит строку, описывающую ошибку в буквенно-цифровых терминах.|
|[Кдбексцептион:: m_strStateNativeOrigin](#m_strstatenativeorigin)|Содержит строку, описывающую ошибку в терминах кодов ошибок, возвращаемых ODBC.|

## <a name="remarks"></a>Замечания

Класс включает два общедоступных члена данных, которые можно использовать для определения причины исключения или для вывода текстового сообщения с описанием исключения. `CDBException` объекты создаются и создаются функциями членов классов базы данных.

> [!NOTE]
> Этот класс является одним из классов ODBC. Если вместо этого используются более новые классы объектов доступа к данным (DAO), используйте вместо него [кдаоексцептион](../../mfc/reference/cdaoexception-class.md) . Все имена классов DAO имеют "Кдао" в качестве префикса. Дополнительные сведения см. в статье [Общие сведения о программировании баз данных](../../data/data-access-programming-mfc-atl.md).

Исключения — это случаи аномального выполнения, включающие условия, которые выходят за пределы контроля программы, например источник данных или ошибки ввода-вывода в сети. Ошибки, которые могут ожидаться в обычном процессе выполнения программы, обычно не считаются исключениями.

Доступ к этим объектам можно получить в области выражения **catch** . Кроме того, можно создавать `CDBException` объекты из собственного кода с помощью `AfxThrowDBException` глобальной функции.

Дополнительные сведения об обработке исключений в целом и об `CDBException` объектах см. в статьях [обработка исключений (MFC)](../../mfc/exception-handling-in-mfc.md) и [исключения: исключения базы данных](../../mfc/exceptions-database-exceptions.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>Требования

**Заголовок:** афксдб. h

## <a name="cdbexceptionm_nretcode"></a><a name="m_nretcode"></a> Кдбексцептион:: m_nRetCode

Содержит код ошибки ODBC типа РЕТКОДЕ, возвращаемый функцией интерфейса прикладного программирования (API) ODBC.

### <a name="remarks"></a>Замечания

Этот тип включает в себя коды с префиксами SQL, определенные в ODBC и AFX_SQL с префиксами, определенными классами базы данных. Для `CDBException` этот элемент будет содержать одно из следующих значений:

- AFX_SQL_ERROR_API_CONFORMANCE драйвер для `CDatabase::OpenEx` вызова или не `CDatabase::Open` соответствует требуемому уровню соответствия API ODBC 1 (SQL_OAC_LEVEL1).

- Не удалось подключиться к источнику данных AFX_SQL_ERROR_CONNECT_FAIL. Вы передали `CDatabase` указатель null конструктору набора записей и последующая попытка создать соединение на основе `GetDefaultConnect` сбоя.

- AFX_SQL_ERROR_DATA_TRUNCATED вы запросили больше данных, чем вы указали в хранилище. Дополнительные сведения о увеличении указанного хранилища данных для `CString` `CByteArray` типов данных или см. в описании `nMaxLength` аргумента для [RFX_Text](record-field-exchange-functions.md#rfx_text) и [RFX_Binary](record-field-exchange-functions.md#rfx_binary) в разделе "макросы и глобальные параметры".

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED вызов `CRecordset::Open` запроса динамического подмножества окончился неудачей. Драйвер не поддерживает динамические подмножества данных.

- AFX_SQL_ERROR_EMPTY_COLUMN_LIST попытке открыть таблицу (или то, что вы указали в качестве вызова процедуры или инструкции **SELECT** ), но в переопределении не указаны столбцы, указанные в вызовах функций обмена полями записи (RFX) `DoFieldExchange` .

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH тип функции RFX в `DoFieldExchange` переопределении несовместим с типом данных столбца в наборе записей.

- AFX_SQL_ERROR_ILLEGAL_MODE вызывается `CRecordset::Update` без ранее вызова метода `CRecordset::AddNew` или `CRecordset::Edit` .

- AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED запрос на блокировку записей для обновления не может быть выполнен, так как драйвер ODBC не поддерживает блокировку.

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED вызывается `CRecordset::Update` или `Delete` для таблицы без уникального ключа и изменения нескольких записей.

- AFX_SQL_ERROR_NO_CURRENT_RECORD попытке изменить или удалить ранее удаленную запись. После удаления необходимо перейти к новой текущей записи.

- AFX_SQL_ERROR_NO_POSITIONED_UPDATES не удалось выполнить запрос динамического подмножества, так как драйвер ODBC не поддерживает позиционированные обновления.

- AFX_SQL_ERROR_NO_ROWS_AFFECTED вы вызвали `CRecordset::Update` или `Delete` , но при начале операции не удается найти запись.

- AFX_SQL_ERROR_ODBC_LOAD_FAILED попытке загрузить ODBC.DLL не удалось; Windows не удалось найти или загрузить эту библиотеку DLL. Эта ошибка является неустранимой.

- AFX_SQL_ERROR_ODBC_V2_REQUIRED не удалось выполнить запрос динамического подмножества, так как требуется драйвер ODBC, соответствующий уровню 2.

- AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY попытке прокрутки не удалась, так как источник данных не поддерживает обратную прокрутку.

- Не удалось AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED вызов `CRecordset::Open` запроса на создание моментального снимка. Этот драйвер не поддерживает моментальные снимки. (Это происходит только в том случае, если отсутствует библиотека курсоров ODBC ODBCCURS.DLL.)

- AFX_SQL_ERROR_SQL_CONFORMANCE драйвер для `CDatabase::OpenEx` вызова или не `CDatabase::Open` соответствует требуемому уровню соответствия ODBC SQL "Minimum" (SQL_OSC_MINIMUM).

- AFX_SQL_ERROR_SQL_NO_TOTAL драйверу ODBC не удалось указать общий размер `CLongBinary` значения данных. Возможно, произошел сбой операции, так как не удалось предварительно выделить глобальный блок памяти.

- AFX_SQL_ERROR_RECORDSET_READONLY попытке обновить набор записей, предназначенный только для чтения, или источник данных доступен только для чтения. Операции обновления не могут быть выполнены с набором записей или `CDatabase` объектом, с которым он связан.

- Сбой функции SQL_ERROR. Сообщение об ошибке, возвращаемое функцией ODBC, `SQLError` сохраняется в элементе `m_strError` данных.

- Сбой функции SQL_INVALID_HANDLE из-за недопустимого обработчика среды, маркера соединения или маркера оператора. Это указывает на ошибку программирования. Дополнительные сведения из функции ODBC недоступны `SQLError` .

Коды с префиксом SQL определяются ODBC. Коды с префиксом AFX определены в АФКСДБ. H, найдено в МФК\ИНКЛУДЕ.

## <a name="cdbexceptionm_strerror"></a><a name="m_strerror"></a> Кдбексцептион:: m_strError

Содержит строку, описывающую ошибку, вызвавшую исключение.

### <a name="remarks"></a>Замечания

Строка описывает ошибку в буквенно-цифровых терминах. Более подробные сведения и пример см. в разделе `m_strStateNativeOrigin` .

## <a name="cdbexceptionm_strstatenativeorigin"></a><a name="m_strstatenativeorigin"></a> Кдбексцептион:: m_strStateNativeOrigin

Содержит строку, описывающую ошибку, вызвавшую исключение.

### <a name="remarks"></a>Замечания

Строка имеет вид "состояние:% s, native:% LD, источник:% s", где коды формата заменяются значениями, описывающими:

- SQLSTATE — строка, завершающаяся нулем, содержащая код ошибки из пяти символов, возвращенный в параметре *сзсклстате* функции ODBC `SQLError` . Значения SQLSTATE перечислены в разделе приложение а, [коды ошибок ODBC](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)в *справочнике программиста по ODBC*. Пример: "S0022".

- Собственный код ошибки, относящийся к источнику данных, возвращаемый в параметре *пфнативиррор* `SQLError` функции. Пример: 207.

- Текст сообщения об ошибке, возвращаемый в параметре *сзеррормсг* `SQLError` функции. Это сообщение состоит из нескольких имен в квадратных скобках. Так как ошибка передается из источника пользователю, каждый компонент ODBC (источник данных, драйвер, диспетчер драйверов) добавляет свое собственное имя. Эти сведения помогают определить происхождение ошибки. Пример: [Microsoft] [драйвер ODBC SQL Server] [SQL Server]

Платформа интерпретирует строку ошибки и помещает ее компоненты в `m_strStateNativeOrigin` ; Если `m_strStateNativeOrigin` содержит сведения о более чем одной ошибке, ошибки разделяются символами новой строки. Платформа помещает буквенно-цифровой текст ошибки в `m_strError` .

Дополнительные сведения о кодах, используемых для создания этой строки, см. в описании функции [SqlError](/sql/odbc/reference/syntax/sqlerror-function) в *справочнике программиста по ODBC*.

### <a name="example"></a>Пример

Из ODBC: "состояние: S0022, native: 207, источник: \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server] недопустимое имя столбца" colname ""

В `m_strStateNativeOrigin` : "состояние: S0022, native: 207, источник: \[ Microsoft] \[ ODBC SQL Server Driver] \[ SQL Server]"

В `m_strError` : "Недопустимое имя столбца" colname ""

## <a name="see-also"></a>См. также раздел

[Класс CException](../../mfc/reference/cexception-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Класс CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Класс CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Класс Кфиелдексчанже](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset:: Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::D удалить](../../mfc/reference/crecordset-class.md#delete)<br/>
[Класс CException](../../mfc/reference/cexception-class.md)
