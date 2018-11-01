---
title: /MANIFESTDEPENDENCY (Указать зависимости манифеста)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: aba4bd1b36bfda35be9e567851596fbedecf38ca
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654926"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Указать зависимости манифеста)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Примечания

/ Параметр MANIFESTDEPENDENCY разрешает Задание атрибутов, которые будут помещены в \<зависимостей > раздел файла манифеста.

См. в разделе [/MANIFEST (Создание Side-by-Side манифеста сборки)](../../build/reference/manifest-create-side-by-side-assembly-manifest.md) сведения о том, как создать файл манифеста.

Дополнительные сведения о \<зависимостей > раздел файла манифеста см. в разделе [файлов конфигурации издателя](/windows/desktop/SbsCs/publisher-configuration-files).

/ MANIFESTDEPENDENCY информацию можно передать в компоновщик, одним из двух способов:

- Непосредственно в командной строке (или в файле ответов) с помощью/MANIFESTDEPENDENCY.

- С помощью [комментарий](../../preprocessor/comment-c-cpp.md) директивы pragma.

В следующем примере показано комментария/MANIFESTDEPENDENCY, переданные с помощью директивы pragma

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

что приводит к следующей записи в файле манифеста:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Точно такие же комментарии/MANIFESTDEPENDENCY может быть передан в командной строке следующим образом:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

Компоновщик будет собирать/MANIFESTDEPENDENCY комментарии, исключить повторяющиеся записи и затем добавьте результирующую строку XML в файл манифеста.  Если компоновщик обнаруживает конфликтующие записи, файл манифеста будет поврежден и приложение не запускается (запись могут добавляться в журнал событий, указывающий источник сбоя).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Выберите **свойства конфигурации** > **компоновщика** > **файл манифеста** страницу свойств.

1. Изменить **Дополнительные зависимости манифеста** свойство.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

1. См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)