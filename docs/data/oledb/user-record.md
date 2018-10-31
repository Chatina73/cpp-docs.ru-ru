---
title: Запись пользователя | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- records, user
- OLE DB providers, user record
- user records
- user records, described
- rowsets, user record
ms.assetid: 9c0d2864-2738-4f62-a750-1016d9c3523f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e37ed0ac918b004513aa64308870a534a7b2af40
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216296"
---
# <a name="user-record"></a>Запись пользователя

Запись пользователя предоставляет структуру кода и данных, представляющий данные столбца для набора строк. Запись пользователя могут создаваться во время компиляции или во время выполнения. При создании поставщика, с помощью **мастер поставщика ATL OLE DB**, мастер создает запись пользователя по умолчанию, который выглядит следующим образом (при условии, что вы указали имя поставщика [краткое имя] из *MyProvider*):

```cpp
class CWindowsFile:
   public WIN32_FIND_DATA
{
public:
  
BEGIN_PROVIDER_COLUMN_MAP(CMyProviderWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
  
};
```

Шаблоны поставщика OLE DB обрабатывают все характеристики OLE DB для взаимодействия с клиентом. Для получения столбца данные, необходимые для ответа, поставщик вызывает `GetColumnInfo` функция, которую необходимо поместить в записи пользователя. Можно явно переопределить `GetColumnInfo` в записи пользователя, например, путем объявления его в h-файл следующим образом:

```cpp
template <class T>
static ATLCOLUMNINFO* GetColumnInfo(T* pThis, ULONG* pcCols) 
```

Это соответствует:

```cpp
static ATLCOLUMNINFO* GetColumnInfo(CommandClass* pThis, ULONG* pcCols)
static ATLCOLUMNINFO* GetColumnInfo(RowsetClass* pThis, ULONG* pcCols)
```

Затем запустите `GetColumnInfo` в записи пользователя CPP-файле.

Макросы PROVIDER_COLUMN_MAP помочь в создании `GetColumnInfo` функции:

- BEGIN_PROVIDER_COLUMN_MAP определяет прототип функции и статический массив `ATLCOLUMNINFO` структуры.

- PROVIDER_COLUMN_ENTRY определяет и инициализирует один `ATLCOLUMNINFO`.

- END_PROVIDER_COLUMN_MAP закрывает массива и функции. Он также помещает число элементов массива в *pcCols* параметра.

При создании записи пользователя во время выполнения, `GetColumnInfo` использует *pThis* параметр для получения указателя на экземпляр набора или команды. Команды и наборы строк должны поддерживать `IColumnsInfo` интерфейс, поэтому сведения о столбцах, которые могут быть взяты из этого указателя.

`CommandClass` и `RowsetClass` команды и строк, используйте запись пользователя.

Более подробный пример переопределения `GetColumnInfo` в записи пользователя, см. в разделе [динамически определить столбцы, возвращенные объекту-получателю](../../data/oledb/dynamically-determining-columns-returned-to-the-consumer.md).

## <a name="see-also"></a>См. также

[Архитектура шаблона поставщика OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
