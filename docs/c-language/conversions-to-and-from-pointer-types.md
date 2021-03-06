---
description: 'Подробнее о следующем: Преобразования в типы указателей и из типов указателей'
title: Преобразования в типы указателей и из типов указателей
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 8eb987358cb3e8375e62b9d03cd21a5e02b9f5c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97293096"
---
# <a name="conversions-to-and-from-pointer-types"></a>Преобразования в типы указателей и из типов указателей

Указатель на один тип значения можно преобразовать в указатель на другой тип. Однако результат может оказаться неопределенным из-за требований к выравниванию, а также размеров различных типов в хранилище. Указатель на один объект можно преобразовать в указатель на другой объект, тип которого требует менее строгого или такого же строгого выравнивания хранилища, и обратно без изменений.

Указатель на тип **`void`** можно преобразовать в указатель на любой тип и из указателя на любой тип без ограничений и потери данных. Если результат преобразуется обратно в исходный тип, восстанавливается исходный указатель.

Если указатель преобразуется в другой указатель того же типа, но с другими или дополнительными квалификаторами, новый указатель совпадает со старым, за исключением ограничений, накладываемых новыми квалификаторами.

Значение указателя можно также преобразовать в целочисленное значение. Путь преобразования зависит от размера указателя и размера целочисленного типа согласно следующим правилам.

- Если размер указателя больше или равен размеру целочисленного типа, указатель ведет себя подобно беззнаковому значению в преобразовании, за исключением того, что он не может быть преобразован в значение с плавающей запятой.

- Если размер указателя меньше размера целочисленного типа, он сначала преобразуется в указатель того же размера, как у целочисленного типа, а затем в целочисленный тип.

И наоборот, целочисленный тип можно преобразовать в тип указателя согласно следующим правилам.

- Если размер целочисленного типа совпадает с размером типа указателя, преобразование просто приводит к обработке целочисленного значения как указателя (целого числа без знака).

- Если размер целочисленного типа отличается от размера типа указателя, сначала целочисленный тип преобразуется в размер указателя по алгоритмам преобразования, которые указаны в таблицах [Преобразование из целочисленных типов со знаком](../c-language/conversions-from-signed-integral-types.md) и [Преобразование из целочисленных типов без знака](../c-language/conversions-from-unsigned-integral-types.md), а затем рассматривается как значение указателя.

Константное целочисленное выражение со значением 0 или аналогичное выражение, приведенное к типу **`void`** <strong>\*</strong>, можно преобразовать в указатель любого типа путем приведения типов, присваивания или сравнения. При этом создается пустой указатель, равный другому пустому указателю того же типа, но не равный любому указателю на функцию или объект. Целые числа, отличные от константы 0, можно преобразовать в тип указателя, но результат будет непереносимым.

## <a name="see-also"></a>См. также

[Преобразования назначений](../c-language/assignment-conversions.md)
