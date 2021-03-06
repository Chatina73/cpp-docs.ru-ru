---
title: '&lt;filesystem&gt;'
description: Описывает классы, функции и типы в filesystem заголовке стандартной библиотеки C++.
ms.date: 01/15/2021
f1_keywords:
- <filesystem>
- filesystem/std::filesystem
- std::filesystem
- std::experimental::filesystem
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: 8dc81692c7c7dc467f3ab8e2ceb8cac19e004ab8
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667474"
---
# `filesystem`

Включите заголовок `<filesystem>` для доступа к классам и функциям, которые управляют и извлекают сведения о путях, файлах и каталогах.

## <a name="syntax"></a>Синтаксис

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> В выпуске Visual Studio 2017 \<filesystem> заголовок еще не является стандартом C++. C++ в Visual Studio 2017 RTW реализует окончательный черновой стандарт, который находится в [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100). Visual Studio 2017 версии 15,7 и более поздних версий поддерживает новый \<filesystem> стандарт c++ 17.
> Это совершенно новая реализация, несовместимая с предыдущей `std::experimental` версией. Она была необходима для поддержки символьную ссылку, исправления ошибок и изменений в стандартном поведении. В настоящее время, включая, \<filesystem> предоставляет новый `std::filesystem` и предыдущий `std::experimental::filesystem` . Включает \<experimental/filesystem> в себя только старую experimental реализацию. experimentalРеализация будет удалена в следующем выпуске библиотек ABI-Break.

Этот заголовок поддерживает файловые системы для одного из двух основных классов операционных систем размещения: Microsoft Windows и POSIX.

Хотя большинство функций являются общими для обеих операционных систем, в этом документе указываются некоторые отличия. Пример:

- Windows поддерживает несколько корневых имен, например `c:` или `\\network_name` . Файловая система состоит из леса деревьев, каждый из которых имеет собственный корневой каталог, такой как `c:\` или `\\network_name\` , и каждый с собственным текущим каталогом для заполнения относительного пути (не является абсолютным путем).

- POSIX поддерживает одно дерево, не имеющее корневого имени, единственного корневого каталога `/` и одного текущего каталога.

Другое важное отличие состоит в представлении путей:

- Windows использует последовательность, завершающуюся символом NULL **`wchar_t`** , в кодировке UTF-16 (один или несколько элементов для каждого char актер).

- POSIX использует последовательность, завершающуюся символом NULL **`char`** , в кодировке UTF-8 (один или несколько элементов для каждого char актер).

- Объект класса `path` хранит путь в собственной форме, но поддерживает простое преобразование между этой хранимой формой и несколькими внешними формами:

  - Последовательность, завершающаяся нулем **`char`** и закодированная в соответствии с приоритетом операционной системы.

  - Последовательность, завершающаяся нулем **`char`** и закодированная как UTF-8.

  - Последовательность, завершающаяся нулем **`wchar_t`** и закодированная в соответствии с приоритетом операционной системы.

  - Последовательность, завершающаяся нулем **`char16_t`** и закодированная как UTF-16.

  - Последовательность, завершающаяся нулем **`char32_t`** и закодированная как UTF-32.

  Взаимные преобразования между этими представлениями выполняются по мере необходимости с помощью одного или нескольких аспектов `codecvt`. Если определенный объект локали не указан, эти аспекты получаются из глобального языкового стандарта.

Еще одно различие заключается в степени детализации, с которой каждая операционная система позволяет указать разрешения доступа к файлу или каталогу.

- Windows записывает, является ли файл доступным только для чтения или доступен для записи, атрибутом, который не имеет смысла для каталогов.

- POSIX записывает, может ли файл быть прочитан, записан или выполнен (просматривается, если каталог). А также сведения о том, разрешена ли каждая операция для владельца, Группа владельца или для всех, и несколько других разрешений.

Общей характеристикой обеих систем является структура, применяемая к пути после корневого имени. Для пути `c:/abc/xyz/def.ext` :

- Имя корня — `c:` .

- Корневой каталог — `/` .

- Корневой путь — `c:/` .

- Относительный путь — `abc/xyz/def.ext` .

- Родительский путь — `c:/abc/xyz` .

- Имя файла — `def.ext`.

- Ресурс имеет значение `def` .

- Расширение — `.ext` .

Незначительное различие — это предпочтительный разделитель между последовательностью каталогов в пути. Обе операционные системы позволяют написать прямую косую черту `/` , но в некоторых контекстах Windows предпочитает обратную косую черту `\` . Реализация сохраняет свой предпочтительный разделитель в элементе данных `preferred_separator` в `path` .

Наконец, `path` объекты имеют важную возможность: их можно использовать везде, где требуется аргумент filename в классах, определенных в заголовке [\<fstream>](fstream.md) .

Дополнительные сведения и примеры кода см. в разделе [Навигация по файловой системе (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Члены

### <a name="classes"></a>Классы

|name|Описание|
|-|-|
|[`directory_entry` см](../standard-library/directory-entry-class.md)|Описывает объект, возвращаемый `directory_iterator` или, `recursive_directory_iterator` и содержит `path` .|
|[`directory_iterator` см](../standard-library/directory-iterator-class.md)|Описывает итератор ввода, выполняющий последовательный перебор имен файлов в каталоге файловой системы.|
|[`filesystem_error` см](../standard-library/filesystem-error-class.md)|Базовый класс для исключений, создаваемых для отчета о переполнении системы низкого уровня.|
|[`path` см](../standard-library/path-class.md)|Определяет класс, который хранит объект типа шаблона `String` , пригодный для использования в качестве имени файла.|
|[`recursive_directory_iterator` см](../standard-library/recursive-directory-iterator-class.md)|Описывает итератор ввода, выполняющий последовательный перебор имен файлов в каталоге файловой системы. Итератор может также просматривать подкаталоги.|
|[`file_status` см](../standard-library/file-status-class.md)|Создает оболочку для `file_type`.|

### <a name="structs"></a>Структуры

|Имя|Описание|
|-|-|
|[`space_info` дереве](../standard-library/space-info-structure.md)|Содержит сведения о томе.|

## <a name="functions"></a>Функции

[\<filesystem> функции](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Операторы

[\<filesystem> операторы](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Перечисления

|Имя|Описание|
|-|-|
|[`copy_options`](../standard-library/filesystem-enumerations.md#copy_options)|Перечисление, используемое с функцией [copy_file](../standard-library/filesystem-functions.md#copy_file) , которое определяет действия в случае, если целевой файл уже существует.|
|[`directory_options`](../standard-library/filesystem-enumerations.md#directory_options)|Перечисление, указывающее параметры итераторов каталога.|
|[`file_type`](../standard-library/filesystem-enumerations.md#file_type)|Перечисление для типов файлов.|
|[`perm_options`](../standard-library/filesystem-enumerations.md#perm_options)| Перечисляет параметры для `permissions` функции. |
|[`perms`](../standard-library/filesystem-enumerations.md#perms)|Тип битовой маски, используемый для передачи разрешений и параметров для разрешений.|

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)
