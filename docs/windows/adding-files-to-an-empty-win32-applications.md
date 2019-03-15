---
title: Добавление файлов в пустые приложения Win32
ms.date: 11/04/2016
helpviewer_keywords:
- empty projects [C++], adding files
- projects [C++], adding items
- blank projects
- files [C++], adding to projects
ms.assetid: 070098e8-0396-49fe-a697-3daa2f1be6de
ms.openlocfilehash: 8facd371ad2dddbb8ce239af5ca536b21a606807
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818210"
---
# <a name="adding-files-to-an-empty-win32-applications"></a>Добавление файлов в пустые приложения Win32

### <a name="to-add-your-files-to-an-empty-windows-desktop-application"></a>Добавление файлов в пустое классическое приложение Windows

1. Выберите каталог в **обозревателе решений**.

2. Щелкните правой кнопкой мыши имя каталога, выберите в контекстном меню команду **Добавить** , а затем выберите пункт **Существующий элемент**.

3. В диалоговом окне **Добавление существующего элемента**перейдите к файлам, которые нужно добавить в проект.

4. Нажмите кнопку **ОК**.

Чтобы добавить файлы, ни источник, заголовок или файлы ресурсов в проект, щелкните правой кнопкой мыши **решение** узел в **обозревателе решений** и добавьте файлы в проект таким же образом. Объект **Разное** будет создана папка для хранения других файлов в проекте.

> [!NOTE]
> Прежде чем приступать к сборке проекта, необходимо будет указать параметры сборки этих файлов, чтобы они были корректным образом включены в готовое приложение. Дополнительные сведения см. в разделах [Задание параметров проекта при помощи страниц свойств](../build/reference/property-pages-visual-cpp.md) и [Сборка программы C/C++](../build/building-c-cpp-programs.md).

## <a name="see-also"></a>См. также

[Создание пустого классического приложения Windows](../windows/creating-an-empty-windows-desktop-application.md)
