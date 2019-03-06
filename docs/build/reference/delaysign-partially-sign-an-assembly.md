---
title: /DELAYSIGN (частичное подписание сборки)
ms.date: 11/04/2016
f1_keywords:
- /delaysign
- VC.Project.VCLinkerTool.DelaySign
helpviewer_keywords:
- /DELAYSIGN linker option
- DELAYSIGN linker option
- -DELAYSIGN linker option
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
ms.openlocfilehash: 753c4d2a2a81803c3b52759b560248d0f4dbe2eb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425683"
---
# <a name="delaysign-partially-sign-an-assembly"></a>/DELAYSIGN (частичное подписание сборки)

```
/DELAYSIGN[:NO]
```

## <a name="arguments"></a>Аргументы

**НЕТ**<br/>
Указывает, что сборка должна быть не подписана частично.

## <a name="remarks"></a>Примечания

Используйте **/delaysign** Если требуется только поместить открытый ключ в сборку. По умолчанию используется **/DELAYSIGN:NO**.

**/Delaysign** никак не действует, за исключением применения с [/keyfile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) или [/keycontainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md).

При запросе полностью подписанной сборки компилятор хэширует файл, содержащий манифест (метаданные сборки), и подписывает хэш закрытым ключом. Итоговая цифровая подпись хранится в файле, содержащем манифест. При отложенной подписи сборки, компоновщик не вычисляет и не сохраняет подпись, а резервирует место в файле для последующего добавления подписи.

Например, с помощью **/delaysign** чтобы поместить сборку в глобальный кэш. После тестирования можно полностью подписать сборку, поместив закрытый ключ в сборку.

См. в разделе [сборки со строгими именами (подписывание сборок) (C + +/ CLI)](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) и [отложенная подпись сборки](/dotnet/framework/app-domains/delay-sign-assembly) Дополнительные сведения о подписи сборки.

Доступны следующие параметры компоновщика, которые влияют на создание сборки.

- [/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)

- [/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)

- [/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)

- [/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)

- [/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств проекта Visual C++ параметр](../../ide/working-with-project-properties.md).

1. Нажмите кнопку **компоновщика** папки.

1. Выберите страницу свойств **Командная строка** .

1. Введите параметр в **Дополнительные параметры** поле.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)
