---
title: _ecvt
ms.date: 04/05/2018
apiname:
- _ecvt
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ecvt
helpviewer_keywords:
- _ecvt function
- numbers, converting
- converting double numbers
- ecvt function
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
ms.openlocfilehash: 36c9cb2e8cd9eb4dd67bb91e9e4dbd36d8d1fc8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605734"
---
# <a name="ecvt"></a>_ecvt

Преобразует **двойные** чисел в строку. Существует более безопасная версия этой функции, см. раздел [_ecvt_s](ecvt-s.md).

## <a name="syntax"></a>Синтаксис

```C
char *_ecvt(
   double value,
   int count,
   int *dec,
   int *sign
);
```

### <a name="parameters"></a>Параметры

*значение*<br/>
Число, которое требуется преобразовать.

*count*<br/>
Сохраненное число разрядов.

*dec*<br/>
Сохраненная позиция десятичной запятой.

*sign*<br/>
Знак преобразованного числа.

## <a name="return-value"></a>Возвращаемое значение

**_ecvt** возвращает указатель на строку разрядов; **NULL** Если произошла ошибка.

## <a name="remarks"></a>Примечания

**_Ecvt** функция преобразует число с плавающей запятой в строку символов. *Значение* параметром является номер с плавающей запятой для преобразования. Эта функция сохраняет до *число* цифры *значение* как строку и добавляет нуль-символ («\0»). Если количество цифр в *значение* превышает *число*, младший разряд округляется. Если доступно менее *число* цифр, строка дополняется нулями.

Общее число разрядов, возвращаемое **_ecvt** не может превышать **_CVTBUFSIZE**.

В строке сохраняются только цифры. Положение десятичной запятой и знак *значение* можно получить из *dec* и *входа* после вызова метода. *Dec* параметр указывает на целочисленное значение, отражающее положение десятичной запятой относительно начала строки. Ноль или отрицательное целое число означают, что десятичная запятая располагается слева от первой цифры. *Входа* указывает параметр в целое число, указывающее знак преобразованного числа. Если целочисленное значение равно 0, число является положительным. В противном случае число будет отрицательным.

Разница между **_ecvt** и **_fcvt** в интерпретацию *число* параметра. **_ecvt** интерпретирует *число* как общее число цифр в выходной строке, тогда как **_fcvt** интерпретирует *число* как количество цифр после десятичной запятой.

**_ecvt** и **_fcvt** используют для преобразования один статически выделенный буфер. Каждый вызов одной из этих подпрограмм уничтожает результат предыдущего вызова.

Эта функция проверяет свои параметры. Если *dec* или *входа* — **NULL**, или *число* равно 0, вызывается обработчик недопустимого параметра, как описано в разделе [параметр Проверка](../../c-runtime-library/parameter-validation.md). Если выполнение может быть продолжено, **errno** присваивается **EINVAL** и **NULL** возвращается.

## <a name="requirements"></a>Требования

|Функция|Обязательный заголовок|
|--------------|---------------------|
|**_ecvt**|\<stdlib.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

```C
// crt_ecvt.c
// compile with: /W3
// This program uses _ecvt to convert a
// floating-point number to a character string.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int     decimal,   sign;
   char    *buffer;
   int     precision = 10;
   double  source = 3.1415926535;

   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996
   // Note: _ecvt is deprecated; consider using _ecvt_s instead
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",
           source, buffer, decimal, sign );
}
```

```Output
source: 3.1415926535   buffer: '3141592654'  decimal: 1  sign: 0
```

## <a name="see-also"></a>См. также

[Преобразование данных](../../c-runtime-library/data-conversion.md)<br/>
[Поддержка чисел с плавающей запятой](../../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
