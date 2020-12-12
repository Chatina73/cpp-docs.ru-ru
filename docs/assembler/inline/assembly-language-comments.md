---
description: 'Дополнительные сведения: Assembly-Language комментарии'
title: Комментарии языка ассемблера
ms.date: 08/30/2018
helpviewer_keywords:
- assembly language [C++], comments
- comments [C++], assembly language
- macros [C++], assembly language
- __asm keyword [C++], instructions
ms.assetid: 0dc10850-77f5-426e-9dab-185ea28e06e4
ms.openlocfilehash: 704f5275afe5cb5629b2e7667fe9107417512198
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118008"
---
# <a name="assembly-language-comments"></a>Комментарии языка ассемблера

**Блок, относящийся только к системам Microsoft**

Инструкции в **`__asm`** блоке могут использовать комментарии на языке ассемблера:

```cpp
__asm mov ax, offset buff ; Load address of buff
```

Поскольку макросы C развертываются в одну логическую строку, в них не следует использовать комментарии в стиле ассемблера. (См. раздел [определение __Asm блоков в качестве макросов C](../../assembler/inline/defining-asm-blocks-as-c-macros.md).) **`__asm`** Блок может также содержать комментарии в стиле C; дополнительные сведения см. в разделе [Использование C или C++ в блоках __asm](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md).

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Использование языка ассемблера в блоках __asm](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
