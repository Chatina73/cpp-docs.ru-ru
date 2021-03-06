---
description: Дополнительные сведения см. в статье разделители для Visual C++ тегов документации.
title: Разделители для тегов документации Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation, delimiters
ms.assetid: debfbdd9-63fa-4c58-a18e-a4d203d241d7
ms.openlocfilehash: 7878fa0454af9eb09c4aa537a3e59d8af4a3ee87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201473"
---
# <a name="delimiters-for-visual-c-documentation-tags"></a>Разделители для тегов документации Visual C++

Для создания тегов документации нужно использовать разделители, по которым компилятор определяет начало и конец комментария.

С тегами в XML-документации можно использовать следующие виды разделителей:

| Разделитель | Описание |
|-|-|
| `///` | Это форма, которая показана в примерах документации и используется в шаблонах проектов Visual Studio C++.  |
| `/** */`  | Это многострочные разделители.  |

На использование разделителей `/** */` распространяется несколько правил форматирования.

- Строка, содержащая разделитель `/**`, не обрабатывается как комментарий, если оставшаяся ее часть представляет собой пробелы. Если первый знак является пробелом, то этот пробел игнорируется, а оставшаяся часть строки обрабатывается. В противном случае весь текст, расположенный в строке после разделителя `/**`, обрабатывается как часть комментария.

- Строка, содержащая разделитель `*/`, игнорируется, если перед разделителем `*/` стоят только пробелы. В противном случае текст строки, расположенный перед разделителем `*/`, обрабатывается как часть комментария, и к нему применяются правила сопоставления шаблонов, описанные в следующем разделе.

- В начале каждой из строк, расположенных после строки, которая начинается с разделителя `/**`, компилятор выполняет поиск общего шаблона. Шаблон может включать необязательный пробел и знак звездочки (`*`), после которого следуют необязательные пробелы. Если компилятор находит общий набор символов в начале каждой строки, он игнорирует этот шаблон для всех строк после разделителя `/**` вплоть до самой строки, содержащей разделитель `*/`, и, возможно, включая ее.

Некоторые примеры.

- В следующем комментарии будет обработана только строка, которая начинается с `<summary>`. Следующие форматы с двумя тегами позволяют создать точно такие же комментарии.

    ```cpp
    /**
    <summary>text</summary>
    */
    /** <summary>text</summary> */
    ```

- Компилятор применяет шаблон " \* " для игнорирования в начале второй и третьей строки.

    ```cpp
    /**
     * <summary>
     *  text </summary>*/
    ```

- Компилятор не обнаруживает шаблон в этом комментарии, так как во второй строке нет звездочки. Следовательно, весь текст во второй и третьей строках, расположенный до `*/`, обрабатывается как часть комментария.

    ```cpp
    /**
     * <summary>
       text </summary>*/
    ```

- Компилятор не обнаруживает шаблон в этом комментарии по двум причинам. Во-первых, отсутствует строка, начинающаяся с согласованного числа пробелов перед звездочкой. Во-вторых, пятая строка начинается с символа табуляции, который отличается от пробелов. Следовательно, весь текст во второй строке, расположенный до `*/`, обрабатывается как часть комментария.

    ```cpp
    /**
      * <summary>
      * text
     *  text2
       *  </summary>
    */
    ```

## <a name="see-also"></a>См. также раздел

[Документация XML](xml-documentation-visual-cpp.md)
