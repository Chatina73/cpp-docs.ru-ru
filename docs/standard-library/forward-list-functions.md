---
description: 'Дополнительные сведения: &lt; функции forward_list &gt;'
title: Функции &lt;forward_list&gt;
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 3f827b777f2e6fa62dd78c7d737d5da84b50610c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324374"
---
# <a name="ltforward_listgt-functions"></a>Функции &lt;forward_list&gt;

## <a name="swap"></a><a name="swap"></a> позиции

Меняет местами элементы двух прямых списков.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Параметры

*слева*\
Объект типа `forward_list`.

*Правильно*\
Объект типа `forward_list`.

### <a name="remarks"></a>Комментарии

Шаблонная функция выполняет `left.swap(right)`.
