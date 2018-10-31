---
title: CCustomWindowsFile | Документация Майкрософт
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- cmyproviderwindowsfile
- ccustomwindowsfile
dev_langs:
- C++
helpviewer_keywords:
- CMyProviderWindowsFile class
- OLE DB providers, wizard-generated files
- CCustomWindowsFile class
ms.assetid: 0e9e72ac-1e1e-445f-a7ac-690c20031f9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bbbde895c7c83264d0ad77bf50bfc14428cdb99f
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216270"
---
# <a name="ccustomwindowsfile"></a>CCustomWindowsFile

Мастер создает класс, который содержит одну строку данных. в этом случае он называется `CCustomWindowsFile`. В следующем коде для `CCustomWindowsFile` — созданный мастером и выводит все файлы в каталоге с помощью `WIN32_FIND_DATA` структуры. `CCustomWindowsFile` наследует от `WIN32_FIND_DATA` структуры:

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

class CCustomWindowsFile: 
   public WIN32_FIND_DATA
{
public:
BEGIN_PROVIDER_COLUMN_MAP(CCustomWindowsFile)
   PROVIDER_COLUMN_ENTRY("FileAttributes", 1, dwFileAttributes)
   PROVIDER_COLUMN_ENTRY("FileSizeHigh", 2, nFileSizeHigh)
   PROVIDER_COLUMN_ENTRY("FileSizeLow", 3, nFileSizeLow)
   PROVIDER_COLUMN_ENTRY_STR("FileName", 4, cFileName)
   PROVIDER_COLUMN_ENTRY_STR("AltFileName", 5, cAlternateFileName)
END_PROVIDER_COLUMN_MAP()
};
```

`CCustomWindowsFile` вызывается [класс записей пользователя](../../data/oledb/user-record.md) так как он также содержит карту, описывающее столбцы в наборе строк поставщика. Сопоставление столбцов поставщика содержит одну запись для каждого поля в набор строк при помощи PROVIDER_COLUMN_ENTRY в. Макросы укажите имя столбца, порядковый номер и смещения для записи структуры. Поставщик записей столбцов в приведенном выше коде содержится значение смещения в `WIN32_FIND_DATA` структуры. Когда потребитель вызывает `IRowset::GetData`, данные передаются в один непрерывный буфер. Вместо выполнения арифметических операций с указателями, карты можно указать элемент данных.

`CCustomRowset` Класс также содержит `Execute` метод. `Execute` является считывания данных из источника. В следующем коде показано, созданный с помощью мастера `Execute` метод. Эта функция использует Win32 `FindFirstFile` и `FindNextFile` API-интерфейсы для извлечения сведений о файлах в каталоге и поместите их в экземпляры `CCustomWindowsFile` класса.

```cpp
/////////////////////////////////////////////////////////////////////
// CustomRS.H

HRESULT Execute(DBPARAMS * pParams, LONG* pcRowsAffected)
{
   USES_CONVERSION;
   BOOL bFound = FALSE;
   HANDLE hFile;
   LPTSTR  szDir = (m_strCommandText == _T("")) ? _T("*.*") :
       OLE2T(m_strCommandText);
   CCustomWindowsFile wf;
   hFile = FindFirstFile(szDir, &wf);
   if (hFile == INVALID_HANDLE_VALUE)
      return DB_E_ERRORSINCOMMAND;
   LONG cFiles = 1;
   BOOL bMoreFiles = TRUE;
   while (bMoreFiles)
   {
      if (!m_rgRowData.Add(wf))
         return E_OUTOFMEMORY;
      bMoreFiles = FindNextFile(hFile, &wf);
      cFiles++;
   }
   FindClose(hFile);
   if (pcRowsAffected != NULL)
      *pcRowsAffected = cFiles;
   return S_OK;
}
```

Каталог для поиска отображается по `m_strCommandText`; он содержит текст, представленный `ICommandText` интерфейса на объект команды. Если каталог не указан, используется текущий каталог.

Этот метод создаст одну запись для каждого файла (соответствует строке) и помещает его в `m_rgRowData` элемент данных. `CRowsetImpl` Класс определяет `m_rgRowData` элемент данных. Данные в этом массиве отображается вся таблица и используется во всех шаблонах.

## <a name="see-also"></a>См. также

[Созданные мастером поставщика файлы](../../data/oledb/provider-wizard-generated-files.md)<br/>
