---
title: fscanf, _fscanf_l, fwscanf, _fwscanf_l
ms.date: 11/04/2016
apiname:
- fscanf
- _fwscanf_l
- _fscanf_l
- fwscanf
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
apitype: DLLExport
f1_keywords:
- fscanf
- fwscanf
- _ftscanf_l
- _fwscanf_l
- _ftscanf
- _fscanf_l
helpviewer_keywords:
- fscanf function
- fwscanf function
- formatted data [C++], reading from streams
- ftscanf_l function
- _ftscanf_l function
- _fwscanf_l function
- data [CRT], reading from streams
- _fscanf_l function
- ftscanf function
- fscanf_l function
- streams [C++], reading formatted data from
- _ftscanf function
- fwscanf_l function
ms.assetid: 9004e978-6c5f-4bb2-98fd-51e5948933f2
ms.openlocfilehash: 5be3f4107d2f05c1863c9c8303ac89e184590baa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594519"
---
# <a name="fscanf-fscanfl-fwscanf-fwscanfl"></a>fscanf, _fscanf_l, fwscanf, _fwscanf_l

Считывают форматированные данные из потока. Доступны более безопасные версии этих функций; см. раздел [fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md).

## <a name="syntax"></a>Синтаксис

```C
int fscanf(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fscanf_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int fwscanf(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwscanf_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Параметры

*поток*<br/>
Указатель на структуру **FILE**.

*format*<br/>
Строка управления форматом.

*Аргумент*<br/>
Необязательные аргументы.

*locale*<br/>
Используемый языковой стандарт.

## <a name="return-value"></a>Возвращаемое значение

Каждая из этих функций возвращает количество полей, которые были успешно преобразованы и присвоены; возвращаемое значение не включает поля, которые были считаны, но не были присвоены. Возвращаемое значение 0 указывает, что поля не были назначены. Если возникает ошибка, или если достигнут конец потока файла до первого преобразования, возвращается значение **EOF** для **fscanf** и **fwscanf**.

Эти функции проверяют свои параметры. Если *поток* или *формат* является пустым указателем, вызывается обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, эти функции возвращают **EOF** и задайте **errno** для **EINVAL**.

## <a name="remarks"></a>Примечания

**Fscanf** функция считывает данные из текущей позиции *поток* в места, указанные функцией *аргумент* (если таковые имеются). Каждый *аргумент* должен быть указателем на переменную-тип, соответствующий спецификатору типа в *формат*. *формат* определяет интерпретацию входных данных, поля и имеет те же форму и функцию как *формат* аргумент для **scanf**; см. в разделе [scanf](scanf-scanf-l-wscanf-wscanf-l.md) для Описание *формат*.

**fwscanf** — это двухбайтовая версия **fscanf**; аргумент format для **fwscanf** — строка расширенных символов. Эти функции ведут себя одинаково, если поток открыт в режиме ANSI. **fscanf** сейчас не поддерживает ввод из потока ЮНИКОДА.

Версии этих функций с **_l** суффиксом идентичны, за исключением того, что они используют переданный параметр языкового стандарта вместо языкового стандарта текущего потока.

### <a name="generic-text-routine-mappings"></a>Сопоставления подпрограмм обработки обычного текста

|Подпрограмма TCHAR.H|_UNICODE и _MBCS не определены|_MBCS определено|_UNICODE определено|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftscanf**|**fscanf**|**fscanf**|**fwscanf**|
|**_ftscanf_l**|**_fscanf_l**|**_fscanf_l**|**_fwscanf_l**|

Дополнительные сведения см. в разделе [поля спецификации формата — функции scanf и Wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**fscanf**, **_fscanf_l**|\<stdio.h>|
|**fwscanf**, **_fwscanf_l**|\<stdio.h> или \<wchar.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_fscanf.c
// compile with: /W3
// This program writes formatted
// data to a file. It then uses fscanf to
// read the various data back from the file.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long l;
   float fp;
   char s[81];
   char c;

   if( fopen_s( &stream, "fscanf.out", "w+" ) != 0 )
      printf( "The file fscanf.out was not opened\n" );
   else
   {
      fprintf( stream, "%s %ld %f%c", "a-string",
               65000, 3.14159, 'x' );
      // Security caution!
      // Beware loading data from a file without confirming its size,
      // as it may lead to a buffer overrun situation.

      // Set pointer to beginning of file:
      fseek( stream, 0L, SEEK_SET );

      // Read data back from file:
      fscanf( stream, "%s", s );   // C4996
      fscanf( stream, "%ld", &l ); // C4996

      fscanf( stream, "%f", &fp ); // C4996
      fscanf( stream, "%c", &c );  // C4996
      // Note: fscanf is deprecated; consider using fscanf_s instead

      // Output data read:
      printf( "%s\n", s );
      printf( "%ld\n", l );
      printf( "%f\n", fp );
      printf( "%c\n", c );

      fclose( stream );
   }
}
```

```Output
a-string
65000
3.141590
x
```

## <a name="see-also"></a>См. также

[Потоковый ввод-вывод](../../c-runtime-library/stream-i-o.md)<br/>
[_cscanf, _cscanf_l, _cwscanf, _cwscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[scanf, _scanf_l, wscanf, _wscanf_l](scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
