---
description: Дополнительные сведения см. в статье переменные среды CL
title: Переменные среды CL
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 1be95d2c2eddd204846fbcdc8675f28d71c25c0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179178"
---
# <a name="cl-environment-variables"></a>Переменные среды CL

Средство CL использует следующие переменные среды:

- CL и \_ CL_, если они определены. Средство CL добавляет параметры и аргументы, определенные в переменной среды CL, в аргументы командной строки и добавляет параметры и аргументы, определенные в \_ CL_, перед обработкой.

- INCLUDE, который должен указывать на подкаталог \инклуде в установке Visual Studio.

- Переменная среды LIBPATH, указывающая каталоги для поиска файлов метаданных, на которые ссылается [#using](../../preprocessor/hash-using-directive-cpp.md). Дополнительные сведения о LIBPATH см. в разделе [#using](../../preprocessor/hash-using-directive-cpp.md).

Можно задать \_ переменную среды CL или CL_ с помощью следующего синтаксиса:

> SET CL = [[*параметр*]... [*файл*]...] [/Link *Link-opt* ...] \
> SET \_ CL \_ = [[*параметр*]... [*файл*]...] [/Link *Link-opt* ...]

Дополнительные сведения о аргументах переменных среды CL и \_ CL_ см. в разделе [синтаксис компилятора компилятором MSVC Command-Line](compiler-command-line-syntax.md).

Эти переменные среды можно использовать для определения наиболее часто используемых файлов и параметров. Затем используйте командную строку, чтобы предоставить больше файлов и параметров для КОМПИЛЯТОРА в соответствии с конкретными целями. \_Длина переменных среды CL и CL_ ограничена 1024 символами (предельный размер входных данных командной строки).

Параметр [/d](d-preprocessor-definitions.md) нельзя использовать для определения символа, который использует знак равенства ( **=** ). Вместо этого можно использовать знак решетки ( **#** ) для знака равенства. Таким образом, можно использовать \_ переменные среды CL или CL_ для определения констант препроцессора с явными значениями, например `/DDEBUG#1` для определения `DEBUG=1` .

Дополнительные сведения см. в разделе [Set Environment Variables](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Примеры

Следующая команда является примером установки переменной среды CL:

> SET CL =/Zp2/Ox/И\ИНКЛУДЕ\МИНКЛС \ЛИБ\БИНМОДЕ. РАСШИРЕНИЕМ

Если задана переменная среды CL, при вводе `CL INPUT.C` в командной строке эффективная команда становится следующим:

> CL/Zp2/Ox/И\ИНКЛУДЕ\МИНКЛС \ЛИБ\БИНМОДЕ. ВХОДНЫЕ ДАННЫЕ OBJ. Ц

В следующем примере простая команда CL компилирует исходные файлы FILE1.c и FILE2.c, а затем компонует объектные файлы FILE1.obj, FILE2.obj и FILE3.obj:

> ЗАДАЙТЕ ПАРАМЕТР CL = FILE1. FILE2 В. Ц
> Задайте \_ CL_ = файл3. Расширением
> CL

Эти переменные среды выполняют вызов CL, так же как и в следующей командной строке:

> CL FILE1. FILE2 В. ФАЙЛ3 В. РАСШИРЕНИЕМ

## <a name="see-also"></a>См. также раздел

[Настройка параметров компилятора](compiler-command-line-syntax.md) \
[Параметры компилятора MSVC](compiler-options.md)
