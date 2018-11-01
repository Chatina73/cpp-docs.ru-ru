---
title: Класс independent_bits_engine
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: 8f420ca054d20cd222b8eda9a4a35a383a8e535a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635842"
---
# <a name="independentbitsengine-class"></a>Класс independent_bits_engine

Создает случайную последовательность чисел с указанным числом разрядов, перемешивая разряды из значений, возвращенных базовым механизмом.

## <a name="syntax"></a>Синтаксис

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Параметры

*ядра*<br/>
Тип базового механизма.

*W*<br/>
**Размер слова**. Размер каждого полученного числа в битах. **Предварительные условия**: `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*<br/>
Беззнаковый целочисленный тип результата. Возможные типы см. в разделе [\<random>](../standard-library/random.md).

## <a name="members"></a>Участники

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Дополнительные сведения о членах механизма см. в разделе [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Примечания

Этот класс шаблона описывает *адаптер механизма* , формирующий значения за счет упаковки разрядов из значений, возвращаемых базовым механизмом, в результате чего *W*-разрядных значений.

## <a name="requirements"></a>Требования

**Заголовок:** \<random>

**Пространство имен:** std

## <a name="see-also"></a>См. также

[\<random>](../standard-library/random.md)<br/>
