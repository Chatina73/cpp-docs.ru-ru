---
title: Справочник по командной строке vcpkg
description: Узнайте, как использовать параметры командной строки для vcpkg в Windows, macOS и Linux.
ms.date: 12/17/2020
ms.topic: reference
ms.technology: cpp-ide
ms.openlocfilehash: 22210f3ee80050890d0b71fcc26461372e77e11e
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099629"
---
# <a name="vcpkg-command-line-reference"></a>Справочник по командной строке vcpkg

Краткий справочник по командам, доступным в vcpkg.

## <a name="commands"></a>Команды

| Команда | Описание |
|--|--|
| **`vcpkg search [pat]`** | Поиск пакетов, доступных для установки |
| **`vcpkg install <pkg>...`** | Установка пакета |
| **`vcpkg remove <pkg>...`** | Удаление пакета |
| **`vcpkg remove --outdated`** | Удаление всех устаревших пакетов |
| **`vcpkg list`** | Вывод списка установленных пакетов |
| **`vcpkg update`** | Отображение списка пакетов для обновления |
| **`vcpkg upgrade`** | Перестроение всех устаревших пакетов |
| **`vcpkg hash <file> [alg]`** | Хэширование файла с помощью конкретного алгоритма (по умолчанию SHA512) |
| **`vcpkg integrate install`** | Предоставление всем пользователям доступа к установленным пакетам. При первом использовании требуются права администратора. |
| **`vcpkg integrate remove`** | Отмена интеграции для всех пользователей |
| **`vcpkg integrate project`** | Создание пакета NuGet со ссылками для использования с конкретным проектом VS |
| **`vcpkg export <pkg>... [opt]...`** | Экспорт пакета |
| **`vcpkg edit <pkg>`** | Открытие порта для редактирования (использует %EDITOR%, по умолчанию "code") |
| **`vcpkg create <pkg> <url> [archivename]`** | Создание пакета |
| **`vcpkg cache`** | Вывод списка кэшированных скомпилированных пакетов |
| **`vcpkg version`** | Отображение сведений о версии |
| **`vcpkg contact --survey`** | Отображение контактных данных для отправки отзывов |

## <a name="options"></a>Параметры

| Параметр | Описание |
|--|--|
| **`--triplet <t>`** | Указание триады значений для целевой архитектуры (по умолчанию: `%VCPKG_DEFAULT_TRIPLET%`, см. также **`vcpkg help triplet`** ). |
| **`--vcpkg-root <path>`** | Указание корневого каталога vcpkg (по умолчанию: `%VCPKG_ROOT%`) |

## <a name="see-also"></a>См. также раздел

[vcpkg: диспетчер пакетов C++ для Windows, Linux и macOS](./vcpkg.md)\
[vcpkg на GitHub](https://github.com/Microsoft/vcpkg)\
[Установка vcpkg](install-vcpkg.md)\
[Интеграция vcpkg](integrate-vcpkg.md)\
[Управление библиотеками с помощью vcpkg](manage-libraries-with-vcpkg.md)\
[Краткое руководство](https://github.com/microsoft/vcpkg/blob/master/docs/README.md)\
[Часто задаваемые вопросы по Аналитике компьютеров](https://github.com/microsoft/vcpkg/blob/master/docs/about/faq.md)
