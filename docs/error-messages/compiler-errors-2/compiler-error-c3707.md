---
title: Ошибка компилятора C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 6faf035c0f4f68b10b187c56bea4cafc776998cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757960"
---
# <a name="compiler-error-c3707"></a>Ошибка компилятора C3707

"функция": метод disp-интерфейса должен иметь DISPID

При использовании метода `dispinterface` его необходимо назначить `dispid`. Чтобы устранить эту ошибку, присвойте `dispid` методу `dispinterface`, например, раскомментируйте атрибут `id` в методе в примере ниже. Дополнительные сведения см. в разделе атрибуты и [идентификатор](../../windows/id.md) [интерфейса](../../windows/dispinterface.md) .

Следующий пример приводит к возникновению ошибки C3707:

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
