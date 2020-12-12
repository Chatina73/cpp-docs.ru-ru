---
description: 'Дополнительные сведения: printf_s, _printf_s_l, wprintf_s, _wprintf_s_l'
title: printf_s, _printf_s_l, wprintf_s, _wprintf_s_l
ms.date: 11/04/2016
api_name:
- _printf_s_l
- wprintf_s
- _wprintf_s_l
- printf_s
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
- wprintf_s
- printf_s
helpviewer_keywords:
- wprintf_s function
- tprintf_s function
- _tprintf_s function
- printf_s_l function
- printf_s function
- _printf_s_l function
- printf function, format specification fields
- printf function, using
- _tprintf_s_l function
- wprintf_s_l function
- formatted text [C++]
- tprintf_s_l function
- _wprintf_s_l function
ms.assetid: 044ebb2e-5cc1-445d-bb4c-f084b405615b
ms.openlocfilehash: d26f18a45f218f6d1921a8603ffed15df24dcc90
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209481"
---
# <a name="printf_s-_printf_s_l-wprintf_s-_wprintf_s_l"></a>printf_s, _printf_s_l, wprintf_s, _wprintf_s_l

Выводит форматированные выходные данные в стандартный поток вывода. Это версии функций [printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
int printf_s(
   const char *format [,
   argument]...
);
int _printf_s_l(
   const char *format,
   locale_t locale [,
   argument]...
);
int wprintf_s(
   const wchar_t *format [,
   argument]...
);
int _wprintf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument]...
);
```

### <a name="parameters"></a>Параметры

*format*<br/>
Формат объекта.

*argument*<br/>
Необязательные аргументы.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Возвращает число выведенных символов или отрицательное значение в случае ошибки.

## <a name="remarks"></a>Комментарии

Функция **printf_s** форматирует и выводит последовательность символов и значений в стандартный выходной поток, **stdout**. Если аргументы следуют за строкой *формата* , строка *формата* должна содержать спецификации, определяющие формат выходных данных для аргументов.

Основное различие между **printf_s** и **printf** состоит в том, что **printf_s** проверяет строку формата на допустимость символов форматирования, тогда как **printf** проверяет, является ли строка формата пустым указателем. Если проверка завершается с ошибкой, то вызывается обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, функция **возвращает значение-1 и устанавливает** для **еинвал**.

Сведения о кодах ошибок, а именно об ошибках, см **. в разделе** _doserrno, код ошибки [, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

поведение **printf_s** и **fprintf_s** идентично, за исключением того, что **printf_s** записывает выходные данные в **stdout** , а не в назначение **файла** типа. Дополнительные сведения см. в разделе [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md).

**wprintf_s** — это версия **printf_s** для расширенных символов; *Format* — это строка расширенных символов. поведение **wprintf_s** и **printf_s** идентично, если поток открыт в режиме ANSI. **printf_s** в настоящее время не поддерживает вывод в поток Юникода.

Версии этих функций с суффиксом **_l** идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо локали текущего потока.

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tprintf_s**|**printf_s**|**printf_s**|**wprintf_s**|
|**_tprintf_s_l**|**_printf_s_l**|**_printf_s_l**|**_wprintf_s_l**|

Аргумент *Format* включает в себя обычные символы, escape-последовательности и (если аргументы следуют *формату*) спецификации формата. Обычные символы и escape-последовательности копируются в **stdout** в порядке их отображения. Например, в строке

```C
printf_s("Line one\n\t\tLine two\n");
```

выводятся следующие выходные данные

```Output
Line one
        Line two
```

[Спецификации формата](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) всегда начинаются со знака процента ( **%** ) и считываются слева направо. Когда **printf_s** встречает первую спецификацию формата (если она есть), она преобразует значение первого аргумента после *Format* и выводит его соответствующим образом. Вторая спецификация формата вызывает преобразование второго аргумента и его вывод и т. д. Если число аргументов превышает количество спецификаций формата, лишние аргументы игнорируются. Если число аргументов меньше количества спецификаций формата, результаты будут не определены.

> [!IMPORTANT]
> Убедитесь, что *format* не является строкой, определяемой пользователем.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**printf_s**, **_printf_s_l**|\<stdio.h>|
|**wprintf_s**, **_wprintf_s_l**|\<stdio.h> или \<wchar.h>|

Консоль не поддерживается в приложениях универсальная платформа Windows (UWP). Стандартные дескрипторы потока, связанные с консолью, **stdin**, **stdout** и **stderr**, должны быть перенаправляться до того, как функции времени выполнения C смогут использовать их в приложениях UWP. Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_printf_s.c
/* This program uses the printf_s and wprintf_s functions
* to produce formatted output.
*/

#include <stdio.h>

int main( void )
{
   char   ch = 'h', *string = "computer";
   int    count = -9234;
   double fp = 251.7366;
   wchar_t wch = L'w', *wstring = L"Unicode";

   /* Display integers. */
   printf_s( "Integer formats:\n"
           "   Decimal: %d  Justified: %.6d  Unsigned: %u\n",
           count, count, count );

   printf_s( "Decimal %d as:\n   Hex: %Xh  C hex: 0x%x  Octal: %o\n",
            count, count, count, count );

   /* Display in different radixes. */
   printf_s( "Digits 10 equal:\n   Hex: %i  Octal: %i  Decimal: %i\n",
            0x10, 010, 10 );

   /* Display characters. */

   printf_s("Characters in field (1):\n%10c%5hc%5C%5lc\n", ch, ch, wch, wch);
   wprintf_s(L"Characters in field (2):\n%10C%5hc%5c%5lc\n", ch, ch, wch, wch);

   /* Display strings. */

   printf_s("Strings in field (1):\n%25s\n%25.4hs\n   %S%25.3ls\n",
   string, string, wstring, wstring);
   wprintf_s(L"Strings in field (2):\n%25S\n%25.4hs\n   %s%25.3ls\n",
       string, string, wstring, wstring);

   /* Display real numbers. */
   printf_s( "Real numbers:\n   %f %.2f %e %E\n", fp, fp, fp, fp );

   /* Display pointer. */
   printf_s( "\nAddress as:   %p\n", &count);

}
```

### <a name="sample-output"></a>Пример выходных данных

```Output
Integer formats:
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062
Decimal -9234 as:
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756
Digits 10 equal:
   Hex: 16  Octal: 8  Decimal: 10
Characters in field (1):
         h    h    w    w
Characters in field (2):
         h    h    w    w
Strings in field (1):
                 computer
                     comp
   Unicode                      Uni
Strings in field (2):
                 computer
                     comp
   Unicode                      Uni
Real numbers:
   251.736600 251.74 2.517366e+002 2.517366E+002

Address as:   0012FF78
```

## <a name="see-also"></a>См. также раздел

[Поддержка операций с плавающей запятой](../../c-runtime-library/floating-point-support.md)<br/>
[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Локаль](../../c-runtime-library/locale.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[Функции vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
