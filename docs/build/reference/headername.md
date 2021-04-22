---
title: /Хеадернаме (сборка единицы заголовка из указанного заголовка)
description: Используйте параметр компилятора/Хеадернаме, чтобы установить сопоставление между файлом заголовка и единицей заголовка для сборки.
ms.date: 04/13/2021
author: tylermsft
ms.author: twhitney
f1_keywords:
- /headerName
helpviewer_keywords:
- /headerName
- Use header unit IFC
ms.openlocfilehash: cb2b5f6e5a85eb3e14ab3b0139d79fc22b080c37
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381727"
---
# <a name="headername-build-a-header-unit-from-the-specified-header"></a>`/headerName` (Построение единицы заголовка из указанного заголовка)

Сборка указанного файла заголовка в единицу заголовка ( *`.ifc`* файл).

## <a name="syntax"></a>Синтаксис

> **`/headerName:quote`** `header-filename`\
> **`/headerName:angle`** `header-filename`

### <a name="arguments"></a>Аргументы

*`header-filename`*\
Имя файла заголовка, который компилятор должен компилировать в единицу заголовка ( *`.ifc`* файл).

## <a name="remarks"></a>Примечания

**`/headerName`** Параметр компилятора доступен начиная с Visual Studio 2019 версии 16,10 (Предварительная версия 2).

Для **`/headerName`** параметра компилятора во всех его формах требуется параметр [/std: c + + Latest](std-specify-language-standard-version.md) . \
При указании **`/headerName:{quote,angle}`** необходимо также указать [`/exportHeader`](module-exportheader.md) .

**`/headerName:quote`** выполняет поиск *`header-filename`* с использованием тех же правил, что `#include "header-name"` и, и создает его как единицу заголовка ( *`.ifc`* файл).
**`/headerName:angle`** выполняет поиск *`header-filename`* с использованием тех же правил, что `#include <header-name>` и, и создает его как единицу заголовка ( *`.ifc`* файл).

### <a name="examples"></a>Примеры

При наличии проекта, который ссылается на заголовочный файл, который он определяет `m.h` , параметр компилятора для его компиляции в единицу заголовка выглядит примерно так:

```Bash
$ cl /std:c++latest /exportHeader /headerName:quote m.h /Fom.h.obj
```

`/headerName:{quote,angle}`Параметр действует как флаг и не требует явно определенного аргумента. Допустимы следующие примеры:

```Bash
$ cl /std:c++latest /exportHeader /headerName:angle /MP /Fo.\ vector iostream algorithm
$ cl /std:c++latest /exportHeader /headerName:quote /MP /Fo.\ my-utilities.h a/b/my-core.h
```

В `/headerName` одной командной строке можно указать несколько параметров, и каждый аргумент после этого параметра будет обрабатываться с указанными *`header-filename`* правилами поиска. Следующий пример обрабатывает все заголовки как два предыдущих примера командной строки аналогичным образом. Он ищет заголовки, используя правила поиска, которые применяются, как если бы они были указаны как: `#include <vector>` , `#include "my-utilties.h"` и `#include "a/b/my-core.h"` :

```bash
$ cl /std:c++latest /exportHeader /headerName:angle /MP /Fo.\ vector iostream algorithm /headerName:quote my-utilities.h a/b/my-core.h
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

> [!NOTE]
> Пользователи обычно не задают этот параметр командной строки. Он задается системой сборки.

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите в раскрывающемся списке **Конфигурация** значение **все конфигурации**.

1. Выберите страницу свойств **Свойства конфигурации**  >  **C/C++**  >  **Командная строка** .

1. Измените свойство **Дополнительные параметры** , чтобы добавить *`/headerName`* Параметры и аргументы. Затем нажмите кнопку **ОК** или **Применить** , чтобы сохранить изменения.

## <a name="see-also"></a>См. также раздел

[`/exportHeader` (Создание единиц заголовка)](module-exportheader.md)\
[`/headerUnit` (Создание единиц заголовка)](headerunit.md)\
[`/reference` (Используйте именованный модуль ИФК)](module-reference.md)\
[`/translateInclude` (преобразование директив include в директивы import)](translateinclude.md)
