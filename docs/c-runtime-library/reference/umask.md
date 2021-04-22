---
title: _umask
description: Справочник по API для _umask; Задает маску разрешений файла по умолчанию.
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: 8923e2a9ef489d35d1e7f55b91bfb632c0d22580
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099304"
---
# <a name="_umask"></a>_umask

Задает маску разрешений файла по умолчанию. Дополнительные сведения о более безопасной версии этой функции см. в разделе [_umask_s](umask-s.md) .

## <a name="syntax"></a>Синтаксис

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Параметры

*пмоде*<br/>
Параметр разрешения по умолчанию.

## <a name="return-value"></a>Возвращаемое значение

**_umask** возвращает предыдущее значение *пмоде*. Ошибки не возвращаются.

## <a name="remarks"></a>Комментарии

Функция **_umask** устанавливает маску разрешений файла для текущего процесса в режим, заданный параметром *пмоде*. Маска разрешений файла изменяет настройки разрешений для новых файлов, созданных с помощью **_creat**, **_open** или **_sopen**. Если бит в битовой маске равен 1, соответствующий бит в запрошенном значении разрешения имеет значение 0 (запрещено). Если бит в битовой маске равен 0, соответствующий бит остается без изменений. Параметр разрешения для нового файла не устанавливается до тех пор, пока файл не будет закрыт в первый раз.

Целочисленное выражение *пмоде* содержит одну или обе следующие константы манифеста, определенные в сис\стат. Высоты

|*пмоде*|Описание|
|-|-|
| **_S_IWRITE** | Разрешена запись. |
| **_S_IREAD** | Разрешено чтение. |
| **_S_IREAD** &#124; **_S_IWRITE** | Разрешены чтение и запись. |

Если заданы обе константы, они соединяются с оператором побитового или ( **&#124;** ). Если аргумент *пмоде* имеет значение **_S_IREAD**, чтение запрещено (файл доступен только для записи). Если аргумент *пмоде* имеет значение **_S_IWRITE**, запись запрещена (файл доступен только для чтения). Например, если в маске установлен бит записи, все новые файлы будут доступны только для чтения. Обратите внимание, что в операционных системах MS-DOS и Windows все файлы доступны для чтения; невозможно предоставить разрешение только на запись. Поэтому Установка бита чтения с **_umask** не влияет на режимы файла.

Если *пмоде* не является сочетанием одной из констант манифеста или включает другой набор констант, функция будет просто игнорировать их.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Библиотеки

Все версии [библиотек времени выполнения языка C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Пример

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>См. также раздел

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
[Низкоуровневые операции ввода-вывода](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[Функция _creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
