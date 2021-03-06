---
description: 'Дополнительные сведения о: file_status классе'
title: Класс file_status
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 8bc789d97f9b90b18214407fadab19e9644012a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324371"
---
# <a name="file_status-class"></a>Класс file_status

Создает оболочку для [file_type](../standard-library/filesystem-enumerations.md#file_type) и [perms](../standard-library/filesystem-enumerations.md#perms).

## <a name="syntax"></a>Синтаксис

```cpp
class file_status;
```

### <a name="constructors"></a>Конструкторы

|Конструктор|Описание|
|-|-|
|[file_status](#file_status)|Конструирует оболочку для [file_type](../standard-library/filesystem-enumerations.md#file_type) и [разрешений](../standard-library/filesystem-enumerations.md#perms)файлов.|

### <a name="member-functions"></a>Функции элементов

|Функция-член|Описание|
|-|-|
|[type](#type)|Возвращает или задает класс `file_type`.|
|[разрешения](#permissions)|Возвращает или задает разрешения для файла.|

### <a name="operators"></a>Операторы

|Оператор|Описание|
|-|-|
|[Оператор =](#op_as)|Операторы-члены присваивания по умолчанию работают корректно.|

## <a name="requirements"></a>Требования

**Заголовок:**\<filesystem>

**Пространство имен:** std:: экспериментальный:: FileSystem, std:: экспериментальный:: FileSystem

## <a name="file_statusfile_status"></a><a name="file_status"></a> file_status:: file_status

Конструирует оболочку для [file_type](../standard-library/filesystem-enumerations.md#file_type) и [разрешений](../standard-library/filesystem-enumerations.md#perms)файлов.

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Параметры

*Ftype*\
`file_type`По умолчанию задано значение `file_type::none` .

*виде*\
Указанный файл `perms` по умолчанию имеет значение `perms::unknown` .

*file_status*\
Сохраненный объект.

## <a name="file_statusoperator"></a><a name="op_as"></a> file_status:: operator =

Операторы-члены присваивания по умолчанию работают корректно.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Параметры

*file_status*\
[File_status](../standard-library/file-status-class.md) , копируемый в `file_status` .

## <a name="type"></a>Тип <a name="type"></a>

Возвращает или задает класс `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Параметры

*Ftype*\
Задается следующим образом: `file_type`.

## <a name="permissions"></a><a name="permissions"></a> чтение

Возвращает или задает разрешения для файла.

Используйте метод задания, чтобы создать файл `readonly` или удалить `readonly` атрибут.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Параметры

*виде*\
Задается следующим образом: `perms`.

## <a name="see-also"></a>См. также раздел

[Справочник по файлам заголовков](../standard-library/cpp-standard-library-header-files.md)\
[Класс Path](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
