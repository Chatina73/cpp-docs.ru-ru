---
description: 'Дополнительные сведения: перегрузка &gt; &gt; оператора для собственных классов'
title: Перегрузка оператора &gt;&gt; для собственных классов
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: d1b89c94a87e94a5bab255ffafb2b049bad4356d
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099486"
---
# <a name="overloading-the--operator-for-your-own-classes"></a>Перегрузка оператора `>>` для собственных классов

Потоки ввода используют оператор извлечения (`>>`) для стандартных типов. Можно написать аналогичные операторы извлечения для собственных типов; успех зависит от правильности использования пустого пространства.

Ниже приведен пример оператора извлечения для класса `Date`, представленного выше.

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>См. также раздел

[Входные потоки](../standard-library/input-streams.md)
