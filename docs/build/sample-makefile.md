---
title: Образец файла makefile
ms.date: 11/04/2016
ms.assetid: 8343ce71-5556-4ae0-8d1e-7efd82673070
ms.openlocfilehash: 248924ff83befdefe1045da197be5328095c0caf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534893"
---
# <a name="sample-makefile"></a>Образец файла makefile

Этот раздел содержит образец файла makefile.

## <a name="sample"></a>Пример

### <a name="code"></a>Код

```
# Sample makefile

!include <win32.mak>

all: simple.exe challeng.exe

.c.obj:
  $(cc) $(cdebug) $(cflags) $(cvars) $*.c

simple.exe: simple.obj
  $(link) $(ldebug) $(conflags) -out:simple.exe simple.obj $(conlibs) lsapi32.lib

challeng.exe: challeng.obj md4c.obj
  $(link) $(ldebug) $(conflags) -out:challeng.exe $** $(conlibs) lsapi32.lib
```

## <a name="see-also"></a>См. также

[Содержимое файла Makefile](../build/contents-of-a-makefile.md)