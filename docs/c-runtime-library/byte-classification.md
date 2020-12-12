---
description: 'Подробнее: классификация байт'
title: Классификация байтов
ms.date: 04/04/2018
f1_keywords:
- c.types.bytes
helpviewer_keywords:
- code page 932
- byte classification routines
- bytes, testing
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
ms.openlocfilehash: 00691ca85366c5cbbe28b023f2a269838128fe9e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97221700"
---
# <a name="byte-classification"></a>Классификация байтов

Каждая из этих подпрограмм проверяет указанный байт многобайтового символа на соответствие условию. Если не указано иное, выходное значение зависит от настройки категории **LC_CTYPE** языкового стандарта; дополнительные сведения см. в разделе [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Версии этих функций без суффикса **_l** используют текущий языковой стандарт для данного поведения, зависящего от языкового стандарта; версии с суффиксом **_l** идентичны, за исключением того, что они используют переданный параметр языкового стандарта.

> [!NOTE]
> По определению символы между 0 и 127 кодировки ASCII являются подмножеством всех многобайтовых кодировок. Например, японская кодировка катакана содержит как символы ASCII, так и другие символы.

Стандартные константы в следующей таблице определены в \<ctype.h> .

## <a name="multibyte-character-byte-classification-routines"></a>Подпрограммы классификации байтов многобайтовых символов

|Подпрограмма|Условие проверки байта|
|-------------|-------------------------|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Старший байт; результат теста зависит от значения категории **LC_CTYPE** текущего языкового стандарта|
|[_ismbbalnum, _ismbbalnum_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|**isalnum** &#124;&#124; **_ismbbkalnum**|
|[_ismbbalpha, _ismbbalpha_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|**isalpha** &#124;&#124; **_ismbbkalnum**|
|[_ismbbgraph, _ismbbgraph_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|То же, что и **_ismbbprint**, но **_ismbbgraph** не включает символ пробела (0x20)|
|[_ismbbkalnum, _ismbbkalnum_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Не входящий в набор ASCII текстовый символ, отличный от знака препинания. Например, только для кодовой страницы 932, функция **_ismbbkalnum** проверяет на принадлежность к алфавитно-цифровым символам катаканы.|
|[_ismbbkana, _ismbbkana_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Катакана (0xA1–0xDF), только для кодовой страницы 932|
|[_ismbbkprint, _ismbbkprint_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Не входящие в набор ASCII текстовые и пунктуационные символы. Например, только для кодовой страницы 932, **_ismbbkprint** проверяет на принадлежность к алфавитно-цифровым или пунктуационным символам катаканы (диапазон: 0xA1–0xDF).|
|[_ismbbkpunct, _ismbbkpunct_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Не входящий в набор ASCII знак препинания. Например, только для кодовой страницы 932, **_ismbbkpunct** проверяет на принадлежность к пунктуационным символам катаканы.|
|[_ismbblead, _ismbblead_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Первый байт многобайтового символа. Например, только для кодовой страницы 932, допустимые диапазоны: 0x81–0x9F, 0xE0–0xFC.|
|[_ismbbprint, _ismbbprint_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|**isprint** &#124;&#124; **_ismbbkprint**. **ismbbprint** включает пробел (0x20)|
|[_ismbbpunct, _ismbbpunct_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|**ispunct** &#124;&#124; **_ismbbkpunct**|
|[_ismbbtrail, _ismbbtrail_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Второй байт многобайтового символа. Например, только для кодовой страницы 932, допустимые диапазоны: 0x40–0x7E, 0x80–0xEC.|
|[_ismbslead, _ismbslead_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Старший байт (в контексте строк)|
|[ismbstrail, _ismbstrail_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Младший байт (в контексте строк)|
|[_mbbtype, _mbbtype_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Возвращает тип байта, основываясь на предыдущем байте|
|[_mbsbtype, _mbsbtype_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Возвращает тип байта в строке|
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Отслеживает состояние преобразования многобайтового символа.|

Макрос **MB_LEN_MAX** , определенный в \<limits.h> , расширяется до максимальной длины в байтах, которую может иметь любой многобайтовый символ. **MB_CUR_MAX**, определенный в \<stdlib.h> , расширяется до максимальной длины в байтах любого многобайтового символа в текущем языковом стандарте.

## <a name="see-also"></a>См. также раздел

[Подпрограммы универсальной среды выполнения C по категориям](../c-runtime-library/run-time-routines-by-category.md)
