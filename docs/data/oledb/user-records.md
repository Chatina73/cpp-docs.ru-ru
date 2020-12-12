---
description: 'Дополнительные сведения: записи пользователей'
title: Записи пользователя
ms.date: 05/09/2019
f1_keywords:
- COLUMN_ENTRY_MAP
helpviewer_keywords:
- rowsets [C++], accessors
- COLUMN_ENTRY macro
- COLUMN_ENTRY_MAP macro
- user records, OLE DB consumer templates
- OLE DB consumer templates, user records
- CAccessor class, example
- BEGIN_ACCESSOR_MAP macro
- accessors [C++], rowsets
- accessors [C++], static
- BEGIN_ACCESSOR macro, example
ms.assetid: 2de9e5eb-53ce-42b1-80fa-57d46600a80c
ms.openlocfilehash: 1d31ef93bb1b06925306c84d436d7a7837a08431
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322329"
---
# <a name="user-records"></a>Записи пользователя

> [!NOTE]
> Мастер объекта-получателя ATL OLE DB недоступен в Visual Studio 2019 и более поздних версиях. Эту функцию все еще можно добавить вручную. Дополнительные сведения см. в статье [Создание объекта-получателя без помощи мастера](creating-a-consumer-without-using-a-wizard.md).

Чтобы использовать статический метод доступа (т. е. метод доступа, полученный из `CAccessor`), потребитель должен иметь запись пользователя. Запись пользователя — это класс C ++, который содержит элементы данных для обработки ввода или вывода. **Мастер потребителя ATL OLE DB** создает запись пользователя для вашего потребителя. Вы можете добавить методы в пользовательскую запись для дополнительных задач, таких как обработка команд.

Следующий код показывает пример записи, которая обрабатывает команды. В пользовательской записи BEGIN_COLUMN_MAP представляет набор строк данных, переданный потребителю от поставщика. BEGIN_PARAM_MAP представляет набор параметров команды. В этом примере для обработки параметров команды используется класс [CCommand](../../data/oledb/ccommand-class.md). Члены данных в записях карты представляют собой смещения в один непрерывный блок памяти для каждого экземпляра класса. Макросы COLUMN_ENTRY соответствуют макросам PROVIDER_COLUMN_ENTRY на стороне поставщика.

Дополнительные сведения о макросах COLUMN_MAP и PARAM_MAP см. в статье [Macros for OLE DB Consumer Templates](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md) (Макросы и глобальные функции для шаблонов потребителей OLE DB).

```cpp
class CArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_COLUMN_MAP(CArtists)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
   COLUMN_ENTRY(3, m_nAge)
END_COLUMN_MAP()

// Parameter binding map
BEGIN_PARAM_MAP(CArtists)
   COLUMN_ENTRY(1, m_nAge)
END_PARAM_MAP()
};
```

## <a name="wizard-generated-user-records"></a>Записи пользователя, созданные мастером

При создании потребителя с помощью **мастера потребителя ATL OLE DB** вы можете выбрать использование шаблонов OLE DB или атрибутов OLE DB. Созданный код в каждом случае отличается. Дополнительные сведения об этом коде см. [Consumer Wizard-Generated Classes](../../data/oledb/consumer-wizard-generated-classes.md) (Классы, создаваемые мастером объекта-получателя).

## <a name="user-record-support-for-multiple-accessors"></a>Поддержка записей пользователя для нескольких методов доступа

Подробное описание сценариев, в которых нужно использовать несколько методов доступа, см. в статье[Using Multiple Accessors on a Rowset ](../../data/oledb/using-multiple-accessors-on-a-rowset.md) (Использование нескольких методов доступа в наборе строк).

В следующем примере показана запись пользователя, измененная для поддержки нескольких методов доступа в наборе строк. Вместо BEGIN_COLUMN_MAP и END_COLUMN_MAP она использует [BEGIN_ACCESSOR_MAP](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor_map) и [BEGIN_ACCESSOR](./macros-and-global-functions-for-ole-db-consumer-templates.md#begin_accessor) для каждого средства доступа. Макрос BEGIN_ACCESSOR указывает номер средства доступа (начиная от нуля) и указывает, является ли средство доступа автоматическим. Автоматические средства доступа вызывают `GetData` для автоматического извлечения данных при вызове [MoveNext](./crowset-class.md#movenext). Неавтоматические средства доступа требуют явного извлечения данных. Используйте неавтоматический метод доступа для привязке к большому полю данных (например, к растровому изображению), которое вы не хотите получать для каждой записи.

```cpp
class CMultiArtists
{
public:
// Data Elements
   CHAR m_szFirstName[20];
   CHAR m_szLastName[30];
   short m_nAge;

// Column binding map
BEGIN_ACCESSOR_MAP(CMultiArtists, 2)
   BEGIN_ACCESSOR(0, true)    // true specifies an auto accessor
    COLUMN_ENTRY(1, m_szFirstName)
    COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false)   // false specifies a manual accessor
    COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()
};
```

## <a name="see-also"></a>См. также раздел

[Шаблоны объекта-получателя OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)
