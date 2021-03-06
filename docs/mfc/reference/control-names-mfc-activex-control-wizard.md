---
description: 'Дополнительные сведения: имена элементов управления, мастер элементов управления ActiveX MFC'
title: Имена элементов управления, мастер элементов управления ActiveX MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.ctl.names
helpviewer_keywords:
- MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
ms.openlocfilehash: 26d329465c13c3988a3e9d4d7ccd06294f3b2be3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345242"
---
# <a name="control-names-mfc-activex-control-wizard"></a>Имена элементов управления, мастер элементов управления ActiveX MFC

Укажите имена класса элемента управления и класса страницы свойств, имена типов и идентификаторы типов для элемента управления. За исключением **краткого имени**, все остальные поля можно изменять независимо друг от друга. Если изменить текст на **короткое имя**, это изменение будет отражено в именах всех остальных полей на этой странице. Этот принцип именования позволяет вам легко распознавать имена при разработке элементов управления.

- **короткое имя;**

   Укажите сокращенное имя элемента управления. По умолчанию это имя основано на имени проекта, которое вы указали в диалоговом окне **Новый проект** . Предоставляемое имя определяет имена классов, имена типов и идентификаторы типов, если эти поля не изменяются по отдельности.

- **Имя класса элемента управления**

   По умолчанию имя класса элемента управления основано на кратком имени, в `C` виде префикса и `Ctrl` суффикса. Например, если короткое имя элемента управления — `Price` , имя класса элемента управления — `CPriceCtrl` .

- **H файл элемента управления**

   По умолчанию имя файла заголовка основано на коротком имени, в `Ctrl` качестве суффикса и в `.h` качестве расширения файла. Например, если короткое имя элемента управления — `Price` , имя файла заголовка — `PriceCtrl.h` . Имя в этом поле должно совпадать с именем класса элемента управления.

- **Файл управления. cpp**

   По умолчанию имя файла заголовка основано на коротком имени, в `Ctrl` качестве суффикса и в `.cpp` качестве расширения файла. Например, если короткое имя элемента управления — `Price` , имя файла заголовка — `PriceCtrl.cpp` . Имя в этом поле должно соответствовать имени заголовка.

- **Имя типа элемента управления**

   По умолчанию имя типа элемента управления основано на кратком имени, за которым следует `Control` . Например, если короткое имя элемента управления имеет значение `Price` , то имя типа класса элемента управления — `Price Control` . Если изменить значение в этом поле, убедитесь, что имя указывает на наследование.

- **Идентификатор типа элемента управления**

   Задает идентификатор типа элемента управления для класса элемента управления. Элемент управления записывает эту строку в реестр при добавлении в проект. Приложения контейнера используют эту строку для создания экземпляра элемента управления.

   По умолчанию идентификатор типа элемента управления основан на имени проекта, которое вы указали в диалоговом окне **Новый проект** , и на короткое имя. Это имя должно совпадать с именем типа.

   По умолчанию идентификатор типа элемента управления выглядит следующим образом:

   *Имя_проекта. ShortName* CTRL. 1

   Если изменить короткое имя в этом диалоговом окне, идентификатор типа элемента управления будет выглядеть следующим образом:

   *Имя_проекта. невшортнаме* CTRL. 1

- **Имя класса с заданной наименей**

   По умолчанию имя класса страницы свойств основано на коротком имени, в `C` качестве префикса и `PropPage` суффиксе. Например, если краткое имя элемента управления — `Price` , имя класса страницы свойств — `CPricePropPage` . Это имя должно совпадать с именем класса элемента управления, к которому добавляется `PropPage` .

- **Файл с заданной. h**

   По умолчанию имя файла заголовка страницы свойств основано на коротком имени, а в качестве `PropPage` суффикса и в `.h` качестве расширения файла. Например, если короткое имя элемента управления — `Price` , то имя файла заголовка страницы свойств будет иметь значение `PricePropPage.h` . Это имя должно совпадать с именем класса.

- **Файл с заданной. cpp**

   По умолчанию имя файла реализации страницы свойств основано на коротком имени, а в качестве `PropPage` суффикса и в `.cpp` качестве расширения файла. Например, если короткое имя элемента управления — `Price` , то имя файла заголовка страницы свойств будет иметь значение `PricePropPage.cpp` . Это имя должно соответствовать имени файла заголовка.

- **Имя типа с предтипом**

   По умолчанию имя типа страницы свойств основано на кратком имени, за которым следует `Property Page` . Например, если короткое имя элемента управления — `Price` , то имя типа страницы свойств будет иметь значение `Price Property Page` . Если изменить значение в этом поле, убедитесь, что имя указывает на класс Control.

- **Идентификатор типа**

   Задает идентификатор класса страницы свойств. Элемент управления записывает эту строку в реестр, когда она применяется к проекту. Приложение-контейнер использует эту строку для создания экземпляра страницы свойств элемента управления.

   По умолчанию идентификатор типа страницы свойств основан на имени проекта, которое вы указали в диалоговом окне **Новый проект** , а также на короткое имя. Это имя должно совпадать с именем типа.

   По умолчанию идентификатор типа страницы свойств выглядит следующим образом:

   *Имя_проекта. ShortName* Заданная 1

   Если изменить короткое имя в этом диалоговом окне, отобразится следующий идентификатор типа страницы свойств:

   *Имя_проекта. невшортнаме* Заданная 1

## <a name="see-also"></a>См. также раздел

[Мастер элементов ActiveX MFC](../../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Параметры приложения, мастер элементов управления ActiveX MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)<br/>
[Параметры элементов управления, мастер элементов управления ActiveX MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)<br/>
[Типы файлов, создаваемых для проектов Visual Studio C++](../../build/reference/file-types-created-for-visual-cpp-projects.md)
