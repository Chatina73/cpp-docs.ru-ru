---
description: 'Подробнее о следующем: Профильная оптимизация'
title: Профильная оптимизация
ms.date: 04/23/2019
helpviewer_keywords:
- profile-guided optimizations
- optimization, profile-guided [C++]
ms.assetid: 2225c307-d3ae-42c1-8345-a5a959d132dc
ms.openlocfilehash: cd6a9627de72ef170e88493ef3e2147a0ccc2bc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187329"
---
# <a name="profile-guided-optimizations"></a>Профильная оптимизация

Профильная оптимизация позволяет оптимизировать весь исполняемый файл, используя данные из тестовых запусков EXE- или DLL-файла. Данные представляют вероятную производительность программы в рабочей среде.

Профильные оптимизации доступны только при компиляции в машинный код для x86 и x64. Они недоступны для исполняемых файлов, которые будут запускаться в среде CLR. Даже если создать сборку со смешанным машинным и управляемым кодом (с помощью параметра компилятора **/clr**), невозможно использовать профильную оптимизацию только для машинного кода. Попытка выполнить сборку проекта с этими параметрами, заданными в интегрированной среде разработки, приведет к ошибке сборки.

> [!NOTE]
> Сведения, полученные из теста профилирования, запускают переопределения оптимизаций, которые в противном случае вступят в силу, если указать **/Ob**, **/Os** или **/Ot**. Дополнительные сведения см. в статьях [Параметр /Ob (расширение встраиваемых функций)](reference/ob-inline-function-expansion.md) и [/Os, /Ot (приоритет размера кода или скорости кода)](reference/os-ot-favor-small-code-favor-fast-code.md).

## <a name="steps-to-optimize-your-app"></a>Действия по оптимизации приложения

При использовании профильной оптимизации выполните указанные ниже действия, чтобы оптимизировать приложение.

- Скомпилируйте один или несколько файлов исходного кода с параметром [/GL](reference/gl-whole-program-optimization.md).

   Каждый модуль, собранный с параметром **/GL**, может быть проанализирован во время тестовых запусков профильной оптимизации для получения информации о поведении во время выполнения. Не каждый модуль в сборке профильной оптимизации требуется компилировать с параметром **/GL**. Однако только модули, скомпилированные с использованием **/GL**, будут обработаны и доступны позднее для профильной оптимизации.

- Выполните компоновку с использованием [/LTCG](reference/ltcg-link-time-code-generation.md) и [/GENPROFILE или /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md).

   Если использовать одновременно и параметр **/LTCG**, и параметр **/GENPROFILE** или **/FASTGENPROFILE**, при запуске инструментированного приложения будет создан файл `.pgd`. После добавления данных тестового запуска в файл `.pgd` они могут использоваться как входные данные для следующего этапа компоновки (создание оптимизированного образа). При указании параметра **/GENPROFILE** можно также добавить аргумент **PGD=** _имя_файла_, чтобы указать нестандартное имя или расположение для файла `.pgd`. Сочетание параметров компоновщика **/LTCG** и **/GENPROFILE** или **/FASTGENPROFILE** заменяет нерекомендуемый параметр компоновщика **/LTCG:PGINSTRUMENT**.

- Профилирование приложения.

   Каждый раз, когда профилируемый сеанс EXE или профилируемый DLL-файл выгружается, создается файл `appname!N.pgc`. Файл `.pgc` содержит сведения об определенном тестовом запуске приложения. *appname* — это имя приложения, а *N* — это номер, начиная с 1, который увеличивается в зависимости от числа других файлов `appname!N.pgc` в каталоге. Можно удалить файл `.pgc`, если тестовый запуск не представляет сценарий, который вы хотите оптимизировать.

   Во время тестового запуска можно принудительно закрыть открытый в текущий момент файл `.pgc` и создать новый файл `.pgc` с помощью служебной программы [pgosweep](pgosweep.md) (например, если конец тестового сценария не совпадает с завершением работы приложения).

   Приложение также может напрямую вызывать функцию PGO [PgoAutoSweep](pgoautosweep.md) для записи данных профиля в момент вызова в файл `.pgc`. Она обеспечивает более точный контроль над кодом, охватываемым записанными данными в файлах `.pgc`. Пример использования этой функции см. в документации по [PgoAutoSweep](pgoautosweep.md).

   При создании инструментированной сборки сбор данных по умолчанию осуществляется в непотокобезопасном режиме, который обеспечивает более высокую скорость, но, возможно, в ущерб точности. С помощью аргумента **EXACT** для **/GENPROFILE** или **/FASTGENPROFILE** можно настроить сбор данных в потокобезопасном режиме, который точнее, но медленнее. Этот параметр также доступен, если вы задаете нерекомендуемую переменную среды [PogoSafeMode](environment-variables-for-profile-guided-optimizations.md#pogosafemode) или нерекомендуемый параметр компоновщика **/POGOSAFEMODE** при создании инструментированной сборки.

- Выполните компоновку с использованием **/LTCG** и **/USEPROFILE**.

   Для создания оптимизированного образа используйте параметры компоновщика **/LTCG** и [/USEPROFILE](reference/useprofile.md). На этом шаге в качестве входных данных принимается файл `.pgd`. При указании параметра **/USEPROFILE** можно также добавить аргумент **PGD=** _имя_файла_, чтобы указать нестандартное имя или расположение для файла `.pgd`. Это имя можно также указать с помощью нерекомендуемого параметра компоновщика **/PGD**. Сочетание параметров **/LTCG** и **/USEPROFILE** заменяет нерекомендуемые параметры компоновщика **/LTCG:PGOPTIMIZE** и **/LTCG:PGUPDATE**.

Можно даже создать оптимизированный исполняемый файл и позже определить, что дополнительное профилирование будет полезно для создания более оптимизированного образа. Если инструментированный образ и соответствующий файл `.pgd` доступны, можно выполнить дополнительные тестовые запуски и повторно создать оптимизированный образ с новым файлом `.pgd`, используя те же самые параметры компоновщика **/LTCG** и **/USEPROFILE**.

> [!NOTE]
> Файлы `.pgc` и `.pgd` являются файлами двоичного типа. При хранении в системе управления версиями избегайте любых возможных автоматических преобразований текстовых файлов.

## <a name="optimizations-performed-by-pgo"></a>Оптимизации, выполняемые в процессе профильной оптимизации

Профильная оптимизация включает в себя перечисленные ниже проверки и улучшения.

- **Встраивание** — например, если функция A часто вызывает функцию B, а функция B относительно небольшая, то профильная оптимизация встраивает функцию B в функцию A.

- **Отражение виртуального вызова** — если виртуальный или другой вызов через указатель функции часто предназначен для определенной функции, профильная оптимизация может вставить условно выполняемый прямой вызов функции.

- **Распределение регистров** — оптимизация на основе данных профиля улучшает распределение регистров.

- **Простая блочная оптимизация** — позволяет разместить часто выполняемые основные блоки, которые временно выполняются во фрейме, в одном наборе страниц (локально). Это минимизирует число используемых страниц, уменьшая тем самым затраты памяти.

- **Оптимизация размера и скорости** — функции, на которые программа тратит больше всего времени, могут быть оптимизированы по скорости.

- **Структура функции** — на основе графа вызовов и поведения профилируемого вызываемого и вызывающего объектов функции, которые, как правило, относятся к одному пути выполнения, размещаются в одном разделе.

- **Оптимизация условного ветвления** — с помощью зондов значений профильная оптимизация может определить, используется ли заданное значение в операторе switch чаще, чем другие значения.  Затем это значение может быть извлечено из оператора switch.  То же можно сделать с инструкциями **`if`** ... **`else`** , где оптимизатор может упорядочить **`if`** ... **`else`** так, чтобы блок **`if`** или **`else`** размещался первым в зависимости от того, какой блок чаще получает значение true.

- **Отделение неиспользуемого кода** — код, который не вызывается во время профилирования, перемещается в специальный раздел, добавляемый в конец набора разделов. Это позволяет вынести раздел из часто используемых страниц.

- **Отделение кода EH** — так как код EH выполняется только в случае исключений, во многих случаях его можно поместить в отдельный раздел. Это происходит, если профильной оптимизации удается определить, что исключения возникают только при исключительных условиях.

- **Встроенные функции памяти** — необходимость в расширении встроенной функции зависит от частоты ее вызова. Встроенная функция может также быть оптимизирована на основе размера блока перемещения или копирования.

## <a name="next-steps"></a>Следующие шаги

Узнайте больше об этих переменных среды, функциях и средствах, которые можно использовать для профильной оптимизации.

[Переменные среды для профильной оптимизации](environment-variables-for-profile-guided-optimizations.md)<br/>
Эти переменные использовались для настройки поведения сценариев тестирования во время выполнения. В настоящее время они являются нерекомендуемыми и заменены новыми параметрами компоновщика. В этом документе описывается, как перейти от использования переменных среды к использованию параметров компоновщика.

[PgoAutoSweep](pgoautosweep.md)<br/>
Функция, которую можно добавить в приложение, чтобы обеспечить детальный контроль над данными, записываемыми в файл `.pgc`.

[pgosweep](pgosweep.md)<br/>
Программа командной строки, которая записывает все данные профиля в файл `.pgc`, закрывает файл `.pgc` и открывает новый файл `.pgc`.

[pgomgr](pgomgr.md)<br/>
Программа командной строки, которая добавляет данные профиля из одного или нескольких файлов `.pgc` в файл `.pgd`.

[Практическое руководство. Слияние нескольких профилей для профильной оптимизации](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)<br/>
Примеры использования **pgomgr**.

## <a name="see-also"></a>См. также

[Дополнительные средства сборки MSVC](reference/c-cpp-build-tools.md)
