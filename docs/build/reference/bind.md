---
description: Дополнительные сведения о:/BIND
title: /BIND
ms.date: 11/04/2016
f1_keywords:
- /bind
helpviewer_keywords:
- -BIND editbin option
- entry points, addresses
- BIND editbin option
- entry points
- /BIND editbin option
- import address table
ms.assetid: 3772b330-1868-4c90-857d-c31faa867982
ms.openlocfilehash: 87ea0265555991fca019760feec4395692c074ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187147"
---
# <a name="bind"></a>/BIND

```
/BIND[:PATH=path]
```

## <a name="remarks"></a>Комментарии

Этот параметр задает адреса точек входа в таблице адресов импорта для исполняемого файла или библиотеки DLL. Используйте этот параметр, чтобы уменьшить время загрузки программы.

Укажите исполняемый файл программы и библиотеки DLL в аргументе *Files* в командной строке EDITBIN. Необязательный аргумент *path* для/BIND указывает расположение библиотек DLL, используемых указанными файлами. Разделяйте несколько каталогов точкой с запятой (**;**). Если *путь* не указан, программа EDITBIN выполняет поиск в каталогах, указанных в переменной среды PATH. Если указан *путь* , программа EDITBIN игнорирует переменную Path.

По умолчанию загрузчик программы задает адреса точек входа при загрузке программы. Время, затрачиваемое этим процессом, зависит от числа библиотек DLL и числа точек входа, на которые ссылается программа. Если программа была изменена с помощью/BIND и базовые адреса для исполняемого файла и его библиотек DLL не конфликтуют с уже загруженными библиотеками DLL, операционной системе не нужно задавать эти адреса. В ситуации, когда файлы основаны на неправильной основе, операционная система перемещает библиотеки DLL программы и повторно вычисляет адреса точек входа, что увеличивает время загрузки программы.

## <a name="see-also"></a>См. также раздел

[Параметры EDITBIN](editbin-options.md)
