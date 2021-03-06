---
description: Дополнительные сведения см. в статье тестирование поставщика Read-Only.
title: Проверка поставщика в режиме "только для чтения"
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: 2fbe0e7fb67b83cae65848939fa63bce42dab173
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272699"
---
# <a name="testing-the-read-only-provider"></a>Проверка поставщика в режиме "только для чтения"

Для тестирования поставщика требуется потребитель. Он помогает, если потребитель может сопоставить с поставщиком. Шаблоны потребителей OLE DB являются тонкой оболочкой для OLE DB и совпадают с COM-объектами поставщика. Поскольку источник поставляется с шаблонами потребителей, с ними легко выполнять отладку поставщика. Шаблоны потребителей также являются очень малым и быстрым способом разработки потребительских приложений.

В примере в этом разделе создается приложение мастера приложений MFC по умолчанию для тестового потребителя. Тестовое приложение — это простое диалоговое окно с добавленным кодом шаблона потребителя OLE DB.

## <a name="to-create-the-test-application"></a>Создание тестового приложения

1. В меню **Файл** выберите **Создать**, а затем пункт **Проект**.

1. В области **типы проектов** выберите **установленная**  >  **Visual C++**  >  Папка **MFC/ATL** . В области **шаблоны** выберите **приложение MFC**.

1. В поле имя проекта введите *тестпров* и нажмите кнопку **ОК**.

   Откроется мастер **приложений MFC** .

1. На странице **Тип приложения** выберите **диалоговое окно на основе**.

1. На странице **Дополнительные функции** выберите **Автоматизация** и нажмите кнопку **Готово**.

> [!NOTE]
> Приложение не требует поддержки автоматизации при добавлении `CoInitialize` в `CTestProvApp::InitInstance` .

Чтобы просмотреть и изменить диалоговое окно **тестпров** (IDD_TESTPROV_DIALOG), выберите его в **представление ресурсов**. Поместите два списка, по одному для каждой строки в наборе строк, в диалоговом окне. Отключите свойство Sort для обоих списков, нажав клавишу **ALT** + **Ввод** при выборе поля со списком и установив для свойства **Sort** значение **false**. Кроме того, разместите кнопку **выполнить** в диалоговом окне, чтобы получить файл. Диалоговое окно завершенное **тестпров** должно содержать два списка с пометкой "строка 1" и "строка 2" соответственно; у него также есть кнопки **ОК**, **Отмена** и **выполнить** .

Откройте файл заголовка для класса диалогового окна (в данном случае Тестпровдлг. h). Добавьте следующий код в файл заголовка (за пределами любых объявлений класса):

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

Код представляет запись пользователя, которая определяет, какие столбцы будут находиться в наборе строк. Когда клиент вызывает `IAccessor::CreateAccessor` , он использует эти записи для указания столбцов для привязки. Шаблоны OLE DB потребителей также позволяют динамически привязывать столбцы. COLUMN_ENTRY макросы — это клиентская версия макросов PROVIDER_COLUMN_ENTRY. Два макроса COLUMN_ENTRY указывают порядковый номер, тип, длину и элемент данных для двух строк.

Добавьте функцию обработчика для кнопки **выполнить** , нажав **клавишу CTRL** и дважды щелкнув кнопку **выполнить** . Поместите следующий код в функцию:

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

`CCommand` `CDataSource` Все классы, и `CSession` принадлежат шаблонам потребителя OLE DB. Каждый класс имитирует COM-объект в поставщике. `CCommand`Объект принимает `CProvider` класс, объявленный в файле заголовка, в качестве параметра шаблона. `CProvider`Параметр представляет привязки, используемые для доступа к данным от поставщика.

Строки для открытия каждого из классов создают каждый COM-объект в поставщике. Чтобы узнать поставщика, используйте `ProgID` поставщик. Можно получить `ProgID` из системного реестра или путем просмотра пользовательского RGS-файла (откройте каталог поставщика и выполните поиск `ProgID` ключа).

Файл MyData.txt включен в `MyProv` пример. Чтобы создать собственный файл, используйте редактор и введите четное число строк, нажимая клавишу **Ввод** между каждой строкой. Измените имя пути при перемещении файла.

Передайте строку "c: \\ \самплес \\ \мипров \\\MyData.txt" в `table.Open` строке. Если выполнить шаг с заходом в `Open` вызов, вы увидите, что эта строка передается в `SetCommandText` метод в поставщике. Обратите внимание, что `ICommandText::Execute` метод использовал эту строку.

Чтобы получить данные, вызовите `MoveNext` для таблицы. `MoveNext` вызывает `IRowset::GetNextRows` функции, `GetRowCount` и `GetData` . Если больше нет строк (то есть текущая позицией в наборе строк больше `GetRowCount` ), цикл завершается.

Если больше нет строк, поставщики возвращают DB_S_ENDOFROWSET. Значение DB_S_ENDOFROWSET не является ошибкой. Всегда следует проверять S_OK, чтобы отменить цикл выборки данных и не использовать макрос "успех".

Теперь вы можете создать и протестировать программу.

## <a name="see-also"></a>См. также раздел

[Усовершенствование простого поставщика Read-Only](../../data/oledb/enhancing-the-simple-read-only-provider.md)
