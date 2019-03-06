---
title: Построения выпуска
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], release builds
- release builds
- debug builds, converting to release build
ms.assetid: fa9a78fa-f4b5-4722-baf4-aec655c4ff0f
ms.openlocfilehash: 346beace1979871cfd9bf4ee0d487e7f85a26eaa
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57426099"
---
# <a name="release-builds"></a>Построения выпуска

Сборки выпуска использует оптимизации. При использовании оптимизации для создание сборки выпуска компилятор не выдает символьную отладочную информацию. Вызывает отсутствие символьную отладочную информацию, а также тот факт, что код не создается для ТРАССИРОВКИ и ASSERT, означает, что размер исполняемого файла уменьшается и будут выполняться быстрее.

В этом разделе представлены сведения о когда и почему следует изменить из отладочной сборки для сборки выпуска. Он также рассматриваются некоторые проблемы, которые могут возникнуть при изменении отладочной сборки выпуска:

- [Создание сборки выпуска](../../build/reference/how-to-create-a-release-build.md)

- [Распространенные проблемы, возникающие при создании сборок выпуска](../../build/reference/common-problems-when-creating-a-release-build.md)

- [Устранение проблем сборки выпуска](../../build/reference/fixing-release-build-problems.md)

   - [Изучив операторы ASSERT](../../build/reference/using-verify-instead-of-assert.md)

   - [Использование отладочного построения для проверки затирания памяти](../../build/reference/using-the-debug-build-to-check-for-memory-overwrite.md)

   - [Отладка построения выпуска](../../build/reference/how-to-debug-a-release-build.md)

   - [Проверка перезаписи памяти](../../build/reference/checking-for-memory-overwrites.md)

## <a name="see-also"></a>См. также

[Сборка проектов C++ в Visual Studio](../../ide/building-cpp-projects-in-visual-studio.md)<br/>
[Справочные сведения о сборке C/C++](../../build/reference/c-cpp-building-reference.md)
