---
description: 'Дополнительные сведения о: memset, wmemset'
title: memset, wmemset
ms.date: 11/04/2016
api_name:
- wmemset
- memset
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- memset
- wmemset
helpviewer_keywords:
- wmemset function
- memset function
ms.assetid: e7ceb01b-df69-49c2-b294-a39358ad4699
ms.openlocfilehash: 547cbbcab4966291ab540b6e57f68d4057995ff8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171352"
---
# <a name="memset-wmemset"></a>memset, wmemset

Устанавливает для буферов значение указанного символа.

## <a name="syntax"></a>Синтаксис

```C
void *memset(
   void *dest,
   int c,
   size_t count
);
wchar_t *wmemset(
   wchar_t *dest,
   wchar_t c,
   size_t count
);
```

### <a name="parameters"></a>Параметры

*dest*<br/>
Указатель на место назначения.

*c*<br/>
Задаваемый символ.

*count*<br/>
Число символов.

## <a name="return-value"></a>Возвращаемое значение

Значение *dest*.

## <a name="remarks"></a>Комментарии

Устанавливает первые символы *подсчета* для *dest* на символ *c*.

**Примечание по безопасности** Убедитесь, что в буфере назначения достаточно места, чтобы не меньше символов *подсчета* . Дополнительные сведения см. в разделе [Как избежать переполнения буфера](/windows/win32/SecBP/avoiding-buffer-overruns).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**memset**|\<memory.h> или \<string.h>|
|**wmemset**|\<wchar.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

```C
// crt_memset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <memory.h>
#include <stdio.h>

int main( void )
{
   char buffer[] = "This is a test of the memset function";

   printf( "Before: %s\n", buffer );
   memset( buffer, '*', 4 );
   printf( "After:  %s\n", buffer );
}
```

### <a name="output"></a>Выходные данные

```Output
Before: This is a test of the memset function
After:  **** is a test of the memset function
```

Ниже приведен пример использования wmemset.

```C
// crt_wmemset.c
/* This program uses memset to
* set the first four chars of buffer to "*".
*/

#include <wchar.h>
#include <stdio.h>

int main( void )
{
   wchar_t buffer[] = L"This is a test of the wmemset function";

   wprintf( L"Before: %s\n", buffer );
   wmemset( buffer, '*', 4 );
   wprintf( L"After:  %s\n", buffer );
}
```

### <a name="output"></a>Вывод

```Output
Before: This is a test of the wmemset function
After:  **** is a test of the wmemset function
```

## <a name="see-also"></a>См. также

[Обработка буфера](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)<br/>
