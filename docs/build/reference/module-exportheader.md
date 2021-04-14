---
title: /Експорсеадер (создание единиц заголовка)
description: Используйте параметр компилятора/Експорсеадер, чтобы создать единицы заголовков модулей для указанных заголовочных или включаемых файлов.
ms.date: 04/13/2020
author: tylermsft
ms.author: twhitney
f1_keywords:
- /exportHeader
helpviewer_keywords:
- /exportHeader
- Create header units
ms.openlocfilehash: c116b3786b17f0a4574acff01b661a212767aa68
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381341"
---
# <a name="exportheader-create-header-units"></a>`/exportHeader` (создание единиц заголовков)

Указывает компилятору создавать единицы заголовка, заданные входными аргументами. Компилятор создает единицы заголовка в виде файлов ИФК ( *`.ifc`* ).

## <a name="syntax"></a>Синтаксис

> **`/exportHeader /headerName:angle`** *`header-name`*
> **`/exportHeader /headerName:quote`** *`header-name`*
> **`/exportHeader`** *`full path to header file`*

### <a name="arguments"></a>Аргументы

Аргумент для `/exportHeader` — это `/headerName` параметр командной строки, указывающий имя  *`header-name`* файла заголовка для экспорта.  

## <a name="remarks"></a>Примечания

**`/exportHeader`** доступен начиная с Visual Studio 2019 версии 16,10 (Предварительная версия 2).

Для **`/exportHeader`** использования параметра компилятора необходимо включить параметр [/std: c + + Latest](std-specify-language-standard-version.md) . 

Один **`/exportHeader`** параметр компилятора может указывать столько аргументов заголовка, сколько требуется для сборки. Их не нужно указывать отдельно.

Компилятор неявно включает новый препроцессор при использовании этого параметра. Это значит, что [`/Zc:preprocessor`](zc-preprocessor.md) компилятор добавляет в командную строку, если какая-либо из форм `/exportHeader` используется в командной строке. Чтобы отказаться от неявного `/Zc:preprocessor` , используйте: `/Zc:preprocessor-`

По умолчанию компилятор не создает объектный файл при компиляции блока заголовка. Чтобы создать объектный файл, укажите **`/Fo`** параметр компилятора. Дополнительные сведения см. в разделе [ `/Fo` (имя объектного файла)](fo-object-file-name.md).

Может оказаться полезным использовать дополнительный вариант **`/showResolvedHeader`** . **`/showResolvedHeader`** Параметр выводит абсолютный путь к файлу, *`header-name`* в который разрешается аргумент.

**`/exportHeader`** может одновременно управлять несколькими входами, даже в **`/MP`** . Мы рекомендуем использовать **`/ifcOutput  <directory>`** для создания отдельного *`.ifc`* файла для каждой компиляции.

### <a name="examples"></a>Примеры

Для создания единицы заголовка, например, `<vector>` может выглядеть следующим образом:

```cmd
cl … /std:c++latest /exportHeader /headerName:angle vector
```

Создание локального заголовка проекта, например, `"utils/util.h"` может выглядеть следующим образом:

```cmd
cl … /std:c++latest /exportHeader /headerName:quote util/util.h
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

Обычно это не должно быть задано в среде разработки Visual Studio. Он задается системой сборки.

## <a name="see-also"></a>См. также раздел

[`/headerUnit` (Используйте заголовок Unit ИФК)](headerunit.md)\
[`/reference` (Используйте именованный модуль ИФК)](module-reference.md)\
[`/translateInclude` (преобразование директив include в директивы import)](translateinclude.md)
