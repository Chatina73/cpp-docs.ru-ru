---
description: 'Подробнее о следующем: Неправильный доступ к объединению'
title: Неправильный доступ к объединению
ms.date: 11/04/2016
ms.assetid: b273d984-62a8-4003-9a87-bf0149d3f2dd
ms.openlocfilehash: edff4d74e4e31b505e8c6b71555358fcd4b7e070
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182116"
---
# <a name="improper-access-to-a-union"></a>Неправильный доступ к объединению

**ANSI 3.3.2.3** Доступ к члену объекта объединения через члена другого типа

Если объявляется объединение двух типов и сохраняется одно значение, но для доступа к объединению используется другой тип, результаты будут ненадежными.

Например, объявлено объединение **`float`** и **`int`** . Сохраняется значение **`float`** , но программа позднее использует это значение как **`int`** . В таком случае полученное значение будет зависеть от внутренних хранимых данных для значений **`float`** . Целочисленное значение будет ненадежным.

## <a name="see-also"></a>См. также

[Структуры, объединения, перечисления и битовые поля](../c-language/structures-unions-enumerations-and-bit-fields.md)
