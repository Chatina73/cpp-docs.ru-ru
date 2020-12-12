---
description: Дополнительные сведения о printf_p параметрах позиционирования
title: Позиционные параметры printf_p
ms.date: 11/04/2016
api_location:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
ms.openlocfilehash: 2db76bc937e52b5945bf39cab1f47161fd3b162c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213433"
---
# <a name="printf_p-positional-parameters"></a>Позиционные параметры printf_p

Позиционные параметры предоставляют возможность определить число аргументов, которые будут заменены в поле в строке формата. Доступны следующие функции `printf` с позиционными параметрами:

| Непозиционные функции printf | Эквиваленты позиционных параметров |
|---|---|
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|
|[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|
|[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|
|[vprintf, _vprintf_l, vwprintf, _vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|
|[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|
|[vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \_ _vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|

## <a name="how-to-specify-positional-parameters"></a>Определение позиционных параметров

### <a name="parameter-indexing"></a>Индексирование параметров

Если позиционное форматирование отсутствует, поведение позиционных функций по умолчанию совпадает с поведением непозиционных. Позиционный параметр для форматирования задается символами `%n$` в начале описателя формата, где `n` — это позиция форматируемого параметра в списке параметров. Первый аргумент после строки форматирования имеет номер позиции 1. Для остальной части описателя формата действуют те же правила, что и для описателя формата `printf`. Дополнительные сведения см. в статье [Синтаксис описания формата: функции printf и wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

Ниже приведен пример позиционного форматирования:

```C
_printf_p("%1$s %2$s", "November", "10");
```

Результат выполнения:

```
November 10
```

Порядок используемых чисел может не совпадать с порядком аргументов. Например, такой формат строки является допустимым:

```C
_printf_p("%2$s %1$s", "November", "10");
```

Результат выполнения:

```
10 November
```

В отличие от традиционных строк форматирования, позиционные параметры можно использовать в строке формата несколько раз. например следующие.

```C
_printf_p("%1$d times %1$d is %2$d", 10, 100);
```

Результат выполнения:

```
10 times 10 is 100
```

Все аргументы должны использоваться в строке формата по меньшей мере один раз. Максимальное число разрешенных позиционных параметров в строке формата задается `_ARGMAX`.

### <a name="width-and-precision"></a>Ширина и точность

С помощью `*n$` можно указать позиционный параметр в качестве описателя ширины или точности, где `n` обозначает позицию нужного параметра в списке параметров. Позиция для значения ширины или точности должна быть указана сразу после символа \*. например следующие.

```C
_printf_p("%1$*2$s","Hello", 10);
```

или

```C
_printf_p("%2$*1$s", 10, "Hello");
```

### <a name="mixing-positional-and-non-positional-arguments"></a>Сочетание позиционных и непозиционных аргументов

Позиционные параметры не могут смешиваться с непозиционными параметрами в одной строке формата. Если используется позиционное форматирование, для всех описателей формата необходимо использовать позиционное форматирование. Однако `printf_p` и связанные функции еще поддерживают непозиционные параметры в строке формата, не содержащей позиционных параметров.

## <a name="example"></a>Пример

```C
// positional_args.c
// Build by using: cl /W4 positional_args.c
// Positional arguments allow the specification of the order
// in which arguments are consumed in a formatting string.

#include <stdio.h>

int main()
{
    int     i = 1,
            j = 2,
            k = 3;
    double  x = 0.1,
            y = 2.22,
            z = 333.3333;
    char    *s1 = "abc",
            *s2 = "def",
            *s3 = "ghi";

    // If positional arguments are unspecified,
    // normal input order is used.
    _printf_p("%d %d %d\n", i, j, k);

    // Positional arguments are numbers followed by a $ character.
    _printf_p("%3$d %1$d %2$d\n", i, j, k);

    // The same positional argument may be reused.
    _printf_p("%1$d %2$d %1$d\n", i, j);

    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);

    // Precision and width specifiers must be int types.
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);
}
```

```Output
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```

## <a name="see-also"></a>См. также раздел

[Синтаксис спецификации формата: функции printf и wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)
