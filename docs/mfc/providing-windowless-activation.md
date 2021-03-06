---
description: 'Дополнительные сведения: предоставление безоконной активации'
title: Предоставление активации без окна
ms.date: 11/04/2016
helpviewer_keywords:
- windowless activation of MFC ActiveX controls
- activation [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], activate options
- activation [MFC], windowless
ms.assetid: 094903b5-c344-42fa-96ff-ce01e16891c5
ms.openlocfilehash: ea9b86c977926e57bd3593ec861498eb5d909f37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248636"
---
# <a name="providing-windowless-activation"></a>Предоставление активации без окна

Код создания окна (то есть все, что происходит при вызове `CreateWindow` ) является дорогостоящим для выполнения. Элемент управления, поддерживающий экранные окна, должен управлять сообщениями для окна. Элементы управления без окон, таким образом, работают быстрее, чем элементы управления с Windows.

Еще больше преимуществ безоконных элементов управления заключается в том, что, в отличие от оконных элементов управления, безоконное Управление поддерживает прозрачное Рисование и непрямоугольные области экрана. Распространенным примером прозрачного элемента управления является текстовый элемент управления с прозрачным фоном. Элементы управления выводят текст, но не фон, так что текст под ним отображается. Более новые формы часто используют непрямоугольные элементы управления, такие как стрелки и скругленные кнопки.

Часто элементу управления не требуется окно, а вместо этого он может использовать службы окон своего контейнера при условии, что контейнер был записан для поддержки объектов без окон. Элементы управления без окон поддерживают обратную совместимость с более старыми контейнерами. В более старых контейнерах, не написанных для поддержки безоконных элементов управления, безоконное управление создает окно, когда оно активно.

Поскольку элементы управления без окон не имеют собственных окон, контейнер (который имеет окно) отвечает за предоставление служб, которые в противном случае были бы предоставлены в собственном окне элемента управления. Например, если элементу управления необходимо запросить фокус клавиатуры, захватить мышь или получить контекст устройства, управление этими операциями осуществляется контейнером. Контейнер направляет сообщения ввода пользователя, отправленные в окно, в соответствующий элемент управления без окон, используя `IOleInPlaceObjectWindowless` интерфейс. (Описание этого интерфейса см. в *пакете SDK для ActiveX* .) `COleControl` функции элементов вызывают эти службы из контейнера.

Чтобы заставить элемент управления использовать безоконную активацию, включите флаг **виндовлессактивате** в набор флагов, возвращаемых [COleControl:: жетконтролфлагс](../mfc/reference/colecontrol-class.md#getcontrolflags). Пример:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-windowless-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#6](../mfc/codesnippet/cpp/providing-windowless-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-windowless-activation_3.cpp)]

Код для включения этого флага создается автоматически при выборе параметра Активация без **окна** на странице [Параметры управления](../mfc/reference/control-settings-mfc-activex-control-wizard.md) мастера элементов управления MFC ActiveX.

Если активация без окон включена, контейнер будет делегировать входные сообщения `IOleInPlaceObjectWindowless` интерфейсу элемента управления. `COleControl`Реализация этого интерфейса отправляет сообщения через карту сообщений элемента управления после правильной настройки координат мыши. Можно обрабатывать сообщения, такие как обычные сообщения в окне, добавляя соответствующие записи в схему сообщений. В обработчиках этих сообщений не следует использовать переменную-член *m_hWnd* (или любую функцию-член, которая ее использует) без предварительной проверки того, что ее значение не равно **null**.

`COleControl` предоставляет функции элементов, которые вызывают захват мыши, фокус клавиатуры, прокрутку и другие службы окон из контейнера, в зависимости от того, что:

- Функция [Focus](../mfc/reference/colecontrol-class.md#getfocus), [SetFocus](../mfc/reference/colecontrol-class.md#setfocus)

- [Захват](../mfc/reference/colecontrol-class.md#getcapture), [сеткаптуре](../mfc/reference/colecontrol-class.md#setcapture), [релеасекаптуре](../mfc/reference/colecontrol-class.md#releasecapture)

- [GetDC](../mfc/reference/colecontrol-class.md#getdc), [релеаседк](../mfc/reference/colecontrol-class.md#releasedc)

- [инвалидатергн](../mfc/reference/colecontrol-class.md#invalidatergn)

- [скроллвиндов](../mfc/reference/colecontrol-class.md#scrollwindow)

- [жетклиентрект](../mfc/reference/colecontrol-class.md#getclientrect)

В безоконных элементах управления всегда следует использовать `COleControl` функции-члены вместо соответствующих `CWnd` функций-членов или связанных с ними функций API Win32.

Может потребоваться, чтобы элемент управления без окон был целевым объектом операции перетаскивания OLE. Как правило, это потребует, чтобы окно элемента управления было зарегистрировано как цель перетаскивания. Поскольку элемент управления не имеет собственного окна, контейнер использует собственное окно в качестве цели перетаскивания. Элемент управления предоставляет реализацию `IDropTarget` интерфейса, к которому контейнер может делегировать вызовы в соответствующее время. Чтобы предоставить этот интерфейс контейнеру, переопределите [COleControl:: жетвиндовлессдроптаржет](../mfc/reference/colecontrol-class.md#getwindowlessdroptarget). Пример:

[!code-cpp[NVC_MFC_AxOpt#8](../mfc/codesnippet/cpp/providing-windowless-activation_4.cpp)]

## <a name="see-also"></a>См. также раздел

[Элементы ActiveX в MFC. Оптимизация](../mfc/mfc-activex-controls-optimization.md)
