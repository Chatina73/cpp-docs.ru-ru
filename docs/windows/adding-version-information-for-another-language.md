---
title: Добавление сведений о версии для другого языка (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
ms.openlocfilehash: 6d79fb575817d5ba743e4efc460154eb03dca4f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534593"
---
# <a name="adding-version-information-for-another-language-c"></a>Добавление сведений о версии для другого языка (C++)

### <a name="to-add-version-information-for-another-language-new-info-block"></a>Добавление сведений о версии для другого языка (новый блок сведений)

1. Откройте ресурс сведений о версии, дважды щелкнув его в [представлении ресурсов](../windows/resource-view-window.md).

   > [!NOTE]
   > Если в проекте еще нет RC-файла, см. раздел [Создание нового файла описания ресурсов](../windows/how-to-create-a-resource-script-file.md).

2. Щелкните правой кнопкой мыши внутри таблицы сведений о версии и выберите в контекстном меню пункт **Создать блок сведений о версии** .

   Эта команда добавляет дополнительный блок сведений в текущий ресурс сведений о версии и открывает его соответствующие свойства в [окне "Свойства"](/visualstudio/ide/reference/properties-window).

3. В окне **Свойства** выберите для нового блока соответствующие язык и кодировку.

Сведения о добавлении ресурсов в управляемые проекты см. в разделе [ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework*. Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделе [Создание файлов ресурсов для приложений рабочего стола](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Сведения о глобализации и локализации ресурсов в управляемых приложениях, см. в разделе [Globalizing and Localizing .NET Framework Applications](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Требования

Win32

## <a name="see-also"></a>См. также

[Редактор сведений о версии](../windows/version-information-editor.md)<br/>
[Сведения о версии (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)