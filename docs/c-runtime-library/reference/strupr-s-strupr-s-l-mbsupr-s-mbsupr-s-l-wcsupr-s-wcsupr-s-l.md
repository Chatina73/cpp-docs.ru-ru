---
title: _strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l
ms.date: 4/2/2020
api_name:
- _strupr_s
- _strupr_s_l
- _mbsupr_s
- _wcsupr_s_l
- _mbsupr_s_l
- _wcsupr_s
- _o__mbsupr_s
- _o__mbsupr_s_l
- _o__strupr_s
- _o__strupr_s_l
- _o__wcsupr_s
- _o__wcsupr_s_l
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strupr_s
- mbsupr_s
- wcsupr_s
- _mbsupr_s_l
- mbsupr_s_l
- wcsupr_s_l
- _wcsupr_s
- _tcsupr_s_l
- _mbsupr_s
- _tcsupr_s
- strupr_s_l
- _wcsupr_s_l
- _strupr_s
- _strupr_s_l
helpviewer_keywords:
- mbsupr_s_l function
- strupr_s_l function
- _wcsupr_s_l function
- _tcsupr_s_l function
- mbsupr_s function
- _wcsupr_s function
- uppercase, converting strings to
- tcsupr_s function
- string conversion [C++], case
- strupr_s function
- wcsupr_s_l function
- _mbsupr_s function
- _mbsupr_s_l function
- _strupr_s_l function
- tcsupr_s_l function
- strings [C++], case
- converting case, CRT functions
- _tcsupr_s function
- strings [C++], converting case
- _strupr_s function
- wcsupr_s function
ms.assetid: 82d3a273-9f6f-4a26-9560-919d891e4581
ms.openlocfilehash: 2fd90f462787df739f41a9e8e10f84d2fc52c456
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362986"
---
# <a name="_strupr_s-_strupr_s_l-_mbsupr_s-_mbsupr_s_l-_wcsupr_s-_wcsupr_s_l"></a>_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l

Преобразуют буквы в строке в прописные с использованием текущего или переданного языкового стандарта. Эти версии функций [_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) отличаются повышенной безопасностью (см. раздел [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md)).

> [!IMPORTANT]
> **_mbsupr_s** и **_mbsupr_s_l** не могут быть использованы в приложениях, выполняемых в Windows Runtime. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t _strupr_s(
   char *str,
   size_t numberOfElements
);
errno_t _wcsupr_s(
   wchar_t * str,
   size_t numberOfElements
);
errno_t _strupr_s_l(
   char * str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _wcsupr_s_l(
   wchar_t * str,
   size_t numberOfElements,
   _locale_t locale
);
errno_t _mbsupr_s(
   unsigned char *str,
   size_t numberOfElements
);
errno_t _mbsupr_s_l(
   unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
template <size_t size>
errno_t _strupr_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wcsupr_s(
   wchar_t (&str)[size]
); // C++ only
template <size_t size>
errno_t _strupr_s_l(
   char (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _wcsupr_s_l(
   wchar_t (&str)[size],
   _locale_t locale
); // C++ only
template <size_t size>
errno_t _mbsupr_s(
   unsigned char (&str)[size]
); // C++ only
template <size_t size>
errno_t _mbsupr_s_l(
   unsigned char (&str)[size],
   _locale_t locale
); // C++ only
```

### <a name="parameters"></a>Параметры

*Ул*<br/>
Строка для преобразования букв.

*numberOfElements*<br/>
Размер буфера.

*Языкового стандарта*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Нуль в случае успеха или ненулевой код ошибки в случае ошибки.

Эти функции проверяют свои параметры. Если *str* является указателем **NULL,** вызывается обработчик параметров недействительного, как описано в [проверке параметра.](../../c-runtime-library/parameter-validation.md) Если выполнение разрешено продолжать, функции возвращают **EINVAL** и устанавливают **errno** **в EINVAL.** Если *numberOfElements* меньше длины строки, функции возвращают **ERANGE** и устанавливают **errno** в **ERANGE.**

## <a name="remarks"></a>Remarks

Функция **_strupr_s** преобразует, на месте, каждая нижняя буква в *str* к uppercase. **_wcsupr_s** является широкохарактерным вариантом **_strupr_s.** **_mbsupr_s** является многобайтной версией символов **_strupr_s.**

Преобразование определяется **LC_CTYPE** параметром категории локализовать. Другие символы не изменяются. Для получения дополнительной информации о **LC_CTYPE,** [см. setlocale](setlocale-wsetlocale.md). Версии этих функций без **_l** суффикса используют текущий локали; видения с **_l** суффикс идентичны, за исключением того, что они используют локали, передаваемую вместо этого. Для получения дополнительной информации см. [Locale](../../c-runtime-library/locale.md).

В C++ использование данных функций упрощено наличием шаблонных перегрузок; перегруженные методы могут автоматически определять длину буфера (что исключает необходимость указания аргумента с размером буфера), а также они могут автоматически заменять более старые, незащищенные функции их новыми безопасными аналогами. Дополнительные сведения см. в разделе [Безопасные перегрузки шаблонов](../../c-runtime-library/secure-template-overloads.md).

Отладка библиотеки версии этих функций сначала заполнить буфер с 0xFE. Чтобы отключить это поведение, используйте [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

По умолчанию глобальное состояние этой функции приспозировано к приложению. Чтобы изменить это, [см. Глобальное состояние в CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsupr_s**|**_strupr_s**|**_mbsupr_s**|**_wcsupr_s**|
|**_tcsupr_s_l**|**_strupr_s_l**|**_mbsupr_s_l**|**_wcsupr_s_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_strupr_s**, **_strupr_s_l**|\<string.h>|
|**_wcsupr_s,** **_wcsupr_s_l,** **_mbsupr_s,** **_mbsupr_s_l**|\<string.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

См. примеры [_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md).

## <a name="see-also"></a>См. также раздел

[Локаль](../../c-runtime-library/locale.md)<br/>
[Интерпретация последовательностей многобайтовых символов](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Манипуляция строками](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)<br/>
