---
description: 'Дополнительные сведения о: кпов, кповф, кповл'
title: cpow, cpowf, cpowl
ms.date: 11/04/2016
api_name:
- cpow
- cpowf
- cpowl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- cpow
- cpowf
- cpowl
- complex/cpow
- complex/cpowf
- complex/copwl
helpviewer_keywords:
- cpow function
- cpowf function
- complex/cpowl function
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
ms.openlocfilehash: 3e12cab3a7ec8c7f3f4bf8cd4739e10f022de8fd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339647"
---
# <a name="cpow-cpowf-cpowl"></a>cpow, cpowf, cpowl

Извлекает значение числа, возведенное в заданную степень; при этом база и экспонента представляют собой комплексные числа. Эта функция имеет ветвь, вырезанную для экспоненты вдоль отрицательной части реальной оси.

## <a name="syntax"></a>Синтаксис

```C
_Dcomplex cpow(
   _Dcomplex x, _Dcomplex y
);
_Fcomplex cpow(
   _Fcomplex x, _Fcomplex y
);  // C++ only
_Lcomplex cpow(
   _Lcomplex x, _Lcomplex y
);  // C++ only
_Fcomplex cpowf(
   _Fcomplex x, _Fcomplex y
);
_Lcomplex cpowl(
   _Lcomplex x, _Lcomplex y
);
```

### <a name="parameters"></a>Параметры

*x*<br/>
База.

*y*<br/>
Экспонента.

## <a name="return-value"></a>Возвращаемое значение

Значение *x* , возведенное в степень *y* , с ветвью *x* на отрицательной реальной оси.

## <a name="remarks"></a>Комментарии

Поскольку C++ допускает перегрузку, можно вызывать перегрузки **кпов** , которые принимают и возвращают **_Fcomplex** и **_Lcomplex** значения. В программе на языке C **кпов** всегда принимает и возвращает значение **_Dcomplex** .

## <a name="requirements"></a>Требования

|Подпрограмма|Заголовок C|Заголовок C++|
|-------------|--------------|------------------|
|**кпов**,               **кповф**, **кповл**|\<complex.h>|\<ccomplex>|

Дополнительные сведения о совместимости см. в разделе [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>См. также раздел

[Алфавитный справочник по функциям](crt-alphabetical-function-reference.md)<br/>
[cexp, cexpf, cexpl](cexp-cexpf-cexpl.md)<br/>
[clog10, clog10f, clog10l](clog10-clog10f-clog10l.md)<br/>
[clog, clogf, clogl](clog-clogf-clogl.md)<br/>
