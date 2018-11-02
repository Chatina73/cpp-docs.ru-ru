---
title: Компилятор предупреждение (уровень 4) C4463
ms.date: 11/04/2016
f1_keywords:
- C4463
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
ms.openlocfilehash: e125a532f87533958ec43ed5580665ad4108856b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474831"
---
# <a name="compiler-warning-level-4-c4463"></a>Компилятор предупреждение (уровень 4) C4463

> переполнения; Назначение *значение* к битовому полю может содержать только значения из *low_value* для *high_value*

Назначенные *значение* находится вне диапазона значений, которые могут содержать битового поля. Типы со знаком битового поля используйте старших бит знака, поэтому если *n* битового поля, имеет размер диапазона для битовых полей со знаком — -2<sup>n-1</sup> 2<sup>n-1</sup>-1, хотя без знака битовые поля находятся в диапазоне от 0 до 2<sup>n</sup>-1.

## <a name="example"></a>Пример

Этот пример создает C4463, так как оно пытается присвоить значение 3 является битовым полем типа `int` объемом 2, который имеет диапазон от -2 до 1.

Чтобы устранить эту проблему, присвоенное значение можно изменить на что-нибудь в диапазон допустимых значений. Если битовое поле предназначен для хранения значений без знака в диапазоне от 0 до 3, можно изменить тип объявления для `unsigned`. Если поле предназначен для хранения значений в диапазоне -4-3, можно изменить размер битового поля до 3.

```cpp
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S {
    int x : 2; // int type treats high-order bit as sign
};

int main() {
    S s;
    s.x = 3; // warning C4463: overflow; assigning 3
    // to bit-field that can only hold values from -2 to 1
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type
    // to unsigned.
}
```
