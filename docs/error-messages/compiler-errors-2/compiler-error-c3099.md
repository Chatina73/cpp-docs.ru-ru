---
title: Ошибка компилятора C3099
ms.date: 11/04/2016
f1_keywords:
- C3099
helpviewer_keywords:
- C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
ms.openlocfilehash: beaa34bb9bed4824383cdad32c6bfd0aea19f6b7
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418585"
---
# <a name="compiler-error-c3099"></a>Ошибка компилятора C3099

keyword: используйте [System::AttributeUsageAttribute] для управляемых атрибутов; используйте [Windows::Foundation::Metadata::AttributeUsageAttribute] для атрибутов WinRT

Используйте <xref:System.AttributeUsageAttribute> для объявления **/CLR** атрибуты. Используйте `Windows::Foundation::Metadata::AttributeUsageAttribute` для объявления атрибутов среды выполнения Windows.

Дополнительные сведения об атрибутах/CLR, см. в разделе [определяемые пользователем атрибуты](../../windows/user-defined-attributes-cpp-component-extensions.md). Для атрибутов, поддерживаемых в среде выполнения Windows, см. в разделе [пространство имен Windows.Foundation.Metadata](/uwp/api/windows.foundation.metadata)

## <a name="example"></a>Пример

В следующем примере показано возникновение ошибки C3099 и приводятся сведения по ее устранению.

```
// C3099.cpp
// compile with: /clr /c
using namespace System;
[usage(10)]   // C3099
// try the following line instead
// [AttributeUsageAttribute(AttributeTargets::All)]
ref class A : Attribute {};
```