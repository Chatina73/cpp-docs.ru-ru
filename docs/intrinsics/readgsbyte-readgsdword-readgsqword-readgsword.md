---
description: 'Дополнительные сведения: __readgsbyte, __readgsdword, __readgsqword, __readgsword'
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword
ms.date: 09/02/2019
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: fb1faf0e785f0d0983d7d3611e68a7515298e61c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340974"
---
# <a name="__readgsbyte-__readgsdword-__readgsqword-__readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Блок, относящийся только к системам Microsoft**

Считывает память из расположения, заданного смещением относительно начала сегмента GS.

## <a name="syntax"></a>Синтаксис

```C
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Параметры

*Собой*\
окне Смещение от начала `GS` до чтения из.

## <a name="return-value"></a>Возвращаемое значение

Содержимое памяти в байтах, слово, двойное слово или куадворд (как указано именем функции с именем) в расположении `GS:[Offset]` .

## <a name="requirements"></a>Требования

|Intrinsic|Архитектура|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**Файл заголовка** \<intrin.h>

## <a name="remarks"></a>Комментарии

Эти подпрограммы доступны только в качестве встроенных.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[__writegsbyte, \_ _writegsdword, \_ _writegsqword, \_ _writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Встроенные объекты компилятора](../intrinsics/compiler-intrinsics.md)
