---
title: /Za, /Ze (отключить расширения языка)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: a3d25f71739f9948f2c0237efbaeaf8fa89f2114
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549725"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (отключить расширения языка)

**/Za** параметр компилятора выдает ошибку для языковых конструкций, которые не совместимы с ANSI C89 или ISO C ++ 11. **/Ze** параметр компилятора, который включен по умолчанию, включает расширения Microsoft.

## <a name="syntax"></a>Синтаксис

```
/Za
/Ze
```

## <a name="remarks"></a>Примечания

> [!NOTE]
>  **/Ze** параметр является устаревшим, так как его поведение включено по умолчанию. Мы рекомендуем использовать [/Zc (соответствие)](../../build/reference/zc-conformance.md) параметры компилятора для управления функциями расширения языка. Список параметров компилятора, см. в разделе **нерекомендуемые и удаленные параметры компилятора** статьи [параметры компилятора, упорядоченные по категориям](../../build/reference/compiler-options-listed-by-category.md).

Компилятор Visual C++ предлагает ряд возможностей, не указанный в стандартов ANSI C89, ISO C99 или ISO C++. Эти компоненты называются расширениями Майкрософт для языков C и C++. Эти расширения являются по умолчанию и не доступен при **/Za** параметра. Дополнительные сведения о конкретных расширениях см. в разделе [расширения Майкрософт для языков C и C++](../../build/reference/microsoft-extensions-to-c-and-cpp.md).

Мы рекомендуем отключить расширения языка, указав **/Za** параметр, если планируется переносить программы в других средах. Когда **/Za** указан, компилятор обрабатывает расширенные ключевые слова как простые идентификаторы Майкрософт, отключает расширения Microsoft и автоматически определяет `__STDC__` предустановленный макрос для программ C.

Другие параметры компилятора, используемые с **/Za** может повлиять на том, как компилятор обеспечивает соответствие стандартам.

Способы задания параметры поведения конкретного стандартам, см. в разделе [/Zc](../../build/reference/zc-conformance.md) параметр компилятора.

Дополнительные сведения о вопросах соответствия в Visual C++, см. в разделе [нестандартное поведение](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. В области навигации выберите **свойства конфигурации**, **C/C++**, **языка**.

1. Изменить **отключить расширения языка** свойство.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)<br/>
[/Zc (соответствие)](../../build/reference/zc-conformance.md)
