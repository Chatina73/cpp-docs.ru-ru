---
title: Тип char
ms.date: 11/04/2016
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
ms.openlocfilehash: bc8d3bef85b82d5bb5c2575b3bc6c6d8a4887140
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345049"
---
# <a name="type-char"></a>Тип char

Тип `char` используется для хранения целочисленного значения члена представительной кодировки. Целочисленное значение — это код ASCII, соответствующий указанному символу.

**Блок, относящийся только к системам Microsoft**

Значения символов типа `unsigned char` находятся в диапазоне от 0 до 0xFF по шестнадцатеричной системе счисления. **signed char** имеет диапазон от 0x80 до 0x7F. Эти диапазоны преобразуются в диапазоны от 0 до 255 и от -128 до +127 по десятичной системе счисления соответственно. Параметр компилятора /J меняет используемый по умолчанию вариант: вместо **signed** устанавливается `unsigned`.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Хранение базовых типов](../c-language/storage-of-basic-types.md)
