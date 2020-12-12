---
description: 'Дополнительные сведения: Добавление поставщика OLE DB ATL'
title: Добавление поставщика OLE DB в ATL
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, adding ATL OLE DB provider to projects
- ATL projects, adding ATL OLE DB providers
- ATL OLE DB providers
ms.assetid: 26fba1e3-880f-4bc6-90e5-2096a48a3a6c
ms.openlocfilehash: e60150e2d8dc57e16a55c75556d109583a95f054
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165671"
---
# <a name="adding-an-atl-ole-db-provider"></a>Добавление поставщика OLE DB в ATL

::: moniker range="msvc-160"

Мастер поставщика OLE DB в ATL недоступен в Visual Studio 2019 и более поздних версиях.

::: moniker-end

::: moniker range="<=msvc-150"

Этот мастер используется для добавления поставщика OLE DB в ATL в проект. Поставщик OLE DB в ATL состоит из источника данных, сеанса, команды и классов набора строк. Проект для его реализации создается как COM-приложение ATL.

## <a name="to-add-an-atl-ole-db-provider-to-your-project"></a>Добавление поставщика OLE DB в ATL в проект

1. В разделе **Представление классов** щелкните проект правой кнопкой мыши. В контекстном меню выберите команду **Добавить**, а затем — **Добавить класс**.

1. В папке **Visual C++** дважды щелкните значок **поставщика OLE DB в ATL** или выберите его и нажмите кнопку **Открыть**.

   Откроется мастер поставщика OLE DB в ATL.

1. Задайте параметры, как описано в статье [ATL OLE DB Provider Wizard](../../atl/reference/atl-ole-db-provider-wizard.md) (Мастер поставщика OLE DB в ATL).

1. Нажмите кнопку **Готово**, чтобы закрыть мастер, который вставит только что созданный код поставщика OLE DB в проект.

::: moniker-end

## <a name="see-also"></a>См. также раздел

[Добавление функциональных возможностей с помощью мастеров кода](../../ide/adding-functionality-with-code-wizards-cpp.md)
