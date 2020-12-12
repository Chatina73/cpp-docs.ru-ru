---
description: 'Дополнительные сведения см. в статье элементы управления ActiveX в MFC: использование страниц свойств на бирже'
title: Элементы управления ActiveX в MFC. Использование стандартных страниц свойств
ms.date: 09/12/2018
f1_keywords:
- CLSID_CPicturePropPage
- CLSID_CColorPropPage
- CLSID_CFontPropPage
helpviewer_keywords:
- picture stock property pages [MFC]
- CLSID_CFontPropPage [MFC]
- color stock property pages [MFC]
- CLSID_CColorPropPage [MFC]
- fonts [MFC], ActiveX controls
- stock properties [MFC], stock property pages
- CLSID_CPicturePropPage [MFC]
- MFC ActiveX controls [MFC], property pages
ms.assetid: 22638d86-ff3e-4124-933e-54b7c2a25968
ms.openlocfilehash: 37cb6e5b5dfa08c5e7935064a66c2c77fe8dcde6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133059"
---
# <a name="mfc-activex-controls-using-stock-property-pages"></a>Элементы управления ActiveX в MFC. Использование стандартных страниц свойств

В этой статье рассматриваются страницы свойств, доступные для элементов управления ActiveX, и способы их использования.

>[!IMPORTANT]
> ActiveX — это устаревшая технология, которую не следует использовать для новой разработки. Дополнительные сведения о современных технологиях, которые заменяют ActiveX, см. в разделе [элементы управления ActiveX](activex-controls.md).

Дополнительные сведения об использовании страниц свойств в элементе управления ActiveX см. в следующих статьях:

- [Элементы управления ActiveX в MFC: страницы свойств](mfc-activex-controls-property-pages.md)

- [Элементы управления ActiveX в MFC. добавление другой страницы настраиваемых свойств](mfc-activex-controls-adding-another-custom-property-page.md)

MFC предоставляет три страницы свойств, предназначенные для использования с элементами управления ActiveX: `CLSID_CColorPropPage` , `CLSID_CFontPropPage` и `CLSID_CPicturePropPage` . На этих страницах отображается пользовательский интерфейс для свойств «цвет», «шрифт» и «изображение» соответственно.

Чтобы включить эти страницы свойств в элемент управления, добавьте их идентификаторы в код, который инициализирует массив идентификаторов страниц свойств элемента управления. В следующем примере этот код находится в файле реализации элемента управления (. CPP), инициализирует массив, чтобы он содержал все три страницы свойств и страницу свойств по умолчанию ( `CMyPropPage` в этом примере используется имя):

[!code-cpp[NVC_MFC_AxOpt#21](codesnippet/cpp/mfc-activex-controls-using-stock-property-pages_1.cpp)]

Обратите внимание, что количество страниц свойств в макросе BEGIN_PROPPAGEIDS равно 4. Представляет количество страниц свойств, поддерживаемое элементом управления ActiveX.

После внесения этих изменений перестройте проект. Теперь у элемента управления есть страницы свойств для свойств шрифт, изображение и цвет.

> [!NOTE]
> Если страницы свойств элемента управления "Стандартный" недоступны, это может быть вызвано тем, что библиотека DLL MFC (MFCxx.DLL) не была правильно зарегистрирована в текущей операционной системе. Это обычно происходит при установке Visual C++ в операционной системе, отличной от той, которая выполняется в данный момент.

> [!TIP]
> Если страницы свойств запасов не видны (см. предыдущее Примечание), зарегистрируйте библиотеку DLL, запустив RegSvr32.exe из командной строки с полным именем пути к библиотеке DLL.

## <a name="see-also"></a>См. также раздел

[Элементы управления ActiveX в MFC](mfc-activex-controls.md)<br/>
[Элементы управления ActiveX в MFC. Добавление свойств хранения](mfc-activex-controls-adding-stock-properties.md)
