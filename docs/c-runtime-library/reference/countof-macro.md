---
title: Макрос _countof
ms.date: 03/22/2018
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
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 60b4350d6cf14a545de67de0bdaee70ee2099006
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536140"
---
# <a name="countof-macro"></a>Макрос _countof

Вычисляет количество элементов в статически выделенном массиве.

## <a name="syntax"></a>Синтаксис

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>Параметры

*array*<br/>
Имя массива.

## <a name="return-value"></a>Возвращаемое значение

Число элементов в массиве, выраженное как **size_t**.

## <a name="remarks"></a>Примечания

**_countof** реализуется как макрос препроцессора подобный функции. Версия C++ имеет дополнительный шаблон механизм для обнаружения во время компиляции, если вместо статически объявленным массива передается указатель.

Убедитесь, что *массива* фактически является массивом, а не указатель. В языке C **_countof** дает ошибочные результаты, если *массива* является указателем. В C++ **_countof** возникает ошибка компиляции, если *массива* является указателем.  Массив передается в качестве параметра в функции *decays к указателю*, что означает, что в функции, нельзя использовать **_countof** чтобы определить область массива.

## <a name="requirements"></a>Требования

|Макрос|Обязательный заголовок|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>Пример

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>См. также

[Оператор sizeof](../../cpp/sizeof-operator.md)<br/>
