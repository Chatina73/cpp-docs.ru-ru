---
title: _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
ms.date: 11/04/2016
apiname:
- _mbsicoll_l
- _stricoll_l
- _mbsicoll
- _wcsicoll_l
- _wcsicoll
- _stricoll
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
- stricoll
- _stricoll
- _wcsicoll
- mbsicoll_l
- _mbsicoll
- _ftcsicoll
- wcsicoll_l
- _tcsicoll
- mbsicoll
- stricoll_l
helpviewer_keywords:
- code pages, using for string comparisons
- _ftcsicoll function
- _mbsicoll_l function
- _mbsicoll function
- mbsicoll function
- stricoll function
- tcsicoll function
- string comparison [C++], culture-specific
- _tcsicoll function
- _stricoll function
- _stricoll_l function
- _wcsicoll function
- mbsicoll_l function
- stricoll_l function
- strings [C++], comparing by code page
- ftcsicoll function
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
ms.openlocfilehash: bd2406751fd2855afd02743c98938e530398e7d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353668"
---
# <a name="stricoll-wcsicoll-mbsicoll-stricolll-wcsicolll-mbsicolll"></a>_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l

Сравнивает строки на основе данных языкового стандарта.

> [!IMPORTANT]
> **_mbsicoll** и **_mbsicoll_l** нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
int _stricoll(
   const char *string1,
   const char *string2
);
int _wcsicoll(
   const wchar_t *string1,
   const wchar_t *string2
);
int _mbsicoll(
   const unsigned char *string1,
   const unsigned char *string2
);
int _stricoll_l(
   const char *string1,
   const char *string2,
   _locale_t locale
);
int _wcsicoll_l(
   const wchar_t *string1,
   const wchar_t *string2,
   _locale_t locale
);
int _mbsicoll_l(
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
|**_NLSCMPERROR**|Произошла ошибка.|

Каждая из этих функций возвращает **_NLSCMPERROR**. Чтобы использовать **_NLSCMPERROR**, включают в себя \<string.h > или \<mbstring.h >. **_wcsicoll** может завершиться ошибкой, если *string1* или *string2* содержит коды расширенных символов, не последовательность сортировки. При возникновении ошибки, **_wcsicoll** может задать **errno** для **EINVAL**. Для проверки ошибки во время вызова **_wcsicoll**, задайте **errno** 0 и проверьте **errno** после вызова метода **_wcsicoll**.

## <a name="remarks"></a>Примечания

Каждая из этих функций сравнивает без учета регистра строки *string1* и *string2* согласно кодовой странице в настоящий момент. Эти функции следует использовать только в том случае, когда есть различие между порядком символов в наборе и лексикографическим порядком символов в текущей кодовой странице и данное различие представляет интерес во время сравнения строк.

**_stricmp** отличается от **_stricoll** в том, что **_stricmp** сравнения определяется **LC_CTYPE**, тогда как **_stricoll** сравнение осуществляется в соответствии с **LC_CTYPE** и **LC_COLLATE** категории языкового стандарта. Дополнительные сведения о **LC_COLLATE** категорию, см. в разделе [setlocale](setlocale-wsetlocale.md) и [категории языкового стандарта](../../c-runtime-library/locale-categories.md). В версиях этих функций без **_l** суффикс использования текущего языкового стандарта; версии с **_l** суффиксом идентичны, за исключением того, что они используют переданный языковой стандарт. Для получения дополнительной информации см. [Locale](../../c-runtime-library/locale.md).

Все эти функции проверяют свои параметры. Если параметр *string1* или *string2* являются **NULL** вызывается указатели, обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают **_NLSCMPERROR** и задайте **errno** для **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsicoll**|**_stricoll**|**_mbsicoll**|**_wcsicoll**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_stricoll**, **_stricoll_l**|\<string.h>|
|**_wcsicoll**, **_wcsicoll_l**|\<wchar.h>, \<string.h>|
|**_mbsicoll**, **_mbsicoll_l**|\<mbstring.h>|

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
