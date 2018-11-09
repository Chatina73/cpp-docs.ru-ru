---
title: Инструменты и функции Visual C++ в выпусках Visual Studio
ms.date: 02/28/2018
helpviewer_keywords:
- versions [C++]
- Visual C++, versions
- editions [C++]
ms.assetid: 3d88607b-9cc4-490a-8d4c-31ee7610a26f
ms.openlocfilehash: 7f40e59ae3e5e883827a212a16d1dd19822dc136
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463756"
---
# <a name="visual-c-tools-and-features-in-visual-studio-editions"></a>Инструменты и функции Visual C++ в выпусках Visual Studio

В следующей таблице перечислены компоненты Visual C++, доступные в Visual Studio. Крестик в ячейке указывает, что компонент доступен. Пустая ячейка означает, что компонент недоступен. Примечания в скобках означают, что компонент доступен с ограничениями.

## <a name="platforms"></a>Платформы

||||||
|-|-|-|-|-|
|Platform|Visual Studio Express для Windows 10|Visual Studio Express для Windows Desktop|Visual Studio Community и Professional|Visual Studio Enterprise|
|Windows Desktop||X|X|X|
|Универсальная платформа Windows (телефоны, планшеты, ПК, Xbox, IoT и HoloLens)|X||X|X|
|Microsoft Store 8.1|||X|X|
|Windows Phone 8.0|||X|X|
|Android|||X|X|
|iOS|||X|X|

## <a name="compilers"></a>Компиляторы

|Компилятор|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|32-разрядный компилятор X86|X|X|X|X|
|Кросс-компилятор X86_arm|X||X|X|
|64-разрядный компилятор x64|||X|X|
|Кросс-компилятор X86_ x64|X|X|X|X|

## <a name="libraries-and-headers"></a>Библиотеки и заголовки

|Библиотека или заголовок|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Заголовки и библиотеки Windows; библиотека CRT|(X)|X|X|X|
|Стандартная библиотека C++|X|X|X|X|
|ATL|||X|X|
|MFC|||X|X|
|Библиотека классов .NET Framework||X|X|X|
|Библиотека поддержки C++ для .NET||X|X|X|
|OpenMP|X|X|X|X|

## <a name="project-templates"></a>Шаблоны проектов

|Шаблон|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|--------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Шаблоны XAML для UWP, Windows 8.1, Windows Phone 8.0|X||X|X|
|Приложение Direct3D|X||X|X|
|Библиотека DLL (универсальные приложения для Windows)|X||X|X|
|Статическая библиотека (универсальные приложения для Windows)|X||X|X|
|Компонент среды выполнения Windows|X||X|X|
|Приложение модульного тестирования (универсальное приложение Windows)|X||X|X|
|Проект ATL|||X|X|
|Библиотека классов (CLR)||X|X|X|
|Консольное приложение CLR||X|X|X|
|Пустой проект CLR||X|X|X|
|Специальный мастер|||X|X|
|Пустой проект||X|X|X|
|Проект, использующий файл makefile||X|X|X|
|Элемент управления ActiveX библиотеки MFC|||X|X|
|Приложение MFC|||X|X|
|Библиотека DLL MFC|||X|X|
|Тестовый проект|X|X|X|X|
|Консольное приложение Win32||X|X|X|
|Проект Win32||X|X|X|

## <a name="tools"></a>Инструменты

|Средство|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|----------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Инкрементный компоновщик (Link.exe)|X|X|X|X|
|Служебная программа обслуживания программ (Nmake.exe)||X|X|X|
|Генератор библиотек (Lib.exe)|X|X|X|X|
|Компилятор ресурсов Windows (Rc.exe)|X|X|X|X|
|Конвертер ресурсов Windows в объекты (CvtRes.exe)||X|X|X|
|Служебная программа Browse Information Maintenance (BscMake.exe)|X|X|X|X|
|C++ Name Undecorator (Undname.exe)|X|X|X|X|
|COFF/PE Dumper (Dumpbin.exe)|X|X|X|X|
|COFF/PE Editor (Editbin.exe)|X|X|X|X|
|MASM (Ml.exe)|||X|X|
|Spy++|||X|X|
|ErrLook|||X|X|
|AtlTrace|||X|X|
|Devenv.com|||X|X|
|Правила вывода|||X|X|
|Обновление проектов VCBuild с расширением VCPROJ до MSBuild (VCUpgrade.exe)|X|X|X|X|
|Оптимизация с использованием профиля|||X|X|

## <a name="debugging-features"></a>Средства отладки

|Средство отладки|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|-----------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Отладка машинного кода|X|X|X|X|
|natvis (визуализация собственного типа)|X|X|X|X|
|Отладка графики|X||X|X|
|Отладка управляемого кода||X|X|X|
|Использование GPU|X||X|X|
|Использование памяти|X||X|X|
|Удаленная отладка|X|X|X|X|
|Отладка SQL|||X|X|
|Статический анализ кода|Ограниченный|Ограниченный|X|X|

## <a name="designers-and-editors"></a>Редакторы и конструкторы

|Редактор или конструктор|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Конструктор XAML|X||X|X|
|Конструктор и редактор стилей CSS|X|X|X|X|
|Конструктор и редактор HTML|X|X|X|X|
|XML-редактор|X|X|X|X|
|Редактор исходного кода|X|X|X|X|
|Возможности повышения производительности: рефакторинг, IntelliSense, форматирование кода C++|X|X|X|X|
|Конструктор Windows Forms||X|X|X|
|Конструктор данных|||X|X|
|Собственный редактор ресурсов (RC-файлы)|||X|X|
|редакторы ресурсов|X|X|X|X|
|Редактор моделей|X||X|X|
|Конструктор шейдеров|X||X|X|

## <a name="data-features"></a>Средства работы с данными

|Средство работы с данными|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Конструктор данных|||X|X|
|Объекты данных|||X|X|
|Веб-службы|||X|X|
|обозревателя серверов|||X|X|

## <a name="build-and-project-systems"></a>Системы сборки и проектов

|Функция сборки или проекта|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Построение с помощью командной строки (msbuild.exe)|X|X|X|X|
|Собственное многоплатформенное нацеливание||X|X|X|
|Управляемое многоплатформенное нацеливание||X|X|X|
|Параллельное построение|X|X|X|X|
|Настройки сборки|X|X|X|X|
|Расширяемость страниц свойств|X|X|X|X|

## <a name="automation-and-extensibility"></a>Автоматизация и расширяемость

|Автоматизация и расширяемость|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|----------------------------------|---------------------------------------|-----------------------------------------------|---------------------------------------------|------------------------------|
|Объектные модели расширения среды|||X|X|
|Модель кода|||X|X|
|модель проекта|||X|X|
|Модель редактора ресурсов|||X|X|
|Модель мастера|||X|X|
|Объектная модель отладчика|||X|X|

## <a name="application-lifecycle-management-tools"></a>Средства управления жизненным циклом приложения

||||||
|-|-|-|-|-|
|Средство|Visual Studio Express для Windows|Visual Studio Express для Windows Desktop|Visual Studio Professional и Community|Visual Studio Enterprise|
|Модульное тестирование (собственная платформа)|X|X|X|X|
|Модульное тестирование (управляемая платформа)||X|X|X|
|Покрытие кода||||X|
|Тестирование вручную||||X|
|Произвольное тестирование||||X|
|Управление тестовыми случаями||||X|
|Карта кода и диаграммы зависимостей|||только для чтения|X|
|Отладка карты кода||||X|

## <a name="see-also"></a>См. также

[Установка Visual Studio](/visualstudio/install/install-visual-studio)<br/>
[Новые возможности Visual Studio](/visualstudio/ide/whats-new-in-visual-studio)<br/>
[Типы проектов Visual C++](../ide/visual-cpp-project-types.md)<br/>
[SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686)<br/>
