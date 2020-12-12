---
description: Дополнительные сведения о:/MANIFESTDEPENDENCY (указание зависимостей манифеста)
title: /MANIFESTDEPENDENCY (Указать зависимости манифеста)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalManifestDependencies
helpviewer_keywords:
- MANIFESTDEPENDENCY linker option
- /MANIFESTDEPENDENCY linker option
- -MANIFESTDEPENDENCY linker option
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
ms.openlocfilehash: 129dc84818b0bda9b2106c0d07dca5b605dc6f96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199171"
---
# <a name="manifestdependency-specify-manifest-dependencies"></a>/MANIFESTDEPENDENCY (Указать зависимости манифеста)

```
/MANIFESTDEPENDENCY:manifest_dependency
```

## <a name="remarks"></a>Комментарии

/MANIFESTDEPENDENCY позволяет указать атрибуты, которые будут помещены в \<dependency> раздел файла манифеста.

Сведения о создании файла манифеста см. в разделе [/manifest (создание манифеста параллельной сборки)](manifest-create-side-by-side-assembly-manifest.md) .

Дополнительные сведения о \<dependency> разделах файла манифеста см. в разделе [файлы конфигурации издателя](/windows/win32/SbsCs/publisher-configuration-files).

Сведения о/MANIFESTDEPENDENCY могут передаваться компоновщику одним из двух способов:

- Непосредственно в командной строке (или в файле ответов) с помощью/МАНИФЕСТДЕПЕНДЕНЦИ.

- Через директиву pragma [комментария](../../preprocessor/comment-c-cpp.md) .

В следующем примере показан комментарий/MANIFESTDEPENDENCY, переданный через pragma,

```cpp
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")
```

в результате в файле манифеста будет приведена следующая запись:

```xml
<dependency>
  <dependentAssembly>
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />
  </dependentAssembly>
</dependency>
```

Те же/MANIFESTDEPENDENCY комментарии можно передавать в командной строке следующим образом:

```cmd
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"
```

Компоновщик будет получать комментарии/MANIFESTDEPENDENCY, удалять дублирующиеся записи, а затем добавлять результирующую XML-строку в файл манифеста.  Если компоновщик обнаружит конфликтующие записи, файл манифеста станет поврежденным и приложение не сможет запуститься (в журнал событий может быть добавлена запись, указывающая на источник сбоя).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Подробнее см. в статье [Настройка компилятора C++ и свойства сборки в Visual Studio](../working-with-project-properties.md).

1. Откройте   >    >  страницу свойств **файл манифеста** компоновщика свойств конфигурации.

1. Измените свойство **Дополнительные зависимости манифеста** .

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

1. См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>.

## <a name="see-also"></a>См. также раздел

[Справочник по компоновщику MSVC](linking.md)<br/>
[Параметры компоновщика MSVC](linker-options.md)
