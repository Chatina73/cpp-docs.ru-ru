---
description: Дополнительные сведения:. PDB-файлы в качестве входных файлов компоновщика
title: PDB-файлы в качестве входных файлов компоновщика
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 713d42e7e95b5d1e7e3b1f9be21203b75569cdbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201161"
---
# <a name="pdb-files-as-linker-input"></a>PDB-файлы в качестве входных файлов компоновщика

Объектные файлы (obj), скомпилированные с помощью параметра/Zi, содержат имя базы данных программы (PDB). Не указывайте имя PDB-файла объекта компоновщику. При необходимости LINK использует внедренное имя, чтобы найти PDB-файл. Это также относится к отлаживаемым объектам, содержащимся в библиотеке. PDB-файл для отлаживаемой библиотеки должен быть доступен компоновщику вместе с библиотекой.

LINK также использует PDB-файл для хранения отладочной информации для EXE-файла или DLL-файла. PDB-файл программы является выходным файлом и входным файлом, так как LINK обновляет PDB при пересборке программы.

## <a name="see-also"></a>См. также раздел

[Входные файлы ссылок](link-input-files.md)<br/>
[Параметры компоновщика MSVC](linker-options.md)
