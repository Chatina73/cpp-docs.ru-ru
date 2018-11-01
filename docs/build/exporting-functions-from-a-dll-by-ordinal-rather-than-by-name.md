---
title: Экспорт функций из библиотеки DLL по порядковому номеру, а не по имени
ms.date: 11/04/2016
f1_keywords:
- NONAME
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
ms.openlocfilehash: 6a5ac13fdc85b3cb1626aefa28b92866a8c856c1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503421"
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Экспорт функций из библиотеки DLL по порядковому номеру, а не по имени

Экспорт функций из библиотеки DLL проще экспортировать их по имени. Это происходит при использовании **__declspec(dllexport)**, например. Но можно также экспортировать функции по порядковому номеру. С помощью этого способа необходимо использовать DEF-файл, а не **__declspec(dllexport)**. Чтобы указать порядковый номер функции, добавьте номер к имени функции в DEF-файле. Сведения об указании порядковых номеров см. в разделе [Экспорт из DLL с использованием DEF-файлы](../build/exporting-from-a-dll-using-def-files.md).

> [!TIP]
>  Если вы хотите оптимизировать размер файла библиотеки DLL, используйте **NONAME** атрибута для каждой экспортируемой функции. С помощью **NONAME** атрибут, порядковые номера хранятся в библиотеки DLL экспортировать таблицу, а не имена функций. Это может быть значительную экономию при экспорте множество функций.

## <a name="what-do-you-want-to-do"></a>Выберите действие

- [Использовать DEF-файла для экспорта по порядковому номеру](../build/exporting-from-a-dll-using-def-files.md)

- [Использовать __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)

## <a name="see-also"></a>См. также

[Экспорт из библиотеки DLL](../build/exporting-from-a-dll.md)