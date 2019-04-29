---
title: Интерпретация оператора индекса
ms.date: 08/27/2018
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
ms.openlocfilehash: 1c3d5bca66cb294503805fd5b7691331ac380ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375318"
---
# <a name="interpretation-of-subscript-operator"></a>Интерпретация оператора индекса

Как и другие операторы, оператор индекса (**\[]**) может быть переопределен пользователем. Поведение оператора индекса по умолчанию, если он не перегружен, — совмещать имя массива и индекс с помощью следующего метода.

\*((*имя массива*) + (*индекс*))

Как всегда в добавлениях, включающих типы указателей, масштабирование выполняется автоматически с учетом размера типа. Таким образом, результирующее значение не *индекс* байтов от начала координат *имя массива*; скорее, это *индекс*-й элемент массива. (Дополнительные сведения об этом преобразовании см. в разделе [Аддитивные операторы](../cpp/additive-operators-plus-and.md).)

Аналогично, для многомерных массивов адрес извлекается с использованием следующего метода.

((*имя массива*) + (*индекс*1 \* *max*2 \* *max*3 \* ... \* *max*n) + (*индекс*2 \* *max*3 \* ... \* *max*n) +... + *индекс*n))

## <a name="see-also"></a>См. также

[Массивы](../cpp/arrays-cpp.md)<br/>
