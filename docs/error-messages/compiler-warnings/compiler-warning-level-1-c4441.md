---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4441'
title: Предупреждение компилятора (уровень 1) C4441
ms.date: 11/04/2016
f1_keywords:
- C4441
helpviewer_keywords:
- C4441
ms.assetid: 7fc540a5-e41f-47cf-aa37-b2b699c2685e
ms.openlocfilehash: f09e25696edffadaeb843d0dbb7ec47f4bcf8a49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212575"
---
# <a name="compiler-warning-level-1-c4441"></a>Предупреждение компилятора (уровень 1) C4441

Соглашение о вызовах "CC1" игнорируется; Вместо этого используется "cc2"

Функции-члены в управляемых определяемых пользователем типах и универсальных функциях должны использовать [__clrcall](../../cpp/clrcall.md) соглашения о вызовах.  Используемый компилятор `__clrcall` .

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4441.

```cpp
// C4441.cpp
// compile with: /clr /W1 /c
generic <class ItemType>
void __cdecl Test(ItemType item) {}   // C4441
// try the following line instead
// void Test(ItemType item) {}

ref struct MyStruct {
   void __cdecl Test(){}   // C4441
   void Test2(){}   // OK
};
```
