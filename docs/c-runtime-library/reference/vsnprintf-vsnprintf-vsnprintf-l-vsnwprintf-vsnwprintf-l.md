---
title: vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l
description: Справочник по API для vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf и _vsnwprintf_l; который записывает форматированные выходные данные, используя указатель на список аргументов.
ms.date: 3/9/2021
api_name:
- _vsnprintf
- _vsnprintf_l
- _vsnwprintf
- _vsnwprintf_l
- _vsnprintf
- _vsnprintf;
- vsnprintf; _vsnprintf
- _vsnwprintf;
- _vsnprintf_l;
- _vsnwprintf_l;
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
- ntoskrnl.exe
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf
- _vsnwprintf
- _vsntprintf
- vsnprintf
- stdio/vsnprintf
- stdio/_vsnprintf
- stdio/_vsnprintf_l
- stdio/_vsnwprintf
- stdio/_vsnwprintf_l
- _vsnprintf_l
- _vsnwprintf_l
helpviewer_keywords:
- vsntprintf function
- _vsnwprintf_l function
- vsnwprintf_l function
- vsntprintf_l function
- _vsntprintf function
- _vsnprintf_l function
- vsnprintf function
- _vsntprintf_l function
- vsnprintf_l function
- _vsnwprintf function
- _vsnprintf function
- formatted text [C++]
- vsnwprintf function
ms.openlocfilehash: 870afc9cae241e61daebcac06089d01ac2fc3675
ms.sourcegitcommit: b04b39940b0c1e265f80fc1951278fdb05a1b30a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102622001"
---
# <a name="vsnprintf-_vsnprintf-_vsnprintf_l-_vsnwprintf-_vsnwprintf_l"></a>vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l

Записывают форматированные выходные данные с помощью указателя на список аргументов. Существуют более безопасные версии этих функций; см. раздел [vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l](vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md).

## <a name="syntax"></a>Синтаксис

```C
int vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf(
   char *buffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_l(
   char *buffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_l(
   wchar_t *buffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnprintf_l(
   char (&buffer)[size],
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_l(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Параметры

*двойной*<br/>
Место хранения выходных данных.

*count*<br/>
Наибольшее количество символов для записи.

*format*<br/>
Спецификация формата.

*аргптр*<br/>
Указатель на список аргументов.

*locale*<br/>
Используемый языковой стандарт.

Дополнительные сведения см. в разделе [Спецификации формата](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Возвращаемое значение

Функция **vsnprintf** возвращает количество записанных символов, не считая завершающего нуль символа. Если размер буфера, указанный в параметре *Count* , не достаточен для хранения выходных данных, указанных в *формате* и *аргптр*, возвращаемое значение **vsnprintf** — это количество символов, которые будут записаны без учета null, если *количество* было достаточно большим. Если возвращаемое значение больше, чем *Count* -1, выходные данные усекаются. Возвращаемое значение –1 указывает, что произошла ошибка кодирования.

Функции **_vsnprintf** и **_vsnwprintf** возвращают число записанных символов, если количество записываемых символов меньше или равно *Count*. Если число записываемых символов больше, чем *Count*, эти функции возвращают значение-1, указывающее на усечение выходных данных.

Значение, возвращаемое всеми этими функциями, не включает завершающее значение null, независимо от того, записано ли оно.

- Если параметр *Count* равен нулю, а *buffer* имеет **значение NULL**, возвращается число символов, которые будут записаны функциями. Значение не учитывает завершающее **значение NULL**. Этот результат можно использовать для выделения достаточного места в буфере для строки и ее завершающего символа NULL, а затем вызвать функцию снова для заполнения буфера.
- Если *Count* равно нулю, но значение *buffer* не **равно NULL**, запись не производится и функция возвращает `-1` .
- Если *параметр format* имеет **значение NULL** или если *буфер* равен **null** , а значение *Count* не равно нулю, эти функции вызывают обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают-1 **и устанавливают для** **еинвал** значение.

## <a name="remarks"></a>Remarks

Каждая из этих функций принимает указатель на список аргументов, затем форматирует данные и записывает *их в память, на которую* указывает *буфер*. Функция **vsnprintf** всегда записывает знак завершения null, даже если он усекает выходные данные. При использовании **_vsnprintf** и **_vsnwprintf** буфер будет завершаться нулем, только если в конце есть место (то есть если количество символов для записи меньше, чем *Count*).

> [!IMPORTANT]
> Чтобы предотвратить определенные виды угроз безопасности, убедитесь, что этот *Формат* не является определяемой пользователем строкой. Дополнительные сведения см. в разделе [Как избежать переполнения буфера](/windows/win32/SecBP/avoiding-buffer-overruns).
> Начиная с Windows 10 версии 2004 (сборка 19041), `printf` семейство функций выводит в соответствии с правилами IEEE 754 только округленные числа с плавающей запятой. В предыдущих версиях Windows полностью непредставленные числа с плавающей запятой, которые заканчиваются на "5", всегда округляются. IEEE 754 указывает, что они должны округляться до ближайшей четной цифры (также называемой "округление банка"). Например, оба значения `printf("%1.0f", 1.5)` и `printf("%1.0f", 2.5)` должны округляться в 2. Ранее 1,5 бы округлялись до 2 и 2,5, округляя до 3. Это изменение влияет только на точное представление чисел. Например, 2,35 (который, когда представлен в памяти, находится ближе к 2.35000000000000008), по-своему округляется до 2,4. Округление, выполненное этими функциями, теперь также учитывает режим округления с плавающей запятой, установленный [`fesetround`](fegetround-fesetround2.md) . Ранее округление всегда выбрало `FE_TONEAREST` поведение. Это изменение влияет только на программы, созданные с помощью Visual Studio 2019 версии 16,2 и более поздних версий. Чтобы использовать устаревшее поведение округления с плавающей точкой, свяжите с ["legacy_stdio_float_rounding. obj"](../link-options.md).

> [!NOTE]
> Чтобы убедиться в наличии места для завершающего значения NULL при вызове **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** и **_vsnwprintf_l**, убедитесь, что *число* строго меньше длины буфера, и инициализируйте буфер до значения null перед вызовом функции.
>
> Поскольку **vsnprintf** всегда записывает завершающее значение null, параметр *Count* может быть равен размеру буфера.

Начиная с UCRT в Visual Studio 2015 и Windows 10, **vsnprintf** больше не идентичен **_vsnprintf**. Функция **vsnprintf** соответствует стандарту C99. **_vnsprintf** сохраняется для обеспечения обратной совместимости с более старым кодом Visual Studio.

Версии этих функций с суффиксом **_l** идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо локали текущего потока.

В C++ эти функции имеют шаблонные перегрузки, которые вызывают более новые и безопасные аналоги этих функций. Дополнительные сведения см. в разделе [Безопасные перегрузки шаблонов](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf**|**_vsnprintf**|**_vsnprintf**|**_vsnwprintf**|
|**_vsntprintf_l**|**_vsnprintf_l**|**_vsnprintf_l**|**_vsnwprintf_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок (C)|Обязательный заголовок (C++)|
|-------------|---------------------------|-------------------------------|
|**vsnprintf**, **_vsnprintf** **_vsnprintf_l**|\<stdio.h>|\<stdio.h> или \<cstdio>|
|**_vsnwprintf**, **_vsnwprintf_l**|\<stdio.h> или \<wchar.h>|\<stdio.h>, \<wchar.h>, \<cstdio> или \<cwchar>|

Функции **_vsnprintf**, **_vsnprintf_l**, **_vsnwprintf** и **_vsnwprintf_l** являются специфичными для Microsoft. Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example-use-wide-characters-with-_vsnwprintf"></a>Пример. Использование расширенных символов с `_vsnwprintf()`

```C
// crt_vsnwprintf.c
// compile by using: cl /W3 crt_vsnwprintf.c

// To turn off error C4996, define this symbol:
#define _CRT_SECURE_NO_WARNINGS

#include <stdio.h>
#include <wtypes.h>

#define BUFFCOUNT (10)

void FormatOutput(LPCWSTR formatstring, ...)
{
    int nSize = 0;
    wchar_t buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    // Note: _vsnwprintf is deprecated; consider vsnwprintf_s instead
    nSize = _vsnwprintf(buff, BUFFCOUNT - 1, formatstring, args); // C4996
    wprintf(L"nSize: %d, buff: %ls\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput(L"%ls %ls", L"Hi", L"there");
    FormatOutput(L"%ls %ls", L"Hi", L"there!");
    FormatOutput(L"%ls %ls", L"Hi", L"there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

Поведение изменяется в том случае, если вместо этого использовать vsnprintf с узкими строковыми параметрами. Параметр *Count* может быть целым размером буфера, а возвращаемое значение — число символов, которые были бы записаны, если *количество* было достаточно большим:

## <a name="example-use-vsnprintf-with-narrow-strings"></a>Пример. Использование `vsnprintf()` с узкими строками

```C
// crt_vsnprintf.c
// compile by using: cl /W4 crt_vsnprintf.c
#include <stdio.h>
#include <stdarg.h> // for va_list, va_start
#include <string.h> // for memset

#define BUFFCOUNT (10)

void FormatOutput(char* formatstring, ...)
{
    int nSize = 0;
    char buff[BUFFCOUNT];
    memset(buff, 0, sizeof(buff));
    va_list args;
    va_start(args, formatstring);
    nSize = vsnprintf(buff, sizeof(buff), formatstring, args);
    printf("nSize: %d, buff: %s\n", nSize, buff);
    va_end(args);
}

int main() {
    FormatOutput("%s %s", "Hi", "there");   //  8 chars + null
    FormatOutput("%s %s", "Hi", "there!");  //  9 chars + null
    FormatOutput("%s %s", "Hi", "there!!"); // 10 chars + null
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: 10, buff: Hi there!
```

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Функции vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
[Синтаксис спецификации формата: функции printf и wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
