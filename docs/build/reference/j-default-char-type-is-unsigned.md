---
title: /J (тип знака по умолчанию не подписан)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: 931253b0a50e8b8f96a385400b2afbb1894c9d47
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417701"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (тип знака по умолчанию не подписан)

Изменяет значение по умолчанию `char` тип из `signed char` для `unsigned char`и `char` типа выполняется с дополнением нулями для `int` типа.

## <a name="syntax"></a>Синтаксис

```
/J
```

## <a name="remarks"></a>Примечания

Если `char` значение явно объявляется как `signed`, **/j** параметр не влияет на его, а значение — расширенному знаком нулями для `int` типа.

**/J** определяет параметр `_CHAR_UNSIGNED`, который используется с `#ifndef` в файле LIMITS.h для определения диапазона по умолчанию `char` типа.

ANSI C и C++ не требуют реализации `char` типа. Этот параметр полезен при работе с символьными данными, в конечном итоге будет преобразован в языке, отличном от английского.

> [!NOTE]
>  При использовании этого параметра компилятора с ATL и MFC, ошибка может быть создано. Несмотря на то, что их можно отключить, эту ошибку, определив `_ATL_ALLOW_CHAR_UNSIGNED`, это решение не поддерживается и может работать не всегда.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. В области **Обозреватель решений**откройте контекстное меню для проекта и выберите пункт **Свойства**.

1. В проекте **страницы свойств** диалоговое окно, в области слева в разделе **свойства конфигурации**, разверните **C/C++** , а затем выберите **командной строки**.

1. В **Дополнительные параметры** области укажите **/j** параметр компилятора.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>См. также

[Параметры компилятора](../../build/reference/compiler-options.md)<br/>
[Настройка параметров компилятора](../../build/reference/setting-compiler-options.md)<br/>
[Работа со свойствами проектов](../../ide/working-with-project-properties.md)
