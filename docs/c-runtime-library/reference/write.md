---
title: _write
ms.date: 11/04/2016
apiname:
- _write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: b3fa53b21d4ea23c5f8e59de673f4074deedb505
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383416"
---
# <a name="write"></a>_write

Записывает данные в файл.

## <a name="syntax"></a>Синтаксис

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Параметры

*fd*<br/>
Дескриптор файла, в который записываются данные.

*buffer*<br/>
Записываемые данные.

*count*<br/>
Число байт.

## <a name="return-value"></a>Возвращаемое значение

В случае успешного выполнения **_write** возвращает число фактически записанных байтов. Если объем фактического места на диске меньше, чем размер буфера, функция пытается записать на диск, **_write** завершается ошибкой и не сбрасывается содержимое буфера на диск. Возвращаемое значение-1 указывает на ошибку. Если передается недопустимый параметр, эта функция вызывает обработчик недопустимых параметров, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, функция возвращает -1 и **errno** присваивается одно из трех значений: **Значение EBADF**, который означает, что дескриптор файла является недопустимым, или файл не открыт для записи; **ENOSPC**, что означает не недостаточно места на устройстве для операции; или **EINVAL**, означающее, что *буфера* был пустым указателем или что нерегулярного *число* байтов был передан для записи в файл в режиме Юникода.

Дополнительные сведения об этих и других кодах возврата см. в разделе [errno, _doserrno, _sys_errlist и _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Если файл открыт в текстовом режиме, каждый символ перевода строки заменяется символом возврата каретки - перевода строки пары в выходных данных. Эта замена не влияет на возвращаемое значение.

Когда файл открыт в режиме преобразования Юникода — например, если *fd* открывается с помощью **_open** или **_sopen** и параметра режима, который включает в себя **_O_ WTEXT**, **_O_U16TEXT**, или **_O_U8TEXT**, или если он открыт с помощью **fopen** и параметра режима, который включает в себя **ccs = Юникод**, **ccs = UTF-16LE**, или **ccs = UTF-8**, или если режим изменяется на режим преобразования Юникода с помощью **_setmode**—*буфера* интерпретируется как указатель на массив **wchar_t** , содержащий **UTF-16** данных. Попытка записи нечетного числа байт в этом режиме приводит к возникновению ошибки проверки параметра.

## <a name="remarks"></a>Примечания

**_Write** функцию записи *число* байтов из *буфера* в файл, связанный с *fd*. Операция записи начинается с текущего положения указателя файла (при наличии), связанного с данным файлом. Если файл открыт для добавления, операция начинается с текущего конца файла. После выполнения операции записи указатель файла увеличивается на число фактически записанных байт.

При записи в файлах, открытых в текстовом режиме, **_write** обрабатывает символ CTRL + Z как логический конец файла. При записи в устройство **_write** обрабатывает символ CTRL + Z в буфере как символ окончания вывода.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_write**|\<io.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occured
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>См. также

[Низкоуровневый ввод-вывод](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
