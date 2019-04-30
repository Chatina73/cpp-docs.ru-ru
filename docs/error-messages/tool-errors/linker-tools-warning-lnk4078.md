---
title: Предупреждение средств компоновщика LNK4078
ms.date: 11/04/2016
f1_keywords:
- LNK4078
helpviewer_keywords:
- LNK4078
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
ms.openlocfilehash: d20eb0523ffebe9229d05b6316772259661f6020
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399945"
---
# <a name="linker-tools-warning-lnk4078"></a>Предупреждение средств компоновщика LNK4078

несколько разделов «имя_раздела» с разными атрибутами

Дополнительные разделы, которые имеют одинаковые имя, но разные атрибуты или СВЯЗИ обнаружены два.

Это предупреждение может быть вызвано библиотеки или экспортирует файл импорта, созданный в предыдущей версии LINK или LIB.

Повторно создайте файл и повторно скомпоновать.

## <a name="example"></a>Пример

LNK4078 также может быть вызвана критическое изменение: разделе с [init_seg](../../preprocessor/init-seg.md) на x86 чтения и записи, он является теперь только для чтения.

Следующий пример приводит к возникновению ошибки LNK4078.

```
// LNK4078.cpp
// compile with: /W1
// LNK4078 expected
#include <stdio.h>
#pragma warning(disable : 4075)
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // pointers to destructors.

struct A { A() {} };

int myexit (PF pf) { return 0; }

#pragma section(".mine$a", read, write)
// try the following line instead
// #pragma section(".mine$a", read)
__declspec(allocate(".mine$a")) int ii = 1;

#pragma section(".mine$z", read, write)
// try the following line instead
// #pragma section(".mine$z", read)
__declspec(allocate(".mine$z")) int i = 1;

#pragma data_seg()
#pragma init_seg(".mine$m", myexit)
A bbbb;
A cccc;
int main() {}
```