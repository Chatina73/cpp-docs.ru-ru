---
title: '/експериментал: module (Включение поддержки модуля)'
description: 'Используйте параметр компилятора/експериментал: Module, чтобы включить экспериментальную поддержку компилятора для именованных модулей.'
ms.date: 04/13/2021
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: dd9d3c9f571b50b328dbb52ee4e7561d5684de1f
ms.sourcegitcommit: bac5dde649d5b0447de1d26a73365e36d74595f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107381172"
---
# <a name="experimentalmodule-enable-module-support"></a>/експериментал: module (Включение поддержки модуля)

Включает экспериментальную поддержку компилятора для именованных модулей библиотеки стандартных шаблонов.

## <a name="syntax"></a>Синтаксис

> **/експериментал: module**[ **-** ]

## <a name="remarks"></a>Примечания

Можно включить поддержку экспериментальных модулей, используя **`/experimental:module`** параметр компилятора вместе с параметром [/std: c + + Latest](std-specify-language-standard-version.md) . Используйте **`/experimental:module-`** , чтобы отключить поддержку модуля явным образом.

Этот параметр доступен начиная с Visual Studio 2015 с обновлением 1. Начиная с Visual Studio 2019 версии 16,2, Черновики стандартных модулей C++ 20 не полностью реализованы в компиляторе Microsoft C++. С помощью функции "модули" можно создавать модули с одной секцией и импортировать модули стандартной библиотеки, предоставляемые корпорацией Майкрософт. Модуль и код, который его использует, должны быть скомпилированы с теми же параметрами компилятора.

Дополнительные сведения о модулях и их использовании и создании см. в разделе [Обзор модулей в C++](../../cpp/modules-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Выберите в раскрывающемся списке **Конфигурация** значение **все конфигурации**.

1. Перейдите на   >  страницу свойств языка **C/C++**  >  **Language** .

1. Измените свойство **включить модули C++ (экспериментальное)** и нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также раздел

[`/headerUnit` (Используйте заголовок Unit ИФК)](headerunit.md)\
[`/exportHeader` (Создание единиц заголовка)](module-exportheader.md)\
[`/reference` (Используйте именованный модуль ИФК)](module-reference.md)\
[`/translateInclude` (Преобразование директив include в директивы Import)](translateinclude.md)\
[`/Zc` Соответствия](zc-conformance.md)
