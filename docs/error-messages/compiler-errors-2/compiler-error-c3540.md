---
title: Ошибка компилятора C3540
ms.date: 11/04/2016
f1_keywords:
- C3540
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
ms.openlocfilehash: a041961e8a91832be67d8def8f2a6a3ef70906d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223399"
---
# <a name="compiler-error-c3540"></a>Ошибка компилятора C3540

"тип": sizeof нельзя применить к типу, содержащему "Auto"

Оператор [sizeof](../../cpp/sizeof-operator.md) нельзя применить к указанному типу, так как он содержит **`auto`** спецификатор.

## <a name="example"></a>Пример

В следующем примере выдается C3540.

```cpp
// C3540.cpp
// Compile with /Zc:auto
int main() {
    auto x = 123;
    sizeof(x);    // OK
    sizeof(auto); // C3540
    return 0;
}
```

## <a name="see-also"></a>См. также

[Ключевое слово auto](../../cpp/auto-keyword.md)<br/>
[/Zc: Auto (вывод типа переменной)](../../build/reference/zc-auto-deduce-variable-type.md)<br/>
[Оператор sizeof](../../cpp/sizeof-operator.md)
