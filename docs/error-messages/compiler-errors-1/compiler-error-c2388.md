---
description: 'Дополнительные сведения о: Ошибка компилятора C2388'
title: Ошибка компилятора C2388
ms.date: 11/04/2016
f1_keywords:
- C2388
helpviewer_keywords:
- C2388
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
ms.openlocfilehash: 63a2758b4e214b38c7d999bdc2a33d328709ea67
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123985"
---
# <a name="compiler-error-c2388"></a>Ошибка компилятора C2388

"символ": символ не может быть объявлен одновременно с __declspec (AppDomain) и \_ _declspec (Process)

`appdomain` `process` **`__declspec`** Модификаторы и не могут использоваться для одного и того же символа. Память для хранения переменной выделяется для каждого процесса или каждого домена приложений.

Дополнительные сведения см. в разделах [appdomain](../../cpp/appdomain.md) и [process](../../cpp/process.md).

При компиляции следующего примера возникнет ошибка C2388:

```cpp
// C2388.cpp
// compile with: /clr /c
__declspec(process) __declspec(appdomain) int i;   // C2388
__declspec(appdomain) int i;   // OK
```
