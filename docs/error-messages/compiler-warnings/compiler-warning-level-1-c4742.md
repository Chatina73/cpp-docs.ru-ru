---
description: 'Дополнительные сведения: предупреждение компилятора (уровень 1) C4742'
title: Предупреждение компилятора (уровень 1) C4742
ms.date: 07/22/2020
f1_keywords:
- C4742
helpviewer_keywords:
- C4742
ms.assetid: e520881d-1eeb-48b1-9df0-8017ee8ba076
ms.openlocfilehash: 009c8b894b9c53d3a0c802dbb0f5786fc9934b57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228525"
---
# <a name="compiler-warning-level-1-c4742"></a>Предупреждение компилятора (уровень 1) C4742

> "*переменная*" имеет разное выравнивание в "*file1*" и "*file2*": *Число1* и *число2*

Внешняя переменная, на которую ссылается или определена в двух файлах, имеет различное выравнивание в этих файлах.

## <a name="remarks"></a>Комментарии

Это предупреждение выдается при обнаружении компилятором того, что **`alignof`** для переменной в *file1* отличается от **`alignof`** для переменной в *file2*. Это может быть вызвано использованием несовместимых типов при объявлении переменной в разных файлах или при использовании несовпадающих `#pragma pack` в разных файлах.

Чтобы устранить это предупреждение, используйте одно и то же определение типа или используйте разные имена для переменных.

Дополнительные сведения см. в [`pack`](../../preprocessor/pack.md) разделе [ `alignof` оператор](../../cpp/alignof-operator.md)и.

## <a name="example"></a>Пример

Это первый файл, определяющий тип.

```c
// C4742a.c
// compile with: /c
struct X {
   char x, y, z, w;
} global;
```

Следующий пример приводит к возникновению ошибки C4742.

```c
// C4742b.c
// compile with: C4742a.c /W1 /GL
// C4742 expected
extern struct X {
   int a;
} global;

int main() {
   global.a = 0;
}
```
