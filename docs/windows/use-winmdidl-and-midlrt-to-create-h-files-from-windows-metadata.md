---
title: 'Практическое: использование winmdidl.exe и midlrt.exe для создания h-файлов из метаданных windows | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3f97ef0f285cda7d31ddd53f0a8b0ca9a22f360c
ms.sourcegitcommit: 072e12d6b7a242765bdcc9afe4a14a284ade01fc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50136202"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Практическое руководство. Использование winmdidl.exe и midlrt.exe для создания H-файлов из метаданных Windows

Winmdidl.exe и midlrt.exe разрешают взаимодействие COM-уровня между машинным кодом C++ и компонентами среды выполнения Windows. Winmdidl.exe принимает в качестве входных данных WINMD-файл, содержащий метаданные для компонента среды выполнения Windows, и выводит IDL-файл. Midlrt.exe преобразовывает этот IDL-файл в файлы заголовков, которые можно использовать в коде C++. Оба инструмента запускаются с помощью командной строки.

Эти инструменты используются в следующих двух сценариях:

- создание пользовательских IDL-файлов и файлов заголовков, чтобы приложение C++, написанное с помощью библиотеки шаблонов среды выполнения Windows (WRL), могло использовать пользовательский компонент среды выполнения Windows;

- создание прокси-сервера и файлов-заглушек для определяемых пользователем типов событий в компоненте среды выполнения Windows. Дополнительные сведения см. в разделе [пользовательские события и доступа к событиям в компонентах среды выполнения Windows](/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Эти инструменты требуются только для синтаксического анализа пользовательских WINMD-файлов. IDL- и H-файлы для компонентов операционной системы Windows уже созданы. По умолчанию в Windows 8.1, они находятся в \Program файлы (x86) \Windows Kits\8.1\Include\winrt\\.

## <a name="location-of-the-tools"></a>Расположение инструментов

По умолчанию в [Windows 8.1, winmdidl.exe и midlrt.exe расположены в C:\Program Files (x86) \Windows Kits\8.1\\. Различные версии этих инструментов также доступны в папках \bin\x86\ и \bin\x64\.

## <a name="winmdidl-command-line-arguments"></a>Аргументы командной строки winmdidl

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Блокирует отображение в консоли сообщения об авторских правах и номере версии winmdidl.

**/suppressversioncheck**<br/>
Не используется.

**/ время**<br/>
Выводит общее время выполнения в окно консоли.

**/ outdir:**<em>dir</em><br/>
Задает выходной каталог. Если путь содержит пробелы, используйте кавычки. Выходной каталог по умолчанию  *\<диска >*: \Users\\*\<имя пользователя >* \AppData\Local\VirtualStore\Program Files (x86) \Microsoft Visual Studio 12.0\\.

**/ баннер:**<em>файла</em><br/>
Указывает файл, содержащий пользовательский текст, который необходимо вставить в начало сообщения по умолчанию об авторских правах и версии winmdidl в верхней части сгенерированного IDL-файла. Если путь содержит пробелы, используйте кавычки.

**/utf8**<br/>
Файл будет отформатирован в кодировке UTF-8.

*Winmdfile*<br/>
Имя WINMD-файла для анализа. Если путь содержит пробелы, используйте кавычки.

## <a name="midlrt-command-line-arguments"></a>Аргументы командной строки midlrt

См. в разделе [MIDLRT и среды выполнения Windows компоненты](/windows/desktop/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Примеры

В следующем примере показана работа команды winmdidl в командной строке Visual Studio x86. Она определяет выходную папку и файл, содержащий специальный текст баннера, который следует добавить в сгенерированный IDL-файл.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

В следующем примере показан вывод в окно консоли результата работы команды winmdidl, который указывает, что операция выполнена успешно.

**Создание c:\users\giraffe\documents\\\Test_for_winmdidl.idl**

Затем для созданного IDL-файла выполняется команда midlrt. Обратите внимание, что **metadata_dir** аргумента указывается после имени IDL-файла. Путь \WinMetadata\ является обязательным — это расположение для windows.winmd.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Примечания

Выходной файл операции winmdidl будет иметь то же имя, что и входной файл, но с расширением IDL.

При разработке компонента среды выполнения Windows, который будет доступен из WRL, можно указать в качестве действий после сборки запуск инструментов winmdidl.exe и midlrt.exe для создания IDL- и H-файлов при каждой сборке. Например, см. в разделе [создание событий в компонентах среды выполнения Windows](/uwp/winrt-components/raising-events-in-windows-runtime-components).