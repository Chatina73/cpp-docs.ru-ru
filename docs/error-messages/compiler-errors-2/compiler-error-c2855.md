---
description: 'Дополнительные сведения о: Ошибка компилятора C2855'
title: Ошибка компилятора C2855
ms.date: 02/16/2021
f1_keywords:
- C2855
helpviewer_keywords:
- C2855
ms.openlocfilehash: cc26dbf92ea385ee05681e5fab8b5c4257c2b525
ms.sourcegitcommit: e99db7c3b5f25ece0e152165066c926751a7c2ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100643551"
---
# <a name="compiler-error-c2855"></a>Ошибка компилятора C2855

> параметр командной строки "*параметр*" несовместим с предкомпилированным заголовком

Эта ошибка возникает, когда параметр командной строки отличается от параметров, используемых для создания предкомпилированного заголовка.

## <a name="remarks"></a>Комментарии

Ошибка C2855 может возникать при выполнении добавочной сборки после изменения параметра компилятора. Это также может произойти, если задать конкретные параметры компилятора для отдельных исходных файлов.

Чтобы устранить эту ошибку, повторно создайте предварительно скомпилированный заголовок с помощью указанного параметра командной строки. Чтобы повторно создать предкомпилированный заголовок, создайте связанный исходный файл. Например, проекты, созданные с помощью шаблона Visual Studio, обычно создают исходный файл с именем *`pch.cpp`* для создания предкомпилированного заголовка. (В более ранних версиях Visual Studio этот файл называется *`stdafx.cpp`* .) В других проектах исходный файл для перестроения создается с помощью параметра компилятора [ `/Yc` (создание файла предкомпилированного заголовка)](../../build/reference/yc-create-precompiled-header-file.md) . Рекомендуется перестроить весь проект после внесения изменений в предкомпилированный заголовок.

## <a name="see-also"></a>См. также

[`/Y` (Предварительно скомпилированные заголовки)](../../build/reference/y-precompiled-headers.md)\
[Файлы предкомпилированных заголовков](../../build/creating-precompiled-header-files.md)
