---
description: 'Дополнительные сведения: класс Vector &lt; bool &gt; :: Reference'
title: Класс vector&lt;bool&gt;::reference
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 4e9e4700f8af269f02f038c37d55460bae3a2a96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280486"
---
# <a name="vectorltboolgtreference-class"></a>Класс vector&lt;bool&gt;::reference

`vector<bool>::reference`Класс является прокси-классом, предоставляемым [ \<bool> классом Vector](../standard-library/vector-bool-class.md) для имитации `bool&` .

## <a name="remarks"></a>Комментарии

Необходима смоделированная ссылка, поскольку C++ изначально не допускает прямых ссылок на биты. `vector<bool>` использует только один бит на элемент, ссылку на который можно создать с помощью данного класса прокси. Однако моделирование ссылки является незавершенным, поскольку определенные назначения не являются допустимыми. Например, поскольку адрес `vector<bool>::reference` объекта не может быть получен, следующий код, который пытается использовать, `vector<bool>::operator&` является неправильным:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Инвертирует логическое значение элемента вектора.|
|[bool, оператор](../standard-library/vector-bool-reference-operator-bool.md)|Обеспечивает неявное преобразование из `vector<bool>::reference` в **`bool`** .|
|[Оператор =](../standard-library/vector-bool-reference-operator-assign.md)|Присваивает биту логическое значение или значение, которое содержит элемент со ссылкой.|

## <a name="requirements"></a>Требования

**Заголовок**: \<vector>

**Пространство имен:** std

## <a name="see-also"></a>См. также раздел

[\<vector>](../standard-library/vector.md)\
[Безопасность потоков в стандартной библиотеке C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Справочник по стандартной библиотеке C++](../standard-library/cpp-standard-library-reference.md)
