---
description: 'Дополнительные сведения: _udiv128'
title: _udiv128
ms.date: 04/17/2019
f1_keywords:
- _udiv128
helpviewer_keywords:
- _udiv128 intrinsic
ms.openlocfilehash: f88546a179106f4291fcaeb865f1aad9e67c4045
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333657"
---
# <a name="_udiv128"></a>_udiv128

`_udiv128`Функция делит 128-разрядное целое число без знака на 64-разрядное целое число без знака. Возвращаемое значение содержит частное, а внутренний возвращает остаток через параметр указателя. `_udiv128` зависит **от корпорации Майкрософт**.

## <a name="syntax"></a>Синтаксис

```C
unsigned __int64 _udiv128(
   unsigned __int64 highDividend,
   unsigned __int64 lowDividend,
   unsigned __int64 divisor,
   unsigned __int64 *remainder
);
```

### <a name="parameters"></a>Параметры

*хигхдивиденд* \
окне Старшие 64 бит делимого.

*ловдивиденд* \
окне Младший 64 бит делимого.

*равн* \
окне 64-разрядное целое число для деления на.

*дальнейшем* \
заполняет 64-разрядный целочисленный бит остатка.

## <a name="return-value"></a>Возвращаемое значение

64 бит частного.

## <a name="remarks"></a>Комментарии

Передайте верхние 64 бит 128-разрядного делимого на *хигхдивиденд*, а младшие биты 64 — в *ловдивиденд*. Внутренняя функция делит это значение на *делитель*. Он сохраняет остаток в 64-битовом целом число без знака, на который указывает *остаток*, и возвращает биты числа 64.

`_udiv128`Встроенная функция доступна начиная с Visual Studio 2019 RTM.

## <a name="requirements"></a>Требования

|Intrinsic|Архитектура|Заголовок|
|---------------|------------------|------------|
|`_udiv128`|X64|\<immintrin.h>|

## <a name="see-also"></a>См. также раздел

[_div128](div128.md) \
[Встроенные объекты компилятора](compiler-intrinsics.md)
