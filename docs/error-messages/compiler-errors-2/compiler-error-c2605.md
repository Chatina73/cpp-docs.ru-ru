---
description: 'Дополнительные сведения о: Ошибка компилятора C2605'
title: Ошибка компилятора C2605
ms.date: 11/04/2016
f1_keywords:
- C2605
helpviewer_keywords:
- C2605
ms.assetid: a0e6f132-5acf-4e19-b277-ddf196d182bf
ms.openlocfilehash: e2aa86419b816cc48eecb9b981df73eeb3e48ccd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336241"
---
# <a name="compiler-error-c2605"></a>Ошибка компилятора C2605

name: этот метод зарезервирован в управляемом классе или классе WinRT

Определенные имена зарезервированы компилятором для внутренних функций.  Дополнительные сведения см. в разделе [деструкторы и методы завершения](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Пример

Следующий пример приводит к возникновению ошибки C2605:

```cpp
// C2605.cpp
// compile with: /clr /c
ref class R {
protected:
   void Finalize() {}   // C2605
};
```
