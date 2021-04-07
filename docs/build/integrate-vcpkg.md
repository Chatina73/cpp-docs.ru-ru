---
title: Интеграция vcpkg с Visual Studio или Visual Studio Code
description: Сведения об интеграции vcpkg с Visual Studio в Windows или Visual Studio Code в macOS и Linux.
ms.date: 12/11/2020
ms.technology: cpp-ide
ms.openlocfilehash: a08820ad65781a89ec6bc59a62d615cae2798b4b
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099382"
---
# <a name="integrate-vcpkg-with-visual-studio-or-visual-studio-code"></a>Интеграция vcpkg с Visual Studio или Visual Studio Code

vcpkg — это кроссплатформенный диспетчер пакетов командной строки для библиотек C и C++. Вы можете интегрировать его с Visual Studio в Windows или Visual Studio Code в macOS и Linux.

## <a name="integrate-with-visual-studio-on-windows"></a>Интеграция с Visual Studio в Windows

### <a name="integrate-per-user"></a>Интеграция на уровне пользователя

Из корневого каталога vcpkg выполните команду **`vcpkg integrate install`** , чтобы настроить Visual Studio для поиска всех файлов заголовков и двоичных файлов vcpkg на уровне пользователя. Не нужно изменять пути к каталогам VC++ в Visual Studio. При наличии нескольких клонов vcpkg клон, из которого выполняется эта команда, становится новым расположением по умолчанию.

Теперь вы можете включать заголовки, начиная вводить название папки или заголовка, а затем воспользовавшись вариантом, который предложит функция автозавершения. Не требуются никакие дополнительные действия для привязки библиотек или добавления ссылок на проекты. На рисунке ниже показано, как Visual Studio находит файлы заголовков *`azure-storage-cpp`* . vcpkg помещает свои заголовки во вложенную папку *`/installed`* , распределяя их по целевым платформам. На следующей схеме показан список файлов #include для библиотеки во вложенной папке *`/was`* .

![Всплывающее окно автозавершения IntelliSense в редакторе Visual Studio](media/vcpkg-intellisense.png "vcpkg и IntelliSense")

### <a name="integrate-per-project"></a>Интеграция на уровне проекта

Если вам нужно использовать определенную версию библиотеки, которая отличается от версии в вашем активном экземпляре vcpkg, сделайте следующее.

1. Создайте новый клон vcpkg. Дополнительные сведения см. в разделе [Установка vcpkg](install-vcpkg.md).

1. Перейдите в новый корневой каталог vcpkg.

1. Измените файл портов для библиотеки, чтобы получить нужную версию.

1. Выполните **`vcpkg install <library>`** . Дополнительные сведения см. в разделе [Управление библиотеками с помощью vcpkg](manage-libraries-with-vcpkg.md).

1. Используйте **`vcpkg integrate project`** для создания пакета NuGet, который будет ссылаться на эту библиотеку для каждого конкретного проекта.

## <a name="integrate-with-visual-studio-code-on-linux-or-macos"></a>Интеграция с Visual Studio Code в Linux или macOS

В окне оболочки или терминала перейдите в корневой каталог vcpkg. Выполните команду **`./vcpkg integrate install`** для настройки Visual Studio Code в Linux или macOS. Эта команда задает расположение инструментов и библиотек vcpkg, а также включает технологию IntelliSense в исходных файлах.

## <a name="remove-vcpkg-integration"></a>Удаление интеграции vcpkg

Если вы использовали параметр **`integrate`** , необходимо удалить интеграцию перед удалением экземпляра vcpkg. Чтобы удалить и очистить интеграцию, перейдите в корневой каталог vcpkg. Чтобы очистить интеграцию, в Windows выполните команду **`vcpkg integrate remove`** . В Linux или macOS выполните команду **`./vcpkg integrate remove`** .

## <a name="see-also"></a>См. также раздел

[vcpkg: диспетчер пакетов C++ для Windows, Linux и macOS](./vcpkg.md)\
[vcpkg на GitHub](https://github.com/Microsoft/vcpkg)\
[Установка vcpkg](install-vcpkg.md)\
[Управление библиотеками с помощью vcpkg](manage-libraries-with-vcpkg.md)\
[Справочник по командной строке vcpkg](vcpkg-command-line-reference.md)\
[Краткое руководство](https://github.com/microsoft/vcpkg/blob/master/docs/README.md)\
[Часто задаваемые вопросы по Аналитике компьютеров](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
