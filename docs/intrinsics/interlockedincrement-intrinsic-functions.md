---
title: Встроенные функции _InterlockedIncrement
ms.date: 12/17/2018
f1_keywords:
- _InterlockedIncrement_acq
- _InterlockedIncrement16_rel_cpp
- _InterlockedIncrement16_cpp
- _InterlockedIncrement64_rel
- _InterlockedIncrement_rel
- _InterlockedIncrement64_nf
- _InterlockedIncrement16_acq_cpp
- _InterlockedIncrement_rel_cpp
- _InterlockedIncrement64
- _InterlockedIncrement64_rel_cpp
- _InterlockedIncrement16_nf
- _InterlockedIncrement16_rel
- _InterlockedIncrement16_acq
- _InterlockedIncrement_nf
- _InterlockedIncrement_acq_cpp
- _InterlockedIncrement64_cpp
- _InterlockedIncrement64_acq_cpp
- _InterlockedIncrement
- _InterlockedIncrement_cpp
- _InterlockedIncrement64_acq
- _InterlockedIncrement16
helpviewer_keywords:
- _InterlockedIncrement64_rel intrinsic
- _InterlockedIncrement16_rel intrinsic
- InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16 intrinsic
- _InterlockedIncrement16_acq intrinsic
- _InterlockedIncrement_nf intrinsic
- _InterlockedIncrement_rel intrinsic
- _InterlockedIncrement64_nf intrinsic
- InterlockedIncrement_rel intrinsic
- InterlockedIncrement_acq intrinsic
- _InterlockedIncrement64_acq intrinsic
- _InterlockedIncrement16_nf intrinsic
- _InterlockedIncrement intrinsic
- _InterlockedIncrement64 intrinsic
- InterlockedIncrement64_rel intrinsic
- InterlockedIncrement64 intrinsic
- InterlockedIncrement16 intrinsic
- _InterlockedIncrement_acq intrinsic
- InterlockedIncrement intrinsic
ms.assetid: 37700615-f372-438b-bcef-d76e11839482
ms.openlocfilehash: b41ce5c744bde7cd89cabed6c829cfb06da75129
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039362"
---
# <a name="interlockedincrement-intrinsic-functions"></a>Встроенные функции _InterlockedIncrement

**Блок, относящийся только к системам Microsoft**

Предоставляют встроенную поддержку компилятора для пакета SDK Windows Win32 [InterlockedIncrement](/windows/desktop/api/winnt/nf-winnt-interlockedincrement) функции.

## <a name="syntax"></a>Синтаксис

```
long _InterlockedIncrement(
   long * lpAddend
);
long _InterlockedIncrement_acq(
   long * lpAddend
);
long _InterlockedIncrement_rel(
   long * lpAddend
);
long _InterlockedIncrement_nf(
   long * lpAddend
);
short _InterlockedIncrement16(
   short * lpAddend
);
short _InterlockedIncrement16_acq(
   short * lpAddend
);
short _InterlockedIncrement16_rel(
   short * lpAddend
);
short _InterlockedIncrement16_nf (
   short * lpAddend
);
__int64 _InterlockedIncrement64(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_acq(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_rel(
   __int64 * lpAddend
);
__int64 _InterlockedIncrement64_nf(
   __int64 * lpAddend
);
```

#### <a name="parameters"></a>Параметры

*lpAddend*<br/>
[in, out] Указатель на переменную для увеличения.

## <a name="return-value"></a>Возвращаемое значение

Возвращаемое значение, полученное после увеличения.

## <a name="requirements"></a>Требования

|Встроенная функция|Архитектура|Header|
|---------------|------------------|------------|
|`_InterlockedIncrement`, `_InterlockedIncrement16`, `_InterlockedIncrement64`|x86, ARM, x64|\<intrin.h>|
|`_InterlockedIncrement_acq`, `_InterlockedIncrement_rel`, `_InterlockedIncrement_nf`, `_InterlockedIncrement16_acq`, `_InterlockedIncrement16_rel`, `_InterlockedIncrement16_nf`, `_InterlockedIncrement64_acq`, `_InterlockedIncrement64_rel`, `_InterlockedIncrement64_nf`|ARM|\<intrin.h>|

## <a name="remarks"></a>Примечания

Существуют несколько вариантов `_InterlockedIncrement`, они различаются в зависимости от типов данных, которые включают, и от того, используется ли семантика получения или освобождения конкретного процессора.

Функция `_InterlockedIncrement` работает с 32-разрядными целыми значениями, _InterlockedDecrement16`_InterlockedIncrement16`работает с 16-разрядными целыми значениями и _InterlockedDecrement64`_InterlockedIncrement64`работает с 64-разрядными целыми значениями.

На платформах ARM используйте встроенные функции с суффиксами `_acq` и `_rel`, если нужно получить и освободить семантику, например в начале и конце критической секции. Встроенная функция с суффиксом `_nf` («без границ») не действует как ограничитель памяти.

Переменная, на который указывает параметр `lpAddend`, должна быть выровнена по границе 32 разрядов; в противном случае эта функция не выполняется на многопроцессорных системах x86 и любой системе не-x86. Дополнительные сведения см. в разделе [выровнять](../cpp/align-cpp.md).

Функция Win32 объявляется в `Wdm.h` или `Ntddk.h`.

Эти процедуры доступны только как встроенные объекты.

## <a name="example"></a>Пример

Пример использования `_InterlockedIncrement`, см. в разделе [_InterlockedDecrement](../intrinsics/interlockeddecrement-intrinsic-functions.md).

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Встроенные инструкции компилятора](../intrinsics/compiler-intrinsics.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)<br/>
[Конфликты с 32-разрядным (x86) компилятором](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)