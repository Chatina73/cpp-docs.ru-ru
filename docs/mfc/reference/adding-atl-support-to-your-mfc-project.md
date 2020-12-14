---
description: Дополнительные сведения см. в статье Добавление поддержки ATL в проект MFC.
title: Добавление поддержки ATL в проект MFC
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.adding.atl.mfc
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
ms.openlocfilehash: 1d02bd6e63a01334fcb9a907dc9ea4fe78ff4a48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248246"
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Добавление поддержки ATL в проект MFC

Если вы уже создали приложение на основе MFC, то можете легко добавить поддержку библиотеки ATL с помощью интегрированной среды разработки.

> [!NOTE]
> Эта поддержка действует только для простых COM-объектов, добавленных в исполняемый файл MFC или проект библиотеки DLL. В проекты MFC можно добавить другие COM-объекты (включая элементы управления ActiveX), но эти объекты могут работать не так, как ожидалось.

::: moniker range=">=msvc-160"

1. В обозреватель решений щелкните правой кнопкой мыши узел проекта.

1. В контекстном меню выберите **Добавить** и **Новый элемент**.

1. В левой области выберите **ATL** , а затем в центральной области выберите **поддержка ATL** .

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-add-atl-support-to-your-mfc-project"></a>Добавление поддержки ATL в проект MFC

1. В обозреватель решений щелкните правой кнопкой мыши узел проекта.

1. В контекстном меню выберите команду **Добавить**, а затем нажмите кнопку **Добавить класс**.

1. Выберите **ATL** в левой области, а затем щелкните **Добавить поддержку ATL в проект MFC** в центральной области.

::: moniker-end

Дополнительные сведения о том, как добавление поддержки ATL изменяет код проекта MFC, см. [в разделе сведения о поддержке ATL, добавленной мастером ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md) .

## <a name="see-also"></a>См. также раздел

[Добавление класса](../../ide/adding-a-class-visual-cpp.md)<br/>
[Добавление функциональных возможностей с помощью мастеров кода](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Добавление функции-члена](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Добавление переменной-члена](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Переопределение виртуальной функции](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Обработчик сообщений MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Перемещение по структуре класса](../../ide/navigate-code-cpp.md)
