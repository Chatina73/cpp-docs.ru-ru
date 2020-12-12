---
description: 'Дополнительные сведения об обмене полями записей: использование функций RFX'
title: Обмен полями записей. Использование функций RFX
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: 8b597a6ca8ae43922b6bba57b63ea2fc93fb82d3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298764"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Обмен полями записей. Использование функций RFX

В этом разделе объясняется, как использовать вызовы функций RFX, составляющие текст `DoFieldExchange` переопределения.

> [!NOTE]
> Этот раздел относится к классам, производным от [CRecordset](../../mfc/reference/crecordset-class.md) , в котором не реализована многострочная выборка строк. Если вы используете пакетное получение строк, реализуется пакетный обмен полями записей (Bulk RFX). Bulk RFX аналогичен RFX. Сведения о различиях см. в разделе [набор записей: незначительная выборка записей (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Глобальные функции RFX обмениваются данными между столбцами в источнике данных и элементами данных поля в наборе записей. Вызовы функций RFX записываются в функцию члена функции [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) набора записей. В этом разделе кратко описаны функции и показаны типы данных, для которых доступны функции RFX. [Техническое примечание 43](../../mfc/tn043-rfx-routines.md) . Описание процесса написания собственных функций RFX для дополнительных типов данных.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a> Синтаксис функции RFX

Каждая функция RFX принимает три параметра (и некоторые принимают необязательный четвертый или Пятый параметр):

- Указатель на объект [кфиелдексчанже](../../mfc/reference/cfieldexchange-class.md) . Вы просто передаете `pFX` указатель, передаваемый в `DoFieldExchange` .

- Имя столбца, отображаемое в источнике данных.

- Имя соответствующего элемента данных поля или элемента данных параметра в классе набора записей.

- Используемых В некоторых функциях это максимальная длина передаваемой строки или массива. Значение по умолчанию — 255 байт, но может потребоваться изменить его. Максимальный размер зависит от максимального размера `CString` объекта ( **INT_MAX** (2 147 483 647) байт), но, скорее всего, будут возникать ограничения на драйверы до этого размера.

- Используемых В `RFX_Text` функции иногда используется Пятый параметр для указания типа данных столбца.

Дополнительные сведения см. в разделе функции RFX в [макросах и глобальных](../../mfc/reference/mfc-macros-and-globals.md) элементах в *справочнике по библиотеке классов*. Пример того, когда вы можете использовать параметры, см. в разделе [набор записей: получение сумм и другие статистические результаты (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a> Типы данных RFX

Библиотека классов предоставляет функции RFX для передачи множества различных типов данных между источником данных и наборами записей. В следующем списке перечислены функции RFX по типу данных. В случаях, когда необходимо написать собственные вызовы функций RFX, выберите эти функции по типу данных.

|Функция|Тип данных|
|--------------|---------------|
|`RFX_Bool`|**ЛОГИЧЕСКОМ**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**`double`**|
|`RFX_Single`|**`float`**|
|`RFX_Int`|**`int`**|
|`RFX_Long`|**`long`**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Дополнительные сведения см. в документации по функциям RFX в разделе [макросы и глобальные](../../mfc/reference/mfc-macros-and-globals.md) в *справочнике по библиотеке классов*. Сведения о том, как типы данных C++ сопоставляются с типами данных SQL, см. в таблице типы данных SQL ANSI, сопоставленные с типами данных C++ в [SQL: SQL и C++ Data Types (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>См. также раздел

[Обмен полями записей (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Обмен полями записей: принцип работы RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Набор записей. Параметризация набора записей (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Набор записей. динамическое связывание столбцов данных (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Класс CRecordset](../../mfc/reference/crecordset-class.md)<br/>
[Класс Кфиелдексчанже](../../mfc/reference/cfieldexchange-class.md)
