---
title: _itoa, _itow функции
ms.date: 03/21/2018
apiname:
- itoa
- _itoa
- ltoa
- _ltoa
- ultoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _itoa
- _ltoa
- _ultoa
- _i64toa
- _ui64toa
- _itow
- _ltow
- _ultow
- _i64tow
- _ui64tow
- itoa
- ltoa
- ultoa
- i64toa
- ui64toa
- itow
- ltow
- ultow
- i64tow
- ui64tow
- itot
- _itot
- ltot
- _ltot
- ultot
- _ultot
- i64tot
- _i64tot
- ui64tot
- _ui64tot
- _MAX_ITOSTR_BASE16_COUNT
- _MAX_ITOSTR_BASE10_COUNT
- _MAX_ITOSTR_BASE8_COUNT
- _MAX_ITOSTR_BASE2_COUNT
- _MAX_LTOSTR_BASE16_COUNT
- _MAX_LTOSTR_BASE10_COUNT
- _MAX_LTOSTR_BASE8_COUNT
- _MAX_LTOSTR_BASE2_COUNT
- _MAX_ULTOSTR_BASE16_COUNT
- _MAX_ULTOSTR_BASE10_COUNT
- _MAX_ULTOSTR_BASE8_COUNT
- _MAX_ULTOSTR_BASE2_COUNT
- _MAX_I64TOSTR_BASE16_COUNT
- _MAX_I64TOSTR_BASE10_COUNT
- _MAX_I64TOSTR_BASE8_COUNT
- _MAX_I64TOSTR_BASE2_COUNT
- _MAX_U64TOSTR_BASE16_COUNT
- _MAX_U64TOSTR_BASE10_COUNT
- _MAX_U64TOSTR_BASE8_COUNT
- _MAX_U64TOSTR_BASE2_COUNT
helpviewer_keywords:
- _itot function
- ui64toa function
- _ui64toa function
- converting integers
- itot function
- _i64tow function
- _i64toa function
- _itow function
- ui64tow function
- integers, converting
- itoa function
- _ui64tow function
- i64tow function
- itow function
- i64toa function
- converting numbers, to strings
- _itoa function
ms.assetid: 46592a00-77bb-4e73-98c0-bf629d96cea6
ms.openlocfilehash: 182e7190554382f56d43f94fefe209fd38a7b78b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50464096"
---
# <a name="itoa-itoa-ltoa-ltoa-ultoa-ultoa-i64toa-ui64toa-itow-ltow-ultow-i64tow-ui64tow"></a>itoa, _itoa, ltoa, _ltoa, ultoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, _ultow, _i64tow, _ui64tow

Преобразует целое число в строку. Доступны более безопасные версии этих функций; см. в разделе [_itoa_s, _itow_s функции](itoa-s-itow-s.md).

## <a name="syntax"></a>Синтаксис

```C
char * _itoa( int value, char *buffer, int radix );
char * _ltoa( long value, char *buffer, int radix );
char * _ultoa( unsigned long value, char *buffer, int radix );
char * _i64toa( long long value, char *buffer, int radix );
char * _ui64toa( unsigned long long value, char *buffer, int radix );

wchar_t * _itow( int value, wchar_t *buffer, int radix );
wchar_t * _ltow( long value, wchar_t *buffer, int radix );
wchar_t * _ultow( unsigned long value, wchar_t *buffer, int radix );
wchar_t * _i64tow( long long value, wchar_t *buffer, int radix );
wchar_t * _ui64tow( unsigned long long value, wchar_t *buffer, int radix );

// These Posix versions of the functions have deprecated names:
char * itoa( int value, char *buffer, int radix );
char * ltoa( long value, char *buffer, int radix );
char * ultoa( unsigned long value, char *buffer, int radix );

// The following template functions are C++ only:
template <size_t size>
char *_itoa( int value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( long value, char (&buffer)[size], int radix );

template <size_t size>
char *_itoa( unsigned long value, char (&buffer)[size], int radix );

template <size_t size>
char *_i64toa( long long value, char (&buffer)[size], int radix );

template <size_t size>
char * _ui64toa( unsigned long long value, char (&buffer)[size], int radix );

template <size_t size>
wchar_t * _itow( int value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ltow( long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ultow( unsigned long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _i64tow( long long value, wchar_t (&buffer)[size], int radix );

template <size_t size>
wchar_t * _ui64tow( unsigned long long value, wchar_t (&buffer)[size],
   int radix );
```

### <a name="parameters"></a>Параметры

*значение*<br/>
Число, которое требуется преобразовать.

*buffer*<br/>
Буфер, содержащий результат преобразования.

*radix*<br/>
Основание для преобразования *значение*, который должен быть в диапазоне от 2 до 36.

*size*<br/>
Длина буфера в единицах символьного типа. Этот параметр выводится из *буфера* аргумента в C++.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает указатель на *буфера*. Ошибка не возвращается.

## <a name="remarks"></a>Примечания

**_Itoa**, **_ltoa**, **_ultoa**, **_i64toa**, и **_ui64toa** функций преобразуют разряды заданный *значение* аргумент в строку нуль-символом и сохраняют результат (до 33 символов для **_itoa**, **_ltoa**, и  **_ultoa**и 65 для **_i64toa** и **_ui64toa**) в *буфера*. Если *основание системы счисления* равно 10 и *значение* является отрицательным, первый символ результирующей строки — знак «минус» (**-**). **_Itow**, **_ltow**, **_ultow**, **_i64tow**, и **_ui64tow** функции являются расширенных символов версии **_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, и **_ui64toa**, соответственно.

> [!IMPORTANT]
> Эти функции можно написать после конца буфера слишком мал. Чтобы предотвратить переполнение буфера, убедитесь, что *буфера* достаточно велик для хранения преобразованных цифр, а также конечного нуль символа и символа знака. Неправильное использование этих функций может привести к серьезной уязвимости в коде.

Из-за их потенциальные угрозы безопасности, по умолчанию, эти функции вызывают предупреждение об устаревании [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **эта функция или переменная может быть небезопасным. Рассмотрите возможность использования** *safe_function* **вместо этого. Чтобы отключить об устаревании, используйте _CRT_SECURE_NO_WARNINGS.** Мы рекомендуем изменять исходный код для использования *safe_function* предложенной предупреждающее сообщение. Более безопасные функции не записывать больше символов, чем указанный размер буфера. Дополнительные сведения см. в разделе [_itoa_s, _itow_s функции](itoa-s-itow-s.md).

Чтобы использовать эти функции без предупреждения об устаревании, определите **_CRT_SECURE_NO_WARNINGS** макрос препроцессора, прежде чем включать какие-либо заголовки CRT. Добавив это можно сделать в командной строке в командную строку разработчика **/D_CRT_SECURE_NO_WARNINGS** параметра компилятора **cl** команды. В противном случае задайте макрос в исходных файлах. При использовании предкомпилированных заголовков, задайте макрос в верхней части файла предкомпилированного заголовка включаемый файл, обычно stdafx.h. Чтобы определить макрос в исходном коде, используйте **#define** директиву перед включением любой заголовок CRT, как в следующем примере:

```C
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

В C++ эти функции имеют шаблонные перегрузки, которые вызывают их более безопасные аналоги. Дополнительные сведения см. в разделе [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).

Имена Posix **itoa**, **ltoa**, и **ultoa** существуют как псевдонимы для **_itoa**, **_ltoa**, и **_ultoa** функции. Имена Posix являются устаревшими, так как они не соответствуют реализации функции соглашения об именовании из ISO-C. По умолчанию эти функции вызывают предупреждение об устаревании [C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md): **имя POSIX для этого элемента устарело. Вместо этого используйте имя, соответствующее стандарту ISO C и C++:** *новое_имя*. Мы рекомендуем изменять исходный код, чтобы использовать более безопасные версии этих функций **_itoa_s**, **_ltoa_s**, или **_ultoa_s**. Дополнительные сведения см. в разделе [_itoa_s, _itow_s функции](itoa-s-itow-s.md).

Для переноса исходного кода можно сохранить имена Posix в коде. Для использования этих функций без предупреждение об устаревании, определите оба **_CRT_NONSTDC_NO_WARNINGS** и **_CRT_SECURE_NO_WARNINGS** макросы препроцессора, прежде чем включать какие-либо заголовки CRT. Добавив это можно сделать в командной строке в командную строку разработчика **/D_CRT_SECURE_NO_WARNINGS** и **/D_CRT_NONSTDC_NO_WARNINGS** для параметров компилятора **cl**команды. В противном случае определите макросы в исходных файлах. При использовании предкомпилированных заголовков, определить этот макрос в верхней части файла предкомпилированного заголовка содержит файл, обычно stdafx.h. Чтобы определить макрос в исходном коде, используйте **#define** директивы до включения любой заголовок CRT, как в следующем примере:

```C
#define _CRT_NONSTDC_NO_WARNINGS 1
#define _CRT_SECURE_NO_WARNINGS 1
#include <stdlib.h>
```

### <a name="maximum-conversion-count-macros"></a>Макросы число максимальным преобразованием

Для создания безопасного буферов для преобразований, CRT включает в себя некоторые удобный макросы. Эти определения размера буфера, требуемого для преобразования длинного возможные значения каждого целочисленных типов, включая завершающий символ null и войдите символ для нескольких распространенных баз. Чтобы обеспечить достаточно большим, чтобы получать все преобразования в основании, заданном параметром буфера преобразования *основание системы счисления*, используйте один из них определенные макросы при распределении буфера. Это помогает предотвратить ошибки переполнения буфера, при преобразовании целочисленных типов строк. Эти макросы определяются при включении в источнике stdlib.h и wchar.h.

Для использования этих макросов в функции преобразования строк, объявить ваши буфер соответствующим символьным типом преобразования и использовать значение макроса для целочисленного типа и базового как измерение буфера. В этой таблице перечислены макросы, которые подходят для каждой функции для перечисленных баз.

||||
|-|-|-|
|Функции|radix|Макросы|
|**_itoa**, **_itow**|16<br/>10<br/>8<br/>2|**_MAX_ITOSTR_BASE16_COUNT**<br/>**_MAX_ITOSTR_BASE10_COUNT**<br/>**_MAX_ITOSTR_BASE8_COUNT**<br/>**_MAX_ITOSTR_BASE2_COUNT**|
|**_ltoa**, **_ltow**|16<br/>10<br/>8<br/>2|**_MAX_LTOSTR_BASE16_COUNT**<br/>**_MAX_LTOSTR_BASE10_COUNT**<br/>**_MAX_LTOSTR_BASE8_COUNT**<br/>**_MAX_LTOSTR_BASE2_COUNT**|
|**_ultoa**, **_ultow**|16<br/>10<br/>8<br/>2|**_MAX_ULTOSTR_BASE16_COUNT**<br/>**_MAX_ULTOSTR_BASE10_COUNT**<br/>**_MAX_ULTOSTR_BASE8_COUNT**<br/>**_MAX_ULTOSTR_BASE2_COUNT**|
|**_i64toa**, **_i64tow**|16<br/>10<br/>8<br/>2|**_MAX_I64TOSTR_BASE16_COUNT**<br/>**_MAX_I64TOSTR_BASE10_COUNT**<br/>**_MAX_I64TOSTR_BASE8_COUNT**<br/>**_MAX_I64TOSTR_BASE2_COUNT**|
|**_ui64toa**, **_ui64tow**|16<br/>10<br/>8<br/>2|**_MAX_U64TOSTR_BASE16_COUNT**<br/>**_MAX_U64TOSTR_BASE10_COUNT**<br/>**_MAX_U64TOSTR_BASE8_COUNT**<br/>**_MAX_U64TOSTR_BASE2_COUNT**|

В этом примере макрос число преобразования для определения буфер достаточно велик, чтобы содержать **long long без знака** в по основанию 2:

```cpp
#include <wchar.h>
#include <iostream>
int main()
{
    wchar_t buffer[_MAX_U64TOSTR_BASE2_COUNT];
    std:wcout << _ui64tow(0xFFFFFFFFFFFFFFFFull, buffer, 2) << std::endl;
}
```

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_itot**|**_itoa**|**_itoa**|**_itow**|
|**_ltot**|**_ltoa**|**_ltoa**|**_ltow**|
|**_ultot**|**_ultoa**|**_ultoa**|**_ultow**|
|**_i64tot**|**_i64toa**|**_i64toa**|**_i64tow**|
|**_ui64tot**|**_ui64toa**|**_ui64toa**|**_ui64tow**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**itoa**, **ltoa**, **ultoa**|\<stdlib.h>|
|**_itoa**, **_ltoa**, **_ultoa**, **_i64toa**, **_ui64toa**|\<stdlib.h>|
|**_itow**, **_ltow**, **_ultow**, **_i64tow**, **_ui64tow**|\<stdlib.h> или \<wchar.h>|

Следующие функции и макросы, характерные для Майкрософт. Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

В этом образце демонстрируется использование некоторых функций преобразования целого числа. Обратите внимание на использование **_CRT_SECURE_NO_WARNINGS** макрос для отключения предупреждения C4996.

```C
// crt_itoa.c
// Compile by using: cl /W4 crt_itoa.c
// This program makes use of the _itoa functions
// in various examples.

#define _CRT_SECURE_NO_WARNINGS 1
#include <stdio.h>      // for printf
#include <string.h>     // for strnlen
#include <stdlib.h>     // for _countof, _itoa fns, _MAX_COUNT macros

int main(void)
{
    char buffer[_MAX_U64TOSTR_BASE2_COUNT];
    int r;

    for (r = 10; r >= 2; --r)
    {
        _itoa(-1, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _i64toa(-1LL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
    printf("\n");

    for (r = 10; r >= 2; --r)
    {
        _ui64toa(0xffffffffffffffffULL, buffer, r);
        printf("base %d: %s (%d chars)\n", r, buffer,
            strnlen(buffer, _countof(buffer)));
    }
}
```

```Output
base 10: -1 (2 chars)
base 9: 12068657453 (11 chars)
base 8: 37777777777 (11 chars)
base 7: 211301422353 (12 chars)
base 6: 1550104015503 (13 chars)
base 5: 32244002423140 (14 chars)
base 4: 3333333333333333 (16 chars)
base 3: 102002022201221111210 (21 chars)
base 2: 11111111111111111111111111111111 (32 chars)

base 10: -1 (2 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)

base 10: 18446744073709551615 (20 chars)
base 9: 145808576354216723756 (21 chars)
base 8: 1777777777777777777777 (22 chars)
base 7: 45012021522523134134601 (23 chars)
base 6: 3520522010102100444244423 (25 chars)
base 5: 2214220303114400424121122430 (28 chars)
base 4: 33333333333333333333333333333333 (32 chars)
base 3: 11112220022122120101211020120210210211220 (41 chars)
base 2: 1111111111111111111111111111111111111111111111111111111111111111 (64 chars)
```

## <a name="see-also"></a>См. также

[Преобразование данных](../../c-runtime-library/data-conversion.md)<br/>
[_itoa_s, _itow_s функции](itoa-s-itow-s.md)<br/>
