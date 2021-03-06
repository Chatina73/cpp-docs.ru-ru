---
title: /Zc:trigraphs (подстановка триграфов)
description: Параметр компилятора Microsoft C++, который управляет поддержкой соответствия для триграфов.
ms.date: 07/25/2020
f1_keywords:
- /Zc:trigraphs
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
ms.openlocfilehash: e24f3d2f0064c3acc04b4c3774f47f6e442d5ddd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211857"
---
# <a name="zctrigraphs-trigraphs-substitution"></a>`/Zc:trigraphs`(Подстановка триграфов)

Если **`/Zc:trigraphs`** указан параметр, компилятор заменяет последовательность символов триграф с помощью соответствующего знака пунктуации.

## <a name="syntax"></a>Синтаксис

> **`/Zc:trigraphs`**[**`-`**]

## <a name="remarks"></a>Remarks

*Триграф* состоит из двух последовательных вопросительных знаков ( **`??`** ), за которыми следует уникальный третий символ. Стандарт языка C поддерживает триграфов для исходных файлов, использующих набор символов, который не содержит удобные графические представления для некоторых символов пунктуации. Например, если включены триграфов, компилятор заменяет **`??=`** триграф с помощью **`#`** символа. С помощью C++ 14 триграфов поддерживаются как в C. Стандарт C++ 17 удаляет триграфов из языка C++. В коде C++ **`/Zc:trigraphs`** параметр компилятора позволяет подстановку последовательностей триграф соответствующими символами пунктуации. **`/Zc:trigraphs-`** отключает подстановку триграф.

По **`/Zc:trigraphs`** умолчанию параметр отключен, а параметр не изменяется, если [`/permissive-`](permissive-standards-conformance.md) указан параметр.

Список триграфов C/C++ и пример, демонстрирующий использование триграфов, см. в разделе [триграфов](../../c-language/trigraphs.md).

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите страницу свойств **Свойства конфигурации**  >  **C/C++**  >  **Командная строка** .

1. Измените свойство **Дополнительные параметры** на включить **`/Zc:trigraphs`** или **`/Zc:trigraphs-`** и нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел

[`/Zc`Соответствия](zc-conformance.md)<br/>
[Триграфы](../../c-language/trigraphs.md)
