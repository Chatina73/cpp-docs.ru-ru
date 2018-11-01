---
title: Создание приложения MFC в стиле браузера
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: 1fd61b3e6bcb2f429c43edcabb41e166bcec95c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466161"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Создание приложения MFC в стиле браузера

Веб-приложения в стиле браузера можно получить доступ к сведения из Интернета (например, HTML или активные документы) или интрасети, а также папки в локальной файловой системе и в сети. Путем создания производного класса представления приложения из [CHtmlView](../../mfc/reference/chtmlview-class.md), что сделать приложение веб-браузер, создавая представление с элементом управления WebBrowser.

### <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>Создание веб-приложения браузера, в зависимости от архитектуры документ/представление MFC

1. Следуйте указаниям, приведенным в [Создание приложения MFC](../../mfc/reference/creating-an-mfc-application.md).

1. В мастере приложений MFC [тип приложения](../../mfc/reference/application-type-mfc-application-wizard.md) странице, убедитесь, что **архитектуры Document/view** установлен. (Вы также можете выбрать **одного документа** или **несколько документов**, но не **на основе диалоговых окон**.)

1. На [обзор созданных классов](../../mfc/reference/generated-classes-mfc-application-wizard.md) странице **базового класса** раскрывающееся меню для выбора `CHtmlView`.

1. Выберите любые другие нужные параметры встроенных в общую схему приложения.

1. Нажмите кнопку **Готово**.

Элемент управления WebBrowser поддерживает просмотр веб-страниц через гиперссылки и навигации унифицированный указатель ресурса (URL). Элемент управления сохраняет список журнала, который позволяет пользователю перемещаться вперед и назад по ранее просмотренных узлов, папок и документов. Этот элемент управления напрямую обрабатывает навигации, гиперссылки, списки элементов, Избранное и безопасности. Приложения могут использовать элемент управления WebBrowser как создание контейнера активных документов также активный документ. Таким образом документы, со сложным форматированием, такие как электронные таблицы Microsoft Excel или Word документов можно открыть и редактировать непосредственно из элемента управления WebBrowser. Элемент управления WebBrowser также является контейнер элементов управления ActiveX, который может содержать любой элемент управления ActiveX.

> [!NOTE]
>  Элемент управления WebBrowser ActiveX (и, следовательно `CHtmlView`) доступен только для приложений, работающих в версиях Windows, в какие Internet Explorer 4.0 или более поздней версии была установлена.

Так как `CHtmlView` просто реализует элемент управления браузера Microsoft Web, поддержка для печати не как другой [CView](../../mfc/reference/cview-class.md)-производные классы. Вместо этого элемент управления WebBrowser реализует интерфейс пользователя принтера и печати. В результате `CHtmlView` does не поддерживает предварительный просмотр, платформа для обеспечения и другими функциями службы поддержки печати: например, [CView::OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView::OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting), и [CView::OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), которые доступны в других приложениях MFC.

`CHtmlView` служит оболочкой для элемента управления браузера, который дает приложению представления веб-или HTML-страницы. Мастер создает переопределение, чтобы [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) функцию в классе представления, предоставляя ссылка для перехода на Microsoft Visual C++, веб-сайт:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.msdn.microsoft.com/vstudio/"),
        NULL,
        NULL);
}
```

Вы можете заменить этот узел, или воспользоваться [LoadFromResource](../../mfc/reference/chtmlview-class.md#loadfromresource) функцию-член для открытия страницы HTML, находящейся в скрипте ресурсов проекта в качестве содержимого по умолчанию для представления. Пример:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>См. также

[Пример MFC MFCIE](https://github.com/Microsoft/VCSamples)<br/>
[Мастер приложений MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Работа со свойствами проектов](../../ide/working-with-project-properties.md)<br/>
[Страницы свойств](../../ide/property-pages-visual-cpp.md)<br/>
[Работа со свойствами проектов](../../ide/working-with-project-properties.md)

