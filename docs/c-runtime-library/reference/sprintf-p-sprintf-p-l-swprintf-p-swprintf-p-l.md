---
description: 'Дополнительные сведения: _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l'
title: _sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l
ms.date: 3/9/2021
api_name:
- _sprintf_p
- _swprintf_p_l
- _swprintf_p
- _sprintf_p_l
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
- _sprintf_p
- _swprintf_p_l
- _sprintf_p_l
- _swprintf_p
- sprintf_p
- swprint_p_l
- swprintf_p
- swprintf_p_l
helpviewer_keywords:
- sprintf_p_l function
- swprintf_p function
- swprintf_p_l function
- _sprintf_p function
- _sprintf_p_l function
- _swprintf_p function
- sprintf_p function
- _stprintf_p function
- stprintf_p function
- _swprintf_p_l function
- stprintf_p_l function
- formatted text [C++]
- _stprintf_p_l function
ms.openlocfilehash: 2f0b6dad129a8f3f2f91bf1244c77ae5691a679e
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539271"
---
# <a name="_sprintf_p-_sprintf_p_l-_swprintf_p-_swprintf_p_l"></a>`_sprintf_p`, `_sprintf_p_l`, `_swprintf_p`, `_swprintf_p_l`

Запись форматированных данных в строку с возможностью указать порядок использования параметров в строке формата.

## <a name="syntax"></a>Синтаксис

```C
int _sprintf_p(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format [,
   argument_list]
);
int _sprintf_p_l(
   char *buffer,
   size_t sizeOfBuffer,
   const char *format,
   locale_t locale [,
   argument_list]
);
int _swprintf_p(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format [,
   argument_list]
);
int _swprintf_p_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   const wchar_t *format,
   locale_t locale [,
   argument_list]
);
```

### <a name="parameters"></a>Параметры

*`buffer`*<br/>
Место хранения выходных данных

*`sizeOfBuffer`*<br/>
Наибольшее число символов для хранения.

*`format`*<br/>
Строка управления форматом.

*`argument_list`*<br/>
Необязательные аргументы для строки формата.

*`locale`*<br/>
Используемый языковой стандарт.

Дополнительные сведения см. в разделе [Спецификации формата](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Возвращаемое значение

Число записанных символов или-1, если произошла ошибка.

## <a name="remarks"></a>Комментарии

**`_sprintf_p`** Функция форматирует и сохраняет последовательность символов и значений в *`buffer`* . Каждый аргумент в *`argument_list`* (если таковой имеется) преобразуется и выводится в соответствии с соответствующей спецификацией формата в *`format`* . Аргумент *Format* использует [синтаксис спецификации формата для `printf` `wprintf` функций и](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). После последнего написанного символа добавляется символ null. Если копирование производится между перекрывающимися строками, поведение не определено. Разница между **`_sprintf_p`** и заключается в том **`sprintf_s`** , что **`_sprintf_p`** поддерживает позиционированные параметры, позволяющие указать порядок, в котором аргументы используются в строке формата. Дополнительные сведения см. в разделе « [ `printf_p` позиционированные параметры](../../c-runtime-library/printf-p-positional-parameters.md)».

**`_swprintf_p`** — Это версия с расширенными символами **`_sprintf_p`** ; аргументы указателя для **`_swprintf_p`** — это строки расширенных символов. Обнаружение ошибок кодирования в **`_swprintf_p`** может отличаться от обнаруженных в **`_sprintf_p`** . **`_swprintf_p`** и **`fwprintf_p`** ведут себя одинаково, за исключением того, что **`_swprintf_p`** записывает выходные данные в строку, а не в назначение типа **`FILE`** , и **`_swprintf_p`** требует *`count`* параметр, чтобы указать максимальное число символов для записи. Версии этих функций с **`_l`** суффиксом идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо языкового стандарта текущего потока.

**`_sprintf_p`** Возвращает число байтов, хранящихся в *`buffer`* , без учета завершающего нуль символа. **`_swprintf_p`** Возвращает количество расширенных символов, хранящихся в *`buffer`* , без учета завершающего расширенного символа null. Если *`buffer`* или *`format`* является пустым указателем или строка формата содержит недопустимые символы форматирования, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают-1 и устанавливают **`errno`** для значение **`EINVAL`** .

> [!IMPORTANT]
> Начиная с Windows 10 версии 2004 (сборка 19041), `printf` семейство функций выводит в соответствии с правилами IEEE 754 только округленные числа с плавающей запятой. В предыдущих версиях Windows полностью непредставленные числа с плавающей запятой, которые заканчиваются на "5", всегда округляются. IEEE 754 указывает, что они должны округляться до ближайшей четной цифры (также называемой "округление банка"). Например, оба значения `printf("%1.0f", 1.5)` и `printf("%1.0f", 2.5)` должны округляться в 2. Ранее 1,5 бы округлялись до 2 и 2,5, округляя до 3. Это изменение влияет только на точное представление чисел. Например, 2,35 (который, когда представлен в памяти, находится ближе к 2.35000000000000008), по-своему округляется до 2,4. Округление, выполненное этими функциями, теперь также учитывает режим округления с плавающей запятой, установленный [`fesetround`](fegetround-fesetround2.md) . Ранее округление всегда выбрало `FE_TONEAREST` поведение. Это изменение влияет только на программы, созданные с помощью Visual Studio 2019 версии 16,2 и более поздних версий. Чтобы использовать устаревшее поведение округления с плавающей точкой, свяжите с ["legacy_stdio_float_rounding. obj"](../link-options.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|`TCHAR.H` ассемблер|`_UNICODE` & `_MBCS` не определено|`_MBCS` определяется|`_UNICODE` определяется|
|---------------------|------------------------------------|--------------------|-----------------------|
|**`_stprintf_p`**|**`_sprintf_p`**|**`_sprintf_p`**|**`_swprintf_p`**|
|**`_stprintf_p_l`**|**`_sprintf_p_l`**|**`_sprintf_p_l`**|**`_swprintf_p_l`**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**`_sprintf_p`**, **`_sprintf_p_l`**|`<stdio.h>`|
|**`_swprintf_p`**, **`_swprintf_p_l`**|`<stdio.h>` или `<wchar.h>`|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example-use-_sprintf_p-to-format-data"></a>Пример. Использование `_sprintf_p` для форматирования данных

```C
// crt_sprintf_p.c
// This program uses _sprintf_p to format various
// data and place them in the string named buffer.
//

#include <stdio.h>

int main( void )
{
    char     buffer[200],
            s[] = "computer", c = 'l';
    int      i = 35,
            j;
    float    fp = 1.7320534f;

    // Format and print various data:
    j  = _sprintf_p( buffer, 200,
                     "   String:    %s\n", s );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Character: %c\n", c );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Integer:   %d\n", i );
    j += _sprintf_p( buffer + j, 200 - j,
                     "   Real:      %f\n", fp );

    printf( "Output:\n%s\ncharacter count = %d\n",
            buffer, j );
}
```

```Output
Output:
   String:    computer
   Character: l
   Integer:   35
   Real:      1.732053

character count = 79
```

## <a name="example-error-code-handling"></a>Пример: обработка кода ошибки

```C
// crt_swprintf_p.c
// This is the wide character example which
// also demonstrates _swprintf_p returning
// error code.
#include <stdio.h>

#define BUFFER_SIZE 100

int main( void )
{
    wchar_t buffer[BUFFER_SIZE];
    int     len;

    len = _swprintf_p(buffer, BUFFER_SIZE, L"%2$s %1$d",
                      0, L" marbles in your head.");
    _printf_p( "Wrote %d characters\n", len );

    // _swprintf_p fails because string contains WEOF (\xffff)
    len = _swprintf_p(buffer, BUFFER_SIZE, L"%s",
                      L"Hello\xffff world" );
    _printf_p( "Wrote %d characters\n", len );
}
```

```Output
Wrote 24 characters
Wrote -1 characters
```

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[`_fprintf_p`, `_fprintf_p_l`, `_fwprintf_p`, `_fwprintf_p_l`](fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)<br/>
[`fprintf`, `_fprintf_l`, `fwprintf`, `_fwprintf_l`](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[`_printf_p`, `_printf_p_l`, `_wprintf_p`, `_wprintf_p_l`](printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)<br/>
[`printf`, `_printf_l`, `wprintf`, `_wprintf_l`](printf-printf-l-wprintf-wprintf-l.md)<br/>
[`sprintf`, `_sprintf_l`, `swprintf`, `_swprintf_l`, `__swprintf_l`](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[`scanf`, `_scanf_l`, `wscanf`, `_wscanf_l`](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[`sscanf`, `_sscanf_l`, `swscanf`, `_swscanf_l`](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[`sscanf_s`, `_sscanf_s_l`, `swscanf_s`, `_swscanf_s_l`](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
[`vprintf` Функции](../../c-runtime-library/vprintf-functions.md)<br/>
[`printf_p` Параметры позиционирования](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
