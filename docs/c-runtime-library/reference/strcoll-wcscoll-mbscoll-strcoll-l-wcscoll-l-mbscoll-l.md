---
title: strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
ms.date: 11/04/2016
apiname:
- wcscoll
- _mbscoll
- _mbscoll_l
- strcoll
- _strcoll_l
- _wcscoll_l
apilocation:
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
apitype: DLLExport
f1_keywords:
- wcscoll
- _mbscoll
- _tcscoll
- _ftcscoll
helpviewer_keywords:
- code pages, using for string comparisons
- mbscoll function
- wcscoll_l function
- ftcscoll function
- wcscoll function
- _strcoll_l function
- tcscoll function
- _ftcscoll function
- _tcscoll function
- _wcscoll_l function
- _mbscoll function
- strcoll_l function
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
ms.openlocfilehash: ae72b4cbb2b001a332d41a74883a0e2a9d20a181
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50625191"
---
# <a name="strcoll-wcscoll-mbscoll-strcolll-wcscolll-mbscolll"></a>strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l

Сравнивает строки с помощью текущего языкового стандарта или заданной категории состояния преобразования LC_COLLATE.

> [!IMPORTANT]
> **_mbscoll** и **_mbscoll_l** нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
int strcoll(
   const char *string1,
   const char *string2
);
int wcscoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbscoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _strcoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int wcscoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbscoll_l(
   const unsigned char *string1,
   const unsigned char *string2,
   _locale_t locale
);
```

### <a name="parameters"></a>Параметры

*string1*, *string2*<br/>
Строки с завершающим нулем для сравнения.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает значение, показывающее связь между *string1* для *string2*, как показано ниже.

|Возвращаемое значение|Отношение string1 к string2|
|------------------|----------------------------------------|
|< 0|*string1* меньше, чем *string2*|
|0|*string1* идентичен *string2*|
|> 0|*string1* больше, чем *string2*|

Каждая из этих функций возвращает **_NLSCMPERROR** при возникновении ошибки. Чтобы использовать **_NLSCMPERROR**, включить любой из СТРОК. H или MBSTRING. З. **wcscoll** может завершиться ошибкой, если *string1* или *string2* — **NULL** или содержит коды расширенных символов, не последовательность сортировки. При возникновении ошибки, **wcscoll** может задать **errno** для **EINVAL**. Для проверки ошибки во время вызова **wcscoll**, задайте **errno** 0 и проверьте **errno** после вызова метода **wcscoll**.

## <a name="remarks"></a>Примечания

Каждая из этих функций сравнивает с учетом регистра строки *string1* и *string2* согласно кодовой странице в настоящий момент. Эти функции следует использовать только в том случае, когда есть различие между порядком символов в наборе и лексикографическим порядком символов в текущей кодовой странице и данное различие представляет интерес во время сравнения строк.

Все эти функции проверяют свои параметры. Если параметр *string1* или *string2* является пустым указателем, или если *число* больше, чем **INT_MAX**, вызывается обработчик недопустимого параметра , как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md) . Если выполнение может быть продолжено, эти функции возвращают **_NLSCMPERROR** и задайте **errno** для **EINVAL**.

Сравнение двух строк — это операция, зависящая от языкового стандарта, так как каждый языковой стандарт теперь имеет разные правила для сортировки символов. В версиях этих функций без **_l** суффикс используется языковой стандарт текущего потока для данного поведения, зависящего от языкового стандарта; версии с **_l** суффиксом идентичны соответствующей функции без суффикса, за исключением случаев, они используют языковой стандарт, переданный в качестве параметра вместо текущего языкового стандарта. Для получения дополнительной информации см. [Locale](../../c-runtime-library/locale.md).

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcscoll**|**strcoll**|**_mbscoll**|**wcscoll**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**strcoll**|\<string.h>|
|**wcscoll**|\<wchar.h>, \<string.h>|
|**_mbscoll**, **_mbscoll_l**|\<mbstring.h>|
|**_strcoll_l**|\<string.h>|
|**_wcscoll_l**|\<wchar.h>, \<string.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Языковой стандарт](../../c-runtime-library/locale.md)<br/>
[Операции со строками](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Функции strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
