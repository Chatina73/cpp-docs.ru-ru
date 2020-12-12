---
description: 'Дополнительные сведения: _InterlockedCompareExchange128 встроенных функций'
title: Встроенные функции _InterlockedCompareExchange128
ms.date: 09/02/2019
f1_keywords:
- _InterlockedCompareExchange128_cpp
- _InterlockedCompareExchange128
- _InterlockedCompareExchange128_acq
- _InterlockedCompareExchange128_nf
- _InterlockedCompareExchange128_np
- _InterlockedCompareExchange128_rel
helpviewer_keywords:
- cmpxchg16b instruction
- _InterlockedCompareExchange128 intrinsic
ms.assetid: f05918fc-716a-4f6d-b746-1456d6b96c56
ms.openlocfilehash: ee04a71dafe37d6075a054946cd947f6f3829092
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168141"
---
# <a name="_interlockedcompareexchange128-intrinsic-functions"></a>Встроенные функции _InterlockedCompareExchange128

**Блок, относящийся только к системам Microsoft**

Выполняет 128-битный блок сравнения и обмена.

## <a name="syntax"></a>Синтаксис

```C
unsigned char _InterlockedCompareExchange128(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_acq(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_nf(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_np(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
unsigned char _InterlockedCompareExchange128_rel(
   __int64 volatile * Destination,
   __int64 ExchangeHigh,
   __int64 ExchangeLow,
   __int64 * ComparandResult
);
```

### <a name="parameters"></a>Параметры

*Местоназначение*\
[вход, выход] Указатель на назначение, которое представляет собой массив из 2 64-разрядных целых чисел, которые считаются 128-битным полем. Чтобы избежать общей ошибки защиты, целевые данные должны быть согласованы по 16 байтам.

*ексчанжехигх*\
окне 64-разрядное целое число, которое может быть заменено верхней частью назначения.

*ексчанжелов*\
окне 64-разрядное целое число, которое может быть заменено нижней частью назначения.

*компарандресулт*\
[вход, выход] Указатель на массив из 2 64-разрядных целых чисел (рассматривается как 128-битовое поле) для сравнения с назначением.  На выходе этот массив перезаписывается исходным значением назначения.

## <a name="return-value"></a>Возвращаемое значение

1, если 128-разрядное сравниваемый операнд равно исходному значению назначения. `ExchangeHigh` и `ExchangeLow` Перезаписать 128-разрядное назначение.

0, если сравниваемый операнд не равно исходному значению назначения. Значение места назначения не изменяется, а значение сравниваемый операнд перезаписывается значением назначения.

## <a name="requirements"></a>Требования

|Intrinsic|Архитектура|
|---------------|------------------|
|`_InterlockedCompareExchange128`|x64, ARM64|
|`_InterlockedCompareExchange128_acq`, `_InterlockedCompareExchange128_nf`, `_InterlockedCompareExchange128_rel`|ARM64|
|`_InterlockedCompareExchange128_np`|X64|

**Файл заголовка** \<intrin.h>

## <a name="remarks"></a>Комментарии

`_InterlockedCompareExchange128`Встроенная функция формирует `cmpxchg16b` инструкцию (с `lock` префиксом) для выполнения 128-битного сравнения и обмена. Ранние версии AMD 64-разрядного оборудования не поддерживают эту инструкцию. Чтобы проверить поддержку оборудования для `cmpxchg16b` инструкции, вызовите `__cpuid` встроенную функцию с помощью `InfoType=0x00000001 (standard function 1)` . Бит 13 of `CPUInfo[2]` (ECX) равен 1, если инструкция поддерживается.

> [!NOTE]
> Значение параметра `ComparandResult` всегда перезаписывается. После `lock` инструкции эта функция немедленно копирует начальное значение `Destination` в `ComparandResult` . По этой причине `ComparandResult` и `Destination` должен указывать на отдельные места в памяти во избежание непредвиденного поведения.

Хотя вы можете использовать `_InterlockedCompareExchange128` для синхронизации потоков низкого уровня, не нужно выполнять синхронизацию более 128 бит, если вместо этого можно использовать небольшие функции синхронизации (например, другие `_InterlockedCompareExchange` встроенные). Используйте, `_InterlockedCompareExchange128` Если требуется атомарный доступ к 128-разрядному значению в памяти.

Если запустить код, использующий встроенное на оборудовании, которое не поддерживает эту `cmpxchg16b` инструкцию, результаты будут непредсказуемыми.

На платформах ARM используются встроенные функции с суффиксами `_acq` и `_rel` для получения и освобождения семантики, например, в начале и конце критической секции. Встроенные функции ARM с `_nf` суффиксом ("без ограждения") не действуют как барьер памяти.

Встроенные функции с суффиксом `_np` («нет упреждающей выборки") запрещают возможную вставку компилятором операции упреждающей выборки.

Эта подпрограммы доступна только в качестве встроенной функции.

## <a name="example"></a>Пример

В этом примере используется `_InterlockedCompareExchange128` для замены старшего слова массива из 2 64-разрядных целых чисел на сумму его верхнего и нижнего слов, а также для увеличения нижнего слова. Доступ к `BigInt.Int` массиву является атомарным, но в этом примере используется один поток и игнорируется блокировка для простоты.

```cpp
// cmpxchg16b.c
// processor: x64
// compile with: /EHsc /O2
#include <stdio.h>
#include <intrin.h>

typedef struct _LARGE_INTEGER_128 {
    __int64 Int[2];
} LARGE_INTEGER_128, *PLARGE_INTEGER_128;

volatile LARGE_INTEGER_128 BigInt;

// This AtomicOp() function atomically performs:
//   BigInt.Int[1] += BigInt.Int[0]
//   BigInt.Int[0] += 1
void AtomicOp ()
{
    LARGE_INTEGER_128 Comparand;
    Comparand.Int[0] = BigInt.Int[0];
    Comparand.Int[1] = BigInt.Int[1];
    do {
        ; // nothing
    } while (_InterlockedCompareExchange128(BigInt.Int,
                                            Comparand.Int[0] + Comparand.Int[1],
                                            Comparand.Int[0] + 1,
                                            Comparand.Int) == 0);
}

// In a real application, several threads contend for the value
// of BigInt.
// Here we focus on the compare and exchange for simplicity.
int main(void)
{
   BigInt.Int[1] = 23;
   BigInt.Int[0] = 11;
   AtomicOp();
   printf("BigInt.Int[1] = %d, BigInt.Int[0] = %d\n",
      BigInt.Int[1],BigInt.Int[0]);
}
```

```Output
BigInt.Int[1] = 34, BigInt.Int[0] = 12
```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Встроенные функции компилятора](../intrinsics/compiler-intrinsics.md)\
[Встроенные функции _InterlockedCompareExchange](../intrinsics/interlockedcompareexchange-intrinsic-functions.md)\
[Конфликтует с компилятором x86](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)
