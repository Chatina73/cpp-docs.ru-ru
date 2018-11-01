---
title: Редактор строк (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.string.F1
helpviewer_keywords:
- String editor
- string tables
- string tables [C++], String editor
- string editing
- string editing, string tables
- resource editors [C++], String editor
- strings [C++], editing
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
ms.openlocfilehash: add153f84259985066397b6340fb4281a11beb17
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513663"
---
# <a name="string-editor-c"></a>Редактор строк (C++)

Таблица строк — это ресурс Windows, содержащий список идентификаторов, значений и заголовков для всех строк в приложении. Например, в таблице строк могут содержаться подсказки, выводимые в строке состояния.

В процессе разработки приложения можно использовать несколько таблиц строк для разных языков и ситуаций. Однако исполняемый модуль имеет только одну таблицу строк. Работающее приложение может ссылаться на несколько таблиц строк, если они помещены в разные библиотеки DLL.

Таблицы строк упрощают локализацию приложения на разные языки. Если все строки находятся в таблице строк, вы можете локализовать приложение, переведя строки (и другие ресурсы) и не меняя исходный код. Обычно это удобнее, чем вручную искать и заменять различные строки в исходных файлах.

С помощью редактора можно выполнять следующие действия:

- [искать одну или несколько строк](../windows/finding-a-string.md);

- быстро [вставлять новые записи](../windows/adding-or-deleting-a-string.md) в таблицу строк;

- [перемещать строку из одного файла ресурсов в другой;](../windows/moving-a-string-from-one-resource-file-to-another.md)

- [редактировать свойства ID, Value и Caption на месте](../windows/changing-the-properties-of-a-string.md) и немедленно просматривать изменения;

- [изменять свойство заголовка для нескольких строк;](../windows/changing-the-caption-property-of-multiple-strings.md)

- [добавлять форматирование или специальные символы в строку.](../windows/adding-formatting-or-special-characters-to-a-string.md)

   > [!NOTE]
   > Windows не разрешает создавать пустые таблицы строк. Если вы создадите таблицу строк, не содержащую записей, она будет автоматически удалена при сохранении файла ресурсов.

Сведения о добавлении ресурсов в управляемые проекты (предназначенные среда CLR), см. в разделе [ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index) в *руководства разработчика .NET Framework*. Сведения о вручную добавлять файлы ресурсов в управляемые проекты, осуществлять доступ к ресурсам, отображать статические ресурсы и присваивать строки ресурсов свойствам, см. в разделе [Пошаговое руководство: локализация форм Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Требования

Win32

## <a name="see-also"></a>См. также

[Редакторы ресурсов](../windows/resource-editors.md)<br/>
[Строки](https://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)<br/>
[Сведения о строках](/windows/desktop/menurc/about-strings)

