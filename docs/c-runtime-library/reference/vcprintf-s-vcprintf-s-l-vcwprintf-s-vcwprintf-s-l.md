---
description: 'Дополнительные сведения: _vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l'
title: _vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vcprintf_s
- _vcprintf_s_l
- _vcwprintf_s
- _vcwprintf_s_l
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
- vcprintf_s
- vcwprintf_s_l
- _vcwprintf_s
- _vcwprintf_s_l
- _vcprintf_s_l
- _vtcprintf_s
- vcwprintf_s
- vcprintf_s_l
- _vcprintf_s
helpviewer_keywords:
- _vtcprintf_s_l function
- _vcwprintf_s_l function
- _vtcprintf_s function
- vtcprintf_s_l function
- vcprintf_s_l function
- _vcprintf_s function
- _vcwprintf_s function
- vcwprintf_s_l function
- vcwprintf_s function
- vcprintf_s function
- _vcprintf_s_l function
- vtcprintf_s function
- formatted text [C++]
ms.assetid: 5a46d45a-30db-45df-9850-455cbdac5636
ms.openlocfilehash: 68ac12f9c9ddbebe613ea92ade0b05eeb8e1ab01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339596"
---
# <a name="_vcprintf_s-_vcprintf_s_l-_vcwprintf_s-_vcwprintf_s_l"></a>_vcprintf_s, _vcprintf_s_l, _vcwprintf_s, _vcwprintf_s_l

Записывают форматированные выходные данные в консоль с помощью указателя на список аргументов. Это версии функций [_vcprintf, _vcprintf_l, _vcwprintf, _vcwprintf_l](vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Этот API нельзя использовать в приложениях, выполняемых в среде выполнения Windows. Дополнительные сведения: [Функции CRT, которые не поддерживаются в приложениях универсальной платформы Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Синтаксис

```C
int _vcprintf(
   const char* format,
   va_list argptr
);
int _vcprintf(
   const char* format,
   locale_t locale,
   va_list argptr
);
int _vcwprintf_s(
   const wchar_t* format,
   va_list argptr
);
int _vcwprintf_s_l(
   const wchar_t* format,
   locale_t locale,
   va_list argptr
);
```

### <a name="parameters"></a>Параметры

*format*<br/>
Спецификация формата.

*аргптр*<br/>
Указатель на список аргументов.

*locale*<br/>
Используемый языковой стандарт.

Дополнительные сведения см. в разделе [Синтаксис описания формата: функции printf и wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Возвращаемое значение

Число записанных символов или отрицательное значение в случае ошибки вывода.

Как и менее безопасные версии этих функций, если *Format* является пустым указателем, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Кроме того, в отличие от менее защищенных версий этих функций, если *Формат* не задает допустимый формат, создается исключение недопустимого параметра. Если выполнение может быть продолжено, эти функции возвращают код ошибки и **устанавливают код** ошибки. Код ошибки по умолчанию — **еинвал** , если более конкретное значение не применяется.

## <a name="remarks"></a>Комментарии

Каждая из этих функций принимает указатель на список аргументов, а затем форматирует и записывает указанные данные в консоль. **_vcwprintf_s** — это версия **_vcprintf_s** для расширенных символов. Она принимает строку расширенных символов в качестве аргумента.

Версии этих функций с суффиксом **_l** идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо текущего языкового стандарта.

> [!IMPORTANT]
> Убедитесь, что *format* не является строкой, определяемой пользователем. Дополнительные сведения см. в разделе [Как избежать переполнения буфера](/windows/win32/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vtcprintf_s**|**_vcprintf_s**|**_vcprintf_s**|**_vcwprintf_s**|
|**_vtcprintf_s_l**|**_vcprintf_s_l**|**_vcprintf_s_l**|**_vcwprintf_s_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательные заголовки|
|-------------|---------------------|----------------------|
|**_vcprintf_s**, **_vcprintf_s_l**|\<conio.h> и \<stdarg.h>|\<varargs.h>*|
|**_vcwprintf_s**, **_vcwprintf_s_l**|\<conio.h> или \<wchar.h> , и \<stdarg.h>|\<varargs.h>*|

\* Требуется для совместимости с UNIX V.

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```cpp
// crt_vcprintf_s.cpp
#include <conio.h>
#include <stdarg.h>

// An error formatting function used to print to the console.
int eprintf_s(const char* format, ...)
{
    va_list args;
    va_start(args, format);
    int result = _vcprintf_s(format, args);
    va_end(args);
    return result;
}

int main()
{
    eprintf_s("(%d:%d): Error %s%d : %s\n", 10, 23, "C", 2111,
              "<some error text>");
    eprintf_s("    (Related to symbol '%s' defined on line %d).\n",
              "<symbol>", 5 );
}
```

```Output
(10,23): Error C2111 : <some error text>
    (Related to symbol '<symbol>' defined on line 5).
```

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Функции vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
