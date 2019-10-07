---
title: _initterm, _initterm_e
ms.date: 11/04/2016
api_name:
- _initterm_e
- _initterm
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _initterm_e
- initterm
- _initterm
- initterm_e
helpviewer_keywords:
- initterm function
- initterm_e function
- _initterm function
- _initterm_e function
ms.assetid: 85131efe-c747-429a-8897-bcdedb000172
ms.openlocfilehash: 7e85494bf6c8215d03602ee112e1ff2c0f1cf6f2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954619"
---
# <a name="_initterm-_initterm_e"></a>_initterm, _initterm_e

Внутренние методы, которые выполняют обход таблицы указателей функций и инициализируют их.

Первый указатель представляет собой начальное расположение в таблице, а второй указатель — конечное расположение.

## <a name="syntax"></a>Синтаксис

```C
void __cdecl _initterm(
   PVFV *,
   PVFV *
);

int __cdecl _initterm_e(
   PVFV *,
   PVFV *
);
```

## <a name="return-value"></a>Возвращаемое значение

Ненулевой код ошибки, если инициализация завершается неудачей и генерирует ошибку; 0 при отсутствии ошибок.

## <a name="remarks"></a>Примечания

Эти методы вызываются только внутри системы во время инициализации программы C++. Не следует вызывать эти методы в программе.

Когда эти методы проходят по таблице записей функций, они пропускают **значения NULL** и продолжают работу.

## <a name="see-also"></a>См. также

[Алфавитный указатель функций](crt-alphabetical-function-reference.md)<br/>
