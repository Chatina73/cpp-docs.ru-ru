---
title: db_accessor (C++ атрибут COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_accessor
helpviewer_keywords:
- db_accessor attribute
ms.assetid: ec407a9f-24d7-4822-96d4-7cc6a0301815
ms.openlocfilehash: bfb287261fce4ebf189801c308f57513f2c9f113
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038308"
---
# <a name="dbaccessor"></a>db_accessor

Группы `db_column` атрибуты, которые участвуют в `IAccessor`-привязку на основе.

## <a name="syntax"></a>Синтаксис

```cpp
[ db_accessor(num, auto) ]
```

#### <a name="parameters"></a>Параметры

*num*<br/>
Указывает номер доступа (с индексом отсчитываемый от нуля целое число). Необходимо указать номера доступа в повышении заказ, используя указанное целое число или определенные значения.

*auto*<br/>
Логическое значение, указывающее, является ли метод доступа автоматически извлекается (TRUE) или не получить (FALSE).

## <a name="remarks"></a>Примечания

**db_accessor** определяет базовый метод доступа OLE DB для последующих `db_column` и `db_param` атрибутов в том же классе или функции. **db_accessor** можно использовать на уровне элемента и используется в группу `db_column` атрибуты, которые участвуют в OLE DB `IAccessor`-привязку на основе. Он используется в сочетании со `db_table` или `db_command` атрибуты. Вызвав этот атрибут аналогично вызову [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) и [END_ACCESSOR](../../data/oledb/end-accessor.md) макросы.

**db_accessor** создает набор строк и привязывает его к соответствующей карты метода доступа. Если вы не вызываете **db_accessor**, автоматически создается метод доступа 0 и всех привязок к столбцу будет сопоставлен этот блок метода доступа.

**db_accessor** группы базы данных привязок к столбцам в один или несколько методов доступа. Описание сценариев, в которых необходимо использовать несколько методов доступа, см. в разделе [с помощью нескольких методов доступа в наборе строк](../../data/oledb/using-multiple-accessors-on-a-rowset.md). См. также «Пользователя запись поддержки для нескольких методов доступа» в [записи пользователей](../../data/oledb/user-records.md).

Если поставщик атрибутов потребителя применяет этот атрибут к классу, компилятор переименует класс в \_*YourClassName*Accessor, где *YourClassName* — это имя, которое вы присвоили классу. Также компилятор создаст класс с именем *YourClassName*, производный от \_*YourClassName*Accessor.  В представлении классов отображаются оба класса.

## <a name="example"></a>Пример

В следующем примере используется **db_accessor** для группы столбцов в таблице Orders в базе данных "Борей" в двух методов доступа. Метод доступа 0 является автоматическим, а метод доступа 1 не является.

```cpp
// cpp_attr_ref_db_accessor.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include <atlbase.h>
#include <atldbcli.h>

[ db_command(L"SELECT LastName, FirstName FROM Orders") ]
class CEmployees {
public:
   [ db_accessor(0, TRUE) ];
   [ db_column("1") ] LONG m_OrderID;
   [ db_column("2") ] TCHAR m_CustomerID[6];
   [ db_column("4") ] DBTIMESTAMP m_OrderDate;

   [ db_accessor(1, FALSE) ];
   [ db_column("8") ] CURRENCY m_Freight;
};
```

## <a name="requirements"></a>Требования

### <a name="attribute-context"></a>Контекст атрибута

|||
|-|-|
|**Применение**|Блоки атрибутов|
|**Повторяемый**|Нет|
|**Обязательные атрибуты**|Нет|
|**Недопустимые атрибуты**|Нет|

Дополнительные сведения о контекстах атрибутов см. в разделе [Контексты атрибутов](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>См. также

[Атрибуты объекта-получателя OLE DB](ole-db-consumer-attributes.md)