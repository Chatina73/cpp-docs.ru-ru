---
description: Дополнительные сведения о pragma директиве hdrstop в Microsoft C/C++
title: hdrstop pragma
ms.date: 01/22/2021
f1_keywords:
- hdrstop_CPP
- vc-pragma.hdrstop
helpviewer_keywords:
- hdrstop pragma
- pragma, hdrstop
no-loc:
- pragma
ms.openlocfilehash: caeaeb4a44182b6ba2edfa385a1504fde998cc43
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713614"
---
# <a name="hdrstop-no-locpragma"></a>`hdrstop` pragma

Предоставляет более полный контроль над именами файлов с предварительной компиляцией и расположением, в котором сохраняется состояние компиляции.

## <a name="syntax"></a>Синтаксис

> **`#pragma hdrstop`** [("*имя_файла*")]

## <a name="remarks"></a>Примечания

Имя *файла является именем* предкомпилированного файла заголовка для использования или создания (в зависимости от того, указан ли [`/Yu`](../build/reference/yu-use-precompiled-header-file.md) [`/Yc`](../build/reference/yc-create-precompiled-header-file.md) параметр или). Если *имя файла* не содержит спецификацию пути, предполагается, что предкомпилированный заголовочный файл находится в том же каталоге, что и исходный файл.

Если файл C или C++ содержит объект **`hdrstop`** pragma при компиляции с параметром **`/Yc`** , компилятор сохраняет состояние компиляции вплоть до расположения pragma . Компилированное состояние любого кода, следующего за, pragma не сохраняется.

Используйте файл *filename* , чтобы присвоить имя файлу предкомпилированного заголовка, в котором сохраняется компилированное состояние. Пробел между **`hdrstop`** и *filename* является необязательным. Имя файла, указанное в параметре, **`hdrstop`** pragma является строкой и подчиняется ограничениям любой строки C или C++. В частности, необходимо заключить его в кавычки и использовать escape-символ (обратная косая черта **`\`** ), чтобы указать имена каталогов. Например:

```C
#pragma hdrstop( "c:\\projects\\include\\myinc.pch" )
```

Имя предкомпилированного файла заголовка определяется в соответствии со следующим правилам в порядке приоритета.

1. Аргумент для **`/Fp`** параметра компилятора

2. Аргумент *filename* для `#pragma hdrstop`

3. Базовое имя исходного файла с расширением PCH

Если ни один из **`/Yc`** параметров и не **`/Yu`** **`hdrstop`** pragma указывает имя файла, базовое имя исходного файла используется в качестве базового имени файла предкомпилированного заголовка.

Команды предварительной обработки также можно использовать для выполнения замены макроса.

```C
#define INCLUDE_PATH "c:\\progra~`1\\devstsu~1\\vc\\include\\"
#define PCH_FNAME "PROG.PCH"
.
.
.
#pragma hdrstop( INCLUDE_PATH PCH_FNAME )
```

Следующие правила управляют тем, где **`hdrstop`** pragma можно разместить.

- Она должна находится за пределами любых объявлений или определений данных или функций.

- Она должна задаваться в файле исходного кода, а не заголовка.

## <a name="example"></a>Пример

```C
#include <windows.h>                 // Include several files
#include "myhdr.h"

__inline Disp( char *szToDisplay )   // Define an inline function
{
    // ...                           // Some code to display string
}
#pragma hdrstop
```

В этом примере элемент **`hdrstop`** pragma появляется после включения двух файлов и определения встроенной функции. Это расположение, на первый взгляд, кажется нечетным pragma . Однако следует учесть, что с помощью параметров предварительной компиляции вручную **`/Yc`** и **`/Yu`** с помощью **`hdrstop`** pragma можно выполнить предварительную компиляцию всех исходных файлов или даже встроенного кода. Компилятор Майкрософт не ограничивает предварительную компиляцию только объявлений данных.

## <a name="see-also"></a>См. также раздел

[Директивы pragma и `__pragma` `_Pragma` Ключевые слова и](./pragma-directives-and-the-pragma-keyword.md)
