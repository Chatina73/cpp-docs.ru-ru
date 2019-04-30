---
title: _setmode
ms.date: 11/04/2016
apiname:
- _setmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 67cca27ba03a99d7e192d438a98f1bb3a93845ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356408"
---
# <a name="setmode"></a>_setmode

Задает режим преобразования файлов.

## <a name="syntax"></a>Синтаксис

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Параметры

*fd*<br/>
Дескриптор файла.

*mode*<br/>
Новый режим преобразования.

## <a name="return-value"></a>Возвращаемое значение

При успешном выполнении возвращает предыдущий режим преобразования.

Если функции переданы недопустимые параметры, вызывается обработчик недопустимого параметра, как описано в разделе [Parameter Validation](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эта функция возвращает -1 и задает **errno** либо **значение EBADF**, который указывает недопустимый дескриптор файла, или **EINVAL**, который Указывает на недопустимый *режим* аргумент.

Дополнительные сведения об этих и других кодах возврата см. в разделе [_doserrno, errno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Примечания

**_Setmode** функция задает *режим* нужный режим преобразования для файла, указанного *fd*. Передача **_O_TEXT** как *режим* задается текстовый (преобразованный) режим. Каретки возврата строки веб-канала (CR-LF) преобразуются в один символ перевода на входе строки. Символы перевода строки преобразуются в комбинацию CR-LF в выводе. Передача **_O_BINARY** наборов двоичном (непреобразованном) режиме, в котором такие преобразования подавляются.

Вы также можете передать **_O_U16TEXT**, **_O_U8TEXT**, или **режиме _O_WTEXT** включить режим Юникода, как показано во втором примере далее в этом документе.

> [!CAUTION]
> Режим Юникода — для функций широкая печати (например, `wprintf`) и не поддерживается для узкой функций печати. Использование функции узкий печати в режиме потока Юникода активирует assert.

**_setmode** обычно используется для изменения нужный режим преобразования по умолчанию для **stdin** и **stdout**, но его можно использовать для любого файла. Если применить **_setmode** чтобы дескриптор файла для потока, вызовите **_setmode** перед выполнением любых операций ввода-вывода на поток.

> [!CAUTION]
> Если вы записываете данные в файловый поток, необходимо явно сбросить код с помощью [fflush](fflush.md) перед использованием **_setmode** для изменения режима. Если не выполнить сброс кода, может возникнуть непредвиденное поведение. Если данные не записывались в поток, выполнять сброс кода не нужно.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|Необязательные заголовки|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>Пример

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>См. также

[Обработка файлов](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
