---
description: 'Дополнительные сведения о: Ошибка компилятора C2217'
title: Ошибка компилятора C2217
ms.date: 11/04/2016
f1_keywords:
- C2217
helpviewer_keywords:
- C2217
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
ms.openlocfilehash: 4cd67cb56cb988aa005725435f1829312ee57a31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245542"
---
# <a name="compiler-error-c2217"></a>Ошибка компилятора C2217

для "атрибут1" требуется "атрибут2"

Для первого атрибута функции требуется второй атрибут.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Чтобы устранить ошибку, проверьте указанные ниже возможные причины ее возникновения.

1. Функция interrupt ( `__interrupt` ), объявленная как `near` . Функции прерывания должны быть `far` .

1. Функция прерывания, объявленная с помощью **`__stdcall`** , или **`__fastcall`** . Функции прерывания должны использовать соглашения о вызовах C.

## <a name="example"></a>Пример

C2217 также может возникать при попытке привязки делегата к функции CLR, которая принимает переменное число аргументов. Если функция также имеет перегрузку массива e param, используйте вместо нее. Следующий пример приводит к возникновению ошибки C2217.

```cpp
// C2217.cpp
// compile with: /clr
using namespace System;
delegate void MyDel(String^, Object^, Object^, ...);   // C2217
delegate void MyDel2(String ^, array<Object ^> ^);   // OK

int main() {
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);
   array<Object ^ > ^ x = gcnew array<Object ^>(2);
   x[0] = safe_cast<Object^>(0);
   x[1] = safe_cast<Object^>(1);

   // wl("{0}, {1}", 0, 1);
   wl("{0}, {1}", x);
}
```
