---
title: _lsearch
ms.date: 11/04/2016
apiname:
- _lsearch
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch
- lsearch
helpviewer_keywords:
- _lsearch function
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- linear searches
- searching, linear
- lsearch function
ms.assetid: 8200f608-159a-46f0-923b-1a37ee1af7e0
ms.openlocfilehash: 340e8ac382972b15acc52013d5d6a51352db969c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285660"
---
# <a name="lsearch"></a>_lsearch

Выполняет линейный поиск значения и добавляет значение в конец списка, если оно не найдено. Существует более безопасная версия этой функции; см. раздел [_lsearch_s](lsearch-s.md).

## <a name="syntax"></a>Синтаксис

```C
void *_lsearch(
   const void *key,
   void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Параметры

*key*<br/>
Искомый объект.

*base*<br/>
Указатель на начало массива, где будет производиться поиск.

*номер*<br/>
Число элементов.

*width*<br/>
Ширина каждого элемента массива.

*compare*<br/>
Указатель на подпрограмму сравнения. Первый параметр — это указатель на ключ для поиска. Второй параметр — это указатель на элемент массива, который будет сравниваться с ключом.

## <a name="return-value"></a>Возвращаемое значение

Если ключ найден, **_lsearch** возвращает указатель на элемент массива в *базового* , соответствующий *ключ*. Если ключ не найден, **_lsearch** возвращает указатель на вновь добавленный в конец массива элемент.

## <a name="remarks"></a>Примечания

**_Lsearch** функция выполняет линейный поиск значения *ключ* массива *номер* элементов, каждый из которых *ширины* байт. В отличие от **bsearch**, **_lsearch** не требует, чтобы сортировать массив. Если *ключ* не найден, **_lsearch** добавляет его в конец массива и увеличивает *номер*.

*Сравнения* аргумент — указатель на предоставляемую пользователем подпрограмму, которая сравнивает два элемента массива и возвращает значение, указывающее их связь. **_lsearch** вызовы *сравнения* рутинных один или несколько раз во время поиска, передавая указатели на два элемента массива при каждом вызове. *Сравнение* должна сравнивать элементы и возвращать ненулевое значение (то есть элементы различаются) или 0 (если элементы идентичны).

Эта функция проверяет свои параметры. Если *сравнения*, *ключ* или *номер* — **NULL**, или если *базового* является **NULL**и *номер* не равно нулю, или если *ширины* меньше нуля, вызывается обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, **errno** присваивается **EINVAL** и функция возвращает **NULL**.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_lsearch**|\<search.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_lsearch.c
#include <search.h>
#include <string.h>
#include <stdio.h>

int compare( const void *arg1, const void *arg2 );

int main(void)
{
   char * wordlist[4] = { "hello", "thanks", "bye" };
                            // leave room to grow...
   int n = 3;
   char **result;
   char *key = "extra";
   int i;

   printf( "wordlist before _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );

   result = (char **)_lsearch( &key, wordlist,
                      &n, sizeof(char *), compare );

   printf( "wordlist after _lsearch:" );
   for( i=0; i<n; ++i ) printf( " %s", wordlist[i] );
   printf( "\n" );
}

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}
```

```Output
wordlist before _lsearch: hello thanks bye
wordlist after _lsearch: hello thanks bye extra
```

## <a name="see-also"></a>См. также

[Сортировка и поиск](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch](bsearch.md)<br/>
[_lfind](lfind.md)<br/>
[_lsearch_s](lsearch-s.md)<br/>
