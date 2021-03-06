---
description: 'Дополнительные сведения о: &lt; codecvt &gt; enums'
title: Перечисления &lt;codecvt&gt;
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bcd40f72f563b3ecf91125f7167f206d4b1b6517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234063"
---
# <a name="ltcodecvtgt-enums"></a>Перечисления &lt;codecvt&gt;

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a> Перечисление codecvt_mode

Указывает сведения о конфигурации для аспектов [языкового стандарта](../standard-library/locale-class.md) .

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>Комментарии

Перечисление определяет три константы, которые предоставляют сведения о конфигурации для аспектов языкового стандарта, объявленных в [\<codecvt>](../standard-library/codecvt.md) . Это могут быть следующие значения:

- `consume_header`, чтобы использовать начальную последовательность заголовка при чтении многобайтовой последовательности и определении порядка байтов следующей многобайтовой последовательности для чтения;

- `generate_header`, чтобы создавать начальную последовательность заголовка при записи многобайтовой последовательности для объявления порядка байтов следующей многобайтовой последовательности для записи;

- `little_endian`, чтобы создавать многобайтовую последовательность в прямом порядке байтов, в отличие от порядка "сначала старший байт" по умолчанию.

Эти константы можно связывать логическим оператором OR в произвольные сочетания.

## <a name="see-also"></a>См. также раздел

[\<codecvt>](../standard-library/codecvt.md)
