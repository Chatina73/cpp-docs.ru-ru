---
title: /Qspectre-load-cf
description: Описывает параметр Microsoft C/C++ COMPILER (компилятором MSVC)/Qspectre-load-cf.
ms.date: 01/28/2020
helpviewer_keywords:
- /Qspectre-load-cf
no-loc:
- Qspectre-load-cf
ms.openlocfilehash: c32b843df517cb6fbe662fba0b592cbf745f1764
ms.sourcegitcommit: 0f4ee9056d65043fa5a715f0ad1031c0ed30e2b6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035550"
---
# /Qspectre-load-cf

Указывает создание компилятором инструкций сериализации для каждой инструкции потока управления, содержащей нагрузку. Этот параметр выполняет подмножество мер по устранению рисков, выполненных с помощью параметра [/кспектре-лоад](qspectre-load.md) .

## <a name="syntax"></a>Синтаксис

> **/Qspectre-load-cf**

## <a name="remarks"></a>Remarks

**/Qspectre-load-cf** предписывает компилятору обнаруживать `JMP`, `RET`и `CALL` инструкции потока управления, которые загружаются из памяти, и вставлять инструкции сериализации после загрузки. Там, где это возможно, эти инструкции делятся на нагрузку и передачу потока управления. После загрузки следует `LFENCE`, чтобы обеспечить защиту нагрузки. Бывают случаи, когда компилятору не удается разделить инструкции, например инструкцию `JMP`, поэтому используется альтернативный метод устранения. Например, компилятор уменьшает `jmp [rax]`, добавляя инструкции для загрузки целевого объекта без разрушения перед вставкой ЛФЕНЦЕ, как показано ниже:

```asm
    xor rbx, [rax]
    xor rbx, [rax]  ; force a load of [rax]
    lfence          ; followed by an LFENCE
    jmp [rax]
```

Поскольку **/Qspectre-load-cf** прекращает выдвижение всех нагрузок в инструкциях по управлению потоком, это влияет на производительность. Устранение рисков не подходит для всех. При наличии критических для производительности блоков кода, которые не нуждаются в защите, их можно отключить с помощью `__declspec(spectre(nomitigation))`.

Параметр **/Qspectre-load-cf** отключен по умолчанию и поддерживает все уровни оптимизации.

Параметр **/Qspectre-load-cf** доступен в Visual Studio 2019 версии 16,5 и более поздних версиях. Этот параметр доступен только в компиляторах, предназначенных для процессоров x86 и x64. Он недоступен в компиляторах, предназначенных для процессоров ARM.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Установка данного параметра компилятора в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

2. Выберите **Свойства конфигурации** > странице свойств **создания кода** **C++ C/**  > .

3. Выберите новое значение для свойства **устранения рисков устранением рисков Spectre** . Чтобы применить изменение, нажмите кнопку **ОК**.

### <a name="to-set-this-compiler-option-programmatically"></a>Установка данного параметра компилятора программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также раздел

[Параметры/q (низкоуровневые операции)](q-options-low-level-operations.md)\
\ [параметров компилятора компилятором MSVC](compiler-options.md)
[Синтаксис командной строки компилятора КОМПИЛЯТОРОМ MSVC](compiler-command-line-syntax.md)
