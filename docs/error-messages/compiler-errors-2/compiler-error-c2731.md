---
description: 'Дополнительные сведения о: Ошибка компилятора C2731'
title: Ошибка компилятора C2731
ms.date: 11/04/2016
f1_keywords:
- C2731
helpviewer_keywords:
- C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
ms.openlocfilehash: baae65ff1d09bafe37251b7593dc0d0c91c89f1b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123309"
---
# <a name="compiler-error-c2731"></a>Ошибка компилятора C2731

"идентификатор": функция не может быть перегружена

Функции, `main` , `WinMain` `DllMain` и `LibMain` не могут быть перегружены.

Следующий пример приводит к возникновению ошибки C2731:

```cpp
// C2731.cpp
extern "C" void WinMain(int, char *, char *);
void WinMain(int, short, char *, char*);   // C2731
```
