---
description: 'Дополнительные сведения: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l'
title: scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
ms.date: 03/26/2019
api_name:
- wscanf_s
- _wscanf_s_l
- scanf_s
- _scanf_s_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wscanf_s
- _tscanf_s_l
- _wscanf_s_l
- scanf_s
- _tscanf_s
- _scanf_s_l
helpviewer_keywords:
- reading data [C++], from input streams
- buffers [C++], buffer overruns
- _scanf_s_l function
- _wscanf_s_l function
- tscanf_s_l function
- tscanf_s function
- scanf_s function
- data [C++], reading from input stream
- wscanf_s function
- _tscanf_s_l function
- _tscanf_s function
- scanf_s_l function
- formatted data [C++], from input streams
- wscanf_s_l function
- buffers [C++], avoiding overruns
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
ms.openlocfilehash: 0a23ed2958f29c8027fdd2530cbcb215cbb54ffa
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539351"
---
# <a name="scanf_s-_scanf_s_l-wscanf_s-_wscanf_s_l"></a>`scanf_s`, `_scanf_s_l`, `wscanf_s`, `_wscanf_s_l`

Считывает отформатированные данные из стандартного входного потока. Эти версии [ `scanf` , `_scanf_l` `wscanf` , `_wscanf_l` ](scanf-scanf-l-wscanf-wscanf-l.md) , имеют улучшения безопасности, как описано в разделе [функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
int scanf_s(
   const char *format [,
   argument]...
);
int _scanf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wscanf_s(
   const wchar_t *format [,
   argument]...
);
int _wscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Параметры

*`format`*<br/>
Строка управления форматированием.

*`argument`*<br/>
Необязательные аргументы.

*`locale`*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Возвращает число успешно преобразованных и назначенных полей. Возвращаемое значение не включает поля, которые были считаны, но не были назначены. Возвращаемое значение 0 указывает, что поля не были назначены. Возвращаемое значение — **EOF** для ошибки или, если символ конца файла или символ конца строки находится в первой попытке чтения символа. Если параметр *Format* является **`NULL`** указателем, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Значение, если выполнение может быть продолжено, **`scanf_s`** и **`wscanf_s`** Возврат **конца файла** и установка значения **`errno`** **`EINVAL`** .

Дополнительные сведения об этих и других кодах ошибок см. в статьях [ `errno` ,, `_doserrno` `_sys_errlist` и `_sys_nerr` ](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Комментарии

**`scanf_s`** Функция считывает данные из стандартного входного потока **`stdin`** и записывает их в *`argument`* . Каждый *`argument`* должен быть указателем на тип переменной, который соответствует спецификатору типа в *`format`* . Если копирование производится между перекрывающимися строками, поведение не определено.

**`wscanf_s`** — Это версия с расширенными символами **`scanf_s`** ; аргумент *Format* для **`wscanf_s`** — строка расширенных символов. **`wscanf_s`** и **`scanf_s`** ведут себя одинаково, если поток открыт в режиме ANSI. **`scanf_s`** в настоящее время не поддерживает входные данные из потока Юникода.

Версии этих функций с суффиксом **_l** идентичны, за исключением того, что они используют *`locale`* параметр вместо языкового стандарта текущего потока.

В отличие от **`scanf`** и **`wscanf`** , **`scanf_s`** и **`wscanf_s`** требует указать размеры буферов для некоторых параметров. Укажите размеры для всех **`c`** **`C`** **`s`** **`S`** параметров набора строк управления,,, или **`[]`** . Размер буфера в символах передается как дополнительный параметр. Он сразу следует за указателем на буфер или переменную. Например, при чтении строки размер буфера для этой строки передается следующим образом:

```C
char s[10];
scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9
```

Размер буфера включает значение терминала null. Поле спецификации ширины можно использовать, чтобы убедиться, что считываемый маркер соответствует буферу. Если размер токена слишком велик, в буфер не записывается, если не задана спецификация ширины.

> [!NOTE]
> Параметр size имеет тип **`unsigned`** , а не **`size_t`** . Используйте статическое приведение для преобразования **`size_t`** значения в **`unsigned`** 64-разрядные конфигурации сборки.

Параметр размера буфера описывает максимальное число символов, а не байтов. В этом примере ширина типа буфера не соответствует ширине описателя формата.

```C
wchar_t ws[10];
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));
```

**`S`** Описатель формата означает использование ширины символа, которая является "противоположной" шириной по умолчанию, поддерживаемой функцией. Ширина символа равна одному байту, но функция поддерживает двухбайтовые символы. Этот пример считывает строку длиной до девяти двухбайтовых символов и помещает их в буфер двухбайтовых символов. Символы обрабатываются как однобайтовые значения; первые два символа сохраняются в `ws[0]`, вторые два сохраняются в `ws[1]` и т. д.

В этом примере считывается один символ:

```C
char c;
scanf_s("%c", &c, 1);
```

При считывании нескольких символов для строк, не заканчивающихся нулем, для спецификации ширины и размера буфера используются целые числа.

```C
char c[4];
scanf_s("%4c", c, (unsigned)_countof(c)); // not null terminated
```

Дополнительные сведения см. в разделе [ `scanf` Спецификация ширины](../../c-runtime-library/scanf-width-specification.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|`TCHAR.H` ассемблер|`_UNICODE` & `_MBCS` не определено|`_MBCS` определяется|`_UNICODE` определяется|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tscanf_s`**|**`scanf_s`**|**`scanf_s`**|**`wscanf_s`**|
|**`_tscanf_s_l`**|**`_scanf_s_l`**|**`_scanf_s_l`**|**`_wscanf_s_l`**|

Дополнительные сведения см. в разделе [поля спецификации формата: `scanf` и `wscanf` функции](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**`scanf_s`**, **`_scanf_s_l`**|`<stdio.h>`|
|**`wscanf_s`**, **`_wscanf_s_l`**|`<stdio.h>` или `<wchar.h>`|

Консоль не поддерживается в приложениях универсальная платформа Windows (UWP). Стандартный поток обрабатывает **`stdin`** , **`stdout`** и **`stderr`** должен быть перенаправлен, прежде чем функции времени выполнения C смогут использовать их в приложениях UWP. Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_scanf_s.c
// This program uses the scanf_s and wscanf_s functions
// to read formatted input.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int      i,
            result;
   float    fp;
   char     c,
            s[80];
   wchar_t  wc,
            ws[80];

   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   printf( "The number of fields input is %d\n", result );
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,
           wc, s, ws);
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );
   wprintf( L"The number of fields input is %d\n", result );
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,
            c, wc, s, ws);
}
```

Эта программа создает следующие выходные данные для этих входных данных:

```Input
71 98.6 h z Byte characters
36 92.3 y n Wide characters
```

```Output
The number of fields input is 6
The contents are: 71 98.599998 h z Byte characters
The number of fields input is 6
The contents are: 36 92.300003 y n Wide characters
```

## <a name="see-also"></a>См. также раздел

[Поддержка операций с плавающей запятой](../../c-runtime-library/floating-point-support.md)<br/>
[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Локаль](../../c-runtime-library/locale.md)<br/>
[`fscanf`, `_fscanf_l`, `fwscanf`, `_fwscanf_l`](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[`printf`, `_printf_l`, `wprintf`, `_wprintf_l`](printf-printf-l-wprintf-wprintf-l.md)<br/>
[`sprintf`, `_sprintf_l`, `swprintf`, `_swprintf_l`, `__swprintf_l`](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[`sscanf`, `_sscanf_l`, `swscanf`, `_swscanf_l`](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
