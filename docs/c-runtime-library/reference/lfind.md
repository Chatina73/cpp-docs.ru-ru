---
title: _lfind
ms.date: 11/04/2016
apiname:
- _lfind
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
- lfind
- _lfind
helpviewer_keywords:
- linear searching
- lfind function
- arrays [CRT], searching
- searching, linear
- finding keys in arrays
- _lfind function
ms.assetid: a40ece70-1674-4b75-94bd-9f57cfff18f2
ms.openlocfilehash: 1508d54d6b2f2566e4aee3afef02af45b28e4f48
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579170"
---
# <a name="lfind"></a>_lfind

Выполняет линейный поиск указанного ключа. Существует более безопасная версия этой функции; см. раздел [_lfind_s](lfind-s.md).

## <a name="syntax"></a>Синтаксис

```C
void *_lfind(
   const void *key,
   const void *base,
   unsigned int *num,
   unsigned int width,
   int (__cdecl *compare)(const void *, const void *)
);
```

### <a name="parameters"></a>Параметры

*key*<br/>
Искомый объект.

*base*<br/>
Указатель на начало данных, где будет производиться поиск.

*номер*<br/>
Число элементов массива.

*width*<br/>
Ширина элементов массива.

*compare*<br/>
Указатель на подпрограмму сравнения. Первый параметр — это указатель на ключ для поиска. Второй параметр — это указатель на элемент массива, который будет сравниваться с ключом.

## <a name="return-value"></a>Возвращаемое значение

Если ключ найден, **_lfind** возвращает указатель на элемент массива в *базового* , соответствующий *ключ*. Если ключ не найден, **_lfind** возвращает **NULL**.

## <a name="remarks"></a>Примечания

**_Lfind** функция выполняет линейный поиск значения *ключ* массива *номер* элементов, каждый из которых *ширины* байт. В отличие от **bsearch**, **_lfind** не требует, чтобы сортировать массив. *Базового* аргумент является указателем на базовый массив для поиска. *Сравнения* аргумент — указатель на предоставляемую пользователем подпрограмму, которая сравнивает два элемента массива и возвращает значение, указывающее их связь. **_lfind** вызовы *сравнения* рутинных один или несколько раз во время поиска, передавая указатели на два элемента массива при каждом вызове. *Сравнения* подпрограмма должна сравнивать элементы и возвращать ненулевое значение (то есть элементы различаются) или 0 (если элементы идентичны).

Эта функция проверяет свои параметры. Если *сравнения*, *ключ* или *номер* — **NULL**, или если *базового* является **NULL**и *номер* не равно нулю, или если *ширины* меньше нуля, вызывается обработчик недопустимого параметра, как описано в разделе [проверка параметров](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, **errno** присваивается **EINVAL** и функция возвращает **NULL**.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_lfind**|\<search.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_lfind.c
// This program uses _lfind to search a string array
// for an occurrence of "hello".

#include <search.h>
#include <string.h>
#include <stdio.h>

int compare(const void *arg1, const void *arg2 )
{
   return( _stricmp( * (char**)arg1, * (char**)arg2 ) );
}

int main( )
{
   char *arr[] = {"Hi", "Hello", "Bye"};
   int n = sizeof(arr) / sizeof(char*);
   char **result;
   char *key = "hello";

   result = (char **)_lfind( &key, arr,
                      &n, sizeof(char *), compare );

   if( result )
      printf( "%s found\n", *result );
   else
      printf( "hello not found!\n" );
}
```

```Output
Hello found
```

## <a name="see-also"></a>См. также

[Сортировка и поиск](../../c-runtime-library/searching-and-sorting.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[bsearch](bsearch.md)<br/>
[_lsearch](lsearch.md)<br/>
[qsort](qsort.md)<br/>
