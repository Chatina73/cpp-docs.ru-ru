---
description: 'Дополнительные сведения: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l'
title: strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
ms.date: 4/2/2020
api_name:
- strncmp
- _mbsncmp
- wcsncmp
- _mbsncmp_l
- _o__mbsncmp
- _o__mbsncmp_l
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
- ntdll.dll
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
- _ftcsnccmp
- _ftcsncmp
- _tcsncmp
- _tcsnccmp
- strncmp
- _mbsncmp
- wcsncmp
helpviewer_keywords:
- _tcsnccmp function
- ftcsncmp function
- wcsncmp function
- _ftcsncmp function
- _mbsncmp function
- tcsncmp function
- mbsncmp function
- _mbsncmp_l function
- mbsncmp_l function
- strncmp function
- strings [C++], comparing characters of
- string comparison [C++], strncmp function
- _tcsncmp function
- tcsnccmp function
- ftcsnccmp function
- characters [C++], comparing
- _ftcsnccmp function
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
ms.openlocfilehash: 237f51f1072e97e6bbba0347635616f160faa912
ms.sourcegitcommit: bb35a6c22d896c4640cff00a7321442c544ca219
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2021
ms.locfileid: "105744781"
---
# <a name="strncmp-wcsncmp-_mbsncmp-_mbsncmp_l"></a>strncmp, wcsncmp, _mbsncmp, _mbsncmp_l

Сравнивает символы двух строк вплоть до указанного количества.

> [!IMPORTANT]
> **_mbsncmp** и **_mbsncmp_l** нельзя использовать в приложениях, которые выполняются в среда выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
int strncmp(
   const char *string1,
   const char *string2,
   size_t count
);
int wcsncmp(
   const wchar_t *string1,
   const wchar_t *string2,
   size_t count
);
int _mbsncmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
int _mbsncmp_l(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count,
   _locale_t locale
);int _mbsnbcmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Параметры

*строка1*, *строка2*<br/>
Строки для сравнения.

*count*<br/>
Число сравниваемых символов.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Возвращаемое значение указывает связь подстрок строк *строка1* и *строка2* следующим образом.

|Возвращаемое значение|Описание|
|------------------|-----------------|
|< 0|Строка *строка1* меньше, чем *строка2* подстроки|
|0|Строка *строка1* совпадает с подстрокой *строка_замены*|
|> 0|Строка *строка1* больше, чем *строка2* подстроки|

При ошибке проверки параметров **_mbsncmp** и **_mbsncmp_l** возвращают **_NLSCMPERROR**, который определен в \<string.h> и \<mbstring.h> .

## <a name="remarks"></a>Замечания

Функция **strncmp** выполняет порядковое сравнение не более чем *из первых символов* в *строка1* и *строка_замены* и возвращает значение, указывающее связь между подстроками. **strncmp** — это зависящая от регистра версия **_strnicmp**. **wcsncmp** и **_mbsncmp** — это зависящие от регистра версии **_wcsnicmp** и **_mbsnicmp**.

**wcsncmp** и **_mbsncmp** — это версии **strncmp** для расширенных символов и многобайтовых символов. Аргументы **wcsncmp** — это строки расширенных символов; **_mbsncmp** являются строками многобайтовых символов. **_mbsncmp** распознает последовательности многобайтовых символов в соответствии с многобайтовой кодовой страницей и возвращает **_NLSCMPERROR** об ошибке.

Кроме того, **_mbsncmp** и **_mbsncmp_l** проверить параметры. Если *строка1* или *строка_замены* является пустым указателем и *число* не равно 0, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, **_mbsncmp** и **_mbsncmp_l** возвращают **_NLSCMPERROR** **и установите значение** **еинвал**. **strncmp** и **wcsncmp** не проверяют свои параметры. В остальном эти функции ведут себя одинаково.

Поведение сравнения **_mbsncmp** и **_mbsncmp_l** зависит от значения параметра категории **LC_CTYPE** для языкового стандарта. Эта категория определяет обнаружение начальных и конечных байтов в многобайтовых символах. Дополнительные сведения см. в разделе [setlocale](setlocale-wsetlocale.md). Функция **_mbsncmp** использует текущий языковой стандарт для этого поведения, зависящего от языкового стандарта. Функция **_mbsncmp_l** идентична, за исключением того, что вместо нее используется параметр *locale* . Для получения дополнительной информации см. [Locale](../../c-runtime-library/locale.md). Если языковой стандарт является однобайтовым локальным языком, поведение этих функций идентично **strncmp**.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnccmp**|**strncmp**|**_mbsncmp**|**wcsncmp**|
|**_tcsncmp**|**strncmp**|**_mbsnbcmp**|**wcsncmp**|
|**_tccmp**|Сопоставляется макросу или встраиваемой функции|**_mbsncmp**|Сопоставляется макросу или встраиваемой функции|
|**неприменимо**|**неприменимо**|**_mbsncmp_l**|**неприменимо**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**strncmp**|\<string.h>|
|**wcsncmp**|\<string.h> или \<wchar.h>|
|**_mbsncmp**, **_mbsncmp_l**|\<mbstring.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_strncmp.c
#include <string.h>
#include <stdio.h>

char string1[] = "The quick brown dog jumps over the lazy fox";
char string2[] = "The QUICK brown fox jumps over the lazy dog";

int main( void )
{
   char tmp[20];
   int result;
   printf( "Compare strings:\n      %s\n      %s\n\n",
           string1, string2 );
   printf( "Function:   strncmp (first 10 characters only)\n" );
   result = strncmp( string1, string2 , 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n\n", tmp );
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );
   result = _strnicmp( string1, string2, 10 );
   if( result > 0 )
      strcpy_s( tmp, sizeof(tmp), "greater than" );
   else if( result < 0 )
      strcpy_s( tmp, sizeof(tmp), "less than" );
   else
      strcpy_s( tmp, sizeof(tmp), "equal to" );
   printf( "Result:      String 1 is %s string 2\n", tmp );
}
```

```Output
Compare strings:
      The quick brown dog jumps over the lazy fox
      The QUICK brown fox jumps over the lazy dog

Function:   strncmp (first 10 characters only)
Result:      String 1 is greater than string 2

Function:   strnicmp _strnicmp (first 10 characters only)
Result:      String 1 is equal to string 2
```

## <a name="see-also"></a>См. также

[Управление строками](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Локаль](../../c-runtime-library/locale.md)<br/>
[Интерпретация последовательностей Multibyte-Character](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_mbsnbicmp, _mbsnbicmp_l](mbsnbicmp-mbsnbicmp-l.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[Функции strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
