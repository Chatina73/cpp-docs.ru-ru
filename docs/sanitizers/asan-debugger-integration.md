---
title: Библиотека расширенных функциональных возможностей Visual Studio Аддресссанитизер (Вкасан)
description: Техническое описание вкасан. lib.
ms.date: 03/02/2021
f1_keywords:
- vcasan
helpviewer_keywords:
- vcasan.lib
- vcasan
- vcasand.lib
- libvcasan.lib
- libvcasand.lib
ms.openlocfilehash: 8728fead94b5d2b4827b34f1a5461c08c821f2e7
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471187"
---
# <a name="visual-studio-addresssanitizer-extended-functionality-library-vcasan"></a>Библиотека расширенных функциональных возможностей Visual Studio Аддресссанитизер (Вкасан)

*`VCAsan*.lib`* Библиотеки реализуют расширенные функции интегрированной среды разработки отладчика в Visual Studio. Эти функции позволяют интегрированной среде разработки отображать ошибки Аддресссанитизер в сеансах отладки в режиме реального времени или вне сети путем сохранения файла аварийного дампа с метаданными. Библиотека связывается, когда Аддресссанитизер включается компилятором КОМПИЛЯТОРОМ MSVC.

## <a name="vcasan-library-inventory"></a>Инвентаризация библиотеки Вкасан

| Параметр среды выполнения | Библиотека ссылок Вкасан  |
|---------------|----------------------|
| **`/MT`**           | *`libvcasan.lib`*        |
| **`/MD`**           | *`vcasan.lib`*           |
| **`/MTd`**          | *`libvcasand.lib`*       |
| **`/MDd`**          | *`vcasand.lib`*          |

## <a name="vcasan-library-features"></a>Функции библиотеки Вкасан

### <a name="rich-addresssanitizer-error-report-window-in-visual-studio-ide"></a>Расширенное окно отчета об ошибках Аддресссанитизер в интегрированной среде разработки Visual Studio

Библиотека Вкасан регистрирует обратный вызов в среде выполнения Аддресссанитизер с помощью функции Interface [`__asan_set_error_report_callback`](https://github.com/llvm/llvm-project/blob/1ba5ea67a30170053964a28f2f47aea4bb7f5ff1/compiler-rt/include/sanitizer/asan_interface.h#L256) . Если создается отчет Аддресссанитизер, этот обратный вызов используется для создания исключения, перехваченного Visual Studio. Visual Studio использует данные исключения для создания сообщения, которое отображается для пользователя в интегрированной среде разработки.

> [!NOTE]
> Библиотека Вкасан регистрирует функцию обратного вызова в среде выполнения Аддресссанитизер. Если ваш код вызывает эту функцию регистрации во второй раз, он перезаписывает регистрацию обратного вызова библиотеки Вкасан. Это приводит к утрате всех средств интеграции интегрированной среды разработки Visual Studio. Вернитесь к интерфейсу пользователя IDE по умолчанию. Также возможно, что вызов пользователя, который регистрирует свой обратный вызов, будет потерян. Если возникает какая-либо проблема, [зарегистрируйте ошибку](https://aka.ms/feedback/report?space=62).

### <a name="save-addresssanitizer-errors-in-a-new-type-of-crash-dump-file"></a>Сохранять ошибки Аддресссанитизер в новом типе файла аварийного дампа

При связывании библиотеки Вкасан с исполняемым файлом пользователи могут включить ее для создания аварийного дампа во время выполнения. Затем среда выполнения Аддресссанитизер создает файл дампа при возникновении ошибки диагностики. Чтобы включить эту функцию, пользователь задает `ASAN_SAVE_DUMPS` переменную среды с помощью следующей команды:

`set ASAN_SAVE_DUMPS=MyFileName.dmp`

Файл должен иметь суффикс. dmp для соблюдения соглашений Visual Studio IDE.

Вот что происходит при указании файла дампа для `ASAN_SAVE_DUMPS` : Если ошибка перехвачена средой выполнения аддресссанитизер, она сохраняет файл аварийного дампа, содержащий метаданные, связанные с ошибкой. Отладчик в Visual Studio версии 16,9 и более поздних версий может анализировать метаданные, сохраненные в файле дампа. Можно задать `ASAN_SAVE_DUMPS` для каждого теста, сохранить эти двоичные артефакты, а затем просмотреть их в интегрированной среде разработки с надлежащей индексацией исходного кода.

## <a name="see-also"></a>См. также раздел

[Обзор Аддресссанитизер](./asan.md)\
[Известные проблемы Аддресссанитизер](./asan-known-issues.md)\
[Справочник по сборке и языку Аддресссанитизер](./asan-building.md)\
[Справочник по среде выполнения Аддресссанитизер](./asan-runtime.md)\
[Аддресссанитизер теневых байт](./asan-shadow-bytes.md)\
[Аддресссанитизер облачное или распределенное тестирование](./asan-offline-crash-dumps.md)\
[Примеры ошибок Аддресссанитизер](./asan-error-examples.md)
