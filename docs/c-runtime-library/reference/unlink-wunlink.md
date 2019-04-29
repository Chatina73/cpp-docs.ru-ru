---
title: _unlink, _wunlink
ms.date: 11/04/2016
apiname:
- _unlink
- _wunlink
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tunlink
- _unlink
- wunlink
- _wunlink
helpviewer_keywords:
- files [C++], deleting
- _wunlink function
- wunlink function
- unlink function
- _unlink function
- tunlink function
- files [C++], removing
- _tunlink function
ms.assetid: 5e4f5f1b-1e99-4391-9b18-9ac63c32fae8
ms.openlocfilehash: ec59a02f1302fe4a2149889cf1b48090d061d6b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268776"
---
# <a name="unlink-wunlink"></a>_unlink, _wunlink

Удаляют файл.

## <a name="syntax"></a>Синтаксис

```C
int _unlink(
   const char *filename
);
int _wunlink(
   const wchar_t *filename
);
```

### <a name="parameters"></a>Параметры

*filename*<br/>
Имя удаляемого файла.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций при успешном выполнении возвращает 0. В противном случае функция возвращает -1 и наборы **errno** для **EACCES**, что означает путь указывает файл, доступный только для чтения или каталог, или к **ENOENT**, означающее, что файл или путь не найден.

Дополнительные сведения об этих и других кодах возврата см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Примечания

**_Unlink** функция удаляет файл, указанный параметром *filename*. **_wunlink** — это двухбайтовая версия **_unlink**; *filename* аргумент **_wunlink** — строка расширенных символов. В остальном эти функции ведут себя одинаково.

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tunlink**|**_unlink**|**_unlink**|**_wunlink**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_unlink**|\<io.h> и \<stdio.h>|
|**_wunlink**|\<io.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="code-example"></a>Пример кода

Эта программа использует _unlink для удаления CRT_UNLINK. TXT.

```C
// crt_unlink.c

#include <stdio.h>

int main( void )
{
   if( _unlink( "crt_unlink.txt" ) == -1 )
      perror( "Could not delete 'CRT_UNLINK.TXT'" );
   else
      printf( "Deleted 'CRT_UNLINK.TXT'\n" );
}
```

### <a name="input-crtunlinktxt"></a>Входные данные: crt_unlink.txt

```Input
This file will be deleted.
```

### <a name="sample-output"></a>Пример результатов выполнения

```Output
Deleted 'CRT_UNLINK.TXT'
```

## <a name="see-also"></a>См. также

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
[_close](close.md)<br/>
[remove, _wremove](remove-wremove.md)<br/>
