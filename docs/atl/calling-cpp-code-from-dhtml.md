---
description: 'Дополнительные сведения: вызов кода C++ из DHTML'
title: Вызов кода C++ из DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: d880b0e9cb2f0b9d5228df7da4fc96fceeb87943
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148490"
---
# <a name="calling-c-code-from-dhtml"></a>Вызов кода C++ из DHTML

Элемент управления DHTML может размещаться в контейнере, таком как тестовый контейнер или Internet Explorer. Сведения о том, как получить доступ к тестовому контейнеру, см. в разделе [Тестирование свойств и событий с помощью тестового контейнера](../mfc/testing-properties-and-events-with-test-container.md) .

Контейнер, в котором размещается элемент управления, взаимодействует с элементом управления с помощью интерфейсов обычного элемента управления. DHTML использует интерфейс диспетчеризации, который заканчивается на "UI" для взаимодействия с кодом C++ и Вашим ресурсом HTML. При [изменении элемента управления ATL DHTML](../atl/modifying-the-atl-dhtml-control.md)можно добавлять методы, вызываемые этими разными интерфейсами.

Чтобы просмотреть пример вызова кода C++ из DHTML, [Создайте элемент управления DHTML](../atl/creating-an-atl-dhtml-control.md) с помощью мастера элементов управления ATL и изучите код в файле заголовка и HTML-файле.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Объявление методов WebBrowser в файле заголовка

Для вызова методов C++ из пользовательского интерфейса DHTML необходимо добавить методы в интерфейс ПОЛЬЗОВАТЕЛЬСКОГО интерфейса элемента управления. Например, файл заголовка, созданный мастером элементов управления ATL, содержит метод C++ `OnClick` , который является членом интерфейса пользовательского интерфейса элемента управления, созданного мастером.

Проверьте `OnClick` в файле. h файла элемента управления:

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

Первый параметр, *пдиспбоди*, является указателем на интерфейс диспетчеризации объекта Body. Второй параметр, *варколор*, определяет цвет, применяемый к элементу управления.

## <a name="calling-c-code-in-the-html-file"></a>Вызов кода C++ в HTML-файле

После объявления методов WebBrowser в файле заголовка можно вызывать методы из HTML-файла. Обратите внимание, что в HTML-файле мастер элементов управления ATL вставляет три метода диспетчеризации Windows: три `OnClick` метода, которые отправляют сообщения для изменения цвета фона элемента управления.

Изучите один из методов в HTML-файле:

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

В приведенном выше коде HTML внешний метод Window `OnClick` вызывается как часть тега кнопки. Метод имеет два параметра: `theBody` , который ссылается на текст HTML-документа, и `"red"` , который указывает, что цвет фона элемента управления будет изменен на красный при нажатии кнопки. `Red`Следующий тег является меткой кнопки.

Дополнительные сведения о предоставлении собственных методов см. [в разделе изменение элемента управления DHTML в ATL](../atl/modifying-the-atl-dhtml-control.md) . Дополнительные сведения о HTML-файле см. в разделе [Определение элементов проекта элемента управления DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) .

## <a name="see-also"></a>См. также раздел

[Поддержка элементов управления DHTML](../atl/atl-support-for-dhtml-controls.md)
