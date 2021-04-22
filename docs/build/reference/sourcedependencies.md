---
title: /sourceDependencies (отчет о зависимостях на уровне источника)
description: Описывает параметр компилятора/СаурцедепенденЦиес в Microsoft C++.
ms.date: 04/13/2020
author: tylermsft
ms.author: twhitney
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: cf76d6e31abc7328b82b877bf6f3e2545efc7878
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381354"
---
# <a name="sourcedependencies-list-all-source-level-dependencies"></a>`/sourceDependencies` (Вывод списка всех зависимостей на уровне источника)

Этот параметр командной строки создает JSON-файл, который содержит подробные сведения о зависимостях исходного уровня, использованных во время компиляции. JSON-файл содержит список исходных зависимостей, включая следующие:

- Файлы заголовков. И непосредственно включены, и список заголовков, включаемых в эти заголовки.
- Используемый PCH (если **`/Yu`** указан).
- Имена импортированных модулей
- Пути к файлам и имена импортированных единиц заголовка. И непосредственно импортированы, и импортированы этими модулями и единицами заголовков.

Это предоставляет сведения, необходимые для создания модулей и единиц заголовков в правильном порядке зависимостей.

## <a name="syntax"></a>Синтаксис

> **`/sourceDependencies`** -\
> **`/sourceDependencies`***имя файла*\
> **`/sourceDependencies`***Каталог*

## <a name="arguments"></a>Аргументы

*`-`*\
Если указано одно тире, компилятор выдает JSON исходных зависимостей в `stdout` или в место, где будут перенаправляться выходные данные компилятора.

*`filename`*\
Компилятор записывает выходные данные исходной зависимости в указанное имя файла, которое может включать относительный или абсолютный путь.

*`directory`*\
Если аргумент является каталогом, компилятор создает исходные файлы зависимостей в указанном каталоге. Имя выходного файла основано на полном имени входного файла с добавленным *`.json`* расширением. Например, если файл, предоставленный компилятору, имеет значение *`main.cpp`* , то созданное выходное имя файла будет равно *`main.cpp.json`* .

## <a name="remarks"></a>Примечания

**`/sourceDependencies`** Параметр компилятора доступен начиная с Visual Studio 2019 версии 16,7. По умолчанию оно отключено.

При указании **`/MP`** параметра компилятора рекомендуется использовать **`/sourceDependencies`** с аргументом каталога. Если указать один аргумент имени файла, два экземпляра компилятора могут попытаться открыть выходной файл одновременно и вызвать ошибку. Дополнительные сведения о **`/MP`** см. в разделе [ `/MP` (сборка с несколькими процессами)](mp-build-with-multiple-processes.md).

При возникновении неустранимой ошибки компилятора сведения о зависимостях по-прежнему записываются в выходной файл.

Все пути к файлам отображаются в выходных данных в виде абсолютных путей.

### <a name="examples"></a>Примеры

С учетом следующего примера кода:

```cpp
// ModuleE.ixx:
export module ModuleE;
import ModuleC;
import ModuleD;
import <iostream>;
```

**`/sourceDependencies`** С остальными параметрами компилятора можно использовать:

> `cl ... /sourceDependencies output.json ... main.cpp`

где `...` представляет другие параметры компилятора. Эта командная строка создает JSON-файл *`output.json`* с содержимым, например:

```JSON
{
    "Version": "1.1",
    "Data": {
        "Source": "F:\\Sample\\myproject\\modulee.ixx",
        "ProvidedModule": "ModuleE",
        "Includes": [],
        "ImportedModules": [
            {
                "Name": "ModuleC",
                "BMI": "F:\\Sample\\Outputs\\Intermediate\\MyProject\\x64\\Debug\\ModuleC.ixx.ifc"
            },
            {
                "Name": "ModuleB",
                "BMI": "F:\\Sample\\Outputs\\Intermediate\\ModuleB\\x64\\Debug\\ModuleB.ixx.ifc"
            },
            {
                "Name": "ModuleD",
                "BMI": "F:\\Sample\\Outputs\\Intermediate\\MyProject\\x64\\Debug\\ModuleD.cppm.ifc"
            }
        ],
        "ImportedHeaderUnits": [
            {
                "Header": "f:\\visual studio 16 main\\vc\\tools\\msvc\\14.29.30030\\include\\iostream",
                "BMI": "F:\\Sample\\Outputs\\Intermediate\\HeaderUnits\\x64\\Debug\\iostream_W4L4JYGFJ3GL8OG9.ifc"
            },
            {
                "Header": "f:\\visual studio 16 main\\vc\\tools\\msvc\\14.29.30030\\include\\yvals_core.h",
                "BMI": "F:\\Sample\\Outputs\\Intermediate\\HeaderUnits\\x64\\Debug\\yvals_core.h.ifc"
            }
        ]
    }
}
```

Мы использовали `...` для сокращения путей в отчете. В отчете будут содержаться абсолютные пути. Полученные пути зависят от того, где компилятор находит зависимости. Если результаты являются непредвиденными, может потребоваться проверить параметры пути включения проекта.

`ProvidedModule` Выводит список имен экспортированных модулей или разделов модулей.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

Обычно это не должно быть задано в среде разработки Visual Studio. Он задается системой сборки.

## <a name="see-also"></a>См. также раздел

[Параметры компилятора КОМПИЛЯТОРОМ MSVC](compiler-options.md)<br/>
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md)<br/>
