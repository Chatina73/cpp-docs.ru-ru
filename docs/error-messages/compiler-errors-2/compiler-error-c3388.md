---
title: Ошибка компилятора C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: 3b56aae115b1a1721f3f8a8688e36b25edc7f33f
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780032"
---
# <a name="compiler-error-c3388"></a>Ошибка компилятора C3388

"тип": не допускается в качестве ограничения; предполагается, что "класс ref" продолжит синтаксический разбор

Ограничение для универсального типа указано неправильно. См. в разделе [ограничений для параметров универсального типа (C + +/ CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) Дополнительные сведения.

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C3388:

```
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```