---
description: 'Дополнительные сведения: vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l'
title: vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l
ms.date: 3/9/2021
api_name:
- vfwprintf_s
- _vfprintf_s_l
- vfprintf_s
- _vfwprintf_s_l
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
- _vftprintf_s
- vfwprintf_s
- vfprintf_s
helpviewer_keywords:
- vfprintf_s_l function
- vfwprintf_s_l function
- vfwprintf_s function
- _vfprintf_s_l function
- _vfwprintf_s_l function
- vftprintf_s_l function
- vfprintf_s function
- _vftprintf_s_l function
- formatted text [C++]
- _vftprintf_s function
ms.openlocfilehash: 628339f83aa10e7711a1b6cc293f492ec34f8005
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102621403"
---
# <a name="vfprintf_s-_vfprintf_s_l-vfwprintf_s-_vfwprintf_s_l"></a>vfprintf_s, _vfprintf_s_l, vfwprintf_s, _vfwprintf_s_l

Записывают форматированные выходные данные с помощью указателя на список аргументов. Это версии функций [vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
int vfprintf_s(
   FILE *stream,
   const char *format,
   va_list argptr
);
int _vfprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale,
   va_list argptr
);
int vfwprintf_s(
   FILE *stream,
   const wchar_t *format,
   va_list argptr
);
int _vfwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Параметры

*вышестоящий*<br/>
Указатель на структуру **FILE**.

*format*<br/>
Спецификация формата.

*аргптр*<br/>
Указатель на список аргументов.

*locale*<br/>
Используемый языковой стандарт.

Дополнительные сведения см. в разделе [Спецификации формата](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Возвращаемое значение

**vfprintf_s** и **vfwprintf_s** возвращают число записанных символов, не включая завершающий нуль-символ, или отрицательное значение, если возникает ошибка вывода. Если *поток* или *Формат* является пустым указателем или строка формата содержит недопустимые символы форматирования, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, функции возвращают значение-1 и **задают значение** **еинвал**.

Дополнительные сведения об этих и других кодах ошибок см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Remarks

Каждая из этих функций принимает указатель на список аргументов, затем форматирует и записывает указанные данные в *поток*.

Эти функции отличаются от небезопасных версий только тем, что безопасные версии проверяют, что строка *формата* содержит допустимые символы форматирования.

**vfwprintf_s** — это версия **vfprintf_s** для расширенных символов; Эти две функции ведут себя одинаково, если поток открыт в режиме ANSI. **vfprintf_s** в настоящее время не поддерживает вывод в поток Юникода.

Версии этих функций с суффиксом **_l** идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо локали текущего потока.

> [!IMPORTANT]
> Убедитесь, что *format* не является строкой, определяемой пользователем. Дополнительные сведения см. в разделе [Как избежать переполнения буфера](/windows/win32/SecBP/avoiding-buffer-overruns).
> Начиная с Windows 10 версии 2004 (сборка 19041), `printf` семейство функций выводит в соответствии с правилами IEEE 754 только округленные числа с плавающей запятой. В предыдущих версиях Windows полностью непредставленные числа с плавающей запятой, которые заканчиваются на "5", всегда округляются. IEEE 754 указывает, что они должны округляться до ближайшей четной цифры (также называемой "округление банка"). Например, оба значения `printf("%1.0f", 1.5)` и `printf("%1.0f", 2.5)` должны округляться в 2. Ранее 1,5 бы округлялись до 2 и 2,5, округляя до 3. Это изменение влияет только на точное представление чисел. Например, 2,35 (который, когда представлен в памяти, находится ближе к 2.35000000000000008), по-своему округляется до 2,4. Округление, выполненное этими функциями, теперь также учитывает режим округления с плавающей запятой, установленный [`fesetround`](fegetround-fesetround2.md) . Ранее округление всегда выбрало `FE_TONEAREST` поведение. Это изменение влияет только на программы, созданные с помощью Visual Studio 2019 версии 16,2 и более поздних версий. Чтобы использовать устаревшее поведение округления с плавающей точкой, свяжите с ["legacy_stdio_float_rounding. obj"](../link-options.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vftprintf_s**|**vfprintf_s**|**vfprintf_s**|**vfwprintf_s**|
|**_vftprintf_s_l**|**_vfprintf_s_l**|**_vfprintf_s_l**|**_vfwprintf_s_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательные заголовки|
|-------------|---------------------|----------------------|
|**vfprintf_s**, **_vfprintf_s_l**|\<stdio.h> и \<stdarg.h>|\<varargs.h>*|
|**vfwprintf_s**, **_vfwprintf_s_l**|\<stdio.h> или \<wchar.h> , и \<stdarg.h>|\<varargs.h>*|

\* Требуется для совместимости с UNIX V.

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Функции vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
