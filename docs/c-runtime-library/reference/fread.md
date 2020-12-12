---
description: 'Дополнительные сведения о: fread'
title: fread
ms.date: 4/2/2020
api_name:
- fread
- _o_fread
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fread
helpviewer_keywords:
- reading data [C++], from input streams
- fread function
- data [C++], reading from input stream
- streams [C++], reading data from
ms.assetid: 9a3c1538-93dd-455e-ae48-77c1e23c53f0
ms.openlocfilehash: 131dacd296d4e710ea1b91d9a8578ef06b76a341
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97314052"
---
# <a name="fread"></a>fread

Считывает данные из потока.

## <a name="syntax"></a>Синтаксис

```C
size_t fread(
   void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Параметры

*двойной*<br/>
Место хранения данных.

*size*<br/>
Размер элемента в байтах.

*count*<br/>
Максимальное число читаемых элементов.

*вышестоящий*<br/>
Указатель на структуру **FILE**.

## <a name="return-value"></a>Возвращаемое значение

**fread** возвращает число фактически считанных полных элементов, которое может быть меньше, *Если возникает ошибка или если конец* файла обнаружен до достижения *количества* обращений. Используйте функцию **feof** или **ferror** , чтобы отличать ошибку чтения от условия конца файла. Если параметр *size* или *Count* имеет значение 0, **fread** возвращает 0, а содержимое буфера не изменяется. Если *Stream* или *buffer* является пустым указателем, **fread** вызывает обработчик недопустимого параметра, как описано в разделе [Проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эта функция **устанавливает** **еинвал** и возвращает 0.

Дополнительные сведения об этих кодах ошибок см. в разделе [ \_ досеррно, код ошибки, \_ sys \_ еррлист и \_ sys \_ Нерр](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) .

## <a name="remarks"></a>Комментарии

Функция **fread** считывает до *подсчета* *размера* байтов из входного *потока* и сохраняет их в *буфер*. Указатель файла, связанный с *потоком* (при его наличии), увеличивается на число фактически считанных байтов. Если данный поток открыт в [текстовом режиме](../../c-runtime-library/text-and-binary-mode-file-i-o.md), то символы новой строки в стиле Windows преобразуются в символы новой строки в стиле UNIX. То есть пары символов возврата каретки и перевода строки (CRLF) заменяются символами перевода строки (LF). Замена не влияет на указатель файла или возвращаемое значение. В случае ошибки позиция указателя файла будет неопределенной. Значение частично считанного элемента не может быть определено.

При использовании в потоке текстового режима, если объем запрошенных данных (то есть  \* *число* размеров) больше или равен размеру внутреннего буфера **файла** \* (по умолчанию это 4096 байт, настраиваемый с помощью [setvbuf](../../c-runtime-library/reference/setvbuf.md)), потоковые данные копируются непосредственно в предоставленный пользователем буфер, а в этом буфере выполняется преобразование новой строки. Поскольку преобразованные данные могут быть короче, чем данные потока, скопированные в буфер, данные за *буфер* \[ *RETURN_VALUE* \* *Размер*] (где *RETURN_VALUE* является возвращаемым значением из **fread**) могут содержать непреобразованные данные из файла. По этой причине мы советуем использовать символьные данные, заканчивающиеся нулем, в *буфере* \[ *RETURN_VALUE* \* *size*], если цель буфера — использовать в качестве строки в стиле C. Дополнительные сведения о влиянии текстового и двоичного режимов см. в разделе [fopen](fopen-wfopen.md) .

Эта функция блокирует работу других потоков. Если требуется версия без блокировки, используйте **_fread_nolock**.

По умолчанию глобальное состояние этой функции ограничивается приложением. Чтобы изменить это, см. раздел [глобальное состояние в CRT](../global-state.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**fread**|\<stdio.h>|

Дополнительные сведения о совместимости см. в статье [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_fread.c
// This program opens a file named FREAD.OUT and
// writes 25 characters to the file. It then tries to open
// FREAD.OUT and read in 25 characters. If the attempt succeeds,
// the program displays the number of actual items read.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char list[30];
   int  i, numread, numwritten;

   // Open file in text mode:
   if( fopen_s( &stream, "fread.out", "w+t" ) == 0 )
   {
      for ( i = 0; i < 25; i++ )
         list[i] = (char)('z' - i);
      // Write 25 characters to stream
      numwritten = fwrite( list, sizeof( char ), 25, stream );
      printf( "Wrote %d items\n", numwritten );
      fclose( stream );

   }
   else
      printf( "Problem opening the file\n" );

   if( fopen_s( &stream, "fread.out", "r+t" ) == 0 )
   {
      // Attempt to read in 25 characters
      numread = fread( list, sizeof( char ), 25, stream );
      printf( "Number of items read = %d\n", numread );
      printf( "Contents of buffer = %.25s\n", list );
      fclose( stream );
   }
   else
      printf( "File could not be opened\n" );
}
```

```Output
Wrote 25 items
Number of items read = 25
Contents of buffer = zyxwvutsrqponmlkjihgfedcb
```

## <a name="see-also"></a>См. также раздел

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[Ввод-вывод текстовых и двоичных файлов](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
[fopen](fopen-wfopen.md)<br/>
[fwrite](fwrite.md)<br/>
[_read](read.md)<br/>
