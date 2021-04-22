---
title: Файлы заголовков стандартной библиотеки C++
description: Файлы заголовков стандартной библиотеки C++, по категориям
ms.date: 08/31/2020
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: de4a6a31102c5a4245aeb4600c3e76205c9d195f
ms.sourcegitcommit: 82a0d23b04d0776c00209d885689cbc5be36d3b9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106099707"
---
# <a name="c-standard-library-header-files"></a>Файлы заголовков стандартной библиотеки C++

Файлы заголовков для стандартной библиотеки и расширений C++ по категориям.

## <a name="headers-by-category"></a>Заголовки по категориям

::: moniker range=">=msvc-150"

| Категория | Заголовки |
| - | - |
| [Алгоритмы](./algorithms.md) | [`<algorithm>`](algorithm.md), [`<cstdlib>`](cstdlib.md), [`<numeric>`](numeric.md) |
| Атомарные операции |  [`<atomic>`](atomic.md)<sup>стр</sup> |
| Оболочки библиотек C | [`<cassert>`](cassert.md), [`<ccomplex>`](ccomplex.md) <sup>11 a б</sup>, [`<cctype>`](cctype.md) ,, [`<cerrno>`](cerrno.md) , [`<cfenv>`](cfenv.md) <sup>11</sup>, [`<cfloat>`](cfloat.md) , [`<cinttypes>`](cinttypes.md) <sup>11</sup>, [`<ciso646>`](ciso646.md) <sup>b</sup>, [`<climits>`](climits.md) ,,,, [`<clocale>`](clocale.md) [`<cmath>`](cmath.md) [`<csetjmp>`](csetjmp.md) [`<csignal>`](csignal.md) , [`<cstdalign>`](cstdalign.md) <sup>11 a b</sup>, [`<cstdarg>`](cstdarg.md) , [`<cstdbool>`](cstdbool.md) <sup>11 а b</sup>, [`<cstddef>`](cstddef.md) [`<cstdint>`](cstdint.md) <sup>11</sup>, [`<cstdio>`](cstdio.md) , [`<cstdlib>`](cstdlib.md) , [`<cstring>`](cstring.md) , [`<ctgmath>`](ctgmath.md) <sup>11 a b</sup> [`<ctime>`](ctime.md) [`<cuchar>`](cuchar.md) <sup></sup> [`<cwchar>`](cwchar.md) , 11,,[`<cwctype>`](cwctype.md) |
| Основные понятия | `<concepts>`<sup>20</sup> |
| [Контейнеры](./stl-containers.md) | |
| Контейнеры последовательности | [`<array>`](array.md)<sup>11</sup>, [`<deque>`](deque.md) , [`<forward_list>`](forward-list.md) <sup>11</sup>, [`<list>`](list.md) ,[`<vector>`](vector.md) |
| Упорядоченные ассоциативные контейнеры| [`<map>`](map.md), [`<set>`](set.md) |
| Неупорядоченные ассоциативные контейнеры | [`<unordered_map>`](unordered-map.md)<sup>11</sup>, [`<unordered_set>`](unordered-set.md) <sup>11</sup> |
| Переходники контейнеров | [`<queue>`](queue.md), [`<stack>`](stack.md) |
| Представления контейнеров | [`<span>`](span.md)<sup>20</sup> |
| [Ошибки и обработка исключений](../cpp/errors-and-exception-handling-modern-cpp.md) | [`<cassert>`](cassert.md), [`<exception>`](exception.md) , [`<stdexcept>`](stdexcept.md) , [`<system_error>`](system-error.md) <sup>11</sup> |
| Общие служебные программы | `<any>`<sup>17</sup>, [`<bit>`](bit.md) <sup>20</sup>, [`<bitset>`](bitset.md) , [`<cstdlib>`](cstdlib.md) , `<execution>` <sup>17</sup>, [`<functional>`](functional.md) , [`<memory>`](memory.md) , `<memory_resource>` <sup>17</sup>, `<optional>` <sup>17</sup>, [`<ratio>`](ratio.md) <sup>11</sup>, [`<scoped_allocator>`](scoped-allocator.md) <sup>11</sup>, [`<tuple>`](tuple.md) <sup>11</sup>, [`<type_traits>`](type-traits.md) <sup>11</sup>, [`<typeindex>`](typeindex.md) <sup>11</sup>, [`<utility>`](utility.md) `<variant>` <sup>17</sup> |
| [Ввод-вывод и форматирование](../text/string-and-i-o-formatting-modern-cpp.md) | [`<cinttypes>`](cinttypes.md)<sup>11</sup>, [`<cstdio>`](cstdio.md) , [`<filesystem>`](filesystem.md) <sup>17</sup>,,,,, [`<fstream>`](fstream.md) [`<iomanip>`](iomanip.md) [`<ios>`](ios.md) [`<iosfwd>`](iosfwd.md) [`<iostream>`](iostream.md) , [`<istream>`](istream.md) , [`<ostream>`](ostream.md) , [`<sstream>`](sstream.md) , [`<streambuf>`](streambuf.md) , [`<strstream>`](strstream.md) <sup>c</sup>, `<syncstream>` <sup>20</sup> |
| Iterators | [`<iterator>`](iterator.md) |
| Поддержка языков | [`<cfloat>`](cfloat.md), [`<climits>`](climits.md) , [`<codecvt>`](codecvt.md) <sup>11 a</sup>, `<compare>` <sup>20</sup>, `<contract>` <sup>20</sup>, `<coroutine>` <sup>20</sup>,,,,, [`<csetjmp>`](csetjmp.md) [`<csignal>`](csignal.md) [`<cstdarg>`](cstdarg.md) [`<cstddef>`](cstddef.md) [`<cstdint>`](cstdint.md) <sup>11</sup>, [`<cstdlib>`](cstdlib.md) , [`<exception>`](exception.md) , [`<initializer_list>`](initializer-list.md) <sup>11</sup>, [`<limits>`](limits.md) , [`<new>`](new.md) , [`<typeinfo>`](typeinfo.md) , `<version>` <sup>20</sup> |
| Локализация | [`<clocale>`](clocale.md), [`<codecvt>`](codecvt.md) <sup>11 a</sup>, [`<cvt/wbuffer>`](cvt-wbuffer.md) , [`<cvt/wstring>`](cvt-wstring.md) ,[`<locale>`](locale.md) |
| Математические и числовые значения | `<bit>`<sup>20</sup>, [`<cfenv>`](cfenv.md) <sup>11</sup>, [`<cmath>`](cmath.md) , [`<complex>`](complex.md) , [`<cstdlib>`](cstdlib.md) , [`<limits>`](limits.md) , [`<numeric>`](numeric.md) , [`<random>`](random.md) <sup>11</sup>, [`<ratio>`](ratio.md) <sup>11</sup>,[`<valarray>`](valarray.md) |
| [Управление памятью](../cpp/smart-pointers-modern-cpp.md) | [`<allocators>`](allocators-header.md), [`<memory>`](memory.md) , `<memory_resource>` <sup>17</sup>, [`<new>`](new.md) [`<scoped_allocator>`](scoped-allocator.md) <sup>11</sup> |
| Многопоточность | [`<atomic>`](atomic.md)<sup>11</sup>, [`<condition_variable>`](condition-variable.md) <sup>11</sup>, [`<future>`](future.md) <sup>11</sup>, [`<mutex>`](mutex.md) <sup>11</sup>, [`<shared_mutex>`](shared-mutex.md) <sup>14</sup>, [`<thread>`](thread.md) <sup>11</sup> |
| Диапазоны | `<ranges>`<sup>20</sup> |
| Регулярные выражения | [`<regex>`](regex.md)<sup>стр</sup> |
| Строки и символьные данные | [`<charconv>`](charconv.md)<sup>17</sup>, [`<cctype>`](cctype.md) , [`<cstdlib>`](cstdlib.md) , [`<cstring>`](cstring.md) , [`<cuchar>`](cuchar.md) <sup>11</sup>, [`<cwchar>`](cwchar.md) , [`<cwctype>`](cwctype.md) , [`<regex>`](regex.md) <sup>11</sup>, [`<string>`](string.md) , [`<string_view>`](string-view.md) <sup>17</sup> |
| Время | [`<chrono>`](chrono.md)<sup>11</sup>, [`<ctime>`](ctime.md) |

<sup>11</sup> добавлена в стандарт c++ 11.
<sup>14</sup> Добавлено в стандарт c++ 14.
<sup>17</sup> добавлен в стандарт c++ 17.
<sup>20</sup> Добавлено в черновике c++ 20 Standard.
<sup>нерекомендуемый в</sup> стандарте c++ 17.
<sup>b</sup> удалено в черновике c++ 20 Standard.
в языке <sup>c</sup> не рекомендуется использовать в стандарте c++ 98.

::: moniker-end

::: moniker range="msvc-140"

|Категория|Заголовки|
|-|-|
|[Алгоритмы](./algorithms.md)|[`<algorithm>`](algorithm.md)|
|Оболочки библиотек C|[`<cassert>`](cassert.md), [`<cctype>`](cctype.md), [`<cerrno>`](cerrno.md), [`<cfenv>`](cfenv.md), [`<cfloat>`](cfloat.md), [`<cinttypes>`](cinttypes.md), [`<ciso646>`](ciso646.md), [`<climits>`](climits.md), [`<clocale>`](clocale.md), [`<cmath>`](cmath.md), [`<csetjmp>`](csetjmp.md), [`<csignal>`](csignal.md), [`<cstdarg>`](cstdarg.md), [`<cstdbool>`](cstdbool.md), [`<cstddef>`](cstddef.md), [`<cstdint>`](cstdint.md), [`<cstdio>`](cstdio.md), [`<cstdlib>`](cstdlib.md), [`<cstring>`](cstring.md), [`<ctgmath>`](ctgmath.md), [`<ctime>`](ctime.md), [`<cwchar>`](cwchar.md), [`<cwctype>`](cwctype.md)|
|[Контейнеры](./stl-containers.md)||
|Контейнеры последовательности|[`<array>`](array.md), [`<deque>`](deque.md), [`<forward_list>`](forward-list.md), [`<list>`](list.md), [`<vector>`](vector.md)|
|Упорядоченные ассоциативные контейнеры| [`<map>`](map.md), [`<set>`](set.md)|
|Неупорядоченные ассоциативные контейнеры|[`<unordered_map>`](unordered-map.md), [`<unordered_set>`](unordered-set.md)|
|Контейнеры адаптера|[`<queue>`](queue.md), [`<stack>`](stack.md)|
|[Ошибки и обработка исключений](../cpp/errors-and-exception-handling-modern-cpp.md)|[`<exception>`](exception.md), [`<stdexcept>`](stdexcept.md), [`<system_error>`](system-error.md)|
|[Ввод-вывод и форматирование](../text/string-and-i-o-formatting-modern-cpp.md)|[`<filesystem>`](filesystem.md), [`<fstream>`](fstream.md), [`<iomanip>`](iomanip.md), [`<ios>`](ios.md), [`<iosfwd>`](iosfwd.md), [`<iostream>`](iostream.md), [`<istream>`](istream.md), [`<ostream>`](ostream.md), [`<sstream>`](sstream.md), [`<streambuf>`](streambuf.md), [`<strstream>`](strstream.md)|
|Iterators|[`<iterator>`](iterator.md)|
|Локализация|[`<codecvt>`](codecvt.md), [`<cvt/wbuffer>`](cvt-wbuffer.md), [`<cvt/wstring>`](cvt-wstring.md), [`<locale>`](locale.md)|
|Математические и числовые значения|[`<complex>`](complex.md), [`<limits>`](limits.md), [`<numeric>`](numeric.md), [`<random>`](random.md), [`<ratio>`](ratio.md), [`<valarray>`](valarray.md)|
|[Управление памятью](../cpp/smart-pointers-modern-cpp.md)|[`<allocators>`](allocators-header.md), [`<memory>`](memory.md), [`<new>`](new.md), [`<scoped_allocator>`](scoped-allocator.md)|
|Многопоточность|[`<atomic>`](atomic.md), [`<condition_variable>`](condition-variable.md), [`<future>`](future.md), [`<mutex>`](mutex.md), [`<shared_mutex>`](shared-mutex.md), [`<thread>`](thread.md)|
|Другие служебные программы|[`<bitset>`](bitset.md), [`<chrono>`](chrono.md), [`<functional>`](functional.md), [`<initializer_list>`](initializer-list.md), [`<tuple>`](tuple.md), [`<type_traits>`](type-traits.md), [`<typeinfo>`](typeinfo.md), [`<typeindex>`](typeindex.md), [`<utility>`](utility.md)|
|Строки и символьные данные|[`<regex>`](regex.md), [`<string>`](string.md), [`<string_view>`](string-view.md)|

::: moniker-end

## <a name="see-also"></a>См. также раздел

[Использование заголовков библиотеки C++](using-cpp-library-headers.md)\
[Стандартная библиотека C++](cpp-standard-library-reference.md)
