---
description: 'Дополнительные сведения: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32'
title: _stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32
ms.date: 4/2/2020
api_name:
- _wstat64
- _stati64
- _stat32
- _stat32i64
- _stat
- _wstati64
- _wstat32
- _wstat64i32
- _wstat
- _stat64
- _stat64i32
- _wstat32i64
- _o__stat32
- _o__stat32i64
- _o__stat64
- _o__stat64i32
- _o__wstat32
- _o__wstat32i64
- _o__wstat64
- _o__wstat64i32
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tstat32
- tstat
- _tstat64i32
- tstati64
- _wstat64
- _wstat32
- wstati64
- tstat64
- _stati64
- _wstat
- wstat64i32
- stat32i64
- tstat32i64
- _tstat
- _wstati64
- _tstati64
- _wstat32i64
- wstat32
- _wstat64i32
- _stat
- _tstat32
- stat64i32
- wstat64
- stat
- _stat32i64
- _stat32
- stati64
- wstat
- _stat64i32
- stat32
- _tstat32i64
- tstat64i32
- _tstat64
- _stat64
- stat/_stat
- stat/_stat32
- stat/_stat64
- stat/_stati64
- stat/_stat32i64
- stat/_stat64i32
- stat/_wstat
- stat/_wstat32
- stat/_wstat64
- stat/_wstati64
- stat/_wstat32i64
- stat/_wstat64i32
helpviewer_keywords:
- files [C++], status information
- _stat function
- _wstat function
- _stat64i32 function
- tstat function
- _tstat64i32 function
- _stati64 function
- _stat64 function
- tstati64 function
- wstati64 function
- wstat64 function
- _wstat64i32 function
- _tstat32i64 function
- _stat32i64 function
- stat function
- status of files
- _tstat32 function
- tstat64 function
- _wstat64 function
- _tstat function
- _stat32 function
- wstat function
- _wstat32i64 function
- _tstati64 function
- _wstat32 function
- stat64 function
- stati64 function
- _wstati64 function
- _tstat64 function
- files [C++], getting status information
ms.assetid: 99a75ae6-ff26-47ad-af70-5ea7e17226a5
ms.openlocfilehash: 572e1d5f2f1c4eadf5f78c696c78630b84b90791
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099226"
---
# <a name="_stat-_stat32-_stat64-_stati64-_stat32i64-_stat64i32-_wstat-_wstat32-_wstat64-_wstati64-_wstat32i64-_wstat64i32"></a>_stat, _stat32, _stat64, _stati64, _stat32i64, _stat64i32, _wstat, _wstat32, _wstat64, _wstati64, _wstat32i64, _wstat64i32

Получает сведения о состоянии файла.

## <a name="syntax"></a>Синтаксис

```C
int _stat(
   const char *path,
   struct _stat *buffer
);
int _stat32(
   const char *path,
   struct __stat32 *buffer
);
int _stat64(
   const char *path,
   struct __stat64 *buffer
);
int _stati64(
   const char *path,
   struct _stati64 *buffer
);
int _stat32i64(
   const char *path,
   struct _stat32i64 *buffer
);
int _stat64i32(
   const char *path,
   struct _stat64i32 *buffer
);
int _wstat(
   const wchar_t *path,
   struct _stat *buffer
);
int _wstat32(
   const wchar_t *path,
   struct __stat32 *buffer
);
int _wstat64(
   const wchar_t *path,
   struct __stat64 *buffer
);
int _wstati64(
   const wchar_t *path,
   struct _stati64 *buffer
);
int _wstat32i64(
   const wchar_t *path,
   struct _stat32i64 *buffer
);
int _wstat64i32(
   const wchar_t *path,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>Параметры

*путь*<br/>
Указатель на строку, содержащую путь к существующему файлу или каталогу.

*двойной*<br/>
Указатель на структуру, в которой хранятся результаты.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает 0, если получена информация о состоянии файла. Возвращаемое значение, равное-1, указывает на ошибку. в этом случае для параметра « **еноент** **» задано** значение, указывающее, что не удалось найти имя файла или путь. Возвращаемое значение **еинвал** указывает на недопустимый параметр; в этом случае в этом случае **также устанавливается значение** **еинвал** .

Дополнительные сведения об этих и других кодах возврата см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

Отметка даты файла может быть представлена, если она позже, чем полночь, 1 января 1970 и до 23:59:59, 31 декабря 3000, UTC, если не используется **_stat32** или **_wstat32** или определены **_USE_32BIT_TIME_T**. в этом случае дата может быть представлена только до 23:59:59 18 января 2038, UTC.

## <a name="remarks"></a>Комментарии

Функция **_stat** получает сведения о файле или каталоге, указанные по *пути* , и сохраняет их в структуре, на которую указывает *buffer*. **_stat** автоматически обрабатывает строковые аргументы многобайтовых символов соответствующим образом, распознает последовательности многобайтовых символов в соответствии с используемой в данный момент многобайтовой кодовой страницей.

**_wstat** — это версия **_stat** для расширенных символов; Аргумент *пути* к **_wstat** является строкой расширенных символов. поведение **_wstat** и **_stat** идентично, за исключением того, что **_wstat** не обрабатывает строки многобайтовых символов.

Варианты этих функций поддерживают 32- или 64-разрядные типы времени и 32- или 64-разрядные значения длины файлов. Первый числовой суффикс (**32** или **64**) указывает размер используемого типа времени; Вторым суффиксом является либо **I32** , либо **I64**, указывающий, представлен ли размер файла как 32-разрядное или 64-разрядное целое число.

**_stat** эквивалентна **_stat64i32**, а **`struct`** **_stat** содержит 64-разрядное время. Это справедливо, если не определено **_USE_32BIT_TIME_T** , в этом случае действует старое поведение; **_stat** использует 32-разрядное время, а **`struct`** **_stat** содержит 32-бит времени. То же справедливо для **_stati64**.

> [!NOTE]
> **_wstat** не работает с символической ссылкой Windows Vista. В таких случаях **_wstat** всегда будет сообщать размер файла, равный 0. **_stat** правильно работает с символической ссылкой.

Эта функция проверяет свои параметры. Если *путь* или *буфер* имеют **значение NULL**, вызывается обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md).

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>Варианты типов времени и типов длины файлов в функции _stat

|Функции|Определена ли директива _USE_32BIT_TIME_T?|Тип времени|Тип длины файла|
|---------------|------------------------------------|---------------|----------------------|
|**_stat**, **_wstat**|Не определено|64-разрядная|32-разрядная версия|
|**_stat**, **_wstat**|Определено|32-битная|32-битная|
|**_stat32**, **_wstat32**|Не затрагивается определением макроса|32-битная|32-битная|
|**_stat64**, **_wstat64**|Не затрагивается определением макроса|64-разрядная система|64-разрядная система|
|**_stati64**, **_wstati64**|Не определено|64-разрядная система|64-разрядная система|
|**_stati64**, **_wstati64**|Определено|32-разрядная версия|64-разрядная версия|
|**_stat32i64**, **_wstat32i64**|Не затрагивается определением макроса|32-разрядная версия|64-разрядная версия|
|**_stat64i32**, **_wstat64i32**|Не затрагивается определением макроса|64-разрядная|32-разрядная версия|

### <a name="generic-text-routine-mappings"></a>Универсальное текстовое сопоставление функций

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstat**|**_stat**|**_stat**|**_wstat**|
|**_tstat64**|**_stat64**|**_stat64**|**_wstat64**|
|**_tstati64**|**_stati64**|**_stati64**|**_wstati64**|
|**_tstat32i64**|**_stat32i64**|**_stat32i64**|**_wstat32i64**|
|**_tstat64i32**|**_stat64i32**|**_stat64i32**|**_wstat64i32**|

Структура **_stat** , определенная в сис\стат. H включает следующие поля.

|Поле|Описание|
|-|-|
| **st_gid** | Числовой идентификатор группы, которой принадлежит файл (только для UNIX). В системах Windows это поле всегда равно нулю. Перенаправленный файл классифицируется как файл Windows. |
| **st_atime** | Время последнего доступа к файлу. Действительно на дисках, отформатированных в файловой системе NTFS, но не в FAT. |
| **st_ctime** | Время создания файла. Действительно на дисках, отформатированных в файловой системе NTFS, но не в FAT. |
| **st_dev** | Номер диска, содержащего файл (то же, что **st_rdev**). |
| **st_ino** | Номер информационного узла ( **иноде**) для файла (относящийся к UNIX). В файловых системах UNIX **иноде** описывает отметки даты и времени файла, разрешения и содержимое. Если файлы жестко связаны друг с другом, они используют одни и те же **иноде**. **Иноде** и, следовательно, **st_ino**, не имеет смысла в файловых системах FAT, HPFS или NTFS. |
| **st_mode** | Битовая маска для информации о файловом режиме. Бит **_S_IFDIR** задается, если *путь* указывает каталог. бит **_S_IFREG** задается, если *путь* указывает на обычный файл или устройство. Пользовательские биты чтения/записи устанавливаются в соответствии с режимом разрешений файла; пользовательские биты выполнения устанавливаются согласно расширению имени файла. |
| **st_mtime** | Время последнего изменения файла. |
| **st_nlink** | Всегда имеет значение 1 в файловых системах, отличных от NTFS. |
| **st_rdev** | Номер диска, содержащего файл (то же, что **st_dev**). |
| **st_size** | Размер файла в байтах; 64-разрядное целое число для вариаций с суффиксом **I64** . |
| **st_uid** | Числовой идентификатор пользователя, который владеет файлом (только для UNIX). В системах Windows это поле всегда будет равно нулю. Перенаправленный файл классифицируется как файл Windows. |

Если *путь* относится к устройству, **st_size**, различные поля времени, **st_dev** и **st_rdev** поля в структуре **_stat** не имеют смысла. Поскольку STAT.H использует тип [_dev_t](../../c-runtime-library/standard-types.md), который определен в TYPES.H, в коде необходимо включить TYPES.H перед STAT.H.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательные заголовки|
|-------------|---------------------|----------------------|
|**_stat**, **_stat32**, **_stat64**, **_stati64**, **_stat32i64**, **_stat64i32**|\<sys/types.h> за которым следует \<sys/stat.h>|\<errno.h>|
|**_wstat**, **_wstat32**, **_wstat64**, **_wstati64**, **_wstat32i64**, **_wstat64i32**|\<sys/types.h> за которым следует \<sys/stat.h> или \<wchar.h>|\<errno.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_stat.c
// This program uses the _stat function to
// report information about the file named crt_stat.c.

#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
   struct _stat buf;
   int result;
   char timebuf[26];
   char* filename = "crt_stat.c";
   errno_t err;

   // Get data associated with "crt_stat.c":
   result = _stat( filename, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      perror( "Problem getting information" );
      switch (errno)
      {
         case ENOENT:
           printf("File %s not found.\n", filename);
           break;
         case EINVAL:
           printf("Invalid parameter to _stat.\n");
           break;
         default:
           /* Should never be reached. */
           printf("Unexpected error in _stat.\n");
      }
   }
   else
   {
      // Output some of the statistics:
      printf( "File size     : %ld\n", buf.st_size );
      printf( "Drive         : %c:\n", buf.st_dev + 'A' );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid arguments to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
}
```

```Output
File size     : 732
Drive         : C:
Time modified : Thu Feb 07 14:39:36 2002
```

## <a name="see-also"></a>См. также раздел

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_setmbcp](setmbcp.md)<br/>
