---
description: 'Дополнительные сведения о: Ошибка компилятора C2017'
title: Ошибка компилятора C2017
ms.date: 11/04/2016
f1_keywords:
- C2017
helpviewer_keywords:
- C2017
ms.assetid: 1083eed9-9906-4a97-883c-54e52d7e82cd
ms.openlocfilehash: c70bd39cb15a0eff5d209a6fc76e3dc44b990d8e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220907"
---
# <a name="compiler-error-c2017"></a>Ошибка компилятора C2017

недопустимая escape-последовательность

Escape-последовательность, например \t, отображается за пределами символьной или строковой константы.

Следующий пример приводит к возникновению ошибки C2017:

```cpp
// C2017.cpp
int main() {
   char test1='a'\n;   // C2017
   char test2='a\n';   // ok
}
```

C2017 может возникать, когда оператор строчный используется со строками, включающими escape-последовательности.

Следующий пример приводит к возникновению ошибки C2017:

```cpp
// C2017b.cpp
#define TestDfn(x) AfxMessageBox(#x)
TestDfn(CString("\\") + CString(".h\"\n\n"));   // C2017
```
