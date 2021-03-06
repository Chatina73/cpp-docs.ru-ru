---
description: 'Подробнее о следующем: Внешняя компоновка'
title: Внешняя компоновка
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- external linkage, about external linkage
- external linkage
ms.assetid: a6f8ea69-b405-4cdd-bf12-ad5462b73183
ms.openlocfilehash: 6920183c53067462dbaadb8514bf747300eb6a1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196286"
---
# <a name="external-linkage"></a>Внешняя компоновка

Если в первом объявлении на уровне области видимости файла для идентификатора не используется описатель класса хранения **`static`** , объект имеет внешнюю компоновку.

Если в объявлении идентификатора для функции отсутствует описатель *storage-class-specifier*, его компоновка определяется так же, как если бы он был объявлен с описателем *storage-class-specifier* **`extern`** . Если объявление идентификатора объекта содержит область видимости файла и не содержит описатель *storage-class-specifier*, его компоновка является внешней.

Имя идентификатора с внешней компоновкой обозначает ту же функцию или объект данных, что и любое другое объявление того же имени с внешней компоновкой. Два объявления могут находиться в одной записи преобразования или в разных записях преобразования. Если объект или функция также имеет глобальное время жизни, объект или функция используется совместно всей программой.

## <a name="see-also"></a>См. также

[Использование ключевого слова extern для задания компоновки](../cpp/extern-cpp.md)
