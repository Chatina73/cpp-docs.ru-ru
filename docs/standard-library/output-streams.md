---
description: 'Дополнительные сведения: выходные потоки'
title: Потоки вывода
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: ec09a6bee1bcd2f329522b61950f3d051fb57889
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340870"
---
# <a name="output-streams"></a>Потоки вывода

Объект потока вывода является местом назначения для байтов. Три наиболее важных класса потока вывода — `ostream`, `ofstream`, и `ostringstream`.

Класс `ostream` с помощью производного класса `basic_ostream` поддерживает стандартные объекты потока:

- `cout` стандартный вывод;

- `cerr` стандартные ошибки с ограниченным буфером;

- `clog` аналогично `cerr`, но с полной буферизацией.

Объекты редко создаются из `ostream`; обычно используются предопределенные объекты. В некоторых случаях можно переназначить предопределенные объекты после запуска программы. Класс `ostream`, который можно настроить для работы с буфером или без, наилучшим образом подходит для последовательного текстового вывода. Все функции базового класса `ios` включены в `ostream`. При построении объекта класса `ostream` конструктору необходимо указать объект `streambuf`.

Класс `ofstream` поддерживает вывод в файл на диске. Если вам требуется диск только для вывода, создайте объект класса `ofstream`. Можно указать, будут ли объекты `ofstream` принимать двоичные или текстовые данные при создании объекта `ofstream` или при вызове функции-члена `open` для объекта. Многие параметры форматирования и функции-члены применяются к объектам `ofstream`. Включается вся функциональность базовых классов `ios` и `ostream`.

Если в конструкторе указать имя файла, этот файл автоматически открывается при создании объекта. В противном случае можно использовать функцию-член `open` после вызова конструктора по умолчанию.

Подобно функции времени выполнения `sprintf_s`, класс `ostringstream` поддерживает вывод в строки в памяти. Чтобы создать строку в памяти с помощью форматирования потока ввода-вывода, создайте объект класса `ostringstream`.

## <a name="in-this-section"></a>в этом разделе

[Построение объектов потока вывода](../standard-library/constructing-output-stream-objects.md)

[Использование операторов вставки и контрольный формат](../standard-library/using-insertion-operators-and-controlling-format.md)

[Функции члена потока выходного файла](../standard-library/output-file-stream-member-functions.md)

[Влияние буферизации](../standard-library/effects-of-buffering.md)

[Двоичные выходные файлы](../standard-library/binary-output-files.md)

[Перегрузка оператора << для собственных классов](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[Написание собственных манипуляторов без аргументов](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>См. также раздел

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream](../standard-library/basic-ostringstream-class.md)\
[Программирование iostream](../standard-library/iostream-programming.md)
