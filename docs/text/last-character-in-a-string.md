---
description: 'Дополнительные сведения: последний символ в строке'
title: Последний символ в строке
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 10ab90614509508b9667c29ccf166ddaf784a92e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207245"
---
# <a name="last-character-in-a-string"></a>Последний символ в строке

Используйте следующие советы.

- Во многих случаях конечные диапазоны байтов перекрывают набор символов ASCII. Проверки битевисе можно безопасно использовать для любых управляющих символов (менее 32).

- Рассмотрим следующую строку кода, которая может проверить, является ли последний символ в строке символом обратной косой черты:

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   Поскольку не `strlen` поддерживает MBCS, он возвращает число байтов, а не число символов в многобайтовой строке. Кроме того, обратите внимание, что в некоторых кодовых страницах (например, 932) " \\ " (0x5C) является допустимым младшим байтом ( `sz` является строкой C).

   Одно из возможных решений заключается в перезаписи кода следующим образом:

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   В этом коде используются функции MBCS `_mbsrchr` и `_mbsinc` . Поскольку эти функции поддерживают MBCS, они могут различать \\ символ "" и младший байт " \\ ". Код выполняет некоторое действие, если последний символ в строке имеет значение null (' \ 0 ').

## <a name="see-also"></a>См. также раздел

[Советы по программированию многобайтовых кодировок](../text/mbcs-programming-tips.md)<br/>
[Назначение символов](../text/character-assignment.md)
