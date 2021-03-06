---
description: 'Дополнительные сведения: директивы предварительной обработки файлов Makefile'
title: Директивы предварительной обработки файла makefile
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 7c394e3547044be661fea5a8ec86f05a3b93e967
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138076"
---
# <a name="makefile-preprocessing-directives"></a>Директивы предварительной обработки файла makefile

Директивы предварительной обработки не учитывают регистр. Начальная восклицательная точка (!) должна находиться в начале строки. Ноль или более пробелов или символов табуляции могут появляться после восклицательного знака для отступов.

- `!CMDSWITCHES``+`Параметр { `-` &#124; }...

   Включает или выключает каждый *параметр* в списке. Пробелы или символы табуляции должны находиться перед `+` `-` оператором OR; между оператором и [буквами параметров](running-nmake.md#nmake-options)не может быть ни одного оператора. Буквы не учитывают регистр и задаются без косой черты ( `/` ). Чтобы включить некоторые параметры и отключить другие, используйте отдельные спецификации `!CMDSWITCHES` .

   В файле Makefile можно использовать только/D,/I,/N и/S. В Tools.ini все параметры разрешены, кроме/F,/HELP,/NOLOGO,/X и/?. Изменения, указанные в блоке описания, вступают в силу только после следующего блока описания. Эта директива обновляет **макефлагс**; изменения наследуются при рекурсии, если указан **макефлагс** .

- `!ERROR`*текстовая надпись*

   Отображает *текст* в ошибке NMAKE U1050, а затем останавливает NMAKE, даже если используется модификатор команды/K,/i, `.IGNORE` , `!CMDSWITCHES` или тире ( `-` ). Пробелы или символы табуляции перед *текстом* игнорируются.

- `!MESSAGE`*текстовая надпись*

   Отображает *текст* для стандартного вывода. Пробелы или символы табуляции перед *текстом* игнорируются.

- `!INCLUDE` [ `<` ] *имя_файла* [ `>` ]

   Считывает *filename* как файл makefile, а затем переходит к текущему файлу Makefile. NMAKE сначала ищет *имя файла* в указанном или текущем каталоге, а затем рекурсивно через каталоги любых родительских файлов makefile, а затем, если *filename* заключено в угловые скобки ( `< >` ), в каталогах, заданных макросом **include** , изначально задается переменная среды include. Полезен для передачи `.SUFFIXES` параметров, `.PRECIOUS` и правил вывода в рекурсивные файлы Makefile.

- `!IF`*constant_expression*

   Обрабатывает операторы между `!IF` и Next `!ELSE` или, `!ENDIF` Если *constant_expression* принимает ненулевое значение.

- `!IFDEF` *имя макроса*

   Обрабатывает операторы между `!IFDEF` и следующим `!ELSE` или, `!ENDIF` Если определено *имяМакроса* . Считается, что определен пустой макрос.

- `!IFNDEF` *имя макроса*

   Обрабатывает операторы между `!IFNDEF` и Next `!ELSE` или, `!ENDIF` Если *макрос* не определен.

- `!ELSE` [ `IF` *constant_expression* &#124; `IFDEF` *имяМакроса* &#124; `IFNDEF` *имяМакроса*]

   Обрабатывает операторы между `!ELSE` и следующим, `!ENDIF` Если предыдущие `!IF` инструкции, `!IFDEF` или `!IFNDEF` вычислены до нуля. Необязательные ключевые слова обеспечивают дальнейшее управление предварительной обработкой.

- `!ELSEIF`

   Является синонимом элемента `!ELSE IF`

- `!ELSEIFDEF`

   Является синонимом элемента `!ELSE IFDEF`

- `!ELSEIFNDEF`

   Является синонимом элемента `!ELSE IFNDEF`

- `!ENDIF`

   Помечает конец `!IF` `!IFDEF` блока, или `!IFNDEF` . Любой текст `!ENDIF` , напускаемый в той же строке, игнорируется.

- `!UNDEF` *имя макроса*

   Отменяет определение *имяМакроса*.

## <a name="see-also"></a>См. также раздел

- [Предварительная обработка файла makefile](makefile-preprocessing.md)
