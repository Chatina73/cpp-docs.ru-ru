---
title: _access_s, _waccess_s
ms.date: 11/04/2016
apiname:
- _access_s
- _waccess_s
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
- waccess_s
- access_s
- _waccess_s
- _access_s
helpviewer_keywords:
- access_s function
- taccess_s function
- _taccess_s function
- waccess_s function
- _access_s function
- _waccess_s function
ms.assetid: fb3004fc-dcd3-4569-8b27-d817546e947e
ms.openlocfilehash: 17d19527323f3e97edecd22ca7c0a0262b1cfbad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62335689"
---
# <a name="accesss-waccesss"></a>_access_s, _waccess_s

Определяет разрешения на чтение и запись файлов. Это — версия функций [_access, _waccess](access-waccess.md) с усовершенствованиями системы безопасности, описанными в разделе [Возможности безопасности в CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Синтаксис

```C
errno_t _access_s(
   const char *path,
   int mode
);
errno_t _waccess_s(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Параметры

*path*<br/>
Путь к файлу или каталогу.

*mode*<br/>
Настройка разрешений.

## <a name="return-value"></a>Возвращаемое значение

Если файл имеет заданный режим, все функции возвращают значение 0. Если указанный файл не существует или недоступен в заданном режиме, функция возвращает код ошибки. Код ошибки выбирается из набора описанным ниже образом и присваивает `errno` такое же значение.

|Значение errno|Условие|
|-|-|
`EACCES`|Доступ запрещен. Настройка разрешений файла не допускает указанный доступ.
`ENOENT`|Имя файла или путь не найдены.
`EINVAL`|Недопустимый параметр.

Дополнительные сведения см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Примечания

При использовании с файлами, **_access_s** функция определяет, существует ли указанный файл и доступны в виде указанное значение из *режим*. При использовании с каталогами, **_access_s** только определяет, существует ли указанный каталог. В Windows 2000 и более поздних операционных системах, все каталоги доступ чтения и записи.

|значение режима|Проверяет файл на|
|----------------|---------------------|
|00|Существование.|
|02|Разрешение на запись.|
|04|Разрешение на чтение.|
|06|Разрешение на чтение и запись.|

Сами по себе разрешения на чтение или запись файла не обеспечивают возможность открывать файл. Например, если файл заблокирован другим процессом, может оказаться доступны, даже если **_access_s** возвращает 0.

**_waccess_s** — это двухбайтовая версия **_access_s**, где *путь* аргумент **_waccess_s** — строка расширенных символов. В противном случае **_waccess_s** и **_access_s** ведут себя одинаково.

Эти функции проверяют свои параметры. Если *путь* имеет значение NULL или *режим* не указывает действительный режим, вызывается обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции устанавливают параметр `errno` в значение `EINVAL` и возвращают значение `EINVAL`.

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Процедура Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess_s`|**_access_s**|**_access_s**|**_waccess_s**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательный заголовок|
|-------------|---------------------|---------------------|
|**_access_s**|\<io.h>|\<errno.h>|
|**_waccess_s**|\<wchar.h> или \<io.h>|\<errno.h>|

## <a name="example"></a>Пример

В этом примере используется **_access_s** для проверки файла с именем crt_access_s.на существование и возможность записи.

```C
// crt_access_s.c

#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
    errno_t err = 0;

    // Check for existence.
    if ((err = _access_s( "crt_access_s.c", 0 )) == 0 )
    {
        printf_s( "File crt_access_s.c exists.\n" );

        // Check for write permission.
        if ((err = _access_s( "crt_access_s.c", 2 )) == 0 )
        {
            printf_s( "File crt_access_s.c does have "
                      "write permission.\n" );
        }
        else
        {
            printf_s( "File crt_access_s.c does not have "
                      "write permission.\n" );
        }
    }
    else
    {
        printf_s( "File crt_access_s.c does not exist.\n" );
    }
}
```

```Output
File crt_access_s.c exists.
File crt_access_s.c does not have write permission.
```

## <a name="see-also"></a>См. также

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat Functions](stat-functions.md)