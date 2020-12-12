---
description: 'Дополнительные сведения о: memmove, wmemmove'
title: memmove, wmemmove
ms.date: 11/04/2016
api_name:
- memmove
- wmemmove
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
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 15dee8eab2a1b7eedd3891d8673647a711c0e499
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97171391"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Перемещает один буфер в другой. Существуют более безопасные версии этих функций; см. раздел [memmove_s, wmemmove_s](memmove-s-wmemmove-s.md).

## <a name="syntax"></a>Синтаксис

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Параметры

*dest*<br/>
Конечный объект.

*src*<br/>
Исходный объект.

*count*<br/>
Число байтов (**memmove**) или символов (**wmemmove**) для копирования.

## <a name="return-value"></a>Возвращаемое значение

Значение *dest*.

## <a name="remarks"></a>Комментарии

Копирует байты *счетчика* (**memmove**) или символы (**wmemmove**) из *src* в *dest*. Если отдельные области конечного объекта перекрывают области исходного объекта, то обе эти функции гарантируют, что байты исходного объекта в перекрывающейся области будут скопированы, прежде чем будут перезаписаны.

**Примечание о безопасности**. Убедитесь в том, что буфер назначения равен или превосходит по размеру исходный буфер. Дополнительные сведения см. в разделе [Как избежать переполнения буфера](/windows/win32/SecBP/avoiding-buffer-overruns).

Функции **memmove** и **wmemmove** будут считаться устаревшими только в том случае, если константа **_CRT_SECURE_DEPRECATE_MEMORY** определена до инструкции включения, чтобы функции были устаревшими, например, в примере ниже:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

или

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**memmove**|\<string.h>|
|**wmemmove**|\<wchar.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>См. также раздел

[Обработка буфера](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
