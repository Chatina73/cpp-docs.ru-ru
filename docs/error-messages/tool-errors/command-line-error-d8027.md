---
description: 'Дополнительные сведения: Command-Line Error D8027'
title: Ошибка командной строки D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 80d0812571043249616108e99e763b105b527475
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115655"
---
# <a name="command-line-error-d8027"></a>Ошибка командной строки D8027

невозможно выполнить "Component"

Компилятору не удалось запустить указанный компонент компилятора или компоновщик.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Чтобы устранить ошибку, проверьте указанные ниже возможные причины ее возникновения.

1. Недостаточно памяти для загрузки компонента. Если в NMAKE вызывается компилятор, запустите компилятор за пределами файла makefile.

1. Текущей операционной системе не удалось запустить компонент. Убедитесь, что путь указывает на исполняемые файлы, соответствующие вашей операционной системе.

1. Компонент поврежден. Повторно скопируйте компонент с дисков дистрибутива с помощью программы установки.

1. Параметр указан неправильно. Пример:

    ```
    cl /B1 file1.c
    ```
