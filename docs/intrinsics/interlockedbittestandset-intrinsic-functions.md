---
title: Встроенные функции _interlockedbittestandset
ms.date: 12/17/2018
f1_keywords:
- _interlockedbittestandset_cpp
- _interlockedbittestandset_HLEAcquire
- _interlockedbittestandset64
- _interlockedbittestandset
- _interlockedbittestandset_rel
- _interlockedbittestandset64_HLEAcquire
- _interlockedbittestandset_HLERelease
- _interlockedbittestandset_acq
- _interlockedbittestandset_nf
- _interlockedbittestandset64_cpp
- _interlockedbittestandset64_HLERelease
helpviewer_keywords:
- _interlockedbittestandset intrinsic
- _interlockedbittestandset64 intrinsic
- lock_bts instruction
ms.assetid: b1b7e334-53ea-48cf-ba60-5fa3ef51a1fc
ms.openlocfilehash: 2f7dc1cf6501f789d969143bc23469a6ecf7239c
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627219"
---
# <a name="interlockedbittestandset-intrinsic-functions"></a>Встроенные функции _interlockedbittestandset

**Блок, относящийся только к системам Microsoft**

Создать инструкцию, которая проверяет разряд `b` адреса `a` и возвращает его текущее значение перед присваиванием 1.

## <a name="syntax"></a>Синтаксис

```
unsigned char _interlockedbittestandset(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_acq(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLEAcquire(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_HLERelease(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_nf(
   long *a,
   long b
);
unsigned char _interlockedbittestandset_rel(
   long *a,
   long b
);
unsigned char _interlockedbittestandset64(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLEAcquire(
   __int64 *a,
   __int64 b
);
unsigned char _interlockedbittestandset64_HLERelease(
   __int64 *a,
   __int64 b
);
```

#### <a name="parameters"></a>Параметры

*a*<br/>
[in] Указатель памяти для проверки.

*b*<br/>
[in] Позиция разряда для тестирования.

## <a name="return-value"></a>Возвращаемое значение

Значение разряда в позиции `b` перед присваиванием.

## <a name="requirements"></a>Требования

|Встроенная функция|Архитектура|Header|
|---------------|------------------|------------|
|`_interlockedbittestandset`|x86, ARM, x64|\<Intrin.h >|
|`_interlockedbittestandset_acq`, `_interlockedbittestandset_nf`, `_interlockedbittestandset_rel`|ARM|\<Intrin.h >|
|`_interlockedbittestandset_HLEAcquire`, `_interlockedbittestandset_HLERelease`|x86, x64|\<immintrin.h >|
|`_interlockedbittestandset64`|X64|\<Intrin.h >|
|`_interlockedbittestandset64_HLEAcquire`, `_interlockedbittestandset64_HLERelease`|X64|\<immintrin.h >|

## <a name="remarks"></a>Примечания

На процессорах x86 и x64, эти встроенные функции используют `lock bts` инструкции для чтения и присваивания указанному разряду 1. Эта операция является атомарной.

На процессорах ARM используются встроенные функции с суффиксами `_acq` и `_rel` для получения и освобождения семантики, например, в начале и конце критической секции. Встроенные функции ARM с суффиксом `_nf` («без границ») не действуют как барьер памяти.

Для процессоров Intel, поддерживающих инструкции Hardware Lock Elision (HLE), встроенные функции с суффиксами`_HLEAcquire` и `_HLERelease` включают подсказку процессору, как можно повысить производительность, устраняя шаг записи с блокировкой оборудования. Если эти встроенные функции вызываются на процессорах, не поддерживающих HLE, подсказка игнорируется.

Эти процедуры доступны только как встроенные объекты.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Встроенные инструкции компилятора](../intrinsics/compiler-intrinsics.md)<br/>
[Конфликты с 32-разрядным (x86) компилятором](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)