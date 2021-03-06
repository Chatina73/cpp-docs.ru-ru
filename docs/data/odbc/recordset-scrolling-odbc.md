---
description: 'Дополнительные сведения: набор записей: прокрутка (ODBC)'
title: Набор записей. Прокрутка (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets [C++], end of
- recordsets [C++], beginning of
- navigation [C++], recordsets
- recordsets [C++], moving to records
- ODBC recordsets, scrolling
- recordsets [C++], navigating
- scrolling [C++], recordsets
- Move method (recordsets)
ms.assetid: f38d2dcb-1e88-4e41-af25-98b00c276be4
ms.openlocfilehash: 82a4326f2e0a7546d956181e7660ea0f1a437dc6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97204463"
---
# <a name="recordset-scrolling-odbc"></a>Набор записей. Прокрутка (ODBC)

Этот раздел относится к классам ODBC библиотеки MFC.

После открытия набора записей необходимо получить доступ к записям, чтобы отобразить значения, выполнять вычисления, формировать отчеты и т. д. Прокрутка позволяет переходить от записи к записи в наборе записей.

В этом разделе рассматриваются следующие вопросы.

- [Переход от одной записи к другой в наборе записей](#_core_scrolling_from_one_record_to_another).

- [При прокрутке условий и не поддерживается](#_core_when_scrolling_is_supported).

## <a name="scrolling-from-one-record-to-another"></a><a name="_core_scrolling_from_one_record_to_another"></a> Прокрутка от одной записи к другой

Класс `CRecordset` предоставляет `Move` функции-члены для прокрутки в наборе записей. Эти функции перемещают текущую запись по наборам строк. При реализации групповой выборки строк `Move` операция изменяет расположение набора записей по размеру набора строк. Если не реализована многострочная выборка строк, вызов `Move` функции перемещает набор записей по одной записи каждый раз. Дополнительные сведения о групповой выборке строк см. [в разделе набор записей. сбор записей (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

> [!NOTE]
> При перемещении по набору записей удаленные записи могут не пропускаться. Дополнительные сведения см. в описании функции [удаления](../../mfc/reference/crecordset-class.md#isdeleted) элемента.

В дополнение к `Move` функциям `CRecordset` предоставляет функции членов для проверки, прокручена ли прокрутка до начала набора записей.

Чтобы определить, возможна ли прокрутка в наборе записей, вызовите `CanScroll` функцию-член.

#### <a name="to-scroll"></a>Для прокрутки

1. Пересылка одной записи или одного набора строк: вызовите функцию члена [MoveNext](../../mfc/reference/crecordset-class.md#movenext) .

1. Назад на одну запись или один набор строк: вызовите функцию члена [мовепрев](../../mfc/reference/crecordset-class.md#moveprev) .

1. К первой записи в наборе записей: вызовите функцию члена [MoveFirst](../../mfc/reference/crecordset-class.md#movefirst) .

1. К последней записи в наборе записей или к последнему набору строк: вызовите функцию члена [MoveLast](../../mfc/reference/crecordset-class.md#movelast) .

1. *N* записей относительно текущей должности: вызовите функцию элемента [Move](../../mfc/reference/crecordset-class.md#move) .

#### <a name="to-test-for-the-end-or-the-beginning-of-the-recordset"></a>Проверка на окончание или начало набора записей

1. Прокручесь за последнюю запись? Вызовите функцию члена [исеоф](../../mfc/reference/crecordset-class.md#iseof) .

1. Прокручивает первую запись вперед (перемещение назад)? Вызовите функцию члена [исбоф](../../mfc/reference/crecordset-class.md#isbof) .

В следующем примере кода метод `IsBOF` и используется `IsEOF` для определения ограничений набора записей при прокрутке в любом направлении.

```
// Open a recordset; first record is current
CCustSet rsCustSet( NULL );
rsCustSet.Open( );

if( rsCustSet.IsBOF( ) )
    return;
    // The recordset is empty

// Scroll to the end of the recordset, past
// the last record, so no record is current
while ( !rsCustSet.IsEOF( ) )
    rsCustSet.MoveNext( );

// Move to the last record
rsCustSet.MoveLast( );

// Scroll to beginning of the recordset, before
// the first record, so no record is current
while( !rsCustSet.IsBOF( ) )
    rsCustSet.MovePrev( );

// First record is current again
rsCustSet.MoveFirst( );
```

`IsEOF` Возвращает ненулевое значение, если набор записей располагается за последней записью. `IsBOF` Возвращает ненулевое значение, если набор записей располагается впереди первой записи (перед всеми записями). В любом случае нет текущей записи для обработки. Если вызывается, когда уже имеет `MovePrev` `IsBOF` значение true или вызывается `MoveNext` `IsEOF` , если уже имеет значение true, платформа создает исключение `CDBException` . `IsBOF` `IsEOF` Для проверки пустого набора записей также можно использовать и.

Дополнительные сведения о переходе по набору записей см. в разделе [набор записей: закладки и абсолютные позиции (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md).

## <a name="when-scrolling-is-supported"></a><a name="_core_when_scrolling_is_supported"></a> Если прокрутка поддерживается

Изначально сервер SQL предоставил только прямую прокрутку, но ODBC расширяет возможности прокрутки. Доступный уровень поддержки прокрутки зависит от драйверов ODBC, с которыми работает ваше приложение, от драйвера соответствия API ODBC, а также от того, загружена ли библиотека курсоров ODBC в память. Дополнительные сведения см. в разделе [ODBC](../../data/odbc/odbc-basics.md) and [ODBC: Библиотека курсоров ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).

> [!TIP]
> Можно указать, используется ли библиотека курсоров. См. параметры *бусекурсорлиб* и *двоптионс* для [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open).

> [!NOTE]
> В отличие от классов MFC DAO, классы ODBC MFC не предоставляют набор `Find` функций для поиска следующей (или предыдущей) записи, соответствующей указанным критериям.

## <a name="see-also"></a>См. также раздел

[Набор записей (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: Канскролл](../../mfc/reference/crecordset-class.md#canscroll)<br/>
[CRecordset:: Чеккровсетеррор](../../mfc/reference/crecordset-class.md#checkrowseterror)<br/>
[Набор записей. Фильтрация записей (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
