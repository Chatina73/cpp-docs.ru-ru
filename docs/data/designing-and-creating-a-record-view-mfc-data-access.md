---
title: Разработка и создание представления записей (доступ к данным MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- designing forms
- record views, creating
- forms [C++], designing
- record views, designing
- application wizards [C++], creating record view classes
- designing record views
ms.assetid: 1d6f5439-754f-4b8b-a19d-841a4657827b
ms.openlocfilehash: 15a8afde8c86d3dae8198e8f42b2b7c3b49f0dfa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397969"
---
# <a name="designing-and-creating-a-record-view--mfc-data-access"></a>Разработка и создание представления записей (доступ к данным MFC)

Можно создать класс представления записей с [мастер приложений MFC](../mfc/reference/database-support-mfc-application-wizard.md). При использовании мастера приложений он создает класс представления записей и ресурс шаблона диалоговых окон для него (без элементов управления). Для добавления элементов управления в ресурс шаблона диалоговых окон необходимо использовать редактор диалоговых окон Visual C++. С другой стороны, если вы используете **Добавление класса**, необходимо сначала создать ресурс шаблона диалоговых окон в диалоговом окне Редактор и затем создать класс представления записей.

#### <a name="to-create-your-record-view-with-the-mfc-application-wizard"></a>Для создание представления записей с помощью мастера приложений MFC

1. См. в разделе [поддержка базы данных, мастер приложений MFC](../mfc/reference/database-support-mfc-application-wizard.md).

#### <a name="to-design-your-form"></a>Разработка формы

1. См. в разделе [редактор диалоговых окон](../windows/dialog-editor.md).

#### <a name="to-create-your-record-view-class"></a>Чтобы создать класс представления записей

1. См. в разделе [Добавление потребителя MFC ODBC](../mfc/reference/adding-an-mfc-odbc-consumer.md).

В следующих разделах представлены дополнительные сведения об использовании представления записей:

- [Представления записей: Поддержка навигации в представлении записей](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)

- [Представления записей: Использование представления записей](../data/using-a-record-view-mfc-data-access.md)

- [Представления записей: Заполнение списка из второго набора записей](../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md)

## <a name="see-also"></a>См. также

[Представления записей (доступ к данным MFC)](../data/record-views-mfc-data-access.md)<br/>
[Набор записей (ODBC)](../data/odbc/recordset-odbc.md)<br/>
[Список драйверов ODBC](../data/odbc/odbc-driver-list.md)