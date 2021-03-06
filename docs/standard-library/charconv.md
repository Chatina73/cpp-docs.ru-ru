---
description: 'Дополнительные сведения о: &lt; чарконв&gt;'
title: '&lt;чарконв&gt;'
ms.date: 07/22/2020
f1_keywords:
- <charconv>
helpviewer_keywords:
- charconv header
ms.openlocfilehash: 9faab40d2b601317e9dd739053c31000da5ea18b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325212"
---
# <a name="ltcharconvgt"></a>&lt;чарконв&gt;

Быстро преобразуйте последовательность символов в целое число или значение с плавающей запятой, а также наоборот.
Одним из способов использования этой библиотеки является запись и обмен значениями с плавающей запятой в текстовых файлах JSON и.

Функции преобразования настраиваются для повышения производительности, а также поддерживают кратчайшие круговые пути. Самое короткое поведение означает, что при преобразовании числа в тип char записывается достаточно точности, чтобы обеспечить восстановление исходного числа при преобразовании этих символов обратно в число с плавающей запятой. Никакие другие функции CRT и STL не предоставляют эту возможность.

Ниже перечислены некоторые преимущества использования `<charconv>` библиотеки.

- Последовательность символов, представляющих числовое значение, не должна завершаться нулем. Аналогично, при преобразовании числа в символы результат не завершается нулем.
- Функции преобразования не распределяют память. Вы владеете буфером во всех случаях.
- Функции преобразования не вызывают исключение. Они возвращают структуру, содержащую сведения об ошибке.
- Преобразования не учитывают режим выполнения округления в режиме ожидания.
- Преобразования не поддерживают языковой стандарт. Они всегда печатают и анализируют десятичные разделители как "." никогда как "," для национальных настроек, использующих запятые.

## <a name="requirements"></a>Требования

**Заголовок:**\<charconv>

**Пространство имен:** std

/std: требуется c++ 17 или более поздней версии.

## <a name="members"></a>Элементы

### <a name="types"></a>Типы

| Тип | Описание |
|-|:-|
| [chars_format](chars-format-class.md) | Задает тип форматирования, например научный, Hex и т. д. |
| [from_chars_result](from-chars-result-structure.md) | Содержит результат `from_chars` преобразования. |
| [to_chars_result](to-chars-result-structure.md) | Содержит результат `to_chars` преобразования. |

### <a name="functions"></a>Функции

| Компонент | Описание |
|-|:-|
| [from_chars](charconv-functions.md#from_chars) | Преобразование chars в тип Integer, float или Double. |
| [to_chars](charconv-functions.md#to_chars)| Преобразование типа Integer, float или Double в char. |

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](cpp-standard-library-header-files.md)
