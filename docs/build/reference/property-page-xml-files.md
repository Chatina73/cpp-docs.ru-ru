---
title: XML-файлы правил для страниц свойств
ms.date: 04/27/2017
helpviewer_keywords:
- property page XML files
ms.assetid: dd9d9734-4387-4098-8ba6-85b93507731d
ms.openlocfilehash: 17b89f00b2e51c960ed7d3219427b56d92851b81
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826486"
---
# <a name="property-page-xml-rule-files"></a>XML-файлы правил для страниц свойств

Страницы свойств проекта в интегрированной среде разработки настраиваются с помощью XML-файлов в папке VCTargets. Точный путь зависит от того, какие выпуски Visual Studio установлены и какой язык используется в продукте. Для англоязычного выпуска Visual Studio 2017 Enterprise используется путь `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033`. XML-файлы описывают имена правил, категории и отдельные свойства, их тип данных, значения по умолчанию и способ их отображения. При задании свойства в интегрированной среде разработки новое значение сохраняется в файле проекта.

Понимать принципы работы этих файлов и интегрированной среды разработки Visual Studio вам нужно только в следующих случаях: (а) вы хотите создать настраиваемую страницу свойств; или (б) вы хотите настроить свойства проекта средствами, отличными от интегрированной среды разработки Visual Studio.

Сначала откроем страницы свойств для проекта (щелкните узел проекта правой кнопкой мыши в **обозревателе решений** и выберите "Свойства"):

![Свойства проекта Visual C++](../media/cpp-property-page-2017.png)

Каждый узел в области **Свойства конфигурации** вызывается правилом (Rule). Правило иногда представляет отдельное средство, например компилятор, но в целом этот термин обозначает нечто, имеющее свойства, выполняющееся и способное выдать некоторые выходные данные. Каждое правило заполняется из XML-файла в папке VCTargets. Например, приведенное выше правило C/C++ заполняется из cl.xml.

Как показано выше, каждое правило имеет набор свойств, которые упорядочены по категориям. Каждый вложенный узел в правиле представляет категорию. Например, узел оптимизации в C/C++ содержит все свойства, связанные с оптимизацией средства компилятора. Свойства и их значения отображаются в виде таблицы в правой области.

Вы можете открыть cl.xml в Блокноте или редакторе XML (см. снимок ниже). Вы увидите корневой узел "Правило", содержащий такой же список определенных свойств, как и в пользовательском интерфейсе, а также дополнительные метаданные.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--Copyright, Microsoft Corporation, All rights reserved.-->
<Rule Name="CL" PageTemplate="tool" DisplayName="C/C++" SwitchPrefix="/" Order="10" xmlns="http://schemas.microsoft.com/build/2009/properties" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib">
  <Rule.Categories>
    <Category Name="General" DisplayName="General" />
    <Category Name="Optimization" DisplayName="Optimization" />
    <Category Name="Preprocessor" DisplayName="Preprocessor" />
    <Category Name="Code Generation" DisplayName="Code Generation" />
    <Category Name="Language" DisplayName="Language" />
    <Category Name="Precompiled Headers" DisplayName="Precompiled Headers" />
    <Category Name="Output Files" DisplayName="Output Files" />
    <Category Name="Browse Information" DisplayName="Browse Information" />
    <Category Name="Advanced" DisplayName="Advanced" />
    <Category Name="All Options" DisplayName="All Options" Subtype="Search" />
    <Category Name="Command Line" DisplayName="Command Line" Subtype="CommandLine" />
  </Rule.Categories>
...
```

В пользовательском интерфейсе страниц свойств каждому узлу в разделе "Свойства конфигурации" соответствует один XML-файл. Вы можете добавлять или удалять правила в пользовательском интерфейсе, добавляя или удаляя расположения в соответствующих XML-файлах в проекте. Например, вот как Microsoft.CppBuild.targets (на один уровень выше папки 1033) включает файл cl.xml:

```xml
<PropertyPageSchema Condition="'$(ConfigurationType)' != 'Utility'" Include="$(VCTargetsPath)$(LangID)\cl.xml"/>
```

Удалив из cl.xml все данные, вы получите следующую основную схему.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Rule>
  <Rule.DataSource />
  <Rule.Categories>
    <Category />
        ...
  </Rule.Categories>
  <BoolProperty />
  <EnumProperty />
  <IntProperty />
  <StringProperty />
  <StringListProperty />
</Rule>
```

Следующий раздел описывает каждый из основных элементов, а также некоторые метаданные, которые можно к ним подключить.

1. **Правило:**  Правила обычно является корневым узлом в XML-файле; он может иметь множество атрибутов:

    ```xml
    <Rule Name="CL" PageTemplate="tool" SwitchPrefix="/" Order="10"
              xmlns="http://schemas.microsoft.com/build/2009/properties"
              xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
              xmlns:sys="clr-namespace:System;assembly=mscorlib">
      <Rule.DisplayName>
        <sys:String>C/C++</sys:String>
      </Rule.DisplayName>
    ```

   1. **Имя:** Атрибут Name — это идентификатор для правила. Он должен быть уникальным среди всех XML-файлов страниц свойств в проекте.

   2. **PageTemplate:** Значение этого атрибута используется пользовательский интерфейс для выбора из коллекции шаблонов пользовательского интерфейса. Шаблон tool отображает свойства в виде стандартной таблицы. Другими встроенными значениями для этого атрибута являются debugger и generic. См. описание узлов Debugging и General соответственно, чтобы узнать о формате, который дает указание этих значений. Пользовательский интерфейс для шаблона страницы debugger использует раскрывающийся список для переключения между свойствами различных отладчиков, в то время как шаблон generic отображает разные категории свойств на одной странице вместо того, чтобы использовать несколько вложенных узлов категорий внутри узла Rule. Этот атрибут является просто предложением пользовательского интерфейса; сам XML-файл спроектирован так, чтобы не зависеть от пользовательского интерфейса. Другой пользовательский интерфейс может использовать этот атрибут в иных целях.

   В. **SwitchPrefix:** Это префикс, используемый в командной строке для коммутаторов. Значение "/" приведет к использованию параметров такого вида, как /Zi, /nologo, /W3 и т. д.

   Г. **Порядок:** Это предложение по потенциальным клиентом пользовательского интерфейса на относительное расположение этого правила, по сравнению с другими правилами в системе.

   Д. **xmlns:** Это стандартный элемент XAML. Видно, что указано три пространства имен. Они предназначены для пространств имен для классов десериализации XAML, схем XAML и системного пространства имен соответственно.

   f. **Отображаемое имя:** Это имя, которое отображается на странице свойств пользовательского интерфейса для узла правило. Это значение не локализуется. DisplayName является дочерним элементом правила, а не атрибутом (таким как Name или SwitchPrefix) из-за внутренних требований средства локализации. С точки зрения языка XAML оба объекта эквивалентны. Таким образом, вы можете сделать его атрибутом, чтобы убрать все лишнее, или оставить все как есть.

   ж. **Источник данных:** Это очень важное свойство, которое указывает системе проектов, расположение, из которого следует значение свойства чтения и записи и ее группирование данных (как описано ниже). Для cl.xml эти значения таковы:

      ```xml
      <DataSource Persistence="ProjectFile" ItemType="ClCompile" Label="" HasConfigurationCondition="true" />
      ```

   - `Persistence="ProjectFile` сообщает системе проектов, что все свойства для правила должны быть записаны в файл проекта или файл страницы свойств (в зависимости от того, какой узел использовался для порождения страниц свойств). Другое возможное значение — UserFile, записывающее значение в файл USER.

   - `ItemType="ClCompile"` сообщает, что свойства будут храниться в виде метаданных ItemDefinition или метаданных элемента (только в том случае, если страницы свойств были порождены от узла файла в обозревателе решений) этого типа элемента. Если это поле не задано, свойство записывается как общее свойство в PropertyGroup.

   - `Label=""` указывает, что при записи свойств в виде метаданных `ItemDefinition` метка родительского объекта ItemDefinitionGroup будет пустой (каждый элемент MSBuild может иметь метку). Visual Studio 2017 использует группы с меткой для перехода по файлу проекта VCXPROJ. Обратите внимание, что группы, содержащие большинство свойств правила, имеют метку в виде пустой строки.

   - `HasConfigurationCondition="true"` предписывает системе проектов прикрепить условие конфигурации к значению, чтобы оно вступало в силу только для текущей конфигурации проекта (условие можно прикрепить к родительской группе или самому значению). Например, откройте страницы свойств в узле проекта и установите значение "Да" для свойства **Обрабатывать предупреждения как ошибки** в разделе **Свойства конфигурации > C/C++ Общие**. Следующее значение записывается в файл проекта. Обратите внимание, что к родительскому объекту ItemDefinitionGroup прикреплено условие конфигурации.

      ```xml
      <ItemDefinitionGroup Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">
        <ClCompile>
          <TreatWarningAsError>true</TreatWarningAsError>
        </ClCompile>
      </ItemDefinitionGroup>
      ```

      Если бы это значение было задано на странице свойств для конкретного файла, например stdafx.cpp, значение свойства было бы записано в элемент stdafx.cpp в файле проекта, как показано ниже. Обратите внимание на то, как условие конфигурации напрямую прикрепляется к метаданным.

      ```xml
      <ItemGroup>
        <ClCompile Include="stdafx.cpp">
          <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
        </ClCompile>
      </ItemGroup>
      ```

   Еще одним атрибутом **DataSource**, не указанным выше, является **PersistedName**. Его можно использовать для представления свойства в файле проекта под другим именем. По умолчанию для этого атрибута задано значение свойства **Name**.

   Отдельное свойство может переопределять DataSource родительского правила. В этом случае расположение для значения этого свойства будет отличаться от других свойств в этом правиле.

   з. Существуют и другие атрибуты правила, например Description, SupportsFileBatching и т. п, которые здесь не указаны. Полный набор атрибутов, применимых к правилу или любому другому элементу, можно узнать, изучив документацию по этим типам. Кроме того, можно проверить открытые свойства для типов в пространстве имен `Microsoft.Build.Framework.XamlTypes` в сборке `Microsoft.Build.Framework .dll`.

   i. **DisplayName**, **PageTemplate** и **Order** — эти свойства являются единственными объектами, связанными с пользовательским интерфейсом, в этой модели данных. Эти свойства почти наверняка будут использоваться любым пользовательским интерфейсом, служащим для отображения страниц свойств. Свойства **DisplayName** и **Description** присутствуют почти для всех элементов в XML-файле. И только эти два свойства локализуются (локализация этих строк будет описана позже).

1. **Категория:** Правило может иметь несколько категорий. Порядок, в котором они перечислены в XML-файле, является предложением для пользовательского интерфейса отображать категории в том же порядке. Например, как видно в пользовательском интерфейсе, категории в узле C/C++ указаны в следующем порядке: общие, оптимизация, препроцессор...  Этот порядок идентичен тому, что используется в cl.xml. Пример категории выглядит следующим образом:

    ```xml
    <Category Name="Optimization">
      <Category.DisplayName>
        <sys:String>Optimization</sys:String>
      </Category.DisplayName>
    </Category>
    ```

   Приведенный выше фрагмент кода показывает атрибуты **Name** и **DisplayName**, описанные выше. Опять же, для **Category** существуют и другие атрибуты, не указанные выше. Вы можете узнать о них, ознакомившись с документацией или изучив сборки с помощью ildasm.exe.

1. **Свойства:** Это часть XML-файле и содержит список всех свойств в этом правиле. Каждое свойство может иметь один из пяти возможных типов, показанных в приведенной выше основной схеме XAML. Конечно, в файле можно использовать лишь некоторые из этих типов в файле. Свойство имеет несколько атрибутов, позволяющих полноценно описать его. Здесь я поясню только **StringProperty**. Остальные очень похожи.

    ```xml
    <StringProperty Subtype="file" Name="ObjectFileName" Category="Output Files" Switch="Fo">
      <StringProperty.DisplayName>
        <sys:String>Object File Name</sys:String>
      </StringProperty.DisplayName>
      <StringProperty.Description>
        <sys:String>Specifies a name to override the default object file name; can be file or directory name.(/Fo[name])</sys:String>
      </StringProperty.Description>
    </StringProperty>
    ```

   Большинство атрибутов в этом фрагменте коды было описано выше. Новыми являются Subtype, Category и Switch.

   1. **Subtype** — это атрибут, доступный только для **StringProperty** и **StringListProperty** и предоставляющий контекстные сведения. Например, значение file указывает, что свойство представляет путь к файлу. Эта контекстная информация используется для расширения возможностей редактирования, представляя проводник как редактор свойств, позволяющий пользователю выбрать файл визуально.

   2. **Категория:** Этот код объявляет категории, под которой принадлежит это свойство. Попробуйте найти это свойство в категории **Выходные файлы** в пользовательском интерфейсе.

   В. **Ключ:** Если правило представляет инструмент — например средство компилятора — в этом случае большинство свойств правила передаются как коммутаторы к средству исполняемого файла во время сборки. Значение этого атрибута указывает используемый литерал параметра. Приведенное выше свойство указывает, что его параметром должен быть **Fo**. В сочетании с атрибутом **SwitchPrefix** в родительском правиле это свойство передается в исполняемый файл в виде **/Fo"Debug\"** (отображается в командной строке для C/C++ в пользовательском интерфейсе страницы свойств).

   Другие атрибуты свойства:

   Г. **Отображается:** Если для какой-то причине вы не хотите свойство должно отображаться на страницах свойств (но, возможно, по-прежнему доступны во время сборки), присвойте этому атрибуту значение false.

   Д. **Только для чтения:** Если вы хотите предоставить только для чтения представление значения этого свойства на страницах свойств, установите значение true.

   f. **IncludeInCommandLine:** Некоторые свойства могут не должны быть переданы в средство во время сборки. Присвоив этому атрибуту значение false, можно запретить такую передачу.