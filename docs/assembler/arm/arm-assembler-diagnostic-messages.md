---
description: 'Дополнительные сведения: диагностические сообщения ассемблера ARM'
title: Диагностические сообщения ассемблера ARM
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 91e4640c161cbb58522c3680ae5decdb4cc1e992
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118203"
---
# <a name="arm-assembler-diagnostic-messages"></a>Диагностические сообщения ассемблера ARM

Microsoft ARM Assembler (*армасм*) выдает предупреждения и ошибки диагностики при их обнаружении. В этой статье описываются наиболее часто встречающиеся сообщения.

## <a name="syntax"></a>Синтаксис

> <em>filename</em>**(**<em>номер строки</em>**):** \[ **Ошибка** | **предупреждение**] <em>число</em>**:** *сообщение*

## <a name="diagnostic-messages---errors"></a>Диагностические сообщения — ошибки

> A2193: Эта инструкция создает непредсказуемое поведение

Архитектура ARM не гарантирует, что происходит при выполнении этой инструкции.  Дополнительные сведения об четко определенных формах этой инструкции см. в [руководстве по архитектуре ARM](https://go.microsoft.com/fwlink/p/?linkid=246464).

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196: инструкция не может быть закодирована в 16 битах

Указанная инструкция не может быть закодирована как 16-разрядная инструкция Thumb.  Укажите 32-разрядную инструкцию или переставьте код, чтобы переместить целевую метку в диапазон 16-разрядной инструкции.

Ассемблер может попытаться закодировать ветвь в 16 бит и завершить эту ошибку, даже если 32-разрядная ветвь — енкодабле. Эту проблему можно решить с помощью описателя, `.W` чтобы явно пометить ветвь как 32-разрядную.

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202: синтаксис инструкции pre-UAL не разрешен в области THUMB

В коде Thumb должен использоваться синтаксис Unified ассемблера (UAL).  Старый синтаксис больше не принимается

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513: поворот должен быть четным

В режиме ARM существует альтернативный синтаксис для указания констант.  Вместо записи `#<const>` можно написать `#<byte>,#<rot>` , который представляет постоянное значение, полученное путем поворота значения `<byte>` вправо на `<rot>` .  При использовании этого синтаксиса необходимо сделать значение `<rot>` четным.

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557: неправильное число байтов для обратной записи

В инструкциях по загрузке и хранению структуры NEON ( `VLDn` , `VSTn` ) существует альтернативный синтаксис для указания обратной записи в базовый регистр.  Вместо того чтобы помещать восклицательный знак (!) после адреса, можно указать немедленное значение, указывающее смещение, которое должно быть добавлено к базовому регистру.  При использовании этого синтаксиса необходимо указать точное число байтов, которые были загружены или сохранены инструкцией.

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>Диагностические сообщения — предупреждения

> A4228: значение выравнивания превышает выравнивание области; выравнивание не гарантируется

Выравнивание, указанное в `ALIGN` директиве, больше, чем выравнивание включающего объекта `AREA` .  В результате ассемблер не может гарантировать, что `ALIGN` директива будет учитываться.

Чтобы устранить эту проблему, можно указать в `AREA` директиве `ALIGN` атрибут, который больше или равен нужному выравниванию.

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508: использование этой повернутой константы является устаревшим

В режиме ARM существует альтернативный синтаксис для указания констант.  Вместо записи `#<const>` можно написать `#<byte>,#<rot>` , который представляет постоянное значение, полученное путем поворота значения `<byte>` вправо на `<rot>` .  В некоторых контекстах ARM не рекомендуется использовать эти повернутые константы. В этих случаях вместо этого используйте базовый `#<const>` синтаксис.

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509: Эта форма условной инструкции является устаревшей

Эта форма условной инструкции была признана нерекомендуемой ARM в архитектуре ARMv8. Рекомендуется изменить код для использования условных ветвей. Чтобы узнать, какие условные инструкции по-прежнему поддерживаются, обратитесь к [руководству по архитектуре ARM](https://go.microsoft.com/fwlink/p/?linkid=246464).

Это предупреждение не создается при использовании параметра командной строки **-олдит** .

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>См. также раздел

[Справочник по ассемблеру ARM Command-Line](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[Директивы ассемблера ARM](../../assembler/arm/arm-assembler-directives.md)<br/>
