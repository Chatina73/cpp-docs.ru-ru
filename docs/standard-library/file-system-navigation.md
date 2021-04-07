---
title: Навигация по файловой системе
description: Использование API-интерфейсов файловой системы стандартной библиотеки C++ для навигации по файловой системе.
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: f5f85eaf5e665ea4374e71c5eab7434b9c3d34e4
ms.sourcegitcommit: a89eac9acdbd54a181e3bd5d5bc71a3ef3c1abca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106506095"
---
# <a name="file-system-navigation"></a>Навигация по файловой системе

`<filesystem>`Заголовок реализует техническую спецификацию файловой системы C++ ISO/IEC TS 18822:2015 (окончательный вариант черновика: [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)) и имеет типы и функции, позволяющие создавать независимый от платформы код для навигации по файловой системе. Поскольку это межплатформенное приложение, оно содержит интерфейсы API, не относящиеся к системам Windows. Например, `is_fifo(const path&)` всегда возвращает значение **`false`** в Windows.

## <a name="overview"></a>Обзор

Используйте `<filesystem>` API для следующих задач:

- выполнение итерации по файлам и каталогам в указанном пути;

- получение сведений о файлах, включая время создания, размер, расширение и корневой каталог;

- составление, разделение и сравнение путей;

- Создание, копирование и удаление каталогов

- копирование и удаление файлов.

Дополнительные сведения о вводе-выводе файлов с помощью стандартной библиотеки см. в разделе [Программирование iostream](../standard-library/iostream-programming.md).

## <a name="paths"></a>Пути

### <a name="constructing-and-composing-paths"></a>Создание и составление путей

Пути в Windows (начиная с XP) изначально хранятся в Юникоде. [`path`](../standard-library/path-class.md)Класс автоматически выполняет все необходимые преобразования строк. Он принимает аргументы как для широких, так и для узких символьных массивов, а также для `std::string` `std::wstring` типов, отформатированных как UTF8 или UTF16. Класс `path` также автоматически нормализует разделители путей. В аргументах конструктора в качестве разделителя каталогов можно использовать одиночную косую черту. Этот разделитель позволяет использовать одни и те же строки для хранения путей в средах Windows и UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Для объединения двух путей можно использовать перегруженные операторы `/` и `/=` , которые аналогичны операторам `+` и `+=` в `std::string` и `std::wstring`. `path`Объект будет удобным образом предоставлять разделители, если это не так.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Проверка путей

Класс Path имеет несколько методов, возвращающих сведения о различных частях пути. Эта информация отличается от сведений о сущности файловой системы, на которую может ссылаться. Можно получить корень, относительный путь, имя файла, расширение файла и другие сведения. Можно выполнять итерацию по объекту path для проверки всех папок в иерархии. В следующем примере показано, как выполнить итерацию по объекту пути. И, как получить сведения о его частях.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Код создает следующие выходные данные:

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>Сравнение путей

Класс `path` перегружает операторы сравнения на равенство как `std::string` и `std::wstring`. При сравнении двух путей необходимо выполнить сравнение строк после нормализации разделителей. Если пропущена Замыкающая косая черта (или обратная косая черта), она не добавляется и влияет на сравнение. В следующем примере показано, как выполняется сравнение значений пути:

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

Для запуска этого кода вставьте его в полный пример выше перед `main` и раскомментируйте строку, которая вызывает его в основном объекте.

### <a name="converting-between-path-and-string-types"></a>Преобразование между типами пути и строки

Объект `path` может быть неявно преобразован в `std::wstring` или `std::string`. Это означает, что можно передать путь к таким функциям [`wofstream::open`](../standard-library/basic-ofstream-class.md#open) , как, как показано в следующем примере:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>Итерация по каталогам и файлам

`<filesystem>`Заголовок предоставляет [`directory_iterator`](../standard-library/directory-iterator-class.md) тип для итерации по отдельным каталогам и [`recursive_directory_iterator`](../standard-library/recursive-directory-iterator-class.md) класс для рекурсивного прохода по каталогу и его подкаталогам. После создания итератора путем передачи ему объекта `path` итератор указывает на первое значение directory_entry в пути. Создайте конечный итератор путем вызова конструктора по умолчанию.

При итерации по каталогу существует несколько типов элементов, которые можно обнаружить. К этим элементам относятся каталоги, файлы, символические ссылки, файлы сокетов и др. `directory_iterator`Возвращает свои элементы в виде [`directory_entry`](../standard-library/directory-entry-class.md) объектов.
