---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 4) C4681'
title: Предупреждение компилятора (уровень 4) C4681
ms.date: 11/04/2016
f1_keywords:
- C4681
helpviewer_keywords:
- C4681
ms.assetid: a4e6d85f-3e21-4b45-a551-c23d3c554d3f
ms.openlocfilehash: be49b05aaaabb9e247ea65834d478bb1a4863776
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133891"
---
# <a name="compiler-warning-level-4-c4681"></a>Предупреждение компилятора (уровень 4) C4681

"класс": компонентный класс не указывает интерфейс по умолчанию, который является источником событий

Интерфейс [источника](../../windows/attributes/source-cpp.md) для класса не указан.

Следующий пример приводит к возникновению предупреждения C4681:

```cpp
// C4681.cpp
// compile with: /W4 /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[module(name="test")];

[dual, uuid("00000000-0000-0000-0000-000000000000")]
__interface IEvent { [id(3)] HRESULT myEvent(); };

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface ISource { HRESULT Fire(); };

[ coclass,
  source(IEvent),
  default(ISource),
  // Uncomment the following line to resolve.
  // default(IEvent),
  uuid("00000000-0000-0000-0000-000000000002")
]
struct CSource : ISource {   // C4681
   HRESULT Fire() { return 0; }
};
```
