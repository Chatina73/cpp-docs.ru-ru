---
description: 'Дополнительные сведения: `/Zc:auto` (вывод типа переменной)'
title: /Zc:auto (выведение типа переменной)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: d20f377fc653e9c3cceb5c3e81b5e5e8a815bcad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114719"
---
# <a name="zcauto-deduce-variable-type"></a>`/Zc:auto` (Вывод типа переменной)

**`/Zc:auto`** Параметр компилятора сообщает компилятору, как использовать [ `auto` ключевое слово](../../cpp/auto-cpp.md) для объявления переменных. Если задан параметр по умолчанию, **`/Zc:auto`** компилятор выводит тип объявленной переменной из выражения инициализации. Если задано значение **`/Zc:auto-`** , компилятор выделяет переменную для автоматического класса хранения.

## <a name="syntax"></a>Синтаксис

> **`/Zc:auto`**[**`-`**]

## <a name="remarks"></a>Комментарии

Стандарт C++ определяет исходное и измененное значение **`auto`** ключевого слова. До Visual Studio 2010 ключевое слово объявляет переменную в автоматическом классе хранения. то есть переменная с локальным временем существования. Начиная с Visual Studio 2010, ключевое слово выводит тип переменной из выражения инициализации объявления. Используйте **`/Zc:auto`** параметр компилятора, чтобы сообщить компилятору об использовании измененного значения **`auto`** ключевого слова. Параметр включен по **`/Zc:auto`** умолчанию. [`/permissive-`](permissive-standards-conformance.md)Параметр не изменяет значение по умолчанию для **`/Zc:auto`** .

Компилятор выдает соответствующее диагностическое сообщение, если использование **`auto`** ключевого слова противоречит текущему **`/Zc:auto`** параметру компилятора. Дополнительные сведения см. в разделе [ `auto` ключевое слово](../../cpp/auto-cpp.md). Дополнительные сведения о проблемах соответствия с Visual C++ см. в разделе [нестандартное поведение](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Установка параметра компилятора в Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите страницу свойств **Свойства конфигурации**  >  **C/C++**  >  **Командная строка** .

1. Добавьте **`/Zc:auto`** или **`/Zc:auto-`** в область **Дополнительные параметры:** панель.

## <a name="see-also"></a>См. также раздел

[`/Zc` Соответствия](zc-conformance.md)<br/>
[Ключевое слово `auto`](../../cpp/auto-cpp.md)
