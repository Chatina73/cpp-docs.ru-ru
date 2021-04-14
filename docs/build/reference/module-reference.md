---
title: /Reference (использовать именованный модуль ИФК)
description: Используйте параметр компилятора/reference для создания единиц заголовков модулей для указанных заголовочных или включаемых файлов.
ms.date: 04/13/2020
f1_keywords:
- /reference
helpviewer_keywords:
- /reference
- Use named module IFC
ms.openlocfilehash: 00b8938e270ff6e6cd0fc29580b0e8b278888eaa
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381328"
---
# <a name="reference-use-named-module-ifc"></a>`/reference` (использование IFC для именованного модуля)

Указывает компилятору использовать существующую ИФК ( *`.ifc`* ) для текущей компиляции.

## <a name="syntax"></a>Синтаксис

> **`/reference`** *`module-name=filename`*\
> **`/reference`** *`filename`*

### <a name="arguments"></a>Аргументы

*`filename`*\
Имя файла, содержащего *данные ИФК*, которые представляют собой предварительно созданные сведения о модуле. Чтобы импортировать более одного модуля, включите отдельный **`/reference`** параметр для каждого файла.

*`module-name`*\
Допустимое имя экспортированного базового интерфейса основного модуля или полного имени секции модуля.

## <a name="remarks"></a>Примечания

В большинстве случаев этот параметр указывать не нужно, так как система проектов обнаруживает зависимости модулей в решении автоматически.

Для **`/reference`** использования параметра компилятора необходимо включить параметр [/std: c + + Latest](std-specify-language-standard-version.md) . Этот **`/reference`** параметр доступен начиная с Visual Studio 2019 версии 16,10 (Предварительная версия 2).

Если **`/reference`** аргумент имеет значение *`filename`* без *`module-name`* , то файл открывается во время выполнения, чтобы проверить *`filename`* имена аргументов на наличие определенного импорта. Это может привести к снижению производительности среды выполнения в сценариях с множеством **`/reference`** аргументов.

*`module-name`* Должно быть допустимым именем единицы интерфейса основного модуля или полным именем секции модуля. Примеры имен основных интерфейсов модулей включают:

- `M`
- `M.N.O`
- `MyModule`
- `my_module`

Примеры полных имен разделов модулей включают:

- `M:P`
- `M.N.O:P.Q`
- `MyModule:Algorithms`
- `my_module:algorithms`

Если ссылка на модуль создается с помощью *`module-name`* , другие модули в командной строке не просматриваются, если компилятор встречает это имя. Например, при наличии следующей командной строки:

```cmd
cl ... /std:c++latest /reference m.ifc /reference m=n.ifc
```

В приведенном выше случае, если компилятор видит `import m;` , *`m.ifc`* Поиск не выполняется.

### <a name="examples"></a>Примеры

Указанные три модуля, перечисленные в следующей таблице:

| Модуль | Файл ИФК |
|--|--|
| *`M`* | *`m.ifc`* |
| *`M:Part1`* | *`m-part1.ifc`* |
| *`Core.Networking`* | *`Networking.ifc`* |

Ссылочные параметры, использующие аргумент, будут выглядеть следующим образом *`filename`* :

```cmd
cl ... /std:c++latest /reference m.ifc /reference m-part.ifc /reference Networking.ifc
```

Ссылочные параметры, использующие, будут *`module-name=filename`* выглядеть следующим образом:

```cmd
cl ... /std:c++latest /reference m=m.ifc /reference M:Part1=m-part.ifc /reference Core.Networking=Networking.ifc
```

## <a name="see-also"></a>См. также раздел

[`/sourceDependencies:directives` (Список зависимостей модулей и заголовков)](sourcedependencies-directives.md)\
[`/headerUnit` (Используйте заголовок Unit ИФК)](headerunit.md)\
[`/exportHeader` (создание единиц заголовков)](module-exportheader.md)
