---
description: 'Подробнее о следующем: Преобразования из других типов'
title: Преобразования из других типов
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: 0b9497c4873e42f9d08463c4ec1396b178b6f362
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293200"
---
# <a name="conversions-from-other-types"></a>Преобразования из других типов

Поскольку значение **`enum`** по определению имеет тип **`int`** , преобразования в тип **`enum`** и обратно выполняются так же, как и для типа **`int`** . В компиляторе Microsoft C тип integer обрабатывается так же, как и **`long`** .

**Блок, относящийся только к системам Microsoft**

Преобразование между типами структуры и объединения не допускаются.

Любое значение можно преобразовать в тип **`void`** , но результат такого преобразования можно использовать только в контексте, в котором значение выражения отбрасывается, например в операторе выражения.

Тип **`void`** по определению не имеет значения. Поэтому его невозможно преобразовать ни в какой другой тип, а другие типы невозможно преобразовать в **`void`** путем присваивания. Однако значение можно явным образом преобразовать в тип **`void`** , как описано в статье [Преобразования с приведением типов](../c-language/type-cast-conversions.md).

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Преобразования назначений](../c-language/assignment-conversions.md)
