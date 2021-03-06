---
description: 'Дополнительные сведения: дополнительные функции, мастер приложений MFC'
title: Страница "Дополнительные функции" мастера приложений MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: f709f933549c9cc1aa4a53a361682f1c444bbcbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248259"
---
# <a name="advanced-features-mfc-application-wizard"></a>Страница "Дополнительные функции" мастера приложений MFC

В этом разделе представлены параметры, относящиеся к дополнительным возможностям приложения, таким как справка, поддержка печати и т. д. С помощью данных параметров можно включить поддержку дополнительных возможностей, описанных ниже.

- **Контекстно-зависимая справка (HTML)**

   Создает набор файлов справки для контекстной справки, доступной при помощи клавиши F1 и меню «Справка», либо нажатием кнопки « **Справка** » в диалоговом окне. Для поддержки справки требуется компилятор справки. Если компилятор справки отсутствует, его можно установить, заново запустив программу установки.

   Дополнительные сведения см. [в разделе Справка HTML: Context-Sensitive Справка по программам](../../mfc/html-help-context-sensitive-help-for-your-programs.md) и [файлам справки (HTML-справка)](../../build/reference/help-files-html-help.md) .

- **Печать и предварительный просмотр печати**

   Создает код для обработки команд печати, печати и предварительного просмотра путем вызова функций членов в [классе CView](../../mfc/reference/cview-class.md) из библиотеки MFC. Мастер также добавляет в меню приложения команды для этих функций. Поддержка печати доступна только для приложений, которые задают **поддержку архитектуры документов и представлений** на странице мастера [Тип приложения, мастер приложений MFC](../../mfc/reference/application-type-mfc-application-wizard.md) . По умолчанию приложения, использующие архитектуру "документ-представление", поддерживают печать.

- **Служба автоматизации**

   Задает, может ли приложение управлять объектами, реализованными в другом приложении, или предоставляет ли клиентам автоматизации доступ к приложению.

- **Элементы управления ActiveX**

   Указывает, включена ли поддержка элементов управления ActiveX (выбрано по умолчанию). Если этот параметр не выбран и в дальнейшем требуется вставить элементы управления ActiveX в проект, необходимо добавить вызов [афксенаблеконтролконтаинер](ole-initialization.md#afxenablecontrolcontainer) в функцию-член [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) приложения.

- **MAPI (API обмена сообщениями)**

   Указывает, может ли приложение создавать, передавать и хранить почтовые сообщения, а также управлять ими.

- **Сокеты Windows**

   Поддержка служб Windows Sockets, с помощью которых можно создавать приложения, обменивающиеся данными по сетям TCP/IP.

- **Active Accessibility**

   Добавляет поддержку [IAccessible](/windows/win32/api/oleacc/nn-oleacc-iaccessible) для классов, производных от [CWnd](../../mfc/reference/cwnd-class.md), которые можно использовать для настройки пользовательского интерфейса для улучшения взаимодействия с клиентами специальных возможностей.

- **Манифест стандартных элементов управления**

   Включен по умолчанию. Создание манифеста приложения для включения новой библиотеки DLL стандартных элементов управления, поставляемой с Microsoft Windows XP или операционными системами последующих поколений.

   Версия 6 библиотеки DLL стандартных элементов управления не поддерживает автоматическое обновление предыдущих версий стандартных элементов управления, используемых существующим приложением. Чтобы использовать версию 6 библиотеки DLL стандартных элементов управления, необходимо создать манифест приложения, указывающий приложению загрузить новую библиотеку DLL. Эта библиотека DLL стандартных элементов управления также поддерживает темы Windows XP.

   Манифест приложения может также задавать другие библиотеки DLL и версии библиотек, необходимые приложению. Дополнительные сведения о манифестах приложений см. в разделе [изолированные приложения и параллельные сборки](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) в Windows SDK.

- **Поддержка диспетчера перезагрузки**

   Добавляет поддержку для [диспетчера перезапуска Windows](/windows/win32/RstMgr/using-restart-manager). В этом видео показано, как использовать диспетчер перезапуска из MFC. [инструкции: использование нового диспетчера перезапуска](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100)).

- **Дополнительные области фреймов**

   |Параметр|Описание|
   |------------|-----------------|
   |**Закрепляемая область обозревателя**|Создает закрепляемую область, похожую на **Обозреватель решений** Visual Studio слева от главного окна фрейма.|
   |**Закрепляемый фрейм вывода**|Создает закрепляемую область, похожую на область **вывода** Visual Studio, расположенную в главном окне фрейма.|
   |**Закрепляемая область свойств**|Создает закрепляемую область, похожую на область **свойств** Visual Studio справа от главного окна фрейма.|
   |**Панель навигации**|Создание закрепляемой области, аналогичной панели переходов Outlook, слева от фрейма главного окна.|
   |**Заголовок окна**|Создание заголовка окна, аналогичного Office, выше фрейма главного окна.|

- **Число файлов в текущем списке файлов**

   Указывает число файлов, которые будут включены в список последних использовавшихся файлов. Значение по умолчанию — 4.

## <a name="see-also"></a>См. также раздел

[Мастер приложений MFC](../../mfc/reference/mfc-application-wizard.md)
