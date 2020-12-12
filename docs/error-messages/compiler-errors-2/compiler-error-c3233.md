---
description: 'Дополнительные сведения о: Ошибка компилятора C3233'
title: Ошибка компилятора C3233
ms.date: 11/04/2016
f1_keywords:
- C3233
helpviewer_keywords:
- C3233
ms.assetid: a9210830-1136-4f02-ba41-030c85f93547
ms.openlocfilehash: 825269c96e596a53b9f1852ce50741f9a5d70e6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97311998"
---
# <a name="compiler-error-c3233"></a>Ошибка компилятора C3233

"тип": параметр универсального типа уже ограничен

Ограничение универсального параметра в нескольких предложениях `where` недопустимо.

Следующий пример приводит к возникновению ошибки C3233:

```cpp
// C3233.cpp
// compile with: /clr /LD

interface struct C {};
interface struct D {};

generic <class T>
where T : C
where T : D
ref class E {};   // C3233
```
