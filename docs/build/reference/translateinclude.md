---
title: /translateInclude (преобразование директив include в директивы Import)
description: 'Используйте параметр компилятора/Транслатеинклуде, чтобы обрабатывать директивы #include как операторы импорта, если доступна доступная единица заголовка.'
ms.date: 4/13/2021
author: tylermsft
ms.author: twhitney
f1_keywords:
- /translateInclude
helpviewer_keywords:
- /translateInclude
- Translate include directives into import directives
ms.openlocfilehash: e700e79c64be466e33e0ee698114c85eba1f7e18
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381312"
---
# <a name="translateinclude-translate-include-directives-into-import-directives"></a>`/translateInclude` (преобразование директив include в директивы import)

Указывает компилятору обрабатываться `#include` как `import` для тех заголовков, которые были предварительно встроены в файл блока заголовков ( `.ifc` ).

## <a name="syntax"></a>Синтаксис

> **`/translateInclude`**

## <a name="remarks"></a>Примечания

Для **`/translateInclude`** использования параметра компилятора необходимо включить параметр [/std: c + + Latest](std-specify-language-standard-version.md) . `/translateInclude` доступен начиная с Visual Studio 2019 версии 16,10 (Предварительная версия 2).

Этот **`/translateInclude`** параметр позволяет сделать следующее преобразование, в котором пример был `<vector>` встроен в блок заголовка с возможностью импорта:

```cpp
#include <vector>
```

Компилятор заменяет эту директиву следующим:

```cpp
import <vector>;
```

В КОМПИЛЯТОРОМ MSVC доступные единицы заголовков доступны в **`/headerUnit`** параметре, который сопоставляет заголовочный файл с соответствующей предварительно построенной единицей заголовка. Дополнительные сведения см. в разделе [ `/headerUnit` (указание места поиска файла единицы заголовка ( `.ifc` ) для указанного заголовка)](headerunit.md).

### <a name="examples"></a>Примеры

При наличии проекта, который ссылается на два файла заголовков и их единицы заголовка, перечисленные в этой таблице:

| Файл заголовка | Файл ИФК |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

И исходный *`.cpp`* файл, содержащий заголовки,

```cpp
#include "utils/util.h"
#include "app/app.h"

int main() { }
```

**`/translateInclude`** Параметр позволяет компилятору интерпретировать `#include` как `import` для файлов заголовков, которые имеют соответствующий скомпилированный файл заголовка ( *`.ifc`* ) и были указаны в командной строке с помощью `/headerUnit` параметра.

Если `#include` обнаруживается, что не имеет соответствующего блока заголовка, указанного с помощью `/headerUnit` переключателя, он обрабатывается препроцессором как обычная `#include` директива.

 Ниже приведен пример командной строки, которая преобразует директивы include для *`util.h`* и *`app.h`* в импортируемые единицы заголовков.

```CMD
cl /IC:\ /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

## <a name="to-set-this-compiler-option-in-visual-studio"></a>Установка параметра компилятора в Visual Studio

Чтобы включить `/translateInclude` эту функцию, установите в свойствах проекта параметр **преобразовать включает в импорт** :

1. В левой области страницы свойств проекта выберите **Свойства конфигурации**  >  **C/C++**  >  **Общие** .
1. Изменение раскрывающегося списка **перевод включен в импорт** в значение **Да**. 
 ![ диалоговое окно свойств проекта преобразование включается в импорт](../media/vs2019-translate-includes-option.png)


## <a name="see-also"></a>См. также раздел

[ `/headerUnit` (Используйте единицу заголовка ИФК)](headerunit.md). \
[`/exportHeader` (Создание единиц заголовка)](module-exportheader.md)\
[`/reference` (использование IFC для именованного модуля)](module-reference.md)
