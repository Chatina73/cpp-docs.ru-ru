---
title: clog, clogf, clogl
ms.date: 11/04/2016
apiname:
- clog
- clogf
- clogl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clog
- clogf
- clogl
- complex/clog
- complex/clogf
- complex/clogl
helpviewer_keywords:
- clog function
- clogf function
- clogl function
ms.assetid: 870b9b0b-6618-46f3-bfcf-da595cbd5e18
ms.openlocfilehash: fcbc9ba7984898d51f7a3d0beb5ef7c8b6d6892c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636557"
---
# <a name="clog-clogf-clogl"></a>clog, clogf, clogl

Извлекает натуральный логарифм комплексного числа, ветви которого заканчиваются в отрицательной части реальной оси.

## <a name="syntax"></a>Синтаксис

```C
_Dcomplex clog(
   _Dcomplex z
);
_Fcomplex clog(
   _Fcomplex z
);  // C++ only
_Lcomplex clog(
   _Lcomplex z
);  // C++ only
_Fcomplex clogf(
   _Fcomplex z
);
_Lcomplex clogl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Параметры

*z*<br/>
Основание логарифма.

## <a name="return-value"></a>Возвращаемое значение

Натуральный логарифм *z*. Результат неограничен на реальной оси и находится в интервале [-iπ, + iπ] на мнимой оси.

Возможны следующие возвращаемые значения:

|параметр z|Возвращаемое значение|
|-----------------|------------------|
|Положительное число|Десятичный логарифм z|
|Нуль|- ∞|
|Отрицательное число|NaN|
|NaN|NaN|
|+ ∞|+ ∞|

## <a name="remarks"></a>Примечания

Так как C++ допускает перегрузку, можно вызывать перегрузки **clog** , принимающие и возвращающие **_Fcomplex** и **_Lcomplex** значения. В программе на языке C **clog** всегда принимает и возвращает **_Dcomplex** значение.

## <a name="requirements"></a>Требования

|Подпрограмма|Заголовок C|Заголовок C++|
|-------------|--------------|------------------|
|**clog**, **clogf**, **clogl**|\<complex.h>|\<ccomplex>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Алфавитный указатель функций](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[cpow, cpowf, cpowl](cpow-cpowf-cpowl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
