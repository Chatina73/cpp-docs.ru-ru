---
description: 'Дополнительные сведения о: Ошибка компилятора C2243'
title: Ошибка компилятора C2243
ms.date: 11/04/2016
f1_keywords:
- C2243
helpviewer_keywords:
- C2243
ms.assetid: b90065bb-d251-4ba9-8b4c-280ee13fa9c0
ms.openlocfilehash: 48947ee39e61b2db1a64023f730b89d8be8d1907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302198"
---
# <a name="compiler-error-c2243"></a>Ошибка компилятора C2243

Преобразование conversion type из type1 в type2 существует, но недоступно

Защита доступа ( **`protected`** или **`private`** ) не позволила преобразовать указатель на производный класс в указатель на базовый класс.

Следующий пример приводит к возникновению ошибки C2243:

```cpp
// C2243.cpp
// compile with: /c
class B {};
class D : private B {};
class E : public B {};

D d;
B *p = &d;   // C2243

E e;
B *p2 = &e;
```

Базовые классы с **`protected`** или **`private`** доступом недоступны для клиентов производного класса. Эти уровни контроля доступа используются для обозначения того, что базовый класс в реализации должен быть невидим для клиентов. Используйте открытое наследование, чтобы у клиентов производного класса был доступ к неявному преобразованию указателя на производный класс в указатель на базовый класс.
