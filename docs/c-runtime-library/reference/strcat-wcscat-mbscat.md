---
description: 'Дополнительные сведения: strcat, wcscat, _mbscat'
title: strcat, wcscat, _mbscat
ms.date: 11/04/2016
api_name:
- _mbscat
- wcscat
- strcat
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbscat
- _ftcscat
- _tcscat
- strcat
- wcscat
helpviewer_keywords:
- concatenating strings
- mbscat function
- _ftcscat function
- _tcscat function
- ftcscat function
- strcat function
- strings [C++], appending
- _mbscat function
- tcscat function
- strings [C++], concatenating
- appending strings
- wcscat function
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
ms.openlocfilehash: 12ec6f6e0e9f940ef72d0aec742137843238c534
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292160"
---
# <a name="strcat-wcscat-_mbscat"></a>strcat, wcscat, _mbscat

Дополняет строку. Существуют более безопасные версии этих функций; см. раздел [strcat_s, wcscat_s, _mbscat_s](strcat-s-wcscat-s-mbscat-s.md).

> [!IMPORTANT]
> **_mbscat_s** нельзя использовать в приложениях, которые выполняются в среда выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
char *strcat(
   char *strDestination,
   const char *strSource
);
wchar_t *wcscat(
   wchar_t *strDestination,
   const wchar_t *strSource
);
unsigned char *_mbscat(
   unsigned char *strDestination,
   const unsigned char *strSource
);
template <size_t size>
char *strcat(
   char (&strDestination)[size],
   const char *strSource
); // C++ only
template <size_t size>
wchar_t *wcscat(
   wchar_t (&strDestination)[size],
   const wchar_t *strSource
); // C++ only
template <size_t size>
unsigned char *_mbscat(
   unsigned char (&strDestination)[size],
   const unsigned char *strSource
); // C++ only
```

### <a name="parameters"></a>Параметры

*стрдестинатион*<br/>
Строка назначения, завершающаяся нуль-символом.

*стрсаурце*<br/>
Исходная строка, завершающаяся символом NULL.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает строку назначения (*стрдестинатион*). Нет зарезервированных возвращаемых значений для указания ошибки.

## <a name="remarks"></a>Комментарии

Функция **strcat** добавляет *стрсаурце* в *стрдестинатион* и завершает результирующую строку символом NULL. Начальный символ *стрсаурце* перезаписывает завершающий нуль символ *стрдестинатион*. Поведение **strcat** не определено, если исходная и Целевая строки перекрываются.

> [!IMPORTANT]
> Так как **strcat** не проверяет наличие достаточного места в *стрдестинатион* перед добавлением *стрсаурце*, это может стать причиной переполнения буфера. Рекомендуется использовать вместо нее функцию [strncat](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md).

**wcscat** и **_mbscat** — это версии **strcat** для расширенных символов и многобайтовых символов. Аргументы и возвращаемое значение **wcscat** являются строками расширенных символов. **_mbscat** являются строками многобайтовых символов. В остальном эти три функции ведут себя идентично.

В C++ эти функции имеют шаблонные перегрузки, которые вызывают более новые и безопасные аналоги этих функций. Дополнительные сведения см. в разделе [Безопасные перегрузки шаблонов](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscat**|**strcat**|**_mbscat**|**wcscat**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**strcat**|\<string.h>|
|**wcscat**|\<string.h> или \<wchar.h>|
|**_mbscat**|\<mbstring.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

См. пример для [strcpy](strcpy-wcscpy-mbscpy.md).

## <a name="see-also"></a>См. также раздел

[Управление строками](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
