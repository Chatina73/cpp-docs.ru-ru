---
title: Предупреждение компилятора (уровень 1) C4946
ms.date: 11/04/2016
f1_keywords:
- C4946
helpviewer_keywords:
- C4946
ms.assetid: b85cbef0-e053-4de6-9b14-7b0f82d40495
ms.openlocfilehash: f215c621486bf223d8f6c90b0a4f4ae119ad4b1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574230"
---
# <a name="compiler-warning-level-1-c4946"></a>Предупреждение компилятора (уровень 1) C4946

использование reinterpret_cast между связанными классами: "класс 1" и "класс 2"

Не используйте [reinterpret_cast](../../cpp/reinterpret-cast-operator.md) для приведения между связанными типами. Используйте [static_cast](../../cpp/static-cast-operator.md) вместо и полиморфных типов, используйте [dynamic_cast](../../cpp/dynamic-cast-operator.md).

По умолчанию это предупреждение отключено. Дополнительные сведения см. в разделе [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

В следующем примере кода приводит к возникновению ошибки C4946:

```
// C4946.cpp
// compile with: /W1
#pragma warning (default : 4946)
class a {
public:
   a() : m(0) {}
   int m;
};

class b : public virtual a {
};

class b2 : public virtual a {
};

class c : public b, public b2 {
};

int main() {
   c* pC = new c;
   a* pA = reinterpret_cast<a*>(pC);   // C4946
   // try the following line instead
   // a* pA = static_cast<a*>(pC);
}
```