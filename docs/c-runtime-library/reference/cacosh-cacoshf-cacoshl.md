---
title: cacosh, cacoshf, cacoshl
ms.date: 11/04/2016
apiname:
- cacosh
- cacoshf
- cacoshl
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
- cacosh
- cacoshf
- cacoshl
- complex/cacosh
- complex/cacoshf
- complex/cacoshl
helpviewer_keywords:
- cacosh function
- cacoshf function
- cacoshl function
ms.assetid: 83fd05eb-3587-4741-9be6-589a830a1703
ms.openlocfilehash: aa31dfa1b29eda18d34528fc8aa9544e58a5a082
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62340733"
---
# <a name="cacosh-cacoshf-cacoshl"></a>cacosh, cacoshf, cacoshl

Извлекает обратный гиперболический косинус комплексного числа, ветви которого заканчиваются раньше значения 1 на реальной оси. .

## <a name="syntax"></a>Синтаксис

```C
_Dcomplex cacosh(
   _Dcomplex z
);
_Fcomplex cacosh(
   _Fcomplex z
);  // C++ only
_Lcomplex cacosh(
   _Lcomplex z
);  // C++ only
_Fcomplex cacoshf(
   _Fcomplex z
);
_Lcomplex cacoshl(
   _Lcomplex z
);
```

### <a name="parameters"></a>Параметры

*z*<br/>
Комплексное число, указывающее угол в радианах.

## <a name="return-value"></a>Возвращаемое значение

Обратный гиперболический косинус *z*, в радианах. Результат неограничен, отрицательным на реальной оси и находится в интервале [-iπ, + iπ] на мнимой оси.

## <a name="remarks"></a>Примечания

Так как C++ допускает перегрузку, можно вызывать перегрузки **cacosh** , принимающие и возвращающие **_Fcomplex** и **_Lcomplex** значения. В программе на языке C **cacosh** всегда принимает и возвращает **_Dcomplex** значение.

## <a name="requirements"></a>Требования

|Подпрограмма|Заголовок C|Заголовок C++|
|-------------|--------------|------------------|
|**cacosh**,               **cacoshf**, **cacoshl**|\<complex.h>|\<ccomplex>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также

[Алфавитный указатель функций](crt-alphabetical-function-reference.md)<br/>
[catanh, catanhf, catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh, ctanhf, ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan, catanf, catanl](catan-catanf-catanl.md)<br/>
[csinh, csinhf, csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh, casinhf, casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh, ccoshf, ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacos, cacosf, cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan, ctanf, ctanl](ctan-ctanf-ctanl.md)<br/>
[csin, csinf, csinl](csin-csinf-csinl.md)<br/>
[casin, casinf, casinl](casin-casinf-casinl.md)<br/>
[ccos, ccosf, ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt, csqrtf, csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
