---
description: 'Дополнительные сведения о: sscanf, _sscanf_l, swscanf, _swscanf_l'
title: sscanf, _sscanf_l, swscanf, _swscanf_l
ms.date: 08/29/2019
api_name:
- swscanf
- sscanf
- _sscanf_l
- _swscanf_l
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
- _sscanf_l
- _stscanf
- swscanf
- _stscanf_l
- sscanf
- _swscanf_l
helpviewer_keywords:
- swscanf function
- _stscanf function
- sscanf function
- _stscanf_l function
- _sscanf_l function
- _swscanf_l function
- swscanf_l function
- strings [C++], reading data from
- stscanf function
- reading data, strings
- strings [C++], reading
- sscanf_l function
- stscanf_l function
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
ms.openlocfilehash: f5681e1f8e122c6f24151ae5e8d37186d8bd066e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171274"
---
# <a name="sscanf-_sscanf_l-swscanf-_swscanf_l"></a>sscanf, _sscanf_l, swscanf, _swscanf_l

Считывают форматированные данные из строки. Существуют более безопасные версии этих функций; см. раздел [sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).

## <a name="syntax"></a>Синтаксис

```C
int sscanf(
   const char *buffer,
   const char *format [,
   argument ] ...
);
int _sscanf_l(
   const char *buffer,
   const char *format,
   locale_t locale [,
   argument ] ...
);
int swscanf(
   const wchar_t *buffer,
   const wchar_t *format [,
   argument ] ...
);
int _swscanf_l(
   const wchar_t *buffer,
   const wchar_t *format,
   locale_t locale [,
   argument ] ...
);
```

### <a name="parameters"></a>Параметры

*двойной*<br/>
Сохраненные данные

*format*<br/>
Строка управления форматом. Дополнительные сведения см. в разделе [Спецификации формата](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

*argument*<br/>
Необязательные аргументы

*locale*<br/>
Используемый языковой стандарт

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает количество полей, которые были успешно преобразованы и присвоены; возвращаемое значение не включает поля, которые были считаны, но не были присвоены. Возвращаемое значение 0 указывает, что поля не были назначены. Возвращаемое значение — **EOF** для ошибки или, если конец строки достигнут перед первым преобразованием.

Если *buffer* или *Format* является **пустым** указателем, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают-1 **и устанавливают для** **еинвал** значение.

Дополнительные сведения об этих и других кодах ошибок см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Комментарии

Функция **sscanf** считывает данные из *буфера* в расположение, заданное каждым *аргументом*. Каждый *аргумент* должен быть указателем на переменную с типом, который соответствует спецификатору типа в *формате*. Аргумент *Format* управляет интерпретацией полей ввода и имеет ту же форму и функцию, что и аргумент *Format* для функции **scanf** . Если копирование производится между перекрывающимися строками, поведение не определено.

Дополнительные сведения об символах поля типа scanf см. в разделе [символы поля типа scanf](../scanf-type-field-characters.md). Сведения о полях спецификации формата scanf см. в разделе [поля спецификации формата](../format-specification-fields-scanf-and-wscanf-functions.md).

> [!IMPORTANT]
> При чтении строки с помощью **sscanf** всегда указывайте ширину для формата **% s** (например, **"%32"** вместо **"% s"**); в противном случае входные данные неправильного формата могут легко вызвать переполнение буфера.

**swscanf** — это версия **sscanf** для расширенных символов; аргументы для **swscanf** являются строками расширенных символов. **sscanf** не обрабатывает многобайтовые шестнадцатеричные символы. **swscanf** не обрабатывает символы в формате полной ширины в Юникоде или "зоны совместимости". В противном случае поведение **swscanf** и **sscanf** работает одинаково.

Версии этих функций с суффиксом **_l** идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо локали текущего потока.

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_stscanf**|**sscanf**|**sscanf**|**swscanf**|
|**_stscanf_l**|**_sscanf_l**|**_sscanf_l**|**_swscanf_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**sscanf**, **_sscanf_l**|\<stdio.h>|
|**swscanf**, **_swscanf_l**|\<stdio.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_sscanf.c
// compile with: /W3
// This program uses sscanf to read data items
// from a string named tokenstring, then displays them.

#include <stdio.h>

int main( void )
{
   char  tokenstring[] = "15 12 14...";
   char  s[81];
   char  c;
   int   i;
   float fp;

   // Input various data from tokenstring:
   // max 80 character string:
   sscanf( tokenstring, "%80s", s ); // C4996
   sscanf( tokenstring, "%c", &c );  // C4996
   sscanf( tokenstring, "%d", &i );  // C4996
   sscanf( tokenstring, "%f", &fp ); // C4996
   // Note: sscanf is deprecated; consider using sscanf_s instead

   // Output the data read
   printf( "String    = %s\n", s );
   printf( "Character = %c\n", c );
   printf( "Integer:  = %d\n", i );
   printf( "Real:     = %f\n", fp );
}
```

```Output
String    = 15
Character = 1
Integer:  = 15
Real:     = 15.000000
```

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[snprintf, _snprintf, _snprintf_l, _snwprintf, _snwprintf_l](snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)<br/>
