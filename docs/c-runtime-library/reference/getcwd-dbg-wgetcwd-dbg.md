---
title: _getcwd_dbg, _wgetcwd_dbg
ms.date: 11/04/2016
apiname:
- _wgetcwd_dbg
- _getcwd_dbg
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getcwd_dbg
- _wgetcwd_dbg
- getcwd_dbg
- wgetcwd_dbg
helpviewer_keywords:
- wgetcwd_dbg function
- working directory
- _getcwd_dbg function
- getcwd_dbg function
- current working directory
- _wgetcwd_dbg function
- directories [C++], current working
ms.assetid: 8d5d151f-d844-4aa6-a28c-1c11a22dc00d
ms.openlocfilehash: 9616c5f7e29b4f003d3943ba058d1f1a1d5adb5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287232"
---
# <a name="getcwddbg-wgetcwddbg"></a>_getcwd_dbg, _wgetcwd_dbg

Отладочные версии функций [_getcwd, _wgetcwd](getcwd-wgetcwd.md) (доступны только во время отладки).

## <a name="syntax"></a>Синтаксис

```C
char *_getcwd_dbg(
   char *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wgetcwd_dbg(
   wchar_t *buffer,
   int maxlen,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Параметры

*buffer*<br/>
Место хранения пути.

*MaxLen*<br/>
Максимальная длина пути в символах: **char** для **_getcwd_dbg** и **wchar_t** для **_wgetcwd_dbg**.

*blockType*<br/>
Запрошенный тип блока памяти: **_CLIENT_BLOCK** или **_NORMAL_BLOCK**.

*filename*<br/>
Указатель на имя исходного файла, который запросил операцию выделения или **NULL**.

*linenumber*<br/>
Номер строки в файле источника, в которой была запрошена операция выделения или **NULL**.

## <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на *буфера*. Объект **NULL** возвращаемое значение указывает на ошибку, и **errno** устанавливается в значение **ENOMEM**, том, что не хватает памяти для выделения *maxlen* байт (при **NULL** передан аргумент *буфера*), или к **ERANGE**, том, что путь не длиннее *maxlen*  символов.

Дополнительные сведения см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Примечания

**_Getcwd_dbg** и **_wgetcwd_dbg** функции аналогичны **_getcwd** и **_wgetcwd** за исключением того, что, когда **_ Отладка** будет определен, эти функции используют отладочную версию **malloc** и **_malloc_dbg** для выделения памяти в том случае, если **NULL** передается в качестве Первый параметр. Дополнительные сведения см. в разделе [_malloc_dbg](malloc-dbg.md).

Как правило, явно вызывать эти функции не требуется. Вместо этого можно определить **_CRTDBG_MAP_ALLOC** флаг. Когда **_CRTDBG_MAP_ALLOC** определен, вызовы функций **_getcwd** и **_wgetcwd** сопоставляются **_getcwd_dbg** и **_ wgetcwd_dbg**, соответственно, с помощью *blockType* присвоено **_NORMAL_BLOCK**. Таким образом, не нужно явно вызывать эти функции, если вы не хотите пометить блоки кучи как **_CLIENT_BLOCK**. Дополнительные сведения см. в разделе [Типы блоков в отладочной куче](/visualstudio/debugger/crt-debug-heap-details).

## <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Процедура Tchar.h|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd_dbg**|**_getcwd_dbg**|**_getcwd_dbg**|**_wgetcwd_dbg**|

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_getcwd_dbg**|\<crtdbg.h>|
|**_wgetcwd_dbg**|\<crtdbg.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[_getcwd, _wgetcwd](getcwd-wgetcwd.md)<br/>
[Управление каталогами](../../c-runtime-library/directory-control.md)<br/>
[Версии отладки функций выделения кучи](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
