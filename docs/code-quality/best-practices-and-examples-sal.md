---
title: Рекомендации и примеры (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
ms.openlocfilehash: 304ba98ae5118f2ca8fb425c8dd7065bd19c8287
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467038"
---
# <a name="best-practices-and-examples-sal"></a>Рекомендации и примеры (SAL)

Ниже приведены некоторые способы получения максимальной из языка аннотирования исходного кода (SAL) и устранения некоторых распространенных проблем.

## <a name="_in_"></a>\_Где\_

Если функция должна выполнять запись в элемент, используйте `_Inout_` вместо `_In_`. Это особенно важно в случаях автоматического преобразования из старых макросов в SAL. До SAL многие программисты использовали макросы как комментарии — макросы, именованные `IN`, `OUT`, `IN_OUT`или варианты этих имен. Хотя мы рекомендуем преобразовывать эти макросы в SAL, мы советуем соблюдать осторожность при их преобразовании, поскольку код мог быть изменен с момента написания первоначального прототипа, а старый макрос больше не будет отражать то, что делает код. Будьте особенно осторожны с макросом `OPTIONAL` Comment, так как он часто размещается неправильно, например, на неправильной стороне запятой.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

Если вызывающему объекту не разрешено передавать указатель null, используйте `_In_` или `_Out_` вместо `_In_opt_` или `_Out_opt_`. Это относится даже к функции, которая проверяет свои параметры и возвращает ошибку, если она не должна иметь значение NULL. Несмотря на то, что функция проверяет свой параметр на непредвиденное значение NULL и корректно возвращает хорошее защитное программирование, это не означает, что аннотация параметра может иметь необязательный тип (`_*Xxx*_opt_`).

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_перед\_защитой\_ и \_от\_защитного\_

Если функция находится на границе доверия, то рекомендуется использовать примечание `_Pre_defensive_`.  Модификатор "защитное" изменяет определенные заметки, чтобы указать, что в момент вызова интерфейс должен проверяться строго, но в теле реализации он должен предположить, что могут быть переданы неверные параметры. В этом случае, на границе доверия предпочитается макрос `_In_ _Pre_defensive_`, чтобы указать, что, хотя вызывающий объект получит ошибку, если он пытается передать значение NULL, тело функции проанализирует, может ли параметр принимать значение NULL, а все попытки разыменования указателя без проверки его на значение NULL будет отмечены.  Примечание `_Post_defensive_` также доступно для использования в обратных вызовах, где вызывающий код считается надежной стороной, а вызываемый код — ненадежной.

## <a name="_out_writes_"></a>\_\_ных операций записи\_

В следующем примере демонстрируется распространенное неправильное использование `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

`_Out_writes_` аннотации означает, что у вас есть буфер. В нем `cb` выделенных байтов с первым байтом, инициализированным при выходе. Эта аннотация не является строго неправильной и полезна для выражения выделенного размера. Однако он не указывает, сколько элементов инициализируется функцией.

В следующем примере показаны три правильных способа полного указания точного размера инициализированной части буфера.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_\_ ПСТР

Использование `_Out_ PSTR` почти всегда неверно. Это интерпретируется как наличие выходного параметра, указывающего на символьный буфер и заканчивающегося символом NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Такие заметки, как `_In_ PCSTR`, являются общими и полезными. Он указывает на входную строку с завершающим НУЛЕМ, поскольку предварительное условие `_In_` допускает распознавание строки, завершающейся нулем.

## <a name="_in_-wchar-p"></a>\_в\_ WCHAR * p

`_In_ WCHAR* p` говорит, что имеется указатель ввода `p`, указывающий на один символ. Однако в большинстве случаев это не является требуемой спецификацией. Вместо этого, скорее всего, используется спецификация массива, заканчивающегося нулем; для этого используйте `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Отсутствие правильной спецификации завершения NULL является наиболее распространенным. Используйте соответствующую версию `STR`, чтобы заменить тип, как показано в следующем примере.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_диапазона\_\_

Если параметр является указателем и необходимо выразить диапазон значения элемента, на который указывает указатель, используйте `_Deref_out_range_` вместо `_Out_range_`. В следующем примере диапазон * Пкбфиллед выражается, а не Пкбфиллед.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)` не обязательно является обязательным для некоторых средств, так как он может выводиться из `_Out_writes_to_(cbSize,*pcbFilled)`, но он показан здесь для полноты.

## <a name="wrong-context-in-_when_"></a>Неправильный контекст в \_при\_

Еще одна распространенная ошибка — использование вычисления после состояния для предусловий. В следующем примере `_Requires_lock_held_` является предусловием.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Выражение `result` ссылается на значение после состояния, которое недоступно в предварительном состоянии.

## <a name="true-in-_success_"></a>TRUE в \_успешно\_

Если функция завершается успешно, если возвращаемое значение не равно нулю, используйте `return != 0` в качестве условия успеха вместо `return == TRUE`. Ненулевое значение не всегда означает эквивалентность фактического значения, предоставляемого компилятором для `TRUE`. Параметр в `_Success_` — выражение и следующие выражения вычисляются как равные. `return != 0`, `return != false`, `return != FALSE` и `return` без параметров или сравнений.

```cpp
// Incorrect
_Success_(return == TRUE) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Ссылочная переменная

Для ссылочной переменной предыдущая версия SAL использовала подразумеваемый указатель в качестве целевого объекта заметки и требовал добавления `__deref` к заметкам, присоединенным к ссылочной переменной. Эта версия использует сам объект и не требует дополнительных `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Аннотации для возвращаемых значений

В следующем примере показана общая проблема в аннотациях возвращаемого значения.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

В этом примере `_Out_opt_` говорит, что указатель может иметь значение NULL в составе предусловия. Однако предусловия нельзя применить к возвращаемому значению. В этом случае правильная Аннотация `_Ret_maybenull_`.

## <a name="see-also"></a>См. также раздел

[Использование аннотаций SAL для уменьшения количества дефектов в коде C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Основные сведения о языке SAL](../code-quality/understanding-sal.md)  
[Создание примечаний к параметрам и возвращаемым значениям функций](../code-quality/annotating-function-parameters-and-return-values.md)  
[Аннотация поведения функций](../code-quality/annotating-function-behavior.md)  
[Аннотация структур и классов](../code-quality/annotating-structs-and-classes.md)  
[Аннотация поведения блокировки](../code-quality/annotating-locking-behavior.md)  
[Указание времени и места применения примечания](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Встроенные функции](../code-quality/intrinsic-functions.md)
