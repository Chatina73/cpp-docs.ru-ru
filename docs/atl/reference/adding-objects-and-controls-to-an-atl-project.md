---
title: Добавление объектов и элементов управления в проект ATL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: d16e9a9e7b92d2a98f8994227c5641994677fdda
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221204"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>Добавление объектов и элементов управления в проект ATL

Один из мастеров кода ATL можно использовать для добавления объекта или элемента управления в проекты на основе ATL или MFC. Для каждого COM-объект или элемент управления можно добавить мастер формирует .cpp и .h файлы, а также RGS-файл для поддержки реестра на основе сценария. Следующие мастера кода ATL, доступны в Visual Studio:

||||
|-|-|-|
|[Простой объект ATL](../../atl/reference/atl-simple-object-wizard.md)|[Диалоговое окно ATL](../../atl/reference/atl-dialog-wizard.md)|[Элемент управления ATL](../../atl/reference/atl-control-wizard.md)|
|[Страницы свойств ATL](../../atl/reference/atl-property-page-wizard.md)|[ASP-компонента ATL](../../atl/reference/atl-active-server-page-component-wizard.md)|[Потребителя ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[Добавление в MFC поддержки ATL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[Мастер компонентов ATL COM+ 1.0](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[Поставщик OLE DB ATL](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> Прежде чем добавить объект ATL в проект, изучите сведения и требования для объекта в соответствующих разделах справки.

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>Чтобы добавить объект или элемент управления с помощью мастера управления ATL

1. В **обозревателе решений**, щелкните правой кнопкой мыши узел проекта и нажмите кнопку **добавить** в контекстном меню. Нажмите кнопку **добавьте класс**.

   [Добавление класса](../../ide/add-class-dialog-box.md) откроется диалоговое окно.

1. С помощью **ATL** папке, выбранной в **категории** панели выберите объект для вставки из **шаблоны** области. Нажмите кнопку **Открыть**. Откроется мастер кода для выбранного объекта.

   > [!NOTE]
   > Если вы хотите добавить объект ATL в проект MFC, необходимо добавить поддержку ATL в существующий проект. Это можно сделать, следуя инструкциям в [Добавление поддержки ATL в проект MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md).

   Кроме того при попытке добавить объект ATL в проект MFC без ранее Добавление поддержки ATL, Visual Studio предложит укажите нужное поддержки ATL, добавлен в проект. Нажмите кнопку **Да** Добавление поддержки ATL в проект и открыть выбранный мастер ATL.

## <a name="see-also"></a>См. также

[Мастер проектов ATL](../../atl/reference/atl-project-wizard.md)<br/>
[C++типы проектов в Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Основы COM-объектов ATL](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[Программирование с использованием ATL и кода среды выполнения C](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Конфигурации проектов ATL по умолчанию](../../atl/reference/default-atl-project-configurations.md)
