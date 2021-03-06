---
description: 'Подробнее о следующем: Расширенные символы'
title: Расширенные символы
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 64b175402f98c1e687f453a897c8e240fd176e0d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97260830"
---
# <a name="wide-characters"></a>Расширенные символы

**ANSI 3.1.3.4** Значение целочисленной символьной константы, которая содержит более одного символа, или расширенной символьной константы, которая содержит более одного многобайтового символа

Обычная символьная константа, ab, имеет целочисленное значение (int)0x6162. Если размер составляет более одного байта, то ранее считанные байты сдвигаются влево на значение **CHAR_BIT**, а следующий байт сравнивается (при помощи оператора побитового ИЛИ) с младшими битами значения **CHAR_BIT**. Число байтов в многобайтовой символьной константе не может превышать (int) — 4 байта в коде для 32-разрядной системы.

Многобайтовая символьная константа считывается так же и преобразуется в расширенную символьную константу с помощью функции времени выполнения `mbtowc`. Если результат не является допустимой многобайтовой символьной константой, выводится ошибка. В любом случае число байтов, проверяемое функцией `mbtowc`, ограничено значением `MB_CUR_MAX`.

## <a name="see-also"></a>См. также

[Символы](../c-language/characters.md)
