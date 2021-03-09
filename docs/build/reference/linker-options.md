---
title: Параметры компоновщика КОМПИЛЯТОРОМ MSVC
description: Список параметров, поддерживаемых компоновщиком ссылок Microsoft.
ms.date: 09/01/2020
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: e426c085acdd0d7bcfeb00b17dcf733a9b856993
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465318"
---
# <a name="linker-options"></a>Параметры компоновщика

LINK.exe связывает объектные файлы в формате COFF и библиотеки для создания исполняемого файла (EXE) или библиотеки динамической компоновки (DLL).

В таблице ниже перечислены параметры для программы LINK.exe. Подробнее о LINK см. в следующих разделах.

- [Параметры ссылки, управляемой компилятором](compiler-controlled-link-options.md)

- [Входные файлы ссылок](link-input-files.md)

- [Выходные данные ссылки](link-output.md)

- [Зарезервированные слова](reserved-words.md)

В командной строке параметры компоновщика не учитывают регистр; Например, `/base` и это `/BASE` то же самое. Дополнительные сведения о том, как указать каждый параметр в командной строке или в Visual Studio, см. в документации для этого параметра.

Директиву pragma [comment](../../preprocessor/comment-c-cpp.md) можно использовать для задания некоторых параметров компоновщика.

## <a name="linker-options-listed-alphabetically"></a>Параметры компоновщика перечислены в алфавитном порядке

|Параметр|Цель|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Указывает файл ответа.|
|[/ALIGN](align-section-alignment.md)|Задает выравнивание каждой секции.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Указывает, что библиотека DLL не может быть привязана.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Задает поведение нахождения файлов манифеста.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Определяет, должно ли приложение выполняться в среде процесса контейнера приложений.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Добавляет атрибут <xref:System.Diagnostics.DebuggableAttribute> в управляемый образ.|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Создает ссылку на управляемый ресурс.|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Указывает на то, что в сборку должен быть импортирован модуль MSIL.|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Внедряет файл управляемых ресурсов в сборку.|
|[/BASE](base-base-address.md)|Задает базовый адрес для программы.|
|[/цеткомпат](cetcompat.md)|Помечает двоичный файл как совместимый с теневым стеком ЦЕНТРАЛЬНОЕВРОПЕЙСКОЕ время.|
|[/CGTHREADS](cgthreads-compiler-threads.md)|Задает число потоков cl.exe, используемых для оптимизации и создания кода, если задано создание кода во время компоновки.|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Задает тип (IJW, pure или safe) CLR-образа.|
|[ПАРАМЕТР/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Сохраняет последний код ошибки функций, вызываемых с помощью механизма P/Invoke.|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Указывает атрибут потока для применения к точке входа CLR-программы.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Указывает, должен ли компоновщик применять атрибут SuppressUnmanagedCodeSecurity к создаваемым компоновщиком заглушкам PInvoke, осуществляющим вызовы из управляемого кода в библиотеки DLL неуправляемого кода.|
|[/DEBUG](debug-generate-debug-info.md)|Создает отладочную информацию.|
|[/дебугтипе](debugtype-debug-info-options.md)|Указывает, какие данные необходимо включить в отладочную информацию.|
|[/DEF](def-specify-module-definition-file.md)|Передает компоновщику файл определения модуля (DEF).|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Проводит поиск по указанной библиотеке при разрешении внешних ссылок.|
|[/DELAY](delay-delay-load-import-settings.md)|Управляет отложенной загрузкой библиотек DLL.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Включает отложенную загрузку указанной библиотеки DLL.|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Частично подписывает сборку.|
|[/депендентлоадфлаг](dependentloadflag.md)|Устанавливает флаги по умолчанию для загрузок зависимых библиотек DLL.|
|[Стандартных](dll-build-a-dll.md)|Выполняет сборку библиотеки DLL.|
|[/DRIVER](driver-windows-nt-kernel-mode-driver.md)|Создает драйвер режима ядра.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Указывает, следует ли создавать исполняемый образ, который переосновывается во время загрузки, с помощью функции использования макета адресного пространства (ASLR).|
|[/ENTRY](entry-entry-point-symbol.md)|Задает начальный адрес.|
|[/ERRORREPORT](errorreport-report-internal-linker-errors.md)| Не рекомендуется. Отчеты об ошибках контролируются параметрами [отчеты об ошибках Windows (WER)](/windows/win32/wer/windows-error-reporting) . |
|[/EXPORT](export-exports-a-function.md)|Экспортирует функцию.|
|[/FILEALIGN](filealign.md)|Совмещает разделы в выходном файле по кратным заданному значению.|
|[/FIXED](fixed-fixed-base-address.md)|Создает программу, которая может загружаться только по предпочтительному базовому адресу.|
|[/FORCE](force-force-file-output.md)|Принудительное завершение компоновки даже в случае наличия неразрешенных или многократно определенных символов.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Создает образ, для которого можно выполнять горячее обновление.|
|[/GENPROFILE, /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Оба эти параметра указывают создание *`.pgd`* файла компоновщиком для поддержки профильной оптимизации (PGO). /GENPROFILE и /FASTGENPROFILE используют разные параметры по умолчанию.|
|[/GUARD](guard-enable-guard-checks.md)|Включает защиту потока управления.|
|[/HEAP](heap-set-heap-size.md)|Задает размер кучи в байтах.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Определяет поддержку 64-разрядной функции Address Space Layout Randomization (ASLR) с высоким уровнем энтропии.|
|[/IDLOUT](idlout-name-midl-output-files.md)|Указывает имя *`.idl`* файла и другие выходные файлы MIDL.|
|[/IGNORE](ignore-ignore-specific-warnings.md)|Отменяет вывод указанных предупреждений компоновщика.|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Предотвращает обработку сведений об атрибутах в *`.idl`* файле.|
|[/IMPLIB](implib-name-import-library.md)|Переопределяет имя библиотеки импорта по умолчанию.|
|[/INCLUDE](include-force-symbol-references.md)|Принудительное использование ссылок на символы.|
|[/INCREMENTAL](incremental-link-incrementally.md)|Управляет инкрементной компоновкой.|
|[/инферасанлибс](inferasanlibs.md)|Использует выводимые библиотеки очистки.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Указывает на то, что модуль требует проверки подписи во время загрузки.|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Задает контейнер ключей для подписи сборки.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Задает ключ или пару ключей для подписи сборки.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Указывает компилятору на то, что приложение поддерживает адреса, превышающие два гигабайта.|
|[/LIBPATH](libpath-additional-libpath.md)|Указывает путь для поиска перед путем среды библиотеки.|
|[/линкрепро](linkrepro.md)|Указывает путь для создания артефактов воспроизведения ссылок в.|
|[/линкрепротаржет](linkreprotarget.md)|Создает ссылку для воспроизведения только при создании указанного целевого объекта. <sup>16,1</sup>|
|[Указан](ltcg-link-time-code-generation.md)|Задает создание кода во время компоновки.|
|[/MACHINE](machine-specify-target-platform.md)|Указывает целевую платформу.|
|[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md)|Создает параллельный файл манифеста и при необходимости включает его в двоичный файл.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Указывает \<dependentAssembly> раздел в файле манифеста.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Изменяет имя файла манифеста по умолчанию.|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Задает входной файл манифеста для обработки и внедрения компоновщиком в двоичный файл. Этот параметр можно использовать несколько раз, чтобы указать несколько входных файлов манифеста.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Указывает, следует ли внедрять в манифест программы сведения о контроле учетных записей.|
|[/MAP](map-generate-mapfile.md)|Создает файл сопоставления.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Включает указанные сведения в файл сопоставления.|
|[/MERGE](merge-combine-sections.md)|Объединяет разделы.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Задает параметры командной строки MIDL.|
|[/натвис](natvis-add-natvis-to-pdb.md)|Добавляет визуализаторы отладчика из Natvis-файла в базу данных программы (PDB).|
|[/NOASSEMBLY](noassembly-create-a-msil-module.md)|Подавляет создание сборки .NET Framework.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Пропускает все (или только указанные) библиотеки по умолчанию при разрешении внешних ссылок.|
|[/NOENTRY](noentry-no-entry-point.md)|Создает библиотеку DLL, содержащую только ресурсы.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Отключает загрузочный баннер.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Помечает исполняемый файл как файл, проверенный на совместимость с компонентом предотвращения выполнения данных Windows.|
|[Букв](opt-optimizations.md)|Управляет оптимизацией LINK.|
|[/ORDER](order-put-functions-in-order.md)|Помещает секции COMDAT в образ в предопределенном порядке.|
|[/OUT](out-output-file-name.md)|Задает имя выходного файла.|
|[/PDB](pdb-use-program-database.md)|Создает PDB-файл.|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Использует альтернативное местоположение для сохранения файла PDB.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Создает PDB-файл без закрытых символов.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Указывает *`.pgd`* файл для профильной оптимизации.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Устарело** Создает поточно-ориентированную сборку с инструментированием профильной оптимизации.|
|[Загружать](profile-performance-tools-profiler.md)|Создает выходной файл, который может быть использован для профилировщика производительности инструментов.|
|[/RELEASE](release-set-the-checksum.md)|Задает контрольную сумму в *`.exe`* заголовке.|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Указывает на то, что образ будет содержать таблицу безопасных обработчиков исключений.|
|[/SECTION](section-specify-section-attributes.md)|Переопределяет атрибуты секции.|
|[ПАРАМЕТР/SOURCELINK](sourcelink.md)|Указывает файл SourceLink для добавления в PDB.|
|[/STACK](stack-stack-allocations.md)|Задает размер стека (в байтах).|
|[/STUB ПРИЛАГАЕТ](stub-ms-dos-stub-file-name.md)|Присоединяет программу-заглушку MS-DOS к программе Win32.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Указывает операционной системе, как выполнить *`.exe`* файл.|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Указывает операционной системе скопировать выходные данные компоновщика в файл подкачки перед запуском.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Указывает идентификатор ресурса библиотеки типов, создаваемой компоновщиком.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Указывает имя *`.tlb`* файла и другие выходные файлы MIDL.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Создает приложение, специально рассчитанное на запуск под управлением сервера терминалов.|
|[/USEPROFILE](useprofile.md)|Для создания оптимизированного образа использует данные для обучения по оптимизации профиля.|
|[/VERBOSE](verbose-print-progress-messages.md)|Печатает сообщения хода выполнения компоновщика.|
|[/VERSION](version-version-information.md)|Присваивает номер версии.|
|[/вхолеарчиве](wholearchive-include-all-library-object-files.md)|Включает каждый объектный файл из указанных статических библиотек.|
|[/WINMD](winmd-generate-windows-metadata.md)|Включает создание файлов метаданных среды выполнения Windows.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Задает имя файла для выходного файла метаданных среды выполнения Windows (winmd), создаваемого параметром компоновщика [/WINMD](winmd-generate-windows-metadata.md) .|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Задает ключ или пару ключей для подписи файла метаданных среды выполнения Windows.|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Указывает контейнер ключей для подписания файла метаданных Windows.|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Частично подписывает файл метаданных среды выполнения Windows (.winmd), установив открытый ключ в файле winmd.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Обрабатывает предупреждения компоновщика как ошибки.|

<sup>16,1</sup> . Этот параметр доступен начиная с Visual Studio 2019 версии 16,1.

## <a name="see-also"></a>См. также раздел

[Справочные сведения о построении C/C++](c-cpp-building-reference.md)\
[Справочник по компоновщику MSVC](linking.md)
