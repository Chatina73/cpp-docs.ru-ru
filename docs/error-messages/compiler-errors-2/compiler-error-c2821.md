---
description: 'Дополнительные сведения о: Ошибка компилятора C2821'
title: Ошибка компилятора C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: c21c9dc0b1413292e1d73b6448ed008d6fc9a64d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194700"
---
# <a name="compiler-error-c2821"></a>Ошибка компилятора C2821

первый формальный параметр для "operator new" должен иметь тип "unsigned int"

Первый формальный параметр [оператора New](../../standard-library/new-operators.md#op_new) должен быть неподписанным **`int`** .

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C2821:

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```
