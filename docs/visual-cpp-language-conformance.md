---
title: Соответствие стандартам языка Visual C++ | Документы Майкрософт
ms.date: 11/15/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dd4848ae88d7bd66286ef13b3505a741d9b55c5c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060889"
---
# <a name="visual-c-language-conformance"></a>Соответствие стандартам языка Visual C++

Этот раздел содержит сводку по соответствию функций компилятора языковым стандартам ISO C++03, C++11, C++14 и C++17, Draft C++20, а также список функций стандартной библиотеки для компилятора C++ в Visual Studio 2017 и более ранних версий. Каждое название функции компилятора и стандартной библиотеки является ссылкой на документ по C++ стандарта ISO, где находится ее описание (если функция доступна на момент публикации). В столбце поддерживаемых версий перечислены версии Visual Studio, в которых впервые появилась поддержка функции.

Сведения об улучшениях соответствия стандартам и других изменениях в Visual Studio 2017 см. в статьях [C++ conformance improvements in Visual Studio 2017](cpp-conformance-improvements-2017.md) (Улучшения соответствия C++ в Visual Studio 2017) и [What's New for Visual C++ in Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md) (Новые возможности Visual C++ в Visual Studio 2017). Сведения об изменениях соответствия в более ранних версиях см. в статье [Критические изменения в Visual C++](porting/visual-cpp-change-history-2003-2015.md) и [Visual C++ What's New 2003 through 2015](porting/visual-cpp-what-s-new-2003-through-2015.md)(Новые возможности Visual C++ в версиях 2003–2015). Последние новости от команды разработчиков C++ см. в [блоге команды разработчиков Visual C++](https://blogs.msdn.microsoft.com/vcblog/).

> [!NOTE]
> Принципы работы с двоичными файлами в Visual Studio 2017 по сравнению с Visual Studio 2015 существенно не изменились.

## <a name="compiler-features"></a>Функции компилятора

|Область функции| |
|----|---|
|__Основные возможности языка C++03/11__|__Поддерживается__|
|&nbsp;&nbsp;В любом другом месте|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;Двухэтапный поиск по имени|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 Выражение SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 Препроцессор C99](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|Частично <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[N1988 Расширенные целочисленные типы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2006/n1988.pdf)|Н/Д <sup>[E](#note_E)</sup>|
|__Основные возможности языка C++14__|__Поддерживается__|
|&nbsp;&nbsp;[N3323 Настраиваемое контекстное преобразование](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 Двоичные литералы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 Возвращаемые типы auto и decltype(auto)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 Захват при инициализации](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 Универсальные лямбда-выражения](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 Атрибут [[нерекомендуемый]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Освобождение с указанием размера](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 Разделители цифр](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 Шаблоны переменных](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 Расширенный constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017|
|&nbsp;&nbsp;[N3653 NSDMI для статистических выражений](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017|
|&nbsp;&nbsp;[N3664 Предотвращение и объединение выделений ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3664.html)|Н/Д <sup>[F](#note_F)</sup>|
|__Основные возможности языка C++17__|__Поддерживается__|
|&nbsp;&nbsp;[N4086 Удаление триграфов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 Новые правила для автоматического использования с braced-init-lists](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 Имя типа в параметрах шаблона](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 Атрибуты пространств имен и перечислителей](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 Знаковые литералы u8](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4230 Определение вложенных пространств имен](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 Краткие статические операции static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 Обобщенный цикл for на основе диапазона](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 Атрибут [[fallthrough]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 Удаление ключевого слова register](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 Удаление operator++ для типа bool](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 Захват *this по значению](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 Использование пространств имен атрибутов без повторения](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 __has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 Прямая инициализация списком фиксированных перечисляемых типов из целых чисел](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 Лямбда-выражения constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 Атрибут [[nodiscard]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 Атрибут [[maybe_unused]]](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 Структурированные привязки](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 Операторы if в constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[P0305R1 Операторы выбора с инициализаторами](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Шестнадцатеричные литералы с плавающей запятой](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 Разрешение дополнительных аргументов шаблона, не являющихся типом](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 Выражения свертывания](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 Удаление динамических спецификаций исключений](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 Добавление noexcept к системе типов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 Избыточное выделение динамической памяти](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 Встроенные переменные](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 Сопоставление параметров шаблона с совместимыми аргументами](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 Удаление некоторых пустых унарных свертываний](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 Исправление преобразований квалификации](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 Расширенная агрегатная инициализация](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0091R3 Выведение аргументов шаблонов для шаблонов классов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br />&nbsp;&nbsp;[P0512R0 Проблемы с выведением аргумента шаблона класса](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 Объявление параметров шаблона, не являющихся типами, с auto](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 Гарантированный пропуск копирования](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6 <sup>[H](#note_H)</sup>|
|&nbsp;&nbsp;[P0136R1 Перефразирование наследования конструкторов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 Уточнение порядка вычисления выражений](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br />&nbsp;&nbsp;[P0400R0 Порядок вычисления аргументов функции ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 Упаковка расширений в объявлениях using](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 Пропуск нераспознанных атрибутов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0702R1 Исправление выведения шаблона аргумента класса для конструкторов списка инициализаторов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|

|Область функции| |
|----|---|
|__Основные возможности языка C++17 (сообщения о дефектах)__|__Поддерживается__|
|&nbsp;&nbsp;[P0702R1 Исправление выведения шаблона аргумента класса для конструкторов списка инициализаторов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 Упрощение неявного захвата в лямбда-выражении](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0588r1.html)|Нет|
|&nbsp;&nbsp;[CWG 1581: Когда определяются функции-члены constexpr?](https://wg21.cmeerw.net/cwg/issue1581)|Нет|
|&nbsp;&nbsp;[P0962R1 Ослабление правил поиска точки настройки структурированных привязок](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|Нет|
|&nbsp;&nbsp;[P0962R2 Ослабление правил поиска точки настройки выражений for, основанных на диапазоне](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0962r1.html)|Нет|
|&nbsp;&nbsp;[P0969R0 Разрешение структурированных привязок для доступных членов](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|Нет|

|Область функции| |
|----|---|
|__Основные возможности языка C++20__|__Поддерживается__|
|&nbsp;&nbsp;[P0306R4 Добавление &#95;&#95;VA_OPT&#95;&#95 для пропуска и удаления запятых](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0306r4.pdf)|Нет|
|&nbsp;&nbsp;[P0329R4 Назначенный конструктор инициализации](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|Нет|
|&nbsp;&nbsp;[P0409R2 Разрешение захвата объекта [=, this] в лямбда-выражении](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|Нет|
|&nbsp;&nbsp;[P0428R2 Знакомый синтаксис шаблона для универсальных лямбда-выражений](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|Нет|
|&nbsp;&nbsp;[P0683R1 Инициализатор элементов по умолчанию для битовых полей](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0683r1.html)|Нет|
|&nbsp;&nbsp;[P0704R1 Исправления указателей элементов const lvalue, проверенных по ссылке](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|Нет|
|&nbsp;&nbsp;[P0734R0 Основные понятия ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0734r0.pdf)|Нет|

## <a name="standard-library-features"></a>Стандартные возможности библиотеки

|Область функции| |
|---|---|
|__Функции стандартной библиотеки C++20__|__Поддерживается__|
|&nbsp;&nbsp; [P0777R1 Отказ от лишнего вырождения](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0463R1 Порядок байтов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html)|Нет|
|&nbsp;&nbsp;[P0674R1 make_shared() для массивов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|Нет|
|&nbsp;&nbsp;[P0858R0 Требования к итератору constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0809R0 Сравнение неупорядоченных контейнеров](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp; [P0020R3 atomic\<float>, atomic\<double>, atomic\<long double>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html)|Нет|
|&nbsp;&nbsp; [P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br />&nbsp;&nbsp; [P0753R2 манипуляторы osyncstream](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|Нет|
|&nbsp;&nbsp; [P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|Нет|
|&nbsp;&nbsp; [P0202R3 constexpr для \<algorithm> и exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|Нет|
|&nbsp;&nbsp; [P0355R7 \<chrono > для календарей и часовых поясов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|Нет|
|&nbsp;&nbsp;[P0415R1 constexpr для \<complex> (повторно)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|Нет|
|&nbsp;&nbsp; [P0439R0 Класс перечисления memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|Нет|
|&nbsp;&nbsp; [P0457R2 Starts_with()/ends_with() для basic_string/basic_string_view](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|Нет|
|&nbsp;&nbsp; [P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|Нет|
|&nbsp;&nbsp; [P0551R3 Не специализируй шаблоны функции std!](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0551r3.pdf)|Нет|
|&nbsp;&nbsp; [P0600R1 \[\[nodiscard\]\] для STL, часть 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf)|Нет|
|&nbsp;&nbsp; [P0616R0 Использование move() в \<numeric>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0616r0.pdf)|Нет|
|&nbsp;&nbsp; [P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|Нет|
|&nbsp;&nbsp; [P0718R2 atomic\<shared_ptr\<T>>, atomic\<weak_ptr\<T>>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|Нет|
|&nbsp;&nbsp; [P0754R2 \<version>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0754r2.pdf)|Нет|
|&nbsp;&nbsp; [P0767R1 Объявление is_pod нерекомендуемым](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|Нет|
|&nbsp;&nbsp; [P0768R1 Поддержка библиотеки для оператора сравнения "космический корабль"\<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|Нет|
|&nbsp;&nbsp; [P0966R1 string::reserve() не должен сжимать](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0966r1.html)|Нет|
|__Функции стандартной библиотеки C++17__|__Поддерживается__|
|&nbsp;&nbsp;[P0433R2 Интеграция вывода шаблонов для шаблонов классов в стандартной библиотеке](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br />&nbsp;&nbsp;[P0739R0 Улучшение интеграции аргумента шаблона класса со стандартной библиотекой](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0426R1 constexpr для char_traits](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0220R1 Основы работы с библиотеками V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6 <sup>[J](#note_J)</sup>|
|&nbsp;&nbsp;[P0067R5 Простые преобразования строк](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2017 15.7 <sup>[charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: \<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br />&nbsp;&nbsp;[P0337R0 Удаление назначения polymorphic_allocator](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0024R2 Параллельные алгоритмы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br />&nbsp;&nbsp;[P0336R1 Переименование политик параллельного выполнения](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br />&nbsp;&nbsp;[P0394R4 Параллельные алгоритмы следует завершить terminate() для исключений](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br />&nbsp;&nbsp;[P0452R1 Объединение параллельных алгоритмов \<numeric>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0226R1 Специальные математические функции](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br />&nbsp;&nbsp;[P0219R1 Относительные пути для файловой системы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br />&nbsp;&nbsp;[P0317R1 Кэширование записей каталога для файловой системы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p03179r1.html)<br />&nbsp;&nbsp;[P0392R0 Поддержка string_view в путях файловой системы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br />&nbsp;&nbsp;[P0430R2 Поддержка файловых систем, отличных от POSIX](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br />&nbsp;&nbsp;[P0492R2 Разрешение комментариев NB для файловой системы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[K](#note_K)</sup>|
|&nbsp;&nbsp;[P0003R5 Удаление динамических спецификаций исключений](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br />&nbsp;&nbsp;[P0358R1 Исправления для not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0033R1 Переформулировка enable_shared_from_this](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0083R3 Соединение карт и наборов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br />&nbsp;&nbsp;[P0508R0 Уточнение insert_return_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0174R2 Неподдерживаемые части библиотеки](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0302R1 Удаление поддержки распределителя в std::function](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br />&nbsp;&nbsp;[P0497R0 Исправление shared_ptr для массивов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 Неподдерживаемая shared_ptr::unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 Встроенные переменные для стандартной библиотеки](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 Перевод \<codecvt> в разряд нерекомендуемых](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: алгоритм поиска Бойера-Мура ()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 Исправления возвращаемых типов модуля поиска](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0031R0 constexpr для \<array> (Again) и \<iterator>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[Расширение средств управления памяти P0040R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 Определение местоположения возвращаемого значения](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_sizeи т. д.](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R2 Переименование lock\_guard в scoped\_lock с переменным числом аргументов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[L](#note_L)</sup>|
|&nbsp;&nbsp;[P0295R0 gcd(), lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup>[17](#note_17), [byte](#note_byte)</sup>|
|&nbsp;&nbsp;[P0403R1 Файлы UDL для \<string_view> ("meow"sv, и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0418R2 Требования к атомарной функции compare_exchange memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0435R1 Переработка common_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br />&nbsp;&nbsp;[P0548R1 Настройка common\_type и длительности](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0505R0 constexpr для \<chrono> (Again)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0513R0 Подделка хэша](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br />&nbsp;&nbsp;[P0599R1 Хэш noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 Пометка копирования shared_future как noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 Создание future_error из future_errc](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0558R1 Разрешение несоответствий <T>базового класса с атомарным именем](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0604R0 Изменение is\_callable/result\_of на invoke\_result, is\_invocable, is\_nothrow\_invocable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: \<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017|
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: \<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017|
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: \<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 |
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: \<string_view>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017|
|&nbsp;&nbsp;[N4562 Основы работы с библиотеками: \<tuple> apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017|
|&nbsp;&nbsp;[P0032R3 Однородный интерфейса для типа variant, any или optional](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017|
|&nbsp;&nbsp;[P0077R2 is_callable, is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0254R2 Интеграция string_view и std::string](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0307R2 Повторный перевод необязательной в состояние "больше или равно"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017|
|&nbsp;&nbsp;[P0393R3 Перевод варианта в состояние "больше или равно"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017|
|&nbsp;&nbsp;[P0504R0 Пересмотр in_place_t/in_place_type_t\<T>/in_place_index_t\<I>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017|
|&nbsp;&nbsp;[P0510R0 Отклонение вариантов Nothing, Arrays, References и Incomplete Type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0185R1 is_swappable, is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0272R1 Неконстантный basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[N4387 Улучшение pair и tuple](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (Untimed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0004R1 Удаление нерекомендуемых псевдонимов Iostreams](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0006R0 Шаблоны переменных для признаков типов (is_same_v и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 Признаки типов логических операторов (conjunction и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor(), ceil(), round(), abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R0 lock_guard с переменным числом аргументов](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 Безопасные преобразования в unique_ptr\<T[]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 Удаление auto_ptr, random_shuffle() и старой \<functional> Stuff](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 Очистки noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 Доступная для простого копирования функция reference_wrapper](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 insert_or_assign()/try_emplace() For map/unordered_map](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size(), empty(), data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 Ограничение назначений unique_ptr точными значениями](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0063R3 Стандартная библиотека C11](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11), [14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 Поддержка неполных типов в vector/list/forward_list](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|__Функции стандартной библиотеки C++14__|__Поддерживается__|
|&nbsp;&nbsp;[N3462 SFINAE result_of](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 constexpr для \<complex>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 constexpr для \<chrono>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 constexpr для \<array>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 constexpr для \<initializer_list>, \<tuple>, \<utility>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 Файлы UDL для \<chrono>, \<string> (1729ms, "meow"s, и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Пустые однонаправленные итераторы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 Разнородный ассоциативный поиск](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (Timed)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 Исправление функций-членов constexpr без константы](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 equal(), is_permutation(), mismatch() с двойным диапазоном](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 Освобождение с указанием размера](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 Файлы UDL \<complex> (3.14i и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 constexpr для \<functional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 Переименование shared_mutex (Timed) в shared_timed_mutex](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 Требования к минимальным элементам контейнера](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 Прозрачные функции операторов (less\<> и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 Шаблоны псевдонимов для \<type_traits> (decay_t и т. д.)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|
|&nbsp;&nbsp;[N3924 Нерекомендуемое использование rand()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3924.pdf)|Н/Д|

Набор совместно указанных документов означает, что функция была выбрана как соответствующая стандарту, и затем также был одобрен один или несколько документов по улучшению или расширению этой функции. Эти функции реализованы вместе.

### <a name="supported-values"></a>Поддерживаемые значения

__Нет__ означает, что функция еще не реализована.<br/>
__Частично__ означает, что реализация в Visual Studio 2017 является неполной. Дополнительные сведения см. в разделе примечаний.<br/>
__Н/Д__ означает, что функции не описаны в документах с предложениями. Эти документы изменили язык стандарта, но не привели к действиям со стороны разработчиков. Они указаны для полноты представления информации.<br/>
__VS 2010__ — функции, которые поддерживаются в Visual Studio 2010.<br/>
__VS 2013__ — функции, которые поддерживаются в Visual Studio 2013.<br/>
__VS 2015__ — функции, которые поддерживаются в Visual Studio 2015 RTM.<br/>
__VS 2015.2__ и __VS 2015.3__ — функции, которые поддерживаются в Visual Studio 2015 с обновлением 2 и Visual Studio 2015 с обновлением 3, соответственно.<br/>
__VS 2017__ — функции, которые поддерживаются в Visual Studio 2017 RTM.<br/>
__VS 2017 15.3__ — функции, которые поддерживаются в Visual Studio 2017 версии 15.3.<br/>
__VS 2017 15.5__ — функции, которые поддерживаются в Visual Studio 2017 версии 15.5.<br/>
__VS 2017 15.7__ — функции, которые поддерживаются в Visual Studio 2017 версии 15.7.<br/>

### <a name="notes"></a>Примечания

<a name="note_A"></a>__A__ В режиме /std:c++14 спецификации динамических исключений остаются нереализованными и throw() по-прежнему рассматривается как синоним \_\_declspec(nothrow). В C++17 спецификации динамических исключений в основном удалены в P0003R5, за исключением одного vestige: throw(), который является устаревшим и должен вести себя как синоним noexcept. В режиме /std:c++17 параметры MSVC теперь соответствует стандарту, обеспечивая throw() то же поведение, что и noexcept, т. е. через завершение.

Параметр компилятора /Zc:noexceptTypes- требует старого поведения \_\_declspec(nothrow). Вполне вероятно, что throw() будет удален в C++20. Для того чтобы помочь с приведением кода в соответствие с указанными изменениями в стандарте и нашей реализации, для параметров **/std:c++17** и **/permissive-** были добавлены новые предупреждения компилятора для исключений, связанных с несоответствием спецификациям.

<a name="note_B"></a>__B__ Поддерживается в режиме /permissive- Visual Studio 2017 версии 15.7. Дополнительные сведения см. в записи блога [Two-phase name lookup support comes to MSVC](https://blogs.msdn.microsoft.com/vcblog/2017/09/11/two-phase-name-lookup-support-comes-to-msvc/) (В MSVC добавят поддержку двухфазного поиска имени).

<a name="note_C"></a>__C__ Поддержка компилятора для выражения SFINAE была достаточной для стандартной библиотеки с момента выхода Visual Studio 2015 с обновлением 2. Поддерживается в Visual Studio 2017 версии 15.7 независимо от того, установлен ли режим /permissive-. Остаются некоторые ошибки, которые необходимо исправить. Больше не требуется использовать обходное решение "уникальный тег типа", и мы удалили этот обходной путь из реализации STL.

<a name="note_D"></a>__C__ Поддержка компилятора для правил препроцессора C99 является незавершенной в Visual Studio 2017. Поддерживаются макросы с переменным числом аргументов, но в поведении препроцессора существует множество ошибок.  Мы тщательно перерабатываем препроцессор и скоро в качестве эксперимента добавим эти изменения в режим **/permissive-**.

<a name="note_E"></a>__D__ Помечено как "Неприменимо", так как для поддержки расширенных целочисленных типов компиляторы разрешены, но не требуются.  Мы решили не поддерживать их, как GCC и Clang.

<a name="note_F"></a>__D__ Помечено как "Неприменимо", так как для реализации этой оптимизации компиляторы разрешены, но не требуются.

<a name="note_G"></a>__G__ Поддерживается в [/std: c++14](./build/reference/std-specify-language-standard-version.md) с отключаемым предупреждением.

<a name="note_J"></a>__J__ Функции, которые не были завершены в Visual Studio 2015, указаны в другом месте в этой таблице.

<a name="note_K"></a>__K__ Это совершенно новая, несовместимая с предыдущей версией std::experimental реализация, необходимость в которой вызвана добавлением поддержки символьных ссылок, исправлением ошибок и изменениями в поведении, которое требуется для соблюдения стандарта. В настоящее время включение \<filesystem> предоставляет новый std::filesystem и предыдущий std::experimental::filesystem, а включение \<experimental/filesystem> предоставляет только старую экспериментальную реализацию. Экспериментальная реализация будет УДАЛЕНА в следующем выпуске библиотек, содержащем изменения в ABI.

<a name="note_L"></a>__L__ Поддерживается встроенными функциями компилятора.

<a name="note_14"></a>__14__ Эти функции C++17/20 всегда включены, даже если указано значение по умолчанию [/std:c++14](build/reference/std-specify-language-standard-version.md). Это происходит, потому что функция реализована до введения параметров **/std** или из-за сложных условий реализации.

<a name="note_17"></a>__17__ Эти функции выключены параметром компилятора [/std:c++17](./build/reference/std-specify-language-standard-version.md) (или [/std:c++latest](./build/reference/std-specify-language-standard-version.md)).

<a name="note_byte"></a>__byte__ `std::byte` поддерживают [/std:c++17](./build/reference/std-specify-language-standard-version.md) (или [/std:c++latest](./build/reference/std-specify-language-standard-version.md)), но так в некоторых случаях эта версия может конфликтовать с заголовками Windows SDK, предусмотрен детально настроенный макрос явного отказа. Его можно отключить, определив `_HAS_STD_BYTE` как `0`.

<a name="note_C11"></a>__C11__ В Universal CRT реализованы части стандартной библиотеки C11, необходимые для C++17, за исключением альтернативных спецификаторов преобразования E и O C99 `strftime()`, исключительного режима C11 `fopen()` и C11 `aligned_alloc()`. Маловероятно, что последний компонент будет реализован, так как в C11 `aligned_alloc()` указан так, что он становится несовместимым с реализацией `free()`, а именно, `free()` должен быть способен обрабатывать точно выровненные распределения.

<a name="note_rem"></a>__rem__ Компоненты удалены, когда был указан параметр компилятора [/std:c++17](./build/reference/std-specify-language-standard-version.md) (или [/std:c++latest](./build/reference/std-specify-language-standard-version.md)). Эти функции имеют макрос явного отказа: `_HAS_AUTO_PTR_ETC`, `_HAS_FUNCTION_ALLOCATOR_SUPPORT`, `_HAS_OLD_IOSTREAMS_MEMBERS` и `_HAS_UNEXPECTED`.

<a name="note_charconv"></a>__charconv__ from_chars() и to_chars() доступны для целых чисел. В настоящее время мы работаем над from_chars() для чисел с плавающей запятой, за которым последует to_chars().

<a name ="note_parallel"></a> __parallel__ разработка библиотек для параллельных алгоритмов C++17 завершена. Обратите внимание, это не значит, что каждый алгоритм работает параллельно в каждом случае. Параллелизуются наиболее важные алгоритмы, однако сигнатуры политик выполнения предоставляются даже тогда, когда алгоритмы не удалось распараллелить. Центральный заголовок нашей внутренней реализации STL (yvals.h) содержит следующие "замечания по параллельным алгоритмам": C++ допускает реализацию параллельных алгоритмов как вызовов последовательных алгоритмов.   Эта реализация распараллеливает некоторые распространенные вызовы алгоритмов, но не все.

Параллельно работают следующие алгоритмы:

- adjacent_difference, adjacent_find, all_of, any_of, count, count_if, equal, exclusive_scan, find, find_end, find_first_of, find_if, for_each, for_each_n, inclusive_scan, mismatch, none_of, reduce, remove, remove_if, search, search_n, sort, stable_sort, transform, transform_exclusive_scan, transform_inclusive_scan, transform_reduce.

Следующие алгоритмы в настоящее время еще не распараллелены:

- Нет заметного увеличения производительности от параллелизма на целевом оборудовании. Все алгоритмы, которые просто копируют или переставляют элементы без создания ветвей, обычно ограничены пропускной способностью памяти:
  - copy, copy_backward, copy_n, fill, fill_n, move, move_backward, remove, remove_if, replace, replace_if, reverse, reverse_copy, rotate, rotate_copy, swap_ranges
- Существует путаница относительно требований пользователей к параллелизму, по-видимому, как и в категории выше:
  - generate, generate_n
- Вероятно, эффективный параллелизм недостижим:
  - partial_sort, partial_sort_copy
- Оценка пока недоступна. Параллелизм может быть реализован в будущих выпусках, и предполагается, что он улучшит производительность:
  - copy_if, includes, inplace_merge, is_heap, is_heap_until, is_partitioned, is_sorted, is_sorted_until, lexicographical_compare, max_element, merge, min_element, minmax_element, nth_element, partition_copy, remove_copy, remove_copy_if, replace_copy, replace_copy_if, set_difference, set_intersection, set_symmetric_difference, set_union, stable_partition, unique, unique_copy

## <a name="see-also"></a>См. также

[Справочник по языку C++](cpp/cpp-language-reference.md)<br/>
[Стандартная библиотека C++](standard-library/cpp-standard-library-reference.md)<br/>
[Улучшения соответствия C++ в Visual Studio 2017](cpp-conformance-improvements-2017.md)<br/>
[Новые возможности Visual C++ в Visual Studio 2017](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
[Журнал изменений Visual C++ 2003–2015](porting/visual-cpp-change-history-2003-2015.md)<br/>
[Новые возможности Visual C++ 2003–2015](porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
[Блог команды разработчиков Visual C++](https://blogs.msdn.microsoft.com/vcblog/)
