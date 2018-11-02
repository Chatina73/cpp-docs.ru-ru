---
title: Предупреждение компилятора (уровень 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: 56fe0f314142d873fc02136bc2c3fe65e71f4dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544070"
---
# <a name="compiler-warning-level-1-c4399"></a>Предупреждение компилятора (уровень 1) C4399

> "*символ*": символ для каждого процесса не должны быть помечены __declspec(dllimport) при компиляции с параметром/clr: pure

## <a name="remarks"></a>Примечания

**/CLR: pure** параметр компилятора в Visual Studio 2015 не рекомендуется и не поддерживается в Visual Studio 2017.

Данные из образа в машинном коде или изображения с машинным кодом или конструкции среды CLR не могут импортироваться в чистом образе. Чтобы устранить это предупреждение, компиляцию с параметром **/CLR** (не **/CLR: pure**) или удалить `__declspec(dllimport)`.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```