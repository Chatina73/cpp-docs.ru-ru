---
title: Управление библиотеками с помощью vcpkg
description: Узнайте, как управлять библиотеками с помощью vcpkg в Windows, macOS и Linux.
ms.date: 12/11/2020
ms.technology: cpp-ide
ms.openlocfilehash: 5e5fc0e9cb1616155bfe8268f2c55afcee4c4a94
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099252"
---
# <a name="manage-libraries-with-vcpkg"></a>Управление библиотеками с помощью vcpkg

После [установки vcpkg](install-vcpkg.md) его можно использовать для получения и сборки библиотек на локальном компьютере.

## <a name="search-the-list-of-available-libraries"></a>Поиск в списке доступных библиотек

### <a name="windows"></a>[Windows](#tab/windows)

Чтобы узнать, какие пакеты доступны, в командной строке введите **`vcpkg search`** .

Эта команда перечисляет файлы управления во вложенных папках *`vcpkg/ports`* . Вы увидите примерно такой список:

```cmd
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Вы можете выполнить фильтрацию на основе шаблона, например **`vcpkg search ta`** :

```cmd
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-local-machine"></a>Установка библиотеки на локальном компьютере

Получив название библиотеки с помощью **`vcpkg search`** , воспользуйтесь **`vcpkg install`** , чтобы загрузить библиотеку и скомпилировать ее. vcpkg использует файл портов (portfile) библиотеки в каталоге *ports*. Если триада не указана, vcpkg установит и скомпилирует триаду по умолчанию для целевой платформы: x86-windows, x64-linux.cmake или x64-osx.cmake.

Для библиотек Linux vcpkg требует наличия установленного gcc на локальном компьютере. На macOS vcpkg использует Clang.

Если в portfile указаны зависимости, vcpkg скачает и установит и их. После скачивания vcpkg выполнит сборку библиотеки с помощью той же системы сборки, которую использует библиотека. Предпочтительными являются проекты CMake и MSBuild (в Windows), но поддерживается также MAKE и любые другие системы сборки. Если диспетчеру vcpkg не удается найти указанную систему сборки на локальном компьютере, он скачивает и устанавливает ее.

```cmd
> vcpkg install boost:x86-windows

The following packages will be built and installed:
    boost:x86-windows
  * bzip2:x86-windows
  * zlib:x86-windows
Additional packages (*) will be installed to complete this operation.
```

Для проектов CMake используйте `CMAKE_TOOLCHAIN_FILE`, чтобы сделать библиотеки доступными через `find_package()`. Например, в Linux или macOS:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg/scripts/buildsystems/vcpkg.cmake
```

Windows:

```cmd
cmake .. -DCMAKE_TOOLCHAIN_FILE=vcpkg\scripts\buildsystems\vcpkg.cmake
```

Некоторые библиотеки содержат устанавливаемые параметры. Например, при поиске библиотеки curl вы также увидите список поддерживаемых параметров в квадратных скобках:

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

В этом случае квадратные скобки **`[`** и **`]`** являются литералами, а не метасимволами.

Можно указать конкретный параметр для установки в командной строке. Например, чтобы установить библиотеки для curl с использованием серверной части SSL по умолчанию для Windows, используйте команду **`vcpkg install curl[ssl]:x86-windows`** . Эта команда устанавливает необходимые компоненты, включая основную библиотеку (если это необходимо):

```cmd
> vcpkg list
curl:x86-windows            7.68.0-3   A library for transferring data with URLs
curl[non-http]:x86-windows             Enables protocols beyond HTTP/HTTPS/HTTP2
curl[ssl]:x86-windows                  Default SSL backend
curl[sspi]:x86-windows                 SSPI support
curl[winssl]:x86-windows               SSL support (Secure Channel / "WinSSL")
zlib:x86-windows            1.2.11-6   A compression library
```

### <a name="macos"></a>[macOS](#tab/macos)

Чтобы узнать, какие пакеты доступны, в окне терминала перейдите в корневой каталог vcpkg и введите команду **`./vcpkg search`** .

Эта команда перечисляет файлы управления во вложенных папках *`vcpkg/ports`* . Вы увидите примерно такой список:

```Terminal
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Вы можете выполнить фильтрацию на основе шаблона, например **`vcpkg search ta`** :

```Terminal
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-computer"></a>Установка библиотеки на вашем компьютере

Получив название библиотеки с помощью **`vcpkg search`** , воспользуйтесь **`vcpkg install`** , чтобы загрузить библиотеку и скомпилировать ее. vcpkg использует файл портов (portfile) библиотеки в каталоге *ports*. Если триада не указана, vcpkg установит и скомпилирует триаду по умолчанию для целевой платформы: x86-windows, x64-linux.cmake или x64-osx.cmake.

Для библиотек Linux vcpkg требует наличия установленного gcc на локальном компьютере. На macOS vcpkg использует Clang.

Если в portfile указаны зависимости, vcpkg скачает и установит и их. После скачивания vcpkg выполнит сборку библиотеки с помощью той же системы сборки, которую использует библиотека. Предпочтительными являются проекты CMake и MSBuild (в Windows), но поддерживается также MAKE и любые другие системы сборки. Если диспетчеру vcpkg не удается найти указанную систему сборки на локальном компьютере, он скачивает и устанавливает ее.

```Terminal
$ ./vcpkg install boost

The following packages will be built and installed:
    boost:x86-macos
  * bzip2:x86-macos
  * zlib:x86-macos
Additional packages (*) will be installed to complete this operation.
```

Для проектов CMake используйте `CMAKE_TOOLCHAIN_FILE`, чтобы сделать библиотеки доступными через `find_package()`. Пример:

```Terminal
cmake .. -DCMAKE_TOOLCHAIN_FILE=./vcpkg/scripts/buildsystems/vcpkg.cmake
```

Некоторые библиотеки содержат устанавливаемые параметры. Например, при поиске библиотеки curl вы также увидите список поддерживаемых параметров в квадратных скобках:

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

В этом случае квадратные скобки **`[`** и **`]`** являются литералами, а не метасимволами.

Можно указать конкретный параметр для установки в командной строке. Например, чтобы установить библиотеки для curl с использованием серверной части SSL по умолчанию, используйте команду **`./vcpkg install curl[ssl]`** . Эта команда устанавливает необходимые компоненты, включая основную библиотеку (если это необходимо).

### <a name="linux"></a>[Linux](#tab/linux)

Чтобы узнать, какие пакеты доступны, в окне оболочки перейдите в корневой каталог vcpkg и введите команду **`./vcpkg search`** .

Эта команда перечисляет файлы управления во вложенных папках *`vcpkg/ports`* . Вы увидите примерно такой список:

```shell
ace       6.4.3   The ADAPTIVE Communication Environment
anax      2.1.0-1 An open source C++ entity system. \<https://github...
antlr4    4.6-1   ANother Tool for Language Recognition
apr       1.5.2   The Apache Portable Runtime (APR) is a C library ...
asio      1.10.8  Asio is a cross-platform C++ library for network ...
assimp    3.3.1   The Open Asset import library
atk       2.24.0  GNOME Accessibility Toolkit
...
```

Вы можете выполнить фильтрацию на основе шаблона, например **`./vcpkg search ta`** :

```shell
botan       2.0.1      A cryptography library written in C++11
portaudio   19.0.6.00  PortAudio Portable Cross-platform Audio I/O API P...
taglib      1.11.1-2   TagLib Audio Meta-Data Library
```

### <a name="install-a-library-on-your-linux-machine"></a>Установка библиотеки на компьютере Linux

Получив название библиотеки с помощью **`./vcpkg search`** , воспользуйтесь **`/vcpkg install`** , чтобы загрузить библиотеку и скомпилировать ее. vcpkg использует файл портов библиотеки в каталоге *`ports`* . Если триада не указана, vcpkg установит и скомпилирует триаду по умолчанию для целевой платформы, такой как x64-linux.cmake.

Для библиотек Linux vcpkg требует наличия установленного gcc на локальном компьютере.

Если в portfile указаны зависимости, vcpkg скачает и установит и их. После скачивания vcpkg выполнит сборку библиотеки с помощью той же системы сборки, которую использует библиотека. Предпочтительными являются проекты CMake, но поддерживается также MAKE и любые другие системы сборки. Если диспетчеру vcpkg не удается найти указанную систему сборки на локальном компьютере, он скачивает и устанавливает ее.

```shell
$ ./vcpkg install boost:x64-linux

The following packages will be built and installed:
    boost:x64-linux
  * bzip2:x64-linux
  * zlib:x64-linux
Additional packages (*) will be installed to complete this operation.
```

Для проектов CMake используйте `CMAKE_TOOLCHAIN_FILE`, чтобы сделать библиотеки доступными через `find_package()`. Пример:

```shell
cmake .. -DCMAKE_TOOLCHAIN_FILE=./vcpkg/scripts/buildsystems/vcpkg.cmake
```

Некоторые библиотеки содержат устанавливаемые параметры. Например, при поиске библиотеки curl вы также увидите список поддерживаемых параметров в квадратных скобках:

```cmd
> vcpkg search curl
curl                 7.68.0-3         A library for transferring data with URLs
curl[tool]                            Builds curl executable
curl[non-http]                        Enables protocols beyond HTTP/HTTPS/HTTP2
curl[http2]                           HTTP2 support
curl[ssl]                             Default SSL backend
curl[ssh]                             SSH support via libssh2
curl[openssl]                         SSL support (OpenSSL)
curl[winssl]                          SSL support (Secure Channel / "WinSSL")
curl[mbedtls]                         SSL support (mbedTLS)
curl[sectransp]                       SSL support (sectransp)
curl[c-ares]                          c-ares support
curl[sspi]                            SSPI support
curl[brotli]                          brotli support (brotli)
curlpp               2018-06-15-3     C++ wrapper around libcURL
```

В этом случае квадратные скобки **`[`** и **`]`** являются литералами, а не метасимволами.

Можно указать конкретный параметр для установки в командной строке. Например, чтобы установить библиотеки для curl с использованием серверной части SSL по умолчанию, используйте команду **`./vcpkg install curl[ssl]`** . Эта команда устанавливает необходимые компоненты, включая основную библиотеку (если это необходимо).

---

## <a name="list-the-libraries-already-installed"></a>Вывод списка уже установленных библиотек

После установки некоторых библиотек вы можете воспользоваться командой **`vcpkg list`** в Windows, чтобы увидеть, что у вас есть. В Linux и macOS имеются аналогичные команды.

```cmd
> vcpkg list

boost:x86-windows       1.64-3   Peer-reviewed portable C++ source libraries
bzip2:x86-windows       1.0.6-1  High-quality data compressor.
cpprestsdk:x86-windows  2.9.0-2  C++11 JSON, REST, and OAuth library The C++ REST ...
openssl:x86-windows     1.0.2k-2 OpenSSL is an open source project that provides a...
websocketpp:x86-windows 0.7.0    Library that implements RFC6455 The WebSocket Pro...
zlib:x86-windows        1.2.11   A compression library
```

## <a name="target-linux-from-windows-via-wsl"></a>Создание файлов для Linux из Windows посредством WSL

Можно создавать двоичные файлы для Linux на компьютере с Windows с помощью подсистемы Windows для Linux (WSL). Следуйте инструкциям, по [настройке WSL в Windows 10](/windows/wsl/install-win10). Затем настройте подсистему с помощью [расширения Visual Studio для Linux](https://devblogs.microsoft.com/cppblog/targeting-windows-subsystem-for-linux-from-visual-studio/). Все созданные библиотеки для Windows и Linux можно разместить в одной папке. Они доступны как в Windows, так и в WSL.

## <a name="export-compiled-binaries-and-headers"></a><a name="export_binaries_per_project"></a> Экспорт скомпилированных двоичных файлов и файлов заголовков

Требовать от каждого члена команды скачивать и компилировать библиотеки может быть неэффективно. Эту задачу способен выполнить один человек, который может использовать команду **`vcpkg export`** , чтобы собрать двоичные файлы и заголовки или пакет NuGet в один ZIP-архив. Затем он может легко предоставить его другим членам команды.

## <a name="updateupgrade-installed-libraries"></a>Обновление установленных библиотек

Общедоступный каталог регулярно пополняется новейшими версиями библиотек. Используйте **`vcpkg update`** , чтобы определить, какие из ваших локальных библиотек устарели. Когда вы будете готовы обновить свою коллекцию портов до последней версии из общедоступного каталога, выполните команду **`vcpkg upgrade`** . Она автоматически скачивает и перестраивает отдельные или все установленные библиотеки, которые устарели.

По умолчанию команда **`vcpkg upgrade`** лишь выводит список устаревших библиотек, не обновляя их. Для фактического обновления библиотек используйте параметр **`--no-dry-run`** .

```cmd
> vcpkg upgrade --no-dry-run
```

### <a name="upgrade-options"></a>Параметры обновления

- **`--no-dry-run`** : выполнение обновления; если параметр не указан, эта команда просто выводит список устаревших пакетов.
- **`--keep-going`** : продолжение установки пакетов даже при возникновении сбоя для одного из них.
- **`--triplet <t>`** : задание триады по умолчанию для неквалифицированных пакетов.
- **`--vcpkg-root <path>`** : указание каталога vcpkg для использования вместо текущего каталога или каталога средства.

### <a name="upgrade-example"></a>Пример обновления

Следующий пример показывает, как обновить в Windows только указанные библиотеки. В Linux и macOS имеются аналогичные команды. vcpgk автоматически получает зависимости по мере необходимости.

```cmd
c:\users\username\vcpkg> vcpkg upgrade tiny-dnn:x86-windows zlib
The following packages are up-to-date:
   tiny-dnn:x86-windows

The following packages will be rebuilt:
    * libpng[core]:x86-windows
    * tiff[core]:x86-windows
      zlib[core]:x86-windows
Additional packages (*) will be modified to complete this operation.
If you are sure you want to rebuild the above packages, run this command with the --no-dry-run option.
```

## <a name="contribute-new-libraries"></a>Публикация новых библиотек

Вы можете включать в свою коллекцию частных портов какие угодно библиотеки. Чтобы предложить новую библиотеку для открытого каталога, откройте обращение на [странице проблем с vcpkg на сайте GitHub ](https://github.com/Microsoft/vcpkg/issues).

## <a name="remove-a-library"></a>Удаление библиотеки

Введите **`vcpkg remove`** , чтобы удалить установленную библиотеку. Если от нее зависят какие-то другие библиотеки, вам предлагается повторно выполнить команду с параметром **`--recurse`** , что приводит к удалению всех подчиненных библиотек.

## <a name="see-also"></a>См. также раздел

[vcpkg: диспетчер пакетов C++ для Windows, Linux и macOS](./vcpkg.md)\
[vcpkg на GitHub](https://github.com/Microsoft/vcpkg)\
[Установка vcpkg](install-vcpkg.md)\
[Интеграция vcpkg](integrate-vcpkg.md)\
[Справочник по командной строке vcpkg](vcpkg-command-line-reference.md)\
[Краткое руководство](https://github.com/microsoft/vcpkg/blob/master/docs/README.md)\
[Вопросы и ответы](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)\
[Пример установки и использования пакетов: SQLite](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)
