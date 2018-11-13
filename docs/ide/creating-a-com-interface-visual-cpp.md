---
title: Создание интерфейса COM (Visual C++)
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.com.creating.interfaces
helpviewer_keywords:
- COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 2d76dac150f86078e67374eec2e5e2e0f8b9f5e3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51523506"
---
# <a name="creating-a-com-interface-visual-c"></a>Создание интерфейса COM (Visual C++)

Visual C++ предоставляет мастеры и шаблоны для создания проектов, использующих определяющие COM интерфейсы и disp-интерфейсы для COM-объектов и классов автоматизации.

Эти мастеры можно использовать для выполнения трех следующих типичных задач.

- [Добавление поддержки ATL в проект MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

   Добавьте поддержку ATL в приложение MFC после создания проекта MFC с помощью [мастера приложений MFC](../mfc/reference/mfc-application-wizard.md) и последующего запуска мастера кода **Добавление поддержки ATL в MFC**. Эта поддержка действует только для простых COM-объектов, добавленных в исполняемый файл MFC или проект библиотеки DLL. Эти объекты ATL могут иметь несколько интерфейсов.

- [Создание элемента ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)

   Откройте [Мастер элементов ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) для создания элемента управления ActiveX с disp-интерфейсом и схемы событий, определенных в IDL-файле и классе элементов управления, соответственно.

- [Добавление элемента управления ATL](../atl/reference/adding-an-atl-control.md)

   Используйте сочетание [мастера проектов ATL](../atl/reference/atl-project-wizard.md) и [мастера элементов управления ATL](../atl/reference/atl-control-wizard.md), чтобы создать элемент управления ActiveX ATL.

   Вы также можете добавить элемент управления ATL в проект MFC, куда уже добавили поддержку ATL, как описано выше. Кроме того, если вы выбираете пункт **Элемент управления ATL** в диалоговом окне **Добавление класса** и еще не добавили поддержку ATL в проект MFC, Visual Studio отображает диалоговое окно с предложением подтвердить добавление поддержки ATL в ваш проект MFC.

   Этот мастер создает исходный код IDL и схему COM в классах проекта.

После открытия проекта ATL диалоговое окно [Добавление класса](../ide/add-class-dialog-box.md) позволяет вам выбрать дополнительные мастеры и шаблоны для добавления COM-интерфейсов в проект. Следующие мастеры позволяют задать один или несколько интерфейсов для объекта.

- [Мастер компонентов ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)

- [Мастер простых объектов ATL](../atl/reference/atl-simple-object-wizard.md)

- [Мастер ASP-компонента ATL](../atl/reference/atl-active-server-page-component-wizard.md)

- [Мастер элементов управления ATL](../atl/reference/atl-control-wizard.md)

Кроме того, можно реализовать новые интерфейсы для своего элемента управления COM, щелкнув правой кнопкой мыши класс элемента управления объекта в представлении классов и выбрав команду [Реализовать интерфейс](../ide/implement-interface-wizard.md).

> [!NOTE]
>  Visual Studio не предоставляет мастер для добавления интерфейса в проект. Вы можете добавить интерфейс в проект ATL или [добавить поддержку ATL в проект MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md), добавив простой объект с помощью [мастера простых объектов ATL](../atl/reference/atl-simple-object-wizard.md). Кроме того, можно открыть IDL-файл проекта и создать интерфейс, введя следующее:

```
interface IMyInterface {
};
```

Дополнительные сведения см. в разделах [Реализация интерфейса](../ide/implementing-an-interface-visual-cpp.md) и [Добавление объектов и элементов управления в проект ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ предоставляет несколько способов просмотра и [редактирования COM-интерфейсов](../ide/editing-a-com-interface.md), определенных для проектов. В [представлении классов](/visualstudio/ide/viewing-the-structure-of-code) отображаются значки для всех интерфейсов или disp-интерфейсов, определенных в IDL-файле проекта C++.

Для классов COM-объектов на основе ATL представление классов считывает схему COM в классе ATL, чтобы показать связь между классом ATL и любым из реализуемых им интерфейсов.

В представлении классов и его контекстных меню можно работать с интерфейсами следующим образом.

- Добавление объектов ATL в приложение на основе MFC.

- Добавление методов, свойств и событий.

- Переход непосредственно к коду интерфейса элемента с помощью двойного щелчка элемента.

## <a name="see-also"></a>См. также

[Создание проектов для рабочего стола с помощью мастеров приложений](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Добавление функциональных возможностей с помощью мастеров кода](../ide/adding-functionality-with-code-wizards-cpp.md)