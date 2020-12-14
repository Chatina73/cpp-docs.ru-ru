---
description: 'Дополнительные сведения о: Ошибка компилятора C2797'
title: Ошибка компилятора C2797
ms.date: 11/04/2016
f1_keywords:
- C2797
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
ms.openlocfilehash: c10b0acf550a3bbce81210df60dca75a7b2db704
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297568"
---
# <a name="compiler-error-c2797"></a>Ошибка компилятора C2797

Устаревшие Инициализация списка в списке инициализаторов членов или инициализатор нестатических элементов данных не реализован.

Это предупреждение является устаревшим в Visual Studio 2015. В Visual Studio 2013 и более ранних версиях компилятор Microsoft C++ не реализует инициализацию списка внутри списка инициализаторов элементов или инициализатора нестатического члена данных. До Visual Studio 2013 Update 3 в таких случаях инициализация автоматически преобразовывалась в вызов функции, что могло приводить к получению неверного кода. В Visual Studio 2013 Update 3 в таких случаях выводится ошибка.

Этот пример создает C2797:

```
#include <vector>
struct S {
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'

    std::vector<int> v1;
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'
};
```

Этот пример также создает C2797:

```
struct S1 {
    int i;
};

struct S2 {
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664
    S1 s1;
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664
};
```

Чтобы устранить эту проблему, используйте явное создание внутренних списков. Пример:

```
#include <vector>
typedef std::vector<int> Vector;
struct S {
    S() : v1(Vector{1}) {}

    Vector v1;
    Vector v2 = Vector{1, 2};
};
```

Если инициализация списка не требуется:

```
struct S {
    S() : s1("") {}

    std::string s1;
    std::string s2 = std::string("");
};
```

(Компилятор в Visual Studio 2013 делает это неявным образом во всех версиях до Visual Studio 2013 Update 3.)
