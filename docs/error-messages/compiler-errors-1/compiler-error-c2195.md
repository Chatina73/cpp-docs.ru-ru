---
title: Ошибка компилятора C2195
ms.date: 11/04/2016
f1_keywords:
- C2195
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
ms.openlocfilehash: 748516dbcdf5e135964e720d6215f31091bfed9e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758532"
---
# <a name="compiler-error-c2195"></a>Ошибка компилятора C2195

"идентификатор": является сегментом данных

Директива pragma `code_seg` использует имя сегмента, которое используется с директивой pragma `data_seg`.

Следующий пример приводит к возникновению ошибки C2195:

```cpp
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```
