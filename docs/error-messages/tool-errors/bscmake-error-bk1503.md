---
description: 'Дополнительные сведения: BSCMAKE Error BK1503'
title: Ошибка BSCMAKE BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: 0e789aa54241df5245f4c3a02a9307a97d51730c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323003"
---
# <a name="bscmake-error-bk1503"></a>Ошибка BSCMAKE BK1503

не удается выполнить запись в файл "имя файла" [: причина]

BSCMAKE объединяет SBR файлы, созданные во время компиляции, в одну базу данных браузера. Если итоговая база данных браузера превышает 64 МБ, или если количество входных файлов (SBR) превышает 4092, то эта ошибка будет выдаваться.

Если проблема вызвана более чем 4092 SBR-файлами, необходимо уменьшить количество входных файлов. В среде Visual Studio это можно сделать с помощью [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) всего проекта и повторной проверки файла по отдельности по файлам.

Если проблема вызвана расширением BSC-файла, превышающим 64 МБ, уменьшение числа SBR-файлов в качестве входных данных приведет к уменьшению размера полученного BSC-файла. Кроме того, объем информации для просмотра может быть уменьшен с помощью/ем (исключение символов, развернутых в макросах),/ел (исключение локальных переменных) и/ES (исключение системных файлов).

## <a name="see-also"></a>См. также раздел

[Параметры BSCMAKE](../../build/reference/bscmake-options.md)
