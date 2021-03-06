---
description: 'Дополнительные сведения о: Неустранимая ошибка C1010'
title: Неустранимая ошибка C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 2c6d57b2390f727e37d546d7077217e25db40fef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262533"
---
# <a name="fatal-error-c1010"></a>Неустранимая ошибка C1010

> непредвиденный конец файла при поиске предкомпилированного заголовка. Вы забыли добавить *имя*"#include" в источник?

## <a name="remarks"></a>Комментарии

Включаемый файл, указанный параметром [/Yu](../../build/reference/yu-use-precompiled-header-file.md) , отсутствует в файле исходного кода. Этот параметр включен по умолчанию во многих типах проектов Visual Studio C++. Файл включения по умолчанию, заданный этим параметром, — *PCH. h* или *stdafx. h* в Visual Studio 2017 и более ранних версий.

В среде Visual Studio используйте один из следующих методов, чтобы устранить эту ошибку:

- Убедитесь, что вы случайно не удалили, не переименовали или удалили файл заголовка *PCH. h* или исходный файл *PCH. cpp* из текущего проекта. (В более старых проектах эти файлы могут называться *stdafx. h* и *stdafx. cpp*.)

- Убедитесь, что заголовочный файл *PCH. h* или *stdafx. h* включен перед любыми другими директивами кода или препроцессора в исходных файлах. (В Visual Studio этот заголовочный файл задается свойством проекта **файла предкомпилированного заголовка** .)

- Вы можете отключить использование предкомпилированного заголовка. Если отключить предварительно скомпилированные заголовки, это может серьезно повлиять на производительность сборки.

### <a name="to-turn-off-precompiled-headers"></a>Отключение предкомпилированных заголовков

Чтобы отключить использование предкомпилированного заголовка в проекте, выполните следующие действия.

1. В окне **Обозреватель решений** щелкните правой кнопкой мыши имя проекта и выберите пункт **свойства** , чтобы открыть диалоговое окно **страницы свойств** проекта.

1. В раскрывающемся списке **Конфигурация** выберите **все конфигурации**.

1. Выберите   >  страницу свойств  >  **предварительно скомпилированных заголовков** свойств конфигурации C/C++.

1. В списке свойств выберите раскрывающийся список для свойства **предкомпилированного заголовка** , а затем выберите вариант **не использовать предкомпилированные заголовки**. Выберите **ОК** для сохранения внесенных изменений.

1. В окне **Обозреватель решений** щелкните правой кнопкой мыши исходный файл *PCH. cpp* в проекте. (В более ранних проектах файл может называться *stdafx. cpp*.) Выберите **исключить из проекта** , чтобы удалить его из сборки.

1. Используйте команду меню **Сборка**  >  **очистки решения** для каждой создаваемой конфигурации, чтобы удалить все файлы *project_name. pch* в промежуточных каталогах сборки.

## <a name="see-also"></a>См. также раздел

[Файлы предкомпилированных заголовков](../../build/creating-precompiled-header-files.md)\
[/Yc (создание файла предкомпилированного заголовка)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu (использование файла предкомпилированного заголовка)](../../build/reference/yu-use-precompiled-header-file.md)
