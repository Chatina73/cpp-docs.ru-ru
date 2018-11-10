---
title: Тип double
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 42f8ed943fd9d034d5cae8cb057e094363b27d8e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532266"
---
# <a name="type-double"></a>Тип double

Значения типа double с двойной точностью имеют размер 8 байт. Формат напоминает формат чисел с плавающей запятой, за исключением того, что он имеет 11-разрядную экспоненту (ее значение может превышать 1023) и 52-разрядную мантиссу, а также еще один старший разряд. Значения типа double в этом формате могут находиться в диапазоне примерно от 1,7E–308 до 1,7E+308.

**Блок, относящийся только к системам Microsoft**

Тип double содержит 64 разряда: 1 для знака, 11 для экспоненты и 52 для мантиссы. Он имеет диапазон +/–1,7E308 с точностью не менее 15 знаков.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Хранение базовых типов](../c-language/storage-of-basic-types.md)