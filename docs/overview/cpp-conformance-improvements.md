---
title: Улучшения соответствия C++ в Visual Studio 2019
description: Microsoft C++ в Visual Studio развивается в сторону полного соответствия стандарту языка C++20.
ms.date: 03/10/2021
ms.technology: cpp-language
ms.openlocfilehash: 3b78551ee4d8590403cdfaf77c267eef0ab6d811
ms.sourcegitcommit: f8ba5db09d05683b24c58505f0e57c21f85545dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/11/2021
ms.locfileid: "103087263"
---
# <a name="c-conformance-improvements-behavior-changes-and-bug-fixes-in-visual-studio-2019"></a>Улучшения соответствия C++, изменения в поведении и исправления ошибок в Visual Studio 2019

В каждом выпуске Microsoft C/C++ в Visual Studio (MSVC) добавляются улучшения соответствия и исправления ошибок. В этой статье перечислены улучшения в разбивке по основным выпускам и версиям системы. Чтобы перейти непосредственно к изменениям в конкретной версии, используйте список, приведенный ниже в **этой статье**.

В этом документе перечислены изменения в Visual Studio 2019. Инструкции по изменениям в Visual Studio 2017 см. в статье [Улучшения соответствия C++ в Visual studio 2017](cpp-conformance-improvements-2017.md). Полный список предыдущих улучшений соответствия см. в статье [Новые возможности Visual C++ 2003–2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

## <a name="conformance-improvements-in-visual-studio-2019-rtw-version-160"></a><a name="improvements_160"></a> Улучшения соответствия в Visual Studio 2019 RTW (версия 16.0)

Visual Studio 2019 RTW содержит следующие улучшения соответствия, исправления ошибок и изменения в поведении в компиляторе Microsoft C++.

> [!NOTE]
> Возможности C++20 будут доступны в режиме **`/std:c++latest`** до завершения внедрения C++20 для компилятора и IntelliSense. К этому времени мы предоставим режим компилятора **`/std:c++20`** .

### <a name="improved-modules-support-for-templates-and-error-detection"></a>Улучшенные модули поддерживают шаблоны и обнаружение ошибок

Модули теперь официально соответствуют стандарту C ++20. Улучшенная поддержка была добавлена в Visual Studio 2017 версии 15.9. Дополнительные сведения см. в разделе [Улучшенная поддержка шаблонов и обнаружение ошибок в модулях C++ MSVC 2017 версии 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/).

### <a name="modified-specification-of-aggregate-type"></a>Изменена спецификация типа агрегата

Спецификация типа агрегата была изменена в C++20 (см. раздел [Запрет агрегатов с объявленными пользователем конструкторами](https://wg21.link/p1008r1)). В Visual Studio 2019 в **`/std:c++latest`** класс с любым конструктором, объявленным пользователем (например, конструктор, объявленный `= default` или `= delete`), не является агрегатом. Ранее только предоставленные пользователем конструкторы запрещали классу быть агрегатом. Это изменение накладывает дополнительные ограничения на способ инициализации таких типов.

Следующий код компилируется без ошибок в Visual Studio 2017, но вызывает ошибки C2280 и C2440 в Visual Studio 2019 в **`/std:c++latest`** :

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>Частичная поддержка для `operator <=>`

[P0515R3](https://wg21.link/p0515r3) C++20 вводит трехсторонний оператор сравнения `<=>`, также известный как "оператор — космический корабль". Visual Studio 2019 в режиме **`/std:c++latest`** вводит частичную поддержку оператора, вызывая ошибки синтаксиса, который сейчас запрещен. Например, следующий код компилируется без ошибок в Visual Studio 2017, но вызывает различные ошибки в Visual Studio 2019 в **`/std:c++latest`** :

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

Чтобы избежать этих ошибок, добавьте символ пробела в строку, вызывающую ошибку, перед последней скобкой: `U<&S::operator<= > u;`.

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>Ссылки на типы с несоответствием cv-квалификаторов

Ранее MSVC допускал прямую привязку ссылки из типа с несоответствием cv-квалификаторов ниже верхнего уровня. Это делало возможным изменение предположительно постоянных данных, на которые указывала ссылка. Теперь компилятор создает временные данные согласно требованиям стандарта. В Visual Studio 2017 следующий код компилировался без предупреждений. В Visual Studio 2019 компилятор вызывает предупреждение C4172:

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172 <func:#1 "?PData@X@@QBEABQBXXZ"> returning address of local variable or temporary
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>`reinterpret_cast` из перегруженной функции

Аргумент **`reinterpret_cast`** не входит в число контекстов, в которых разрешен адрес перегруженной функции. Следующий код компилируется без ошибок в Visual Studio 2017, но в Visual Studio 2019 вызывает ошибку C2440:

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f); // C2440: cannot convert from 'overloaded-function' to 'fp'
}
```

Чтобы избежать этой ошибки, используйте допустимые приведения для этого сценария:

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>Замыкания лямбда-выражений

В C++14 типы замыкания лямбда-выражений не являются литералами. Основное следствие этого правила заключается в том, что лямбда-выражение не может назначаться переменной **`constexpr`** . Следующий код компилируется без ошибок в Visual Studio 2017, но в Visual Studio 2019 вызывает ошибку C2127:

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 'l': illegal initialization of 'constexpr' entity with a non-constant expression
}
```

Чтобы избежать этой ошибки, удалите квалификатор **`constexpr`** или измените режим совместимости на **`/std:c++17`** .

### <a name="stdcreate_directory-failure-codes"></a>Коды сбоя `std::create_directory`

Безусловная реализация [P1164](https://wg21.link/p1164r1) из C ++ 20. Это изменяет `std::create_directory`, чтобы проверить, был ли целевой объект уже каталогом со сбоем. Ранее все ошибки типа ERROR_ALREADY_EXISTS были включены в коды "Выполнено успешно, но каталог не создан".

### `operator<<(std::ostream, nullptr_t)`

Для [LWG 2221](https://cplusplus.github.io/LWG/issue2221) добавлен `operator<<(std::ostream, nullptr_t)` для записи **`nullptr`** в потоки.

### <a name="more-parallel-algorithms"></a>Другие параллельные алгоритмы

Новые параллельные версии `is_sorted`, `is_sorted_until`, `is_partitioned`, `set_difference`, `set_intersection`, `is_heap` и `is_heap_until`.

### <a name="atomic-initialization"></a>Атомарная инициализация

[P0883 "Устранение атомарной инициализации"](https://wg21.link/p0883r1) меняет `std::atomic`, чтобы инициализировать `T` по значению, а не по умолчанию. Это исправление включается при использовании Clang/LLVM со стандартной библиотекой Майкрософт. Сейчас оно отключено для компилятора Microsoft C++ в качестве обходного решения для ошибки с обработкой **`constexpr`** .

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` и `remove_cvref_t`

Реализация признаков типа `remove_cvref` и `remove_cvref_t` из [P0550](https://wg21.link/p0550r2). Они удаляют ссылочность и cv-квалификацию из типа без ограничения функций и массивов до указателей (в отличие от `std::decay` и `std::decay_t`).

### <a name="feature-test-macros"></a>Макросы тестирования функций

[P0941R2 — макросы тестирования функций](https://wg21.link/p0941r2) завершены с поддержкой `__has_cpp_attribute`. Макросы тестирования функций поддерживаются во всех стандартных режимах.

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>Запрет агрегирования с объявленными пользователем конструкторами

C++20 [P1008R1 — запрет агрегирования с объявленными пользователем конструкторами](https://wg21.link/p1008r1) завершен.

### <a name="reinterpret_cast-in-a-constexpr-function"></a>`reinterpret_cast` в функции `constexpr`

**`reinterpret_cast`** нельзя использовать в функции **`constexpr`** . Компилятор Microsoft C++ раньше отклонял **`reinterpret_cast`** , только если он использовался в контексте **`constexpr`** . В Visual Studio 2019 во всех стандартных режимах языка компилятор правильно выполняет диагностику **`reinterpret_cast`** в определении функции **`constexpr`** . Следующий код теперь вызывает ошибку C3615:

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i); // C3615: constexpr function 'f' cannot result in a constant expression
}
```

Чтобы избежать этой ошибки, удалите модификатор **`constexpr`** из объявления функции.

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>Правильная диагностика для конструктора диапазонов basic_string

В Visual Studio 2019 конструктор диапазонов `basic_string` больше не подавляет диагностику компилятора с помощью **`static_cast`** . Приведенный ниже код компилируется без предупреждений в Visual Studio 2017, несмотря на возможную потерю данных при преобразовании из **`wchar_t`** в **`char`** при инициализации `out`:

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end()); // VS2019 C4244: 'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data.
```

Visual Studio 2019 правильно выдает предупреждение C4244. Чтобы избежать этого предупреждения, можно инициализировать `std::string`, как показано в следующем примере:

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>Неправильные вызовы `+=` и `-=` в `/clr` или `/ZW` теперь корректно обнаруживаются

В Visual Studio 2017 появилась ошибка, из-за которой компилятор пропускал ошибки без предупреждений и не создавал код для недопустимых вызовов **`+=`** и **`-=`** в **`/clr`** или **`/ZW`** . Следующий код компилируется без ошибок в Visual Studio 2017, но в Visual Studio 2019 корректно вызывает ошибку C2845:

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // in VS2019 C2845: 'System::String ^': pointer arithmetic not allowed on this type.
}
```

Чтобы избежать данной ошибки в этом примере, используйте оператор **`+=`** с методом `ToString()`: `s += E::e.ToString();`.

### <a name="initializers-for-inline-static-data-members"></a>Инициализаторы для встроенных статических элементов данных

Доступ к недопустимым элементам в инициализаторах **`inline`** и **`static constexpr`** теперь определяется правильно. Следующий пример компилируется без ошибок в Visual Studio 2017, но в Visual Studio 2019 в режиме **`/std:c++17`** вызывает ошибку C2248:

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // VS2019 C2248: cannot access private member declared in class 'X'.
};
```

Чтобы избежать этой ошибки, объявите элемент `X::c` как защищенный:

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>Возобновлено использование C4800

В MSVC ранее создавалось предупреждение о производительности C4800 для неявных преобразований в **`bool`** . Это предупреждение было слишком назойливым и его нельзя было подавить, в результате чего мы решили удалить его в Visual Studio 2017. Но за время работы Visual Studio 2017 мы получили множество отзывов о полезности этого предупреждения. В выпуске Visual Studio 2019 мы возвращаем предупреждение C4800, тщательно настроив его и дополнив пояснительным предупреждением C4165. Оба этих предупреждения легко подавить: либо с помощью явного приведения, либо путем сравнения с 0 соответствующего типа. C4800 — это по умолчанию отключенное предупреждение уровня 4, а C4165 — это по умолчанию отключенное предупреждение уровня 3. Их можно обнаружить с помощью параметра компилятора **`/Wall`** .

В следующем примере возникают предупреждения C4800 и C4165 в режиме **`/Wall`** :

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

Чтобы избежать предупреждений в предыдущем примере, можно написать следующий код:

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>Функция-член локального класса не имеет тела

В Visual Studio 2017 предупреждение C4822 возникает только в том случае, если явно задан параметр компилятора **`/w14822`** . Оно не отображается, если задан параметр **`/Wall`** . В Visual Studio 2019 C4822 является предупреждением, отключенным по умолчанию, которое можно обнаружить в **`/Wall`** без явного задания **`/w14822`** .

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822: Local class member function doesn't have a body
        };
}
```

### <a name="function-template-bodies-containing-if-constexpr-statements"></a>Тела шаблонов функций, содержащие операторы `if constexpr`

Для тел шаблонов функций, содержащих операторы **`if constexpr`** , включены некоторые проверки [`/permissive-`](../build/reference/permissive-standards-conformance.md), связанные с синтаксическим анализом. Например, в Visual Studio 2017 следующий код вызывает ошибку C7510 только в том случае, если параметр **`/permissive-`** не задан. В Visual Studio 2019 тот же код вызывает ошибки независимо от того, задан ли параметр **`/permissive-`** :

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510: 'Type': use of dependent type name must be prefixed with 'typename'

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

Чтобы избежать этой ошибки, добавьте ключевое слово **`typename`** в объявление `a`: `typename T::Type a;`.

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>Встроенный код сборки не поддерживается в лямбда-выражении

Недавно команда Microsoft C++ узнала о проблеме безопасности, из-за которой использование встроенного ассемблера в лямбда-выражении могло привести к повреждению `ebp` (регистра обратного адреса) во время выполнения. Злоумышленник может воспользоваться этим сценарием. Встроенный ассемблер поддерживается только на 32-разрядной (x86) платформе и плохо взаимодействует с остальными функциями компилятора. Учитывая эти факты и характер проблемы, самым надежным решением было запретить встроенный ассемблер в лямбда-выражении.

Мы нашли "в реальной жизни" только один вариант применения встроенного ассемблера в лямбда-выражении, а именно получение обратного адреса. В этом сценарии можно получить обратный адрес на всех платформах, просто используя `_ReturnAddress()` в компиляторе.

Следующий код вызывает ошибку C7552 как в Visual Studio 2017 версии 15.9, так и в Visual Studio 2019:

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {  // C7552: inline assembler is not supported in a lambda

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

Чтобы избежать этой ошибки, переместите код сборки в именованную функцию, как показано в следующем примере:

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>Отладка перечислителя и `std::move_iterator`

Функция отладки итераторов теперь может правильно развертывать `std::move_iterator`. Например, `std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` теперь использует быстрый путь `memcpy`.

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>Исправления для принудительного применения ключевого слова \<xkeycheck.h>

Исправлено принудительное применение стандартной библиотеки в \<xkeycheck.h> для макросов, заменяющих ключевое слово. Теперь библиотека выдает ключевое слово фактически обнаруженной проблемы вместо сообщения общего характера. Также поддерживаются ключевые слова C ++ 20, а IntelliSense не сообщает, что случайные ключевые слова являются макросами.

### <a name="allocator-types-no-longer-deprecated"></a>Типы распределителей теперь не считаются нерекомендуемыми

`std::allocator<void>`, `std::allocator::size_type` и `std::allocator::difference_type` теперь не считаются нерекомендуемыми.

### <a name="correct-warning-for-narrowing-string-conversions"></a>Правильное предупреждение для сужающих преобразований строк

Из `std::string` удален лишний вызов **`static_cast`** , который не соответствовал стандарту и случайно подавлял предупреждения о сужении C4244. При попытках вызова `std::string::string(const wchar_t*, const wchar_t*)` теперь должным образом выдается предупреждение C4244 о сужении `wchar_t` до `char`.

### <a name="various-fixes-for-filesystem-correctness"></a>Различные исправления для правильности \<filesystem>

- Исправлен сбой `std::filesystem::last_write_time` при попытке изменить последнее время записи каталога.
- Теперь конструктор `std::filesystem::directory_entry` сохраняет результат сбоя, а не создает исключение, если задан несуществующий целевой путь.
- Версия `std::filesystem::create_directory` с двумя параметрами была изменена для вызова версии с одним параметром, так как базовая функция `CreateDirectoryExW` использовала бы `copy_symlink`, если бы `existing_p` был символьной ссылкой.
- `std::filesystem::directory_iterator` больше не завершается сбоем при обнаружении неработающей символьной ссылки.
- `std::filesystem::space` теперь принимает относительные пути.
- `std::filesystem::path::lexically_relative` больше не путается из-за конечных знаков косой черты, как сообщалось в [LWG 3096](https://cplusplus.github.io/LWG/issue3096).
- Найдено обходное решение для проблемы, при которой `CreateSymbolicLinkW` отклонял пути с символами косой черты в `std::filesystem::create_symlink`.
- Найдено обходное решение для проблемы с функцией `delete` удаления режима POSIX, которая существовала в Windows 10 LTSB 1609, но в действительности не удаляла файлы.
- Конструкторы копий `std::boyer_moore_searcher` и `std::boyer_moore_horspool_searcher`, а также операторы присваивания копий теперь действительно копируют элементы.

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Параллельные алгоритмы в Windows 8 и более поздних версий

Библиотека параллельных алгоритмов теперь правильно использует реальное семейство `WaitOnAddress` в Windows 8 и более поздних версий вместо того, чтобы всегда использовать Windows 7 и более ранние фиктивные версии.

### <a name="stdsystem_categorymessage-whitespace"></a>Пробелы в `std::system_category::message()`

`std::system_category::message()` теперь удаляет конечный пробел из возвращенного сообщения.

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>Деление на ноль в `std::linear_congruential_engine`

Некоторые условия, приводящие к тому, что `std::linear_congruential_engine` вызывает деление на ноль, были исправлены.

### <a name="fixes-for-iterator-unwrapping"></a>Исправления для распаковывания итератора

Некоторые механизмы распаковывания итератора впервые были представлены для интеграции пользователя и программиста в Visual Studio 2017 версии 15.8. Это описано в записи блога команды разработчиков C++ [о функциях STL и исправлениях ошибок в VS 2017 15.8](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/). Этот механизм больше не выполняет извлечение итераторов из оболочки, основанных на итераторах стандартной библиотеки. Например, пользователь, который происходит от `std::vector<int>::iterator` и пытается настроить поведение, теперь получает настроенное поведение при вызове алгоритмов стандартной библиотеки, а не поведение указателя.

Функция неупорядоченного контейнера `reserve` теперь действительно резервирует N элементов, как описано в [LWG 2156](https://cplusplus.github.io/LWG/issue2156).

### <a name="time-handling"></a>Обработка времени

- Ранее некоторые значения времени, которые передавались в библиотеку параллелизма, вызывали переполнение, например `condition_variable::wait_for(seconds::max())`. Эти исправленные переполнения ранее изменяли поведение псевдослучайным образом в течение 29-дневного цикла (когда значение миллисекунд uint32_t принималось с переполнением в базовые API Win32).

- Заголовок \<ctime> теперь правильно объявляет `timespec` и `timespec_get` в пространстве имен `std`, а также в глобальном пространстве имен.

### <a name="various-fixes-for-containers"></a>Различные исправления для контейнеров

- Многие функции внутреннего контейнера стандартной библиотеки получили статус `private` для повышения эффективности IntelliSense. В последующих выпусках MSVC ожидаются дополнительные исправления, которые позволят объявлять элементы в качестве `private`.

- Мы устранили проблемы с корректностью безопасности исключений, которые приводили к повреждению контейнеров на основе узлов, таких как `list`, `map` и `unordered_map`. Во время операции переназначения `propagate_on_container_copy_assignment` или `propagate_on_container_move_assignment` мы освобождаем граничный узел контейнера с помощью старого распределителя, выполняем назначение POCCA/POCMA в старом распределителе, а затем пробуем получить граничный узел из нового распределителя. Если это распределение не удавалось, контейнер становился поврежденным. Он даже не мог быть уничтожен, так как обладание граничным узлом является инвариантной жесткой структурой данных. Этот код был исправлен так, чтобы создавать граничный узел, используя распределитель исходного контейнера перед удалением имеющегося граничного узла.

- Контейнеры были исправлены и всегда копируют, перемещают или меняют распределители согласно `propagate_on_container_copy_assignment`, `propagate_on_container_move_assignment` и `propagate_on_container_swap` даже для распределителей, объявленных `is_always_equal`.

- Добавлены перегрузки для компонентных функций слияния и извлечения контейнеров, которые принимают контейнеры rvalue. Дополнительные сведения см. в документе [P0083 "Соединение карт и наборов"](https://wg21.link/p0083r3).

### <a name="stdbasic_istreamread-processing-of-rn-n"></a>Обработка `\r\n`` =>`\n` в `std::basic_istream::read`

Выражение `std::basic_istream::read` исправлено так, чтобы временные данные не записывались в части предоставленного буфера при обработке преобразования `\r\n` в `\n`. Это изменение несколько нивелирует преимущество в производительности, достигнутое в Visual Studio 2017 15.8 для операций чтения размером более 4 КБ. Но при этом сохраняется повышенная эффективность за счет избавления от трех виртуальных вызовов на каждый символ.

### <a name="stdbitset-constructor"></a>Конструктор `std::bitset`

Конструктор `std::bitset` теперь не считывает единицы и нули в обратном порядке для больших наборов битов.

### <a name="stdpairoperator-regression"></a>Регрессия в `std::pair::operator=`

Исправлена регрессия в операторе присваивания `std::pair`, которая появилась при реализации [LWG 2729 "Отсутствует SFINAE для `std::pair::operator=`"; ](https://cplusplus.github.io/LWG/issue2729). Теперь снова правильно принимаются типы, которые можно преобразовывать в `std::pair`.

### <a name="non-deduced-contexts-for-add_const_t"></a>Невыводимые контексты для `add_const_t`

Исправлена ошибка признаков дополнительного типа, где `add_const_t` и связанные функции должны быть невыводимым контекстом. Другими словами, `add_const_t` должен быть псевдонимом для `typename add_const<T>::type`, а не `const T`.

## <a name="conformance-improvements-in-161"></a><a name="improvements_161"></a> Улучшения соответствия C++ в 16.1

### <a name="char8_t"></a>char8_t

[P0482r6](https://wg21.link/p0482r6). C ++ 20 добавляет новый тип символа, который используется для представления частей кода UTF-8. Строковые литералы `u8` в C++20 имеют тип `const char8_t[N]`, а не `const char[N]`, как было раньше. Аналогичные изменения предложены для стандарта C в [N2231](https://wg14.link/n2231). Рекомендации по обеспечению обратной совместимости для **`char8_t`** приведены в [P1423r3](https://wg21.link/p1423r3). Компилятор Microsoft C++ добавляет поддержку типа **`char8_t`** в Visual Studio 2019 версии 16.1, если вы укажете параметр компилятора **`/Zc:char8_t`** . В будущем он будет поддерживаться с [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md), который можно отменить, чтобы восстановить поведение C++17 с помощью **`/Zc:char8_t-`** . Компилятор EDG, лежащий в основе IntelliSense, пока не поддерживает эту возможность. Вы можете видеть ложные ошибки для IntelliSense, которые не влияют на фактическую компиляцию.

#### <a name="example"></a>Пример

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>Метафункция `std::type_identity` и объект функции `std::identity`

[P0887R1 type_identity](https://wg21.link/p0887r1). Устаревшее расширение класса шаблонов `std::identity` было удалено и заменено на метафункцию `std::type_identity` и объект функции `std::identity` в C++20. Они доступны только в [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md).

В следующем примере становится устаревшим предупреждение C4996 для `std::identity` (определено в \<type_traits>) в Visual Studio 2017:

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

В следующем примере показано, как использовать новый `std::identity` (определено в \<functional>) вместе с новым `std::type_identity`:

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>Проверка синтаксиса для универсальных лямбда-выражений

Новый обработчик лямбда-выражений включает некоторые проверки синтаксиса режима совместимости в универсальных лямбда-выражениях в [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) или в другом режиме языка с **`/experimental:newLambdaProcessor`** .

В Visual Studio 2017 этот код компилируется без предупреждений, но в Visual Studio 2019 вызывает ошибку C2760:

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t; // C2760 syntax error: unexpected token 'identifier', expected ';'
    };
}
```

В следующем примере показан правильный синтаксис, который теперь применяется компилятором принудительно:

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>Зависящий от аргументов поиск вызовов функций

[P0846R0](https://wg21.link/p0846r0) (C++20). Улучшена возможность поиска шаблонов функций с помощью поиска, учитывающего аргументы, выражений вызова функции с явно заданными аргументами шаблона. Требует использования **`/std:c++latest`** .

### <a name="designated-initialization"></a>Назначенная инициализация

[P0329R4](https://wg21.link/p0329r4) (C++20). *Назначенная инициализация* позволяет выбирать определенные элементы в агрегатной инициализации с помощью синтаксиса `Type t { .member = expr }`. Требует использования **`/std:c++latest`** .

### <a name="new-and-updated-standard-library-functions-c20"></a>Новые и обновленные функции стандартной библиотеки (C++20)

- `starts_with()` и `ends_with()` для `basic_string` и `basic_string_view`.
- `contains()` для ассоциативных контейнеров;
- `remove()`, `remove_if()` и `unique()` для `list` и `forward_list` теперь возвращают `size_type`;
- `shift_left()`и `shift_right()` добавлены в \<algorithm>.

## <a name="conformance-improvements-in-162"></a><a name="improvements_162"></a> Улучшения соответствия C++ в 16.2

### <a name="noexcept-constexpr-functions"></a>Функции `noexcept` `constexpr`

Функции **`constexpr`** больше не считаются **`noexcept`** по умолчанию при использовании в константном выражении. Это изменение в поведении обусловлено разрешением Основной рабочей группы (Core Working Group, CWG) [1351](https://wg21.link/cwg1351) и включено в [`/permissive-`](../build/reference/permissive-standards-conformance.md). Следующий пример компилируется в Visual Studio 2019 версии 16.1 и более ранних версиях, но вызывает C2338 в Visual Studio 2019 версии 16.2:

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

Чтобы устранить эту ошибку, добавьте выражение **`noexcept`** в объявление функции:

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>Двоичные выражения с различными типами перечисления

В C++20 не рекомендуется использовать обычные арифметические преобразования к операндам, где:

- один операнд имеет тип перечисления, а

- другой — другой тип перечисления или числовой тип с плавающей запятой.

Дополнительные сведения о P1120R0 см. [здесь](https://wg21.link/p1120r0).

В Visual Studio 2019 версии 16.2 и более поздних в следующем примере кода создается предупреждение уровня 4, если включен параметр компилятора [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md):

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

Чтобы избежать этого предупреждения, используйте [`static_cast`](../cpp/static-cast-operator.md) для преобразования второго операнда:

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

При использовании двоичной операции между типом перечисления и типом с плавающей запятой теперь возникает предупреждение, если включен параметр компилятора [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md):

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

Чтобы избежать этого предупреждения, используйте [`static_cast`](../cpp/static-cast-operator.md) для преобразования второго операнда:

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>Равенство и реляционные сравнения массивов

Равенство и сравнение отношений между двумя операндами типа массива являются устаревшими в C++ 20 ([P1120R0](https://wg21.link/p1120r0)). Иными словами, операция сравнения двух массивов (несмотря на схожесть приоритета и экстента) теперь вызвает предупреждение. Начиная с Visual Studio 2019 версии 16.2, следующий код вызывает ошибку C5056, если включен параметр компилятора [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md):

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; } // warning C5056: operator '==': deprecated for array types
}
```

Чтобы избежать этого предупреждения, можно сравнить адреса первых элементов:

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

Чтобы определить, равно ли содержимое двух массивов, используйте функцию [`std::equal`](../standard-library/algorithm-functions.md#equal):

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>Результат определения оператора трехстороннего сравнения в `==` и `!=`

Определение оператора трехстороннего сравнения ( **`<=>`** ) больше не будет переписывать выражения, включающие **`==`** или **`!=`** , если оператор не помечен как **`= default`** ([P1185R2](https://wg21.link/p1185r2)). Следующий пример компилируется в Visual Studio 2019 RTW и версии 16.1, но вызывает C2678 в Visual Studio 2019 версии 16.2:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs; // error C2676
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs; // error C2676
}
```

Чтобы избежать этой ошибки, определите `operator==` или объявите оператор по умолчанию:

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>Улучшения стандартной библиотеки

- \<charconv> `to_chars()` с фиксированной или научной точностью. (Общая точность в настоящее время запланирована на версию 16.4.)
- [P0020R6](https://wg21.link/p0020r6): `atomic<float>`, `atomic<double>`, `atomic<long double>`
- [P0463R1](https://wg21.link/p0463r1): endian
- [P0482R6](https://wg21.link/p0482r6): поддержка библиотек для `char8_t`
- [P0600R1](https://wg21.link/p0600r1): `[[nodiscard]]` для STL, часть 1
- [P0653R2](https://wg21.link/p0653r2): `to_address()`
- [P0754R2](https://wg21.link/p0754r2): \<version>
- [P0771R1](https://wg21.link/p0771r1): `noexcept` для конструктора перемещения `std::function`

### <a name="const-comparators-for-associative-containers"></a>Константные блоки сравнения для ассоциативных контейнеров

Код для поиска и вставки в [`set`](../standard-library/set-class.md), [`map`](../standard-library/map-class.md), [`multiset`](../standard-library/multiset-class.md) и [`multimap`](../standard-library/multimap-class.md) объединен для уменьшения размера кода. Операции вставки теперь вызывают сравнение "меньше чем" для функтора сравнения **`const`** , как это делали ранее операции поиска. Следующий код компилируется в Visual Studio 2019 версии 16.1 и более ранних версиях, но вызывает C3848 в Visual Studio 2019 версии 16.2:

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

Чтобы избежать этой ошибки, используйте оператор сравнения **`const`** :

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

## <a name="conformance-improvements-in-visual-studio-2019-version-163"></a><a name="improvements_163"></a> Улучшения соответствия в Visual Studio 2019 версии 16.3

### <a name="stream-extraction-operators-for-char-removed"></a>Операторы извлечения потока для `char*` удалены

Операторы извлечения потока для указателей на символы были удалены и заменены операторами извлечения для массивов символов (в соответствии с [P0487R1](https://wg21.link/p0487r1)). WG21 считает удаленные перегрузки небезопасными. В режиме [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) следующий пример теперь вызывает ошибку C2679:

```cpp
// stream_extraction.cpp
// compile by using: cl /std:c++latest stream_extraction.cpp

#include <iostream>
#include <iomanip>

int main() {
    char x[42];
    char* p = x;
    std::cin >> std::setw(42);
    std::cin >> p;  // C2679: binary '>>': no operator found which takes a right-hand operand of type 'char *' (or there is no acceptable conversion)
}
```

Чтобы избежать этой ошибки, используйте оператор извлечения с переменной `char[]`:

```cpp
#include <iostream>
#include <iomanip>

int main() {
    char x[42];
    std::cin >> std::setw(42);
    std::cin >> x;  // OK
}
```

### <a name="new-keywords-requires-and-concept"></a>Новые ключевые слова `requires` и `concept`

В компилятор Microsoft C++ добавлены новые ключевые слова: **`requires`** и **`concept`** . Если вы попытаетесь использовать одно из них как идентификатор в режиме [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md), компилятор выдаст ошибку C2059: "синтаксическая ошибка".

### <a name="constructors-as-type-names-disallowed"></a>Конструкторы в качестве имен типов запрещены

В этом случае компилятор больше не считает имена конструкторов внедренными именами классов, когда они появляются в полном имени после псевдонима для специализации шаблона класса. Для объявления других сущностей ранее конструкторы использовались в качестве имени типа. Следующий пример приводит к возникновению ошибки C3646:

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{}; // C3646: 'TotalDuration': unknown override specifier
};
```

Чтобы избежать этой ошибки, объявите `TotalDuration`, как показано ниже:

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>Более строгая проверка функций `extern "C"`

Если функция **`extern "C"`** была объявлена в разных пространствах имен, предыдущие версии компилятора Microsoft C++ не проверяли, совместимы ли объявления. Начиная с Visual Studio 2019 версии 16.3 компилятор проверяет на совместимость. В режиме [`/permissive-`](../build/reference/permissive-standards-conformance.md) следующий код вызывает ошибки C2371 и C2733:

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
    // C2116: 'N::f': function parameter lists do not match between declarations
    // C2733: 'f': you cannot overload a function with 'extern "C"' linkage
```

Чтобы избежать ошибок в предыдущем примере, используйте **`bool`** вместо `BOOL` в обоих объявлениях `f`.

### <a name="standard-library-improvements"></a>Улучшения стандартной библиотеки

Нестандартные заголовки \<stdexcpt.h> и \<typeinfo.h> были удалены. Код, который содержит их, должен включать стандартные заголовки \<exception> и \<typeinfo> соответственно.

## <a name="conformance-improvements-in-visual-studio-2019-version-164"></a><a name="improvements_164"></a> Улучшения соответствия в Visual Studio 2019 версии 16.4

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>Улучшенное принудительное двухэтапное разрешение имени для идентификаторов qualified-id в `/permissive-`

Для двухэтапного поиска имен нужно, чтобы независимые имена, используемые в тексте шаблона, отображались в шаблоне во время определения. Ранее такие имена можно было встретить при создании экземпляра шаблона. Это изменение упрощает написание переносимого и соответствующего требованиям кода в MSVC с флагом [`/permissive-`](../build/reference/permissive-standards-conformance.md).

В Visual Studio 2019 версии 16.4 с установленным флагом **`/permissive-`** в следующем примере поступает сообщение об ошибке, так как при определении шаблона `f<T>` не отображается `N::f`:

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

Как правило, эту ошибку можно исправить, добавив недостающие заголовки или функции либо переменные с опережающим объявлением, как показано в следующем примере:

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>Неявное преобразование целочисленных константных выражений в пустой указатель

Компилятор MSVC теперь реализует [проблему CWG 903](https://wg21.link/cwg903) в режиме соответствия ( **`/permissive-`** ). Это правило запрещает неявное преобразование целочисленных константных выражений (за исключением целочисленного литерала 0) в константы пустого указателя. В следующем примере поступает сообщение об ошибке C2440 в режиме соответствия:

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

Для устранения этой ошибки используйте **`nullptr`** вместо **`false`** . Литерал 0 по-прежнему можно использовать:

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>Стандартные правила для типов целочисленных литералов

В режиме соответствия (реализуется с помощью [`/permissive-`](../build/reference/permissive-standards-conformance.md)) MSVC использует стандартные правила для типов целочисленных литералов. Десятичным литералам, которые были слишком велики для **`signed int`** , ранее присваивался тип **`unsigned int`** . Теперь таким литералам присваивается следующий самый большой тип целого числа **`signed`** , то есть **`long long`** . Кроме того, литералам с суффиксом ll, которые слишком велики для типа **`signed`** , присваивается тип **`unsigned long long`** .

Это изменение может привести к возникновению разных предупреждений системы диагностики и нестандартному поведению при выполнении арифметических операций над литералами.

В приведенном ниже примере показано новое поведение в Visual Studio 2019 версии 16.4. Переменная `i` теперь имеет тип **`unsigned int`** . Поэтому возникает предупреждение. Старшие разряды переменной `j` имеют значение 0.

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

В следующем примере показано, как сохранить прежнее поведение и избежать появления предупреждений и изменений в поведении во время выполнения:

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>Параметры функции, которые затемняют параметры шаблона

При использовании компилятора MSVC теперь происходит ошибка, когда параметр функции затемняет параметр шаблона:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

Чтобы устранить эту ошибку, измените имя одного из параметров:

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>Определяемые пользователем специализации признаков типов

В соответствии с подпунктом *meta.rqmts* стандартного определения при использовании компилятора MSVC теперь поступает сообщение об ошибке при обнаружении пользовательской специализации одного из указанных шаблонов `type_traits` в пространстве имен `std`. Если не указано иное, такие специализации приводят к неопределенному поведению. В следующем примере наблюдается неопределенное поведение, так как нарушено правило. Поэтому выполнение **`static_assert`** завершается с ошибкой C2338.

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

Чтобы избежать этой ошибки, определите структуру, которая наследуется от предпочитаемого `type_trait`, и используйте специализацию:

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>Изменения в предоставленных компилятором операторах сравнения

Компилятор MSVC теперь реализует следующие изменения для операторов сравнения ([P1630R1](https://wg21.link/p1630r1)), когда включен параметр [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md):

Компилятор больше не перезаписывает выражения с помощью `operator==`, если они относятся к типу возвращаемого значения, отличному от **`bool`** . Следующий код теперь вызывает ошибку C2088:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;  // C2088: '!=': illegal for struct
}
```

Чтобы избежать этой ошибки, необходимо явно определить необходимый оператор:

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

Компилятор больше не определяет оператор сравнения по умолчанию, если он является членом класса, подобного объединению. Следующий пример теперь вызывает ошибку C2120:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Чтобы избежать этой ошибки, определите текст для оператора:

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const { ... }
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

Компилятор больше не будет определять оператор сравнения по умолчанию, если класс содержит ссылочный элемент. Следующий код теперь вызывает ошибку C2120:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

Чтобы избежать этой ошибки, определите текст для оператора:

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-165"></a><a name="improvements_165"></a> Улучшения соответствия в Visual Studio 2019 версии 16.5

### <a name="explicit-specialization-declaration-without-an-initializer-isnt-a-definition"></a>Явное объявление специализации без инициализатора не является определением

В `/permissive-` MSVC теперь применяет стандартное правило о том, что явные объявления специализации без инициализаторов не являются определениями. Ранее объявление рассматривалось как определение с инициализатором по умолчанию. Этот эффект можно наблюдать во время компоновки, так как программа, зависимая от этого поведения, теперь может иметь неразрешенные символы. Теперь такой пример приводит к ошибке:

```cpp
template <typename> struct S {
    static int a;
};

// In permissive-, this declaration isn't a definition, and the program won't link.
template <> int S<char>::a;

int main() {
    return S<char>::a;
}
```

```Output
error LNK2019: unresolved external symbol "public: static int S<char>::a" (?a@?$S@D@@2HA) referenced in function _main at link time.
```

Чтобы устранить эту проблему, добавьте инициализатор:

```cpp
template <typename> struct S {
    static int a;
};

// Add an initializer for the declaration to be a definition.
template <> int S<char>::a{};

int main() {
    return S<char>::a;
}
```

### <a name="preprocessor-output-preserves-newlines"></a>Выходные данные препроцессора сохраняют символы новой строки

Экспериментальный препроцессор теперь сохраняет символы новой строки и пробелы при использовании **`/P`** или **`/E`** с **`/experimental:preprocessor`** .

Если рассматривать этот пример исходного кода:

```cpp
#define m()
line m(
) line
```

Предыдущие выходные данные **`/E`** имели вид:

```Output
line line
#line 2
```

Новые выходные данные **`/E`** имеют вид:

```Output
line
 line
```

### <a name="import-and-module-keywords-are-context-dependent"></a>Ключевые слова `import` и `module` являются контекстно-зависимыми.

Согласно [P1857R1](https://wg21.link/P1857R1), директивы препроцессора `import` и `module` имеют новые ограничения синтаксиса. Этот пример больше не компилируется:

```cpp
import // Invalid
m;     // error C2146: syntax error: missing ';' before identifier 'm'
```

Чтобы устранить эту проблему, оставьте import в той же строке:

```cpp
import m; // OK
```

### <a name="removal-of-stdweak_equality-and-stdstrong_equality"></a>Удаление `std::weak_equality` и `std::strong_equality`

Для объединения [P1959R0](https://wg21.link/P1959R0) требуется, чтобы компилятор удалил поведение и ссылки на типы `std::weak_equality` и `std::strong_equality`.

Код в этом примере больше не компилируется:

```cpp
#include <compare>

struct S {
    std::strong_equality operator<=>(const S&) const = default;
};

void f() {
    nullptr<=>nullptr;
    &f <=> &f;
    &S::operator<=> <=> &S::operator<=>;
}
```

Теперь этот пример приводит к следующим ошибкам:

```Output
error C2039: 'strong_equality': is not a member of 'std'
error C2143: syntax error: missing ';' before '<=>'
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C4430: missing type specifier - int assumed. Note: C++ does not support default-int
error C7546: binary operator '<=>': unsupported operand types 'nullptr' and 'nullptr'
error C7546: binary operator '<=>': unsupported operand types 'void (__cdecl *)(void)' and 'void (__cdecl *)(void)'
error C7546: binary operator '<=>': unsupported operand types 'int (__thiscall S::* )(const S &) const' and 'int (__thiscall S::* )(const S &) const'
```

Чтобы устранить эту проблему, внесите обновления, чтобы предпочитать встроенные реляционные операторы и заменить удаленные типы:

```cpp
#include <compare>

struct S {
    std::strong_ordering operator<=>(const S&) const = default; // prefer 'std::strong_ordering'
};

void f() {
    nullptr != nullptr; // use pre-existing builtin operator != or ==.
    &f != &f;
    &S::operator<=> != &S::operator<=>;
}
```

### <a name="tls-guard-changes"></a>Изменения TLS Guard

Ранее локальные по отношению к потоку переменные в библиотеках DLL не инициализировались должным образом. За исключением потока, загрузившего библиотеку DLL, они не инициализировались до их первого использования в потоках, существовавших до загрузки библиотеки DLL. Теперь эта ошибка устранена. Локальные по отношению к потоку переменные в подобной библиотеке DLL инициализируются непосредственно перед их первым использованием в таких потоках.

Это новое поведение проверки инициализации при использовании локальных по отношению к потоку переменных можно отключить с помощью параметра компилятора **`/Zc:tlsGuards-`** . Кроме того, можно добавить атрибут `[[msvc:no_tls_guard]]` к конкретным локальным по отношению к потоку переменным.

### <a name="better-diagnosis-of-call-to-deleted-functions"></a>Улучшенная диагностика вызовов удаленных функций

Наш компилятор был менее строгим по отношению к вызовам удаленных функций. Например, если вызовы происходили в контексте тела шаблона, вызов не диагностировался. Кроме того, если существовало несколько экземпляров вызовов удаленных функций, выводилась только одна запись диагностики. Теперь запись диагностики выводится для каждого из них.

Одно из последствий такого нового поведения может привести к небольшому критическому изменению: Код, вызвавший удаленную функцию, не будет диагностирован, если он никогда не требовался для создания кода. Теперь мы выполняем диагностику заранее.

В этом примере показан код, который теперь выдает ошибку:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s{};
};

U u{ 0 };
```

```Output
error C2280: 'S::S(void)': attempting to reference a deleted function
note: see declaration of 'S::S'
note: 'S::S(void)': function was explicitly deleted
```

Чтобы устранить эту проблему, удалите вызовы удаленных функций:

```cpp
struct S {
  S() = delete;
  S(int) { }
};

struct U {
  U() = delete;
  U(int i): s{ i } { }

  S s;  // Do not call the deleted ctor of 'S'.
};

U u{ 0 };
```

## <a name="conformance-improvements-in-visual-studio-2019-version-166"></a><a name="improvements_166"></a> Улучшения соответствия в Visual Studio 2019 версии 16.6

### <a name="standard-library-streams-reject-insertions-of-mis-encoded-character-types"></a>Потоки стандартной библиотеки отклоняют вставки типов символов с неправильным кодированием

Обычно в результате вставки **`wchar_t`** в `std::ostream` и вставки **`char16_t`** или **`char32_t`** в `std::ostream` или `std::wostream` выводится целочисленное значение. При вставке указателей на эти типы символов выводится значение указателя. Оба варианта не являются интуитивно понятными для программистов. Чаще всего ожидается, что стандартная библиотека перекодирует символ или строку символов, оканчивающуюся нулем, и выведет результат.

Предложение C++20 [P1423R3](https://wg21.link/p1423r3) реализует добавление перегрузок операторов вставки удаленных потоков для этих сочетаний потоков и символов или символьных указателей. В режиме **`/std:c++latest`** перегрузки делают эти вставки неправильно сформированными, а не вызывают то, что, скорее всего, является нежелательным поведением. При обнаружении компилятор выдает ошибку C2280. Вы можете определить макрос типа "escape hatch" `_HAS_STREAM_INSERTION_OPERATORS_DELETED_IN_CXX20` равным `1`, чтобы восстановить предыдущее поведение. (Предложение также реализует удаление операторов вставки потока для **`char8_t`** . Наша стандартная библиотека реализовывала аналогичные перегрузки, когда мы добавили поддержку **`char8_t`** , так что неправильное поведение для **`char8_t`** никогда не возникало.)

В следующем примере показано поведение при этом изменении:

```cpp
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << cw << ' ' << pw << '\n';
    std::cout << c16 << ' ' << p16 << '\n';
    std::cout << c32 << ' ' << p32 << '\n';
    std::wcout << c16 << ' ' << p16 << '\n';
    std::wcout << c32 << ' ' << p32 << '\n';
}
```

Теперь код вызывает следующие диагностические сообщения:

```Output
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,wchar_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<char,std::char_traits<char>> &std::<<<std::char_traits<char>>(std::basic_ostream<char,std::char_traits<char>> &,char32_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char16_t)': attempting to reference a deleted function
error C2280: 'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::<<<std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char32_t)': attempting to reference a deleted function
```

Вы можете вернуть старое поведение во всех режимах языка, преобразуя типы символов в **`unsigned int`** или типы указателей на символы в `const void*`:

```c++
#include <iostream>
int main() {
    const wchar_t cw = L'x', *pw = L"meow";
    const char16_t c16 = u'x', *p16 = u"meow";
    const char32_t c32 = U'x', *p32 = U"meow";
    std::cout << (unsigned)cw << ' ' << (const void*)pw << '\n'; // Outputs "120 0052B1C0"
    std::cout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::cout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
    std::wcout << (unsigned)c16 << ' ' << (const void*)p16 << '\n'; // Outputs "120 0052B1CC"
    std::wcout << (unsigned)c32 << ' ' << (const void*)p32 << '\n'; // Outputs "120 0052B1D8"
}
```

### <a name="changed-return-type-of-stdpow-for-stdcomplex"></a>Изменен тип возвращаемого значения `std::pow()` для `std::complex`

Ранее реализация MSVC правил повышения для типа возвращаемого значения шаблона функции `std::pow()` была неправильной. Например, раньше функция `pow(complex<float>, int)` возвращала тип `complex<float>`. Теперь она правильно возвращает тип `complex<double>`. Исправление было реализовано безусловно для всех режимов соответствия стандартам в Visual Studio 2019 версии 16.6.

Это изменение может привести к ошибкам компилятора. Например, ранее можно было умножить `pow(complex<float>, int)` на **`float`** . Поскольку `complex<T> operator*` ожидает аргументы одинакового типа, следующий пример теперь вызывает ошибку компилятора C2676:

```cpp
// pow_error.cpp
// compile by using: cl /EHsc /nologo /W4 pow_error.cpp
#include <complex>

int main() {
    std::complex<float> cf(2.0f, 0.0f);
    (void) (std::pow(cf, -1) * 3.0f);
}
```

```Output
pow_error.cpp(7): error C2676: binary '*': 'std::complex<double>' does not define this operator or a conversion to a type acceptable to the predefined operator
```

Существует множество способов исправления.

- Измените тип множимого **`float`** на **`double`** . Этот аргумент можно преобразовать непосредственно в `complex<double>`, чтобы обеспечить соответствие типу, возвращаемому `pow`.

- Ограничьте результат `pow` типом `complex<float>`, выполнив `complex<float>{pow(ARG, ARG)}`. Затем можно будет умножить этот результат на значение с типом **`float`** .

- Передайте в `pow` тип **`float`** , а не **`int`** . Эта операция может занять больше времени.

- В некоторых случаях можно вообще не использовать `pow`. Например, `pow(cf, -1)` можно заменить на операцию деления.

### <a name="switch-related-warnings-for-c"></a>Предупреждения в C, связанные с оператором switch

Начиная с Visual Studio 2019 версии 16.6, компилятор реализует некоторые существовавшие ранее предупреждения C++ для кода, скомпилированного как код C. На разных уровнях теперь включены следующие предупреждения: C4060, C4061, C4062, C4063, C4064, C4065, C4808 и C4809. Предупреждения C4065 и C4060 по умолчанию отключены в C.

Предупреждения активируются, если отсутствуют операторы **`case`** , не определены **`enum`** или определены неверные параметры типа **`bool`** (то есть тех, что содержат слишком много операторов case). Пример:

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
        default: break; // C4809: switch statement has redundant 'default' label;
                        // all possible 'case' labels are given
    }
}
```

Чтобы исправить этот код, удалите лишний оператор case **`default`** :

```c
#include <stdbool.h>

int main() {
    bool b = true;
    switch (b) {
        case true: break;
        case false: break;
    }
}
```

### <a name="unnamed-classes-in-typedef-declarations"></a>Безымянные классы в объявлениях `typedef`

Начиная с Visual Studio 2019 версии 16.6, поведение объявлений **`typedef`** ограничено для соответствия предложению [P1766R1](https://wg21.link/P1766R1). В этом обновлении безымянные классы в объявлении **`typedef`** могут содержать только следующие элементы:

- нестатические элементы данных;
- классов-элементов;
- перечисления элементов;
- инициализаторы элементов по умолчанию.

Те же ограничения применяются рекурсивно к каждому вложенному классу. Ограничение должно обеспечить простоту структур с именами **`typedef`** для связывания. Они должны быть достаточно простыми, чтобы не нужно было вычислять связывания до того, как компилятор дойдет до имени **`typedef`** для связывания.

Это изменение влияет на все режимы соответствия стандартам компилятора. В режиме по умолчанию ( **`/std:c++14`** ) и режиме **`/std:c++17`** компилятор выдает предупреждение C5208 для кода, который не соответствует стандартам. Если указан параметр **`/permissive-`** , компилятор выдает предупреждение C5208 как ошибку в режиме **`/std:c++14`** , а в режиме **`/std:c++17`** выдает ошибку C7626. Компилятор выдает ошибку C7626 для кода, не соответствующего требованиям, если указан параметр **`/std:c++latest`** .

В приведенном ниже примере показаны конструкции, которые теперь нельзя использовать в безымянных структурах. В зависимости от указанного режима соответствия стандартам, выдаются ошибки или предупреждения C5208 или C7626:

```cpp
struct B { };
typedef struct : B { // inheriting from 'B'; ill-formed
    void f(); // ill-formed
    static int i; // ill-formed
    struct U {
        void f(); // nested class has non-data member; ill-formed
    };
    int j = 10; // default member initializer; ill-formed
} S;
```

Приведенный выше код можно исправить, присвоив безымянному классу имя:

```cpp
struct B { };
typedef struct S_ : B {
    void f();
    static int i;
    struct U {
        void f();
    };
    int j = 10;
} S;
```

### <a name="default-argument-import-in-ccli"></a>Импорт аргументов по умолчанию в C++/CLI

Растущее число интерфейсов API имеет в .NET Core аргументы по умолчанию. Вот почему теперь поддерживается импорт аргументов по умолчанию в C++/CLI. Это изменение может нарушить работу существующего кода, в котором объявлено несколько перегрузок, как показано в следующем примере:

```cpp
public class R {
    public void Func(string s) {}   // overload 1
    public void Func(string s, string s2 = "") {} // overload 2;
}
```

При импорте этого класса в C++/CLI вызов одной из перегрузок приводит к ошибке:

```cpp
    (gcnew R)->Func("abc"); // error C2668: 'R::Func' ambiguous call to overloaded function
```

Компилятор выдает ошибку C2668, потому что обе перегрузки соответствуют этому списку аргументов. Во второй перегрузке второй аргумент заполняется аргументом по умолчанию. Чтобы обойти эту проблему, удалите избыточную перегрузку (1). Также можно использовать полный список аргументов и явно указать аргументы по умолчанию.

## <a name="conformance-improvements-in-visual-studio-2019-version-167"></a><a name="improvements_167"></a> Улучшения соответствия в Visual Studio 2019 версии 16.7

### <a name="is-trivially-copyable-definition"></a>Определение *is trivially copyable*

В C++20 изменилось определение *is trivially copyable*. Если у класса есть нестатический элемент данных, имеющий тип с квалификатором **`volatile`** , то этот элемент больше не подразумевает, что создаваемые компилятором конструкторы копирования или перемещения или соответствующий оператор присваивания являются нетривиальными. Комитет по стандартизации C++ применил это изменение в виде отчета об ошибках, имеющего обратное действие. В MSVC поведение компилятора не меняется в разных языковых режимах, таких как **`/std:c++14`** или **`/std:c++latest`** .

Вот пример этого нового поведения:

```cpp
#include <type_traits>

struct S
{
    volatile int m;
};

static_assert(std::is_trivially_copyable_v<S>, "Meow!");
```

Этот код не компилируется в версиях MSVC до Visual Studio 2019 версии 16.7. Существует предупреждение компилятора, отключенного по умолчанию, которое можно использовать для обнаружения этого изменения. Если вы компилируете приведенный выше код с помощью **`cl /W4 /w45220`** , вы увидите следующее предупреждение:

```Output
warning C5220: `'S::m': a non-static data member with a volatile qualified type no longer implies that compiler generated copy/move constructors and copy/move assignment operators are non trivial`
```

### <a name="pointer-to-member-and-string-literal-conversions-to-bool-are-narrowing"></a>Сужающие преобразования указателя на элемент и строкового литерала в `bool`

Комитет по стандартизации C++ недавно применил отчет об ошибках [P1957R2](https://wg21.link/p1957r2), который считает `T*` до **`bool`** сужающим преобразованием. Компилятор MSVC устранил ошибку в реализации, которая ранее выполняла диагностику `T*` в **`bool`** на предмет сужения, но не обнаруживала преобразования строкового литерала в **`bool`** или указателя на элемент в **`bool`** .

Следующая программа с неправильным форматом в Visual Studio 2019 версии 16.7:

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" }); // error: conversion from 'const char [8]' to 'bool' requires a narrowing conversion

    int (X::* p) = nullptr;
    f(X { p }); // error: conversion from 'int X::*' to 'bool' requires a narrowing conversion
}
```

Чтобы исправить этот код, либо добавьте явные сравнения для **`nullptr`** , либо избегайте контекстов, в которых сужающие преобразования имеют неправильный формат:

```cpp
struct X { bool b; };
void f(X);

int main() {
    f(X { "whoops?" != nullptr }); // Absurd, but OK

    int (X::* p) = nullptr;
    f(X { p != nullptr }); // OK
}
```

### <a name="nullptr_t-is-only-convertible-to-bool-as-a-direct-initialization"></a>`nullptr_t` можно преобразовать только в `bool` как прямую инициализацию

В C++11 **`nullptr`** можно преобразовать только в **`bool`** в качестве *прямого преобразования* (например, при инициализации **`bool`** с помощью заключенного в фигурные скобки списка инициализаторов). Это ограничение никогда принудительно не применялось к MSVC. MSVC теперь реализует правило в [`/permissive-`](../build/reference/permissive-standards-conformance.md). Неявные преобразования теперь диагностируются как с неправильным форматом. Контекстное преобразование в **`bool`** по-прежнему разрешено, так как `bool b(nullptr)` прямой инициализации является допустимым.

В большинстве случаев ошибку можно исправить, заменив **`nullptr`** на **`false`** , как показано в этом примере:

```cpp
struct S { bool b; };
void g(bool);
bool h() { return nullptr; } // error, should be 'return false;'

int main() {
    bool b1 = nullptr; // error: cannot convert from 'nullptr' to 'bool'
    S s { nullptr }; // error: cannot convert from 'nullptr' to 'bool'
    g(nullptr); // error: cannot convert argument 1 from 'nullptr' to 'bool'

    bool b2 { nullptr }; // OK: Direct-initialization
    if (!nullptr) {} // OK: Contextual conversion to bool
}
```

### <a name="conforming-initialization-behavior-for-array-initializations-with-missing-initializers"></a>Согласование поведения инициализации для инициализаций массива с отсутствующими инициализаторами

Ранее в MSVC было не согласованное поведение для инициализаций массива с отсутствующими инициализаторами. MSVC всегда называется конструктором по умолчанию для каждого элемента массива, который не имеет инициализатора. Стандартным поведением является инициализация каждого элемента с помощью пустого списка инициализаторов, заключенных в фигурные скобки ( **`{}`** ). Контекст инициализации для пустого списка инициализаторов, заключенных в фигурные скобки, — это инициализация копии, которая не допускает вызовов явных конструкторов. Также могут возникнуть различия в среде выполнения, так как использование `{}` для инициализации может вызвать конструктор, который принимает `std::initializer_list`, а не конструктор по умолчанию. Такое поведение согласования включается в [`/permissive-`](../build/reference/permissive-standards-conformance.md).

Вот пример этого измененного поведения:

```cpp
struct B {
    explicit B() {}
};

void f() {
    B b1[1]{}; // Error in /permissive-, because aggregate init calls explicit ctor
    B b2[1]; // OK: calls default ctor for each array element
}
```

### <a name="initialization-of-class-members-with-overloaded-names-is-correctly-sequenced"></a>Инициализация элементов класса с перегруженными именами правильно упорядочена

Мы обнаружили ошибку во внутреннем представлении элементов данных класса, если имя типа также перегружено как имя элемента данных. Эта ошибка привела к несогласованности при агрегатной инициализации и порядке инициализации элементов. Созданный код инициализации теперь является правильным. Однако это изменение может привести к ошибкам или предупреждениям в источнике, который случайно полагался на элементы с неправильным порядком, как показано в следующем примере:

```cpp
// Compiling with /w15038 now gives:
// warning C5038: data member 'Outer::Inner' will be initialized after data member 'Outer::v'
struct Outer {
    Outer(int i, int j) : Inner{ i }, v{ j } {}

    struct Inner { int x; };
    int v;
    Inner Inner; // 'Inner' is both a type name and data member name in the same scope
};
```

В предыдущих версиях конструктор неправильно инициализирует элемент данных `Inner` перед элементом данных `v`. (Стандарт C++ требует, чтобы порядок инициализации совпадал с порядком объявления элементов). Теперь, когда созданный код соответствует стандарту, список инициализации элементов является неупорядоченным. Компилятор выдает предупреждение для этого примера. Чтобы устранить эту проблему, измените порядок в списке инициализации элементов в соответствии с порядком объявления.

### <a name="overload-resolution-involving-integral-overloads-and-long-arguments"></a>Разрешение перегрузки, включающее целочисленные перегрузки и аргументы `long`

Стандарт C++ требует ранжирования **`long`** для преобразования **`int`** в качестве стандартного преобразования. Предыдущие компиляторы MSVC неправильно ранжируют его как целочисленное повышение уровня, ранги которого более высокие для разрешения перегрузки. Это ранжирование может привести к успешному разрешению перегрузки, если оно считается неоднозначным.

Компилятор теперь правильно рассматривает ранг в режиме [`/permissive-`](../build/reference/permissive-standards-conformance.md). Недопустимый код диагностируется правильно, как показано в следующем примере:

```cpp
void f(long long);
void f(int);

int main() {
    long x {};
    f(x); // error: 'f': ambiguous call to overloaded function
    f(static_cast<int>(x)); // OK
}
```

Устранить эту проблему можно несколькими способами:

- В месте вызова измените тип переданного аргумента на **`int`** . Вы можете либо изменить тип переменной, либо привести ее.

- Если имеется много мест вызова, можно добавить другую перегрузку, принимающую аргумент **`long`** . В этой функции приведите и переадресуйте аргумент к перегрузке **`int`** .

### <a name="use-of-undefined-variable-with-internal-linkage"></a>Использование неопределенной переменной с внутренней компоновкой

Версии MSVC до принятия Visual Studio 2019 версии 16.7 используют объявленную переменную (не определена) **`extern`** с внутренней компоновкой. Такие переменные не могут быть определены в другой единице трансляции и не могут формировать допустимую программу. Теперь компилятор выполняет диагностику этого случая во время компиляции. Ошибка аналогична ошибке для неопределенных статических функций.

```cpp
namespace {
    extern int x; // Not a definition, but has internal linkage because of the anonymous namespace
}

int main()
{
    return x; // Use of 'x' that no other translation unit can possibly define.
}
```

Эта программа ранее была неправильно скомпилирована и скомпонована, но теперь будет выдавать ошибку C7631.

```Output
error C7631: '`anonymous-namespace'::x': variable with internal linkage declared but not defined
```

Такие переменные должны быть определены в той же единице трансляции, в которой они используются. Для этого можно предоставить явный инициализатор или отдельное определение.

### <a name="type-completeness-and-derived-to-base-pointer-conversions"></a>Заполнение типа и преобразования указателя из производного в базовый

В стандартах C++ до C++20 для преобразования из производного класса в базовый не требовалось, чтобы производный класс был полным типом класса. Комитет по стандартизации C++ утвердил изменение (относится ко всем версиям языка C++) в отчете об ошибках, имеющем обратное действие. Это изменение обеспечивает процесс преобразования с признаками типа, например `std::is_base_of`, который требует, чтобы производный класс был полным типом класса.

Ниже приведен пример:

```cpp
template<typename A, typename B>
struct check_derived_from
{
    static A a;
    static constexpr B* p = &a;
};

struct W { };
struct X { };
struct Y { };

// With this change this code will fail as Z1 is not a complete class type
struct Z1 : X, check_derived_from<Z1, X>
{
};

// This code failed before and it will still fail after this change
struct Z2 : check_derived_from<Z2, Y>, Y
{
};

// With this change this code will fail as Z3 is not a complete class type
struct Z3 : W
{
    check_derived_from<Z3, W> cdf;
};
```

Это изменение в поведении применяется ко всем режимам языка C++ компилятора MSVC, а не только **`/std:c++latest`** .

### <a name="narrowing-conversions-are-more-consistently-diagnosed"></a>Более согласованная проверка сужающих преобразований

MSVC выдает предупреждение для сужающих преобразований в инициализаторе списка в фигурных скобках. Ранее компилятор не проверял сужающие преобразования от больших базовых типов **`enum`** до более узких целочисленных типов. (Компилятор неправильно считает их целочисленным повышением уровня вместо преобразования.) Если сужающее преобразование является преднамеренным, можно избежать предупреждения, используя **`static_cast`** для аргумента инициализатора. Или выберите больший целочисленный тип назначения.

Ниже приведен пример использования явного **`static_cast`** для устранения предупреждения:

```cpp
enum E : long long { e1 };
struct S { int i; };

void f(E e) {
    S s = { e }; // warning: conversion from 'E' to 'int' requires a narrowing conversion
    S s1 = { static_cast<int>(e) }; // Suppress warning with explicit conversion
}
```

## <a name="conformance-improvements-in-visual-studio-2019-version-168"></a><a name="improvements_168"></a> Улучшения соответствия в Visual Studio 2019 версии 16.8

### <a name="class-rvalue-used-as-lvalue-extension"></a>Расширение "Класс rvalue, используемый как lvalue"

В MSVC есть расширение, которое позволяет использовать класс rvalue в качестве lvalue. Это расширение не продлевает время существования класса rvalue, что может привести к неопределенному поведению во время выполнения. Теперь мы принудительно применяем стандартное правило, запрещая это расширение в **`/permissive-`** .
Если вы пока не можете использовать **`/permissive-`** , запретите расширение явным образом с помощью **`/we4238`** . Пример:

```cpp
// Compiling with /permissive- now gives:
// error C2102: '&' requires l-value
struct S {};

S f();

void g()
{
    auto p1 = &(f()); // The temporary returned by 'f' is destructed after this statement. So 'p1' points to an invalid object.

    const auto &r = f(); // This extends the lifetime of the temporary returned by 'f'
    auto p2 = &r; // 'p2' points to a valid object
}
```

### <a name="explicit-specialization-in-non-namespace-scope-extension"></a>Расширение "Явная специализация в области, отличной от пространства имен"

MSVC имеет расширение, которое позволяло использовать явную специализацию в области, отличной от пространства имен. Теперь, после разрешения CWG 727, это поведение считается стандартным. При этом есть различия в поведении. Мы скорректировали поведение нашего компилятора в соответствии со стандартом.

```cpp
// Compiling with 'cl a.cpp b.cpp /permissive-' now gives:
//   error LNK2005: "public: void __thiscall S::f<int>(int)" (??$f@H@S@@QAEXH@Z) already defined in a.obj
// To fix the linker error,
// 1. Mark the explicit specialization with 'inline' explicitly. Or,
// 2. Move its definition to a source file.

// common.h
struct S {
    template<typename T> void f(T);
    template<> void f(int);
};

// This explicit specialization is implicitly inline in the default mode.
template<> void S::f(int) {}

// a.cpp
#include "common.h"

int main() {}

// b.cpp
#include "common.h"
```

### <a name="checking-for-abstract-class-types"></a>Проверка на наличие типов абстрактного класса

Стандарт C++20 изменил процесс, который компиляторы используют для обнаружения типа абстрактного класса в качестве параметра функции. В частности, это больше не считается ошибкой SFINAE. Ранее, если компилятор обнаруживал, что в специализации шаблона функции есть параметр функции, являющийся экземпляром типа абстрактного класса, формат такой специализации считался неправильным. Она не добавлялась в набор подходящих функций-кандидатов. В C++20 проверка параметра с типом абстрактного класса не выполняется до самого вызова функции. В результате код при компиляции не вызывает ошибку. Приведем пример:

```cpp
class Node {
public:
    int index() const;
};

class String : public Node {
public:
    virtual int size() const = 0;
};

class Identifier : public Node {
public:
    const String& string() const;
};

template<typename T>
int compare(T x, T y)
{
    return x < y ? -1 : (x > y ? 1 : 0);
}

int compare(const Node& x, const Node& y)
{
    return compare(x.index(), y.index());
}

int f(const Identifier& x, const String& y)
{
    return compare(x.string(), y);
}
```

Ранее при вызове `compare` была бы предпринята попытка специализировать шаблон функции `compare`, используя аргумент шаблона `String` для `T`. Такая специализация считалась бы недопустимой, так как `String` является абстрактным классом. В качестве единственного подходящего кандидата можно было бы использовать `compare(const Node&, const Node&)`. Но теперь в C++20 проверка на тип абстрактного класса не выполняется до самого вызова функции. Таким образом, специализация `compare(String, String)` добавляется в набор подходящих кандидатов и выбирается как лучший вариант, так как преобразование из `const String&` в `String` считается более правильным, чем преобразование из `const String&` в `const Node&`.

Чтобы исправить этот пример, в C++20 можно использовать концепции; то есть измените определение `compare` следующим образом:

```cpp
template<typename T>
int compare(T x, T y) requires !std::is_abstract_v<T>
{
    return x < y ? -1 : (x > y ? 1 : 0);
}
```

Или, если концепции C++ недоступны, можно вернуться к SFINAE:

```cpp
template<typename T, std::enable_if_t<!std::is_abstract_v<T>, int> = 0>
int compare(T x, T y)
{
    return x < y ? -1 : (x > y ? 1 : 0);
}
```

### <a name="support-for-p0960r3---allow-initializing-aggregates-from-a-parenthesized-list-of-values"></a>Поддержка P0960R3 — разрешение инициализации агрегатов из списка значений в скобках

В C++20 [P0960R3](https://wg21.link/P0960R3) включена поддержка инициализации агрегата с помощью списка инициализаторов, заключенного в скобки. Например, в C++20 подходящим считается следующий код:

```cpp
struct S {
    int i;
    int j;
};

S s(1, 2);
```

Эта функция является в основном аддитивной, то есть она позволяет компилировать код, который не компилировался ранее. Но она также изменяет поведение `std::is_constructible`. В режиме C++17 использование **`static_assert`** приводит к ошибке, но в режиме C++20 код выполняется успешно:

```cpp
static_assert(std::is_constructible_v<S, int, int>, "Assertion failed!");
```

Если эта характеристика типа используется для управления разрешением перегрузки, это может привести к изменению поведения при переходе с версии C++17 на C++20.

### <a name="overload-resolution-involving-function-templates"></a>Разрешение перегрузки с использованием шаблонов функций

Ранее компилятор разрешал в режиме **`/permissive-`** компиляцию некоторых фрагментов кода, которые не должны компилироваться. Это приводило к тому, что компилятор вызывал неверную функцию и изменял поведение во время выполнения:

```cpp
int f(int);

namespace N
{
    using ::f;
    template<typename T>
    T f(T);
}

template<typename T>
void g(T&& t)
{
}

void h()
{
    using namespace N;
    g(f);
}
```

Этот вызов `g` использует набор перегрузок, который содержит две функции: `::f` и `N::f`. Так как `N::f` является шаблоном функции, компилятор должен обрабатывать аргумент функции как *невыведенный контекст*. В этом примере это означает, что вызов `g` должен завершиться ошибкой, так как компилятор не может вывести тип для параметра шаблона `T`. К сожалению, компилятор не мог не учитывать то, что уже счел `::f` хорошим соответствием для вызова этой функции. Так что вместо завершения с ошибкой компилятор создал бы код для вызова `g` с аргументом `::f`.

Учитывая, что во многих случаях использование `::f` в качестве аргумента функции является ожидаемым для пользователя поведением, ошибка возникает, только если код компилируется с **`/permissive-`** .

### <a name="migrating-from-await-to-c20-coroutines"></a>Переход от `/await` к сопрограммам C++20

Стандартные сопрограммы C++20 теперь по умолчанию включены в **`/std:c++latest`** . Они отличаются от сопрограмм TS и их поддержка включается параметром **`/await`** . Переход от **`/await`** к стандартным сопрограммам может потребовать некоторых изменений в исходном коде.

#### <a name="non-standard-keywords"></a>Нестандартные ключевые слова

Старые ключевые слова **`await`** и **`yield`** не поддерживаются в режиме C++20. Вместо них в коде необходимо использовать **`co_await`** и **`co_yield`** . Также стандартный режим не позволяет использовать `return` в сопрограмме. Все **`return`** в сопрограмме должны использовать **`co_return`** .

```cpp
// /await
task f_legacy() {
    ...
    await g();
    return n;
}
// /std:c++latest
task f() {
    ...
    co_await g();
    co_return n;
}
```

#### <a name="types-of-initial_suspendfinal_suspend"></a>Типы initial_suspend и final_suspend

В режиме **`/await`** функции обещания начальной и окончательной приостановки могут объявляться как возвращающие значение **`bool`** . Такое поведение не является стандартным. В C++20 такие функции должны возвращать тип класса, поддерживающий ожидание, например поддерживающие ожидание тривиальные типы: `std::suspend_always`, если функция ранее возвращала **`true`** , или `std::suspend_never`, если она возвращала **`false`** .

```cpp
// /await
struct promise_type_legacy {
    bool initial_suspend() noexcept { return false; }
    bool final_suspend() noexcept { return true; }
    ...
};

// /std:c++latest
struct promise_type {
    auto initial_susepend() noexcept { return std::suspend_never{}; }
    auto final_suspend() noexcept { return std::suspend_always{}; }
    ...
};
```

#### <a name="type-of-yield_value"></a>Тип `yield_value`

В C++20 функция обещания `yield_value` должна возвращать тип, поддерживающий ожидание. В режиме **`/await`** функция `yield_value` могла возвращать **`void`** и всегда приостанавливала работу. Такие функции можно заменить функцией, которая возвращает `std::suspend_always`.

```cpp
// /await
struct promise_type_legacy {
    ...
    void yield_value(int x) { next = x; };
};

// /std:c++latest
struct promise_type {
    ...
    auto yield_value(int x) { next = x; return std::suspend_always{}; }
};
```

#### <a name="exception-handling-function"></a>Функция обработки исключений

**`/await`** поддерживает тип обещания без функции обработки исключений или с функцией обработки исключений с именем `set_exception`, которая принимает `std::exception_ptr`. В C++20 тип обещания должен иметь функцию с именем `unhandled_exception`, которая не принимает аргументы. При необходимости можно получить объект исключения из `std::current_exception`.

```cpp
// /await
struct promise_type_legacy {
    void set_exception(std::exception_ptr e) { saved_exception = e; }
    ...
};
// /std:c++latest
struct promise_type {
    void unhandled_exception() { saved_exception = std::current_exception(); }
    ...
};
```

#### <a name="deduced-return-types-of-coroutines-not-supported"></a>Выведенные возвращаемые типы сопрограмм не поддерживаются

В C++20 не поддерживаются сопрограммы с типом возвращаемого значения, который включает тип заполнителя, например **`auto`** . Типы возвращаемых значений в сопрограммах должны быть объявлены явно. В режиме **`/await`** эти выведенные типы всегда используют экспериментальный тип и требуют включать заголовок с определением требуемого типа: Это может быть `std::experimental::task<T>`, `std::experimental::generator<T>` или `std::experimental::async_stream<T>`.

```cpp
// /await
auto my_generator() {
    ...
    co_yield next;
};

// /std:c++latest
#include <experimental/generator>
std::experimental::generator<int> my_generator() {
    ...
    co_yield next;
};
```

#### <a name="return-type-of-return_value"></a>Тип возвращаемого значения `return_value`

Возвращаемое значение функции обещания `return_value` должно иметь тип **`void`** . В режиме **`/await`** тип возвращаемого значения может быть любым и он игнорируется. Такая диагностика помогает обнаружить неочевидные ошибки, например те, которые вызваны ошибочным предположением, что вызывающему объекту возвращается значение `return_value`.

```cpp
// /await
struct promise_type_legacy {
    ...
    int return_value(int x) { return x; } // incorrect, the return value of this function is unused and the value is lost.
};

// /std:c++latest
struct promise_type {
    ...
    void return_value(int x) { value = x; }; // save return value
};
```

#### <a name="return-object-conversion-behavior"></a>Поведение при преобразовании возвращаемого объекта

Если объявленный тип возвращаемого значения сопрограммы не совпадает с типом возвращаемого значения функции обещания `get_return_object`, то возвращаемый из `get_return_object` объект преобразуется в тип возвращаемого значения сопрограммы. В режиме **`/await`** такое преобразование выполняется раньше, еще до выполнения основного текста сопрограммы. В **`/std:c++latest`** такое преобразование выполняется, только когда значение фактически возвращается вызывающему объекту. Благодаря этому сопрограммы, которые не приостанавливаются в начальной точке приостановки, могут использовать в ходе выполнения объект, возвращаемый из `get_return_object`.

#### <a name="coroutine-promise-parameters"></a>Параметры обещаний сопрограмм

В C++20 компилятор пытается передать параметры сопрограммы (если они есть) в конструктор типа обещания. В случае неудачи он повторяет попытку с конструктором по умолчанию. В режиме **`/await`** использовался только конструктор по умолчанию. Это изменение может привести к изменению поведения, если в обещании есть несколько конструкторов или используется преобразование параметра сопрограммы в тип обещания.

```cpp
struct coro {
    struct promise_type {
        promise_type() { ... }
        promise_type(int x) { ... }
        ...
    };
};

coro f1(int x);

// Under /await the promise gets constructed using the default constructor.
// Under /std:c++latest the promise gets constructed using the 1-argument constructor.
f1(0);

struct Object {
template <typename T> operator T() { ... } // Converts to anything!
};

coro f2(Object o);

// Under /await the promise gets constructed using the default constructor
// Under /std:c++latest the promise gets copy- or move-constructed from the result of
// Object::operator coro::promise_type().
f2(Object{});
```

### <a name="permissive--and-c20-modules-are-on-by-default-under-stdclatest"></a>Модули `/permissive-` и C++20 в `/std:c++latest` по умолчанию включены

Поддержка модулей C++20 по умолчанию включена в **`/std:c++latest`** . Дополнительные сведения об этом изменении и о тех сценариях, в которых **`module`** и **`import`** условно рассматриваются как ключевые слова, см. в блоге [Standard C++20 Modules support with MSVC in Visual Studio 2019 version 16.8](https://devblogs.microsoft.com/cppblog/standard-c20-modules-support-with-msvc-in-visual-studio-2019-version-16-8/) (Поддержка стандартных модулей C++20 в MSVC при работе с Visual Studio 2019 версии 16.8).

В качестве обязательного условия для поддержки модулей теперь **`permissive-`** по умолчанию включается при указании **`/std:c++latest`** . Дополнительные сведения см. в разделе [`/permissive-`](../build/reference/permissive-standards-conformance.md).

Если код ранее компилировался в **`/std:c++latest`** и для него нужно другое поведение компилятора, вы можете отключить в компиляторе режим строгого соответствия с помощью **`permissive`** . Этот параметр компилятора нужно включить в список аргументов командной строки после **`/std:c++latest`** . При этом использование **`permissive`** приведет к такой ошибке, если обнаружится использования модулей:

> error C1214: Modules conflict with non-standard behavior requested via '*option*' (Ошибка C1214. Модули конфликтуют с нестандартным поведением, запрошенным параметром option).

Здесь параметр *option* чаще всего принимает следующие значения:

| Параметр | Описание |
|--|--|
| **`/Zc:twoPhase-`** | Двухэтапный поиск имен является обязательным для модулей C++20 и подразумевается параметром **`permissive-`** . |
| **`/Zc:hiddenFriend-`** | Стандартные скрытые правила поиска имен являются обязательными для модулей C++ 20 и подразумеваются параметром **`permissive-`** . |
| **`/Zc:preprocessor-`** | Соответствующий препроцессор требуется только для использования и создания блока заголовка C++20. Для именованных модулей этот параметр не требуется. |

Параметр [`/experimental:module`](../build/reference/experimental-module.md) по-прежнему требуется для использования модулей *`std.*`* , которые поставляются в комплекте с Visual Studio, так как они еще не стандартизированы.

Параметр **`/experimental:module`** также подразумевает **`/Zc:twoPhase`** и **`/Zc:hiddenFriend`** . Ранее для кода, компилируемого с использованием модулей, иногда применялся режим **`/Zc:twoPhase-`** , если модуль только использовался. Такое поведение больше не поддерживается.

## <a name="conformance-improvements-in-visual-studio-2019-version-169"></a><a name="improvements_169"></a> Улучшения соответствия в Visual Studio 2019 версии 16.9

### <a name="copy-initialization-of-temporary-in-reference-direct-initialization"></a>Инициализация копированием для временной прямой инициализации в ссылке

Выпущенное основной рабочей группой решение проблемы [CWG 2267](https://wg21.link/cwg2267) касается несогласованности между списком инициализаторов в круглых и фигурных скобках. Данное решение проблемы гармонизирует эти две формы.

Visual Studio 2019 версии 16.9 реализует измененное поведение во всех режимах компилятора **`/std`** . Однако, так как это потенциально критическое изменение исходного кода, оно поддерживается только в том случае, если код компилируется с использованием **`/permissive-`** .

В этом примере демонстрируется изменение в поведении:

```cpp
struct A { };

struct B {
    explicit B(const A&);
};

void f()
{
    A a;
    const B& b1(a);     // Always an error
    const B& b2{ a };   // Allowed before resolution to CWG 2267 was adopted: now an error
}
```

### <a name="destructor-characteristics-and-potentially-constructed-subobjects"></a>Характеристики деструктора и потенциально сконструированные подобъекты

Выпущенное основной рабочей группой решение проблемы [CWG 2336](https://wg21.link/cwg2336) устраняет пропуск в спецификациях неявных исключений деструкторов в классах, имеющих виртуальные базовые классы. Пропуск означает, что деструктор в производном классе может иметь более слабую спецификацию исключений, чем базовый класс, если этот базовый класс был абстрактным и имеет базовый класс `virtual`.

Visual Studio 2019 версии 16.9 реализует измененное поведение во всех режимах компилятора **`/std`** .

В этом примере показано изменение интерпретации:

```cpp
class V {
public:
    virtual ~V() noexcept(false);
};

class B : virtual V {
    virtual void foo () = 0;
    // BEFORE: implicitly defined virtual ~B() noexcept(true);
    // AFTER: implicitly defined virtual ~B() noexcept(false);
};

class D : B {
    virtual void foo ();
    // implicitly defined virtual ~D () noexcept(false);
};
```

До этого изменения для неявно определенного деструктора для `B` было задано значение `noexcept`, так как учитывались только потенциально сконструированные подобъекты. При этом базовый класс `V` не является потенциально сконструированным подобъектом, поскольку он является базовым классом `virtual`, а `B` — это абстрактный класс. Однако базовый класс `V` является потенциально сконструированным подобъектом класса `D`, поэтому `D::~D` определяется как `noexcept(false)`, в результате чего производный класс имеет более слабую спецификацию исключений, чем его базовый класс. Такая интерпретация ненадежна. Она может привести к неправильному поведению во время выполнения, если в деструкторе класса, производного от B, возникает исключение.

При таком изменении деструктор также может выдавать исключение, если у него есть виртуальный деструктор. Кроме того, любой виртуальный базовый класс содержит деструктор, который потенциально может выдавать исключение.

### <a name="similar-types-and-reference-binding"></a>Подобные типы и привязка ссылок

Выпущенное основной рабочей группой решение проблемы [CWG 2352](https://wg21.link/cwg2352) касается несогласованности между правилами привязки ссылок и изменениями в подобии типов. Сведения о несоответствии приведены в более ранних сообщениях о дефектах (например, [CWG 330](https://wg21.link/cwg330)). После этого изменения код, в котором ранее ссылка привязывалась к временной переменной, теперь может быть привязан напрямую, если используемые типы отличаются только CV-квалификаторами.

Visual Studio 2019 версии 16.9 реализует измененное поведение во всех режимах компилятора **`/std`** . Это может привести к критическому изменению в исходном коде.

В этом примере показано изменение в поведении:

```cpp
int *ptr;
const int *const &f() {
    return ptr; // Now returns a reference to 'ptr' directly.
    // Previously returned a reference to a temporary and emitted C4172
}
```

Обновление может привести к изменению в поведении программы, если оно предполагало введение временной переменной:

```cpp
int func() {
    int i1 = 13;
    int i2 = 23;
    
    int* iptr = &i1;
    int const * const&  iptrcref = iptr;

    // iptrcref is a reference to a pointer to i1 with value 13.
    if (*iptrcref != 13)
    {
        return 1;
    }
    
    // Now change what iptr points to.

    // Prior to CWG 2352 iptrcref should be bound to a temporary and still points to the value 13.
    // After CWG 2352 it is bound directly to iptr and now points to the value 23.
    iptr = &i2;
    if (*iptrcref != 23)
    {
        return 1;
    }

    return 0;
}
```

### <a name="zctwophase-and-zctwophase--switch-behavior-change"></a>Изменение в поведении параметров `/Zc:twoPhase` и `/Zc:twoPhase-`

Как правило, параметры компилятора MSVC работают по принципу выбора последнего значения. К сожалению, в случае с **`/Zc:twoPhase`** и **`/Zc:twoPhase-`** это не так. Эти параметры были "закреплены", поэтому их невозможно переопределить последующими параметрами. Например:

`cl /Zc:twoPhase /permissive a.cpp`

В этом случае первый параметр **`/Zc:twoPhase`** инициирует двухэтапный поиск имен. Предполагалось, что второй параметр отключает режим строгого соответствия (он противоположен параметру **`/permissive-`** ), но **`/Zc:twoPhase`** он не отключал.

Visual Studio 2019 версии 16.9 изменяет это поведение во всех режимах компилятора **`/std`** . **`/Zc:twoPhase`** и **`/Zc:twoPhase-`** больше не "закреплены", и их можно переопределить последующими параметрами.

### <a name="explicit-noexcept-specifiers-on-destructor-templates"></a>Явные описатели noexcept в шаблонах деструктора

Компилятор ранее принимал шаблон деструктора, объявленный с использованием спецификации, не предполагающей создание исключений, но определенный без явного описателя noexcept. Неявная спецификация деструктора с исключениями зависит от свойств класса -properties, которые могут быть неизвестны в точке определения шаблона. Стандарт C++ также требует такого поведения: если деструктор объявлен без описателя noexcept, он имеет неявную спецификацию с исключениями и ни одно другое объявление функции не может иметь описатель noexcept.

Visual Studio 2019 версии 16.9 изменяет это поведение на поведение согласования во всех режимах компилятора **`/std`** .

В этом примере показано изменение в поведении компилятора:

```cpp
template <typename T>
class B {
    virtual ~B() noexcept; // or throw()
};

template <typename T>
B<T>::~B() { /* ... */ } // Before: no diagnostic.
// Now diagnoses a definition mismatch. To fix, define the implementation by 
// using the same noexcept-specifier. For example,
// B<T>::~B() noexcept { /* ... */ }
```

### <a name="rewritten-expressions-in-c20"></a>Перезаписанные выражения в C++20

Начиная с Visual Studio 2019 версии 16.2 в **`/std:c++latest`** компилятор принимал код, подобный приведенному ниже.

```cpp
#include <compare>

struct S {
    auto operator<=>(const S&) const = default;
    operator bool() const;
};

bool f(S a, S b) {
    return a < b;
}
```

Однако компилятор не вызывал функцию сравнения, даже если это ожидалось. Приведенный выше код следует переписать, заменив `a < b` на `(a <=> b) < 0`. Вместо этого компилятор использовал определяемую пользователем функцию преобразования `operator bool()` и выполнял сравнение `bool(a) < bool(b)`. Начиная с Visual Studio 2019 версии 16.9, компилятор переписывает выражение, используя ожидаемое выражение оператора трехстороннего сравнения.

#### <a name="source-breaking-change"></a>Критическое изменение исходного кода

Правильное применение преобразований к перезаписанным выражениям приводит к другому результату: компилятор также правильно выполняет диагностику неоднозначностей при попытке перезаписи выражения. Рассмотрим следующий пример.

```cpp
struct Base {
    bool operator==(const Base&) const;
};

struct Derived : Base {
    Derived();
    Derived(const Base&);
    bool operator==(const Derived& rhs) const;
};

bool b = Base{} == Derived{};
```

В C++17 этот код был бы принят благодаря преобразованию производного класса в базовый (`Derived`) в правой части выражения. В C++20 также добавляется кандидат для синтезированного выражения: `Derived{} == Base{}`. Из-за правил в стандарте, определяющих, какая функция выбирается на основе преобразования, невозможно определить, что выбрать: `Base::operator==` или `Derived::operator==`. Это обусловлено тем, что последовательности преобразования в двух выражениях ничем не лучше и ничем не хуже друг друга. Поэтому пример кода приводит к неоднозначности.

Чтобы устранить неоднозначность, добавьте новый кандидат, к которому не будет применяться последовательность из двух преобразований:

```cpp
bool operator==(const Derived&, const Base&);
```

#### <a name="runtime-breaking-change"></a>Критическое изменение в среде выполнения

Благодаря правилам переписывания операторов в C++20 можно разрешить перегрузку, чтобы найти новый кандидат, который не был бы найден в режиме языка более низкого уровня. Кроме того, новый кандидат может оказаться более подходящем, чем старый. Рассмотрим следующий пример.

```cpp
struct iterator;
struct const_iterator {
  const_iterator(const iterator&);
  bool operator==(const const_iterator &ci) const;
};

struct iterator {
  bool operator==(const const_iterator &ci) const { return ci == *this; }
};
```

В C++17 единственным кандидатом для `ci == *this` является `const_iterator::operator==`. Он подходит, поскольку `*this` преобразуется в `const_iterator` с помощью преобразования производного класса в базовый. В C++20 добавляется другой перезаписанный кандидат: `*this == ci`, который вызывает `iterator::operator==`. Этот кандидат не требует преобразований, поэтому он подходит лучше, чем `const_iterator::operator==`. Проблема с новым кандидатом заключается в том, что эта функция еще только определяется в настоящее время, поэтому новая семантика функции вызывает бесконечное рекурсивное определение `iterator::operator==`.

Чтобы помочь в работе с таким кодом, как в этом примере, компилятор реализует новое предупреждение:

```cmd
$ cl /std:c++latest /c t.cpp
t.cpp
t.cpp(8): warning C5232: in C++20 this comparison calls 'bool iterator::operator ==(const const_iterator &) const' recursively
```

Чтобы исправить код, необходимо явно указать, какое преобразование следует использовать:

```cpp
struct iterator {
  bool operator==(const const_iterator &ci) const { return ci == static_cast<const const_iterator&>(*this); }
};
```

## <a name="see-also"></a>См. также

[Таблица соответствия Microsoft Visual C++ стандартам языка](visual-cpp-language-conformance.md)
