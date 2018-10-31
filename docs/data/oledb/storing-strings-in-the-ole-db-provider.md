---
title: Хранение строк в поставщике OLE DB | Документация Майкрософт
ms.custom: ''
ms.date: 10/26/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user records, editing
ms.assetid: 36cb9635-067c-4cad-8f85-962f28026f6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 46529a97ff38071c71ecdaf93e41f3eeb405c8a6
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216439"
---
# <a name="storing-strings-in-the-ole-db-provider"></a>Хранение строк в поставщике OLE DB

В MyProviderRS.h **мастер поставщика ATL OLE DB** создает запись пользователя по умолчанию с именем `CWindowsFile`. Для обработки двух строк, измените `CWindowsFile` или добавьте собственную запись пользователя, как показано в следующем коде:

```cpp
////////////////////////////////////////////////////////////////////////
class CAgentMan: 
   public WIN32_FIND_DATA
   DWORD dwBookmark;              // Add this
   TCHAR szCommand[256];          // Add this
   TCHAR szText[256];             // Add this
   TCHAR szCommand2[256];         // Add this
   TCHAR szText2[256];            // Add this
  
{
public:
BEGIN_PROVIDER_COLUMN_MAP()
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command"), 1, 256, GUID_NULL, CAgentMan, szCommand)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text"), 2, 256, GUID_NULL, CAgentMan, szText) 
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Command2"), 3, 256, GUID_NULL, CAgentMan, szCommand2)
   PROVIDER_COLUMN_ENTRY_STR(OLESTR("Text2"),4, 256, GUID_NULL, CAgentMan, szText2)
END_PROVIDER_COLUMN_MAP()
   bool operator==(const CAgentMan& am) // This is optional 
   {
      return (lstrcmpi(cFileName, wf.cFileName) == 0);
   }
};
```

Члены данных `szCommand` и `szText` представляют две строки с `szCommand2` и `szText2` с дополнительными столбцами, при необходимости. Элемент данных `dwBookmark` не нужен для этого простого поставщика только для чтения, но будет использоваться позднее для добавления `IRowsetLocate` интерфейс; см. в разделе [Усовершенствование простого чтения только поставщика](../../data/oledb/enhancing-the-simple-read-only-provider.md). `==` Оператор сравнивает экземпляры (реализация этот оператор является необязательным).

Если это сделано, ваш поставщик должен быть готовым для компиляции и выполнения. Чтобы протестировать поставщика, требуется объект-получатель с соответствующими функциями. [Реализация простых объектов получателей](../../data/oledb/implementing-a-simple-consumer.md) показано создание объекта-получателя для тестирования. Выполните тестовый объект-получатель для поставщика. Убедитесь, что тестовый объект-получатель получает соответствующие строки от поставщика, при нажатии кнопки **запуска** кнопку **тестовый объект-получатель** диалоговое окно.

После успешного тестирования поставщика можно расширить его функциональные возможности, реализовав дополнительные интерфейсы. Пример показан в [Усовершенствование простого поставщика только для чтения](../../data/oledb/enhancing-the-simple-read-only-provider.md).

## <a name="see-also"></a>См. также

[Реализация простого поставщика, предназначенного только для чтения](../../data/oledb/implementing-the-simple-read-only-provider.md)<br/>
