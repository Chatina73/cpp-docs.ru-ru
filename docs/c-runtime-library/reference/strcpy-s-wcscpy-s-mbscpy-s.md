---
description: 'Дополнительные сведения: strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l'
title: strcpy_s, wcscpy_s, _mbscpy_s, _mbscpy_s_l
ms.date: 5/28/2020
api_name:
- wcscpy_s
- _mbscpy_s
- _mbscpy_s_l
- strcpy_s
- _o__mbscpy_s
- _o__mbscpy_s_l
- _o_strcpy_s
- _o_wcscpy_s
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strcpy_s
- _mbscpy_s
- _mbscpy_s_l
- _tcscpy_s
- wcscpy_s
helpviewer_keywords:
- strcpy_s function
- _tcscpy_s function
- _mbscpy_s function
- _mbscpy_s_l function
- copying strings
- strings [C++], copying
- tcscpy_s function
- wcscpy_s function
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
ms.openlocfilehash: 3cbfa2b2f8450adf07b2040fb2be0932377c9e37
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539569"
---
# <a name="strcpy_s-wcscpy_s-_mbscpy_s-_mbscpy_s_l"></a>`strcpy_s`, `wcscpy_` s, `_mbscpy_s` , `_mbscpy_s_l`

Копирует строку. Эти версии [ `strcpy` , `wcscpy` `_mbscpy` ](strcpy-wcscpy-mbscpy.md) обладают усовершенствованиями системы безопасности, как описано в разделе [функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **`_mbscpy_s`** и **`_mbscpy_s_l`** не могут использоваться в приложениях, выполняемых в среда выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t strcpy_s(
   char *dest,
   rsize_t dest_size,
   const char *src
);
errno_t wcscpy_s(
   wchar_t *dest,
   rsize_t dest_size,
   const wchar_t *src
);
errno_t _mbscpy_s(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src
);
errno_t _mbscpy_s_l(
   unsigned char *dest,
   rsize_t dest_size,
   const unsigned char *src,
   _locale_t locale
);
```

```cpp
// Template functions are C++ only:
template <size_t size>
errno_t strcpy_s(
   char (&dest)[size],
   const char *src
); // C++ only
template <size_t size>
errno_t wcscpy_s(
   wchar_t (&dest)[size],
   const wchar_t *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s(
   unsigned char (&dest)[size],
   const unsigned char *src
); // C++ only
template <size_t size>
errno_t _mbscpy_s_l(
   unsigned char (&dest)[size],
   const unsigned char *src,
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Параметры

*`dest`*<br/>
Расположение строкового буфера назначения.

*`dest_size`*<br/>
Размер буфера строк назначения в **`char`** единицах для узких и многобайтовых функций, а также **`wchar_t`** единиц для расширенных функций. Это значение должно быть больше нуля и не больше **`RSIZE_MAX`** . Убедитесь, что этот размер учетных записей завершается `NULL` после строки.

*`src`*<br/>
Исходная строка, завершающаяся нулем.

*`locale`*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Ноль в случае успешного выполнения; в противном случае — код ошибки.

### <a name="error-conditions"></a>Ситуации, которые могут привести к ошибке

|*`dest`*|*`dest_size`*|*`src`*|Возвращаемое значение|Содержимое *`dest`*|
|----------------------|------------------------|-----------------|------------------|----------------------------------|
|**`NULL`**|any|any|**`EINVAL`**|не изменено|
|any|any|**`NULL`**|**`EINVAL`**|*`dest[0]`* Задайте значение 0.|
|any|0 или слишком мал|any|**`ERANGE`**|*`dest[0]`* Задайте значение 0.|

## <a name="remarks"></a>Комментарии

**`strcpy_s`** Функция копирует содержимое в адрес *`src`* , включая завершающий символ null, в расположение, указанное параметром *`dest`* . Строка назначения должна быть достаточно велика для сохранения исходной строки и завершающего нуля. Поведение **`strcpy_s`** не определено, если строки источника и назначения перекрываются.

**`wcscpy_s`** — Это версия с расширенными символами **`strcpy_s`** , а **`_mbscpy_s`** — версия многобайтовых символов. Аргументы класса **`wcscpy_s`** — это строки расширенных символов; они **`_mbscpy_s`** **`_mbscpy_s_l`** являются строками многобайтовых символов. В остальном эти функции ведут себя одинаково. **`_mbscpy_s_l`** функция идентична **`_mbscpy_s`** , за исключением того, что использует переданный параметр языкового стандарта вместо текущего языкового стандарта. Дополнительные сведения см. на веб-сайте [`locale`](../../c-runtime-library/locale.md).

Если *`dest`* или *`src`* является пустым указателем или если размер строки назначения *`dest_size`* слишком мал, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают **`EINVAL`** и устанавливают значение, **`errno`** **`EINVAL`** Если *`dest`* или *`src`* является пустым указателем, и возвращают **`ERANGE`** и устанавливают **`errno`** в, **`ERANGE`** когда строка назначения слишком мала.

После успешного выполнения конечная строка всегда завершается нулем.

В C++ использование данных функций упрощено наличием шаблонных перегрузок, которые могут автоматически определять длину буфера, а также автоматически заменять более старые, незащищенные функции их новыми безопасными аналогами. Дополнительные сведения см. в разделе [Безопасные перегрузки шаблонов](../../c-runtime-library/secure-template-overloads.md).

Версии отладочной библиотеки этих функций сначала заполняют буфер 0xFE. Чтобы отключить это поведение, используйте [`_CrtSetDebugFillThreshold`](crtsetdebugfillthreshold.md) .

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|`TCHAR.H` ассемблер|`_UNICODE` & `_MBCS` не определено|`_MBCS` определяется|`_UNICODE` определяется|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_tcscpy_s`**|**`strcpy_s`**|**`_mbscpy_s`**|**`wcscpy_s`**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**`strcpy_s`**|`<string.h>`|
|**`wcscpy_s`**|`<string.h>` или `<wchar.h>`|
|**`_mbscpy_s`**|`<mbstring.h>`|

Эти функции относятся только к Microsoft. Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

В отличие от кода качества производства, этот пример вызывает безопасные строковые функции без проверки на наличие ошибок:

```C
// crt_strcpy_s.c
// Compile by using: cl /W4 crt_strcpy_s.c
// This program uses strcpy_s and strcat_s
// to build a phrase.

#include <string.h>     // for strcpy_s, strcat_s
#include <stdlib.h>     // for _countof
#include <stdio.h>      // for printf
#include <errno.h>      // for return values

int main(void)
{
    char stringBuffer[80];

    strcpy_s(stringBuffer, _countof(stringBuffer), "Hello world from ");
    strcat_s(stringBuffer, _countof(stringBuffer), "strcpy_s ");
    strcat_s(stringBuffer, _countof(stringBuffer), "and ");
    strcat_s(stringBuffer, _countof(stringBuffer), "strcat_s!");

    printf("stringBuffer = %s\n", stringBuffer);
}
```

```Output
stringBuffer = Hello world from strcpy_s and strcat_s!
```

При создании кода C++ версии шаблона могут быть проще в использовании.

```cpp
// crt_wcscpy_s.cpp
// Compile by using: cl /EHsc /W4 crt_wcscpy_s.cpp
// This program uses wcscpy_s and wcscat_s
// to build a phrase.

#include <cstring>  // for wcscpy_s, wcscat_s
#include <cstdlib>  // for _countof
#include <iostream> // for cout, includes <cstdlib>, <cstring>
#include <errno.h>  // for return values

int main(void)
{
    wchar_t stringBuffer[80];
    // using template versions of wcscpy_s and wcscat_s:
    wcscpy_s(stringBuffer, L"Hello world from ");
    wcscat_s(stringBuffer, L"wcscpy_s ");
    wcscat_s(stringBuffer, L"and ");
    // of course we can supply the size explicitly if we want to:
    wcscat_s(stringBuffer, _countof(stringBuffer), L"wcscat_s!");

    std::wcout << L"stringBuffer = " << stringBuffer << std::endl;
}
```

```Output
stringBuffer = Hello world from wcscpy_s and wcscat_s!
```

## <a name="see-also"></a>См. также раздел

[Управление строками](../../c-runtime-library/string-manipulation-crt.md) <br/>
[`strcat`, `wcscat`, `_mbscat`, `_mbscat_l`](strcat-wcscat-mbscat.md) <br/>
[`strcmp`, `wcscmp`, `_mbscmp`, `_mbscmp_l`](strcmp-wcscmp-mbscmp.md) <br/>
[`strncat_s`, `_strncat_s_l`, `wcsncat_s`, `_wcsncat_s_l`, `_mbsncat_s`, `_mbsncat_s_l`](strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md) <br/>
[`strncmp`, `wcsncmp`, `_mbsncmp`, `_mbsncmp_l`](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md) <br/>
[`strncpy_s`, `_strncpy_s_l`, `wcsncpy_s`, `_wcsncpy_s_l`, `_mbsncpy_s`, `_mbsncpy_s_l`](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md) <br/>
[`_strnicmp`, `_wcsnicmp`, `_mbsnicmp`, `_strnicmp_l`, `_wcsnicmp_l`, `_mbsnicmp_l`](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md) <br/>
[`strrchr`, `wcsrchr`, `_mbsrchr`, `_mbsrchr_l`](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md) <br/>
[`strspn`, `wcsspn`, `_mbsspn`, `_mbsspn_l`](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
