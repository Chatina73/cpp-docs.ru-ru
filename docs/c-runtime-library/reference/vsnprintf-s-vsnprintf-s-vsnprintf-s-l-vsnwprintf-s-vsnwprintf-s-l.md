---
description: 'Дополнительные сведения: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l'
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: 27c91d6064b4a92da8a6f09e7d7e5b6bfb8bf95f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342157"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

Записывают форматированные выходные данные с помощью указателя на список аргументов. Это версии функций [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) с усовершенствованной безопасностью, как описано в разделе [Функции безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>Параметры

*двойной*<br/>
Место хранения выходных данных.

*сизеофбуффер*<br/>
Размер *буфера* для вывода в виде числа символов.

*count*<br/>
Максимальное количество символов для записи (не включая завершающий нуль-символ) или [_TRUNCATE](../../c-runtime-library/truncate.md).

*format*<br/>
Спецификация формата.

*аргптр*<br/>
Указатель на список аргументов.

*locale*<br/>
Используемый языковой стандарт.

Дополнительные сведения см. в разделе [Спецификации формата](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="return-value"></a>Возвращаемое значение

**vsnprintf_s**, **_vsnprintf_s** и **_vsnwprintf_s** возвращают число записанных символов, не включая завершающее значение null, или отрицательное значение, если возникает либо усечение данных, либо ошибка выхода.

* Если параметр *Count* меньше *сизеофбуффер* и число символов в данных меньше или равно *Count*, либо *Count* [_TRUNCATE](../../c-runtime-library/truncate.md) и число символов в данных меньше *сизеофбуффер*, то записываются все данные и возвращается число символов.

* Если параметр *Count* имеет значение меньше, чем *сизеофбуффер* , но *количество* символов в данных превышает, то первые символы *подсчета* записываются. Происходит усечение оставшихся данных, и возвращается значение-1 без вызова обработчика недопустимого параметра.

* Если параметр *Count* имеет значение [_TRUNCATE](../../c-runtime-library/truncate.md) и количество символов в данных равно или превышает *сизеофбуффер*, то будет записана большая часть строки, как в *буфере* (с завершающим значением NULL). Происходит усечение оставшихся данных, и возвращается значение-1 без вызова обработчика недопустимого параметра.

* Если параметр *Count* равен или превышает значение *сизеофбуффер* , но число символов в данных меньше *сизеофбуффер*, то все данные записываются (с завершающим значением NULL), а число символов возвращается.

* Если *Count* и количество символов в данных равно или превышает *сизеофбуффер*, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение продолжится после обработчика недопустимых параметров, эти функции задают для *буфера* пустую строку, устанавливают значение **очистки в** **ERANGE** и возвращают-1.

* Если *buffer* или *Format* является пустым указателем или **значение** *Count* меньше или равно нулю, вызывается обработчик недопустимых параметров. Если выполнение может быть продолжено, эти функции **устанавливают** значение **еинвал** и возвращают-1.

### <a name="error-conditions"></a>Ситуации, которые могут привести к ошибке

|**Condition**|Возвращает|**errno**|
|-----------------|------------|-------------|
|*буфер* имеет **значение NULL**|-1|**еинвал**|
|*Формат* имеет **значение NULL**|-1|**еинвал**|
|*число* <= 0|-1|**еинвал**|
|*сизеофбуффер* слишком мал (и *count* ! = **_TRUNCATE**)|-1 (и *буфер* , для которого задана пустая строка)|**ERANGE**|

## <a name="remarks"></a>Комментарии

**vsnprintf_s** совпадает с **_vsnprintf_s**. **vsnprintf_s** входит в соответствие стандарту ANSI. **_vnsprintf** сохраняется для обеспечения обратной совместимости.

Каждая из этих функций принимает указатель на список аргументов, затем форматирует и записывает *данные в память* , на которую указывает *буфер* , и добавляет завершающее значение null.

Если параметр *Count* имеет значение [_TRUNCATE](../../c-runtime-library/truncate.md), то эти функции записываются как часть строки, как в *буфере* , оставляя место для завершающего null. Если вся строка (с завершающим значением NULL) помещается в *буфер*, эти функции возвращают количество записанных символов (не включая завершающее значение null); в противном случае эти функции возвращают значение-1, чтобы указать, что произошло усечение.

Версии этих функций с суффиксом **_l** идентичны за исключением того, что они используют переданный параметр языкового стандарта вместо локали текущего потока.

> [!IMPORTANT]
> Убедитесь, что *format* не является строкой, определяемой пользователем. Дополнительные сведения см. в разделе [Как избежать переполнения буфера](/windows/win32/SecBP/avoiding-buffer-overruns).

> [!NOTE]
> Чтобы убедиться в наличии места для завершающего значения NULL, убедитесь, что *число* строго меньше длины буфера, или используйте **_TRUNCATE**.

В C++ использование данных функций упрощено наличием шаблонных перегрузок; перегруженные методы могут автоматически определять длину буфера (что исключает необходимость указания аргумента с размером буфера), а также они могут автоматически заменять более старые, незащищенные функции их новыми безопасными аналогами. Дополнительные сведения см. в разделе [Безопасные перегрузки шаблонов](../../c-runtime-library/secure-template-overloads.md).

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательные заголовки|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> и \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h> и \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h> или \<wchar.h> , и \<stdarg.h>|\<varargs.h>*|

\* Требуется для совместимости с UNIX V.

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Функции vprintf](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
