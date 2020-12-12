---
description: 'Дополнительные сведения о: _emit Псеудоинструктион'
title: Псевдоинструкция _emit
ms.date: 08/30/2018
f1_keywords:
- _emit
helpviewer_keywords:
- byte defining (inline assembly)
- _emit pseudoinstruction
ms.assetid: 004c48f3-364c-4e82-9a51-e326f9cc7b2b
ms.openlocfilehash: d3e2a39312c94ff0e4868bed9afa74011051a129
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97117813"
---
# <a name="_emit-pseudoinstruction"></a>Псевдоинструкция _emit

**Блок, относящийся только к системам Microsoft**

**_Emit** псеудоинструктион определяет один байт в текущем положении в текущем сегменте текста. **_Emit** псеудоинструктион напоминает директиву [базы данных](../../assembler/masm/db.md) MASM.

В следующем примере в код помещаются байты 0x4A, 0x43 и 0x4B:

```cpp
#define randasm __asm _emit 0x4A __asm _emit 0x43 __asm _emit 0x4B
.
.
.
__asm {
    randasm
    }
```

> [!CAUTION]
> Если псевдокоманда `_emit` создает инструкции, которые изменяют регистры, а приложение компилируется с включенными оптимизациями, то компилятор не в состоянии определить, на какие регистры она действует. Например, если `_emit` создает инструкцию, которая изменяет регистр **RAX** , компилятор не знает, что **RAX** изменился. Затем компилятор может сделать неверное допущение о значении этого регистра после выполнения встроенного кода на языке ассемблера. Поэтому запущенное приложение может работать непредсказуемым образом.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Использование языка ассемблера в блоках __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
