---
description: 'Дополнительные сведения: сообщения векторизатора и параллелизатора'
title: Сообщения векторизатора и параллелизатора
ms.date: 02/16/2021
f1_keywords:
- C5011
- C5002
- C5021
- C5001
- C5012
ms.openlocfilehash: 3e2d458d177b8a7032276d29940a7ff2dac83b36
ms.sourcegitcommit: e99db7c3b5f25ece0e152165066c926751a7c2ed
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2021
ms.locfileid: "100643564"
---
# <a name="vectorizer-and-parallelizer-messages"></a>Сообщения векторизатора и параллелизатора

Можно использовать параметры компилятора Microsoft C++ [`/Qpar-report`](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md) и [`/Qvec-report`](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md) настроить [автоматическую параллелизации и автоматическое](../../parallel/auto-parallelization-and-auto-vectorization.md) упорядочивание для вывода кодов причин и информационных сообщений о его активности. В этой статье описываются коды причины и сообщения.

## <a name="informational-messages"></a><a name="BKMK_InformationalMessages"></a> Информационные сообщения

В зависимости от заданного уровня отчетов для каждого цикла выводится одно из следующих информационных сообщений.

Сведения о кодах причины см. в следующей части статьи.

| Информационное сообщение | Описание |
|--|--|
| 5001 | Цикл векторизирован. |
| 5002 | Цикл не был векторен из-за причины "*Описание*". |
| 5011 | Цикл параллелизован. |
| 5012 | Цикл не был параллельен из-за причины "*Описание*". |
| 5021 | Не удалось связать цикл с директивой pragma. |

В следующих разделах перечислены возможные коды причин для параллелизатора и векторизатора.

## <a name="5xx-reason-codes"></a><a name="BKMK_ReasonCode50x"></a> коды причин 5xx

Коды причин 5 *XX* применяются как к параллелизатора, так и к векторизатора.

| Код причины | Объяснение |
|--|--|
| 500 | Универсальное сообщение, охватывающее несколько вариантов (например, цикл включает несколько выходов), или заголовок цикла не заканчивается путем увеличения переменной удержания. |
| 501 | Переменная удержания не является локальной. или верхняя граница не является инвариантным циклом. |
| 502 | Индукционная переменная изменяется не простым приращением на 1, а каким-то другим образом. |
| 503 | Цикл содержит обработку исключений или операторы switch. |
| 504 | Тело цикла может вызвать исключение, которое требует удаления объекта C++. |

```cpp
void code_500(int *A)
{
    // Code 500 is emitted if the loop has non-vectorizable flow.
    // This can include "if", "break", "continue", the conditional
    // operator "?", or function calls.
    // It also encompasses correct definition and use of the induction
    // variable "i", in that the increment "++i" or "i++" must be the last
    // statement in the loop.

    int i = 0;
    while (i<1000)
    {
        if (i == 4)
        {
            break;
        }

        ++i;

        A[i] = A[i] + 1;
    }
    // To resolve code 500, use a 'for' loop with single increment of
    // induction variable.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

int bound();
void code_501_example1(int *A)
{
    // Code 501 is emitted if the compiler cannot discern the
    // induction variable of this loop. In this case, when it checks
    // the upperbound of 'i', the compiler cannot prove that the
    // function call "bound()" returns the same value each time.
    // Also, the compiler cannot prove that the call to "bound()"
    // does not modify the values of array A.

    for (int i=0; i<bound(); ++i)
    {
        A[i] = A[i] + 1;
    }

    // To resolve code 501, ensure that the induction variable is
    // a local variable, and ensure that the upperbound is a
    // provably loop invariant value.

    for (int i=0, imax = bound(); i<imax; ++i)
    {
        A[i] = A[i] + 1;
    }
}

int i;
void code_501_example2(int *A)
{
    // Code 501 is emitted if the compiler cannot discern the
    // induction variable of this loop. In this case, 'i' is
    // a global.

    for (i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }

    // To resolve code 501, ensure that the induction variable is
    // a local variable, and ensure that the upperbound is a
    // provably loop invariant value.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_502(int *A)
{
    // Code 502 is emitted if the compiler cannot discern
    // the induction variable of the loop. In this case,
    // there are three increments to "i", one of which
    // is conditional.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
        ++i;

        if (i < 100)
        {
            ++i;
        }
    }

    // To resolve code 502, ensure that there is just one
    // increment of the induction variable, placed in the usual
    // spot in the "for" loop.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_503(int *A, int x)
{
    // Code 503 is emitted if there are inadmissible
    // operations in the loop - for example, exception handling and
    // switch statements.

    for (int i = 0; i<1000; ++i)
    {
        switch (x)
        {
        case 1: A[i] = A[i] + 1;
        case 2: A[i] = A[i] + 2;
        case 3: A[i] = A[i] + 3;
            break;
        }
    }

    // To resolve code 503, try to remove as many switch statements
    // and exception handling constructs as possible.
}

// compile with /EHsc

int code_504_helper();
class C504
{
public:
    C504();
    ~C504();
};

void code_504(int *A) {
    // Code 504 is emitted if a C++ object was created and
    // that object requires EH unwind tracking information under
    // /EHs or /EHsc.

    for(int i = 0; i < 1000; ++i)
    {
        C504 c;
        A[i] = code_504_helper();
    }

}
```

## <a name="10xx-reason-codes"></a><a name="BKMK_ReasonCode100x"></a> коды причин 10xx

Коды причин 10 *XX* относятся к параллелизатора.

| Код причины | Объяснение |
|--|--|
| 1000 | Компилятор обнаружил зависимость данных в теле цикла. |
| 1001 | Компилятор обнаружил в теле цикла присваивание скалярной переменной, и эта скалярная переменная используется вне цикла. |
| 1002 | Компилятор попытался распараллелить цикл, содержащий вложенный уже параллелизованный цикл. |
| 1003 | Тело цикла содержит встроенный вызов, который может считывать данные из памяти и записывать их в память. |
| 1004 | В теле цикла есть скалярное сокращение. Скалярная редукция может возникать при векторизации цикла. |
| 1005 | `no_parallel`Указана директива pragma. |
| 1006 | Эта функция содержит OpenMP. Устраните эту проблему, удалив OpenMP в этой функции. |
| 1007 | Переменная выведения цикла или границы цикла не подписаны на 32-разрядные числа ( `int` или `long` ). Устраните его, изменив тип переменной удержания. |
| 1008 | Компилятор обнаружил, что этот цикл не выполняет достаточную работу для выравнивания автоматической параллелизации. |
| 1009 | Компилятор обнаружил попытку параллелизации `do` - `while` цикла "". Циклы параллелизатора только для целей Auto `for` . |
| 1010 | Компилятор обнаружил, что цикл использует "not-equaled" ( `!=` ) для своего условия. |

```cpp
int A[1000];
void func();
void code_1000()
{
    // Code 1000 is emitted if the compiler detects a
    // data dependence in the loop body.

    // You can resolve this by using the ivdep pragma.
    // CAUTION -- the compiler will trust your
    // assertion that there are no data dependencies
    // in the loop body. If there are, you are generating
    // code that may have race conditions.

#pragma loop(hint_parallel(0))
    //#pragma loop(ivdep) // ivdep will force this through.
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i-1] + 1;  // data dependence here
        func();             // data dependence here
    }
}

int code_1001()
{
    // Code 1001 is emitted if the compiler detects
    // a store to a scalar variable in the loop
    // body, and that scalar has a use beyond the loop.

    // Resolve this by rewriting your code so
    // that the scalar is not needed.

    int s = 0;
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i)
    {
        s = A[i];
    }
    return s;
}

void code_1002()
{
    // Code 1002 is emitted when the compiler tries to
    // parallelize a loop that has an inner loop that
    // has already been parallelized.

#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) // emit code 1002 for this loop
    {
#pragma loop(hint_parallel(0))
        for (int j=0; j<1000; ++j) // this loop gets parallelized
        {
            A[j] = A[j] + 1;
        }
    }
}

extern "C" void __stosb(unsigned char*, unsigned char, size_t);
void code_1003(unsigned char *dst)
{
    // Code 1003 is emitted when the loop body contains an intrinsic
    // call that may read or write to memory.

    // This can be resolved by using the ivdep pragma.
    // CAUTION -- the compiler will trust your
    // assertion that there are no data dependencies
    // in the loop body. If there are, you are generating
    // code that may have race conditions.

#pragma loop(hint_parallel(0))
    //#pragma loop(ivdep) // ivdep will force this through.
    for (int i=0; i<1000; ++i)
    {
        __stosb(dst, 'c', 10);
        A[i] = A[i] + 1;
    }
}

int code_1004()
{
    // Code 1004 is emitted when there is a scalar reduction
    // in the loop body, which can occur if the loop has been
    // vectorized.

    // You can resolve this by rewriting your code so that it
    // does not have a scalar reduction.

    int s = 0;
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i)
    {
        s += A[i];
    }
    return s;
}

void code_1005()
{
    // Code 1005 is emitted when the
    // no_parallel pragma is specified.

#pragma loop(no_parallel)
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

#include <omp.h>

// Compile with /openmp
void code_1006()
{
    // Code 1006 is emitted when this function contains
    // openmp. Resolve this by removing any openmp in this
    // function.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }

#pragma omp parallel num_threads(4)
    {
        int i = omp_get_thread_num();
        A[i] = A[i] + 1;
    }
}

void code_1007()
{
    // Code 1007 is emitted when the loop induction variable
    // or the loop bounds are not signed 32-bit numbers (int
    // or long). Resolve this by changing the type of the
    // induction variable.

#pragma loop(hint_parallel(0))
    for (unsigned int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_1008()
{
    // Code 1008 is emitted when the compiler detects that
    // this loop does not perform enough work to warrant
    // auto-parallelization.

    // You can resolve this by specifying the hint_parallel
    // pragma. CAUTION -- if the loop does not perform
    // enough work, parallelizing might cause a potentially
    // large performance penalty.

    // #pragma loop(hint_parallel(0)) //  hint_parallel will force this through
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_1009()
{
    // Code 1009 is emitted when the compiler tries to parallelize a
    // "do-while" loop. The auto-parallelizer only targets "for" loops.

    int i = 0;
#pragma loop(hint_parallel(0))
    do
    {
        A[i] = A[i] + 1;
    }
    while (++i < 1000);
}

void code_1010()
{
    // Code 1010 is emitted when the compiler tries to parallelize a
    // loop with a condition code of "!=".

    // You can resolve this by replacing it with an ordering comparator
    // like "<".
#pragma loop(hint_parallel(0))
    for (int i = 0; i != 1000; ++i)
    {
        A[i]++;
    }
}
```

## <a name="11xx-reason-codes"></a><a name="BKMK_ReasonCode110x"></a> коды причин 11xx

Коды причин 11 *XX* применяются к векторизатора.

| Код причины | Объяснение |
|--|--|
| 1100 | Цикл содержит поток управления, например " `if` " или " `?:` ". |
| 1101 | Цикл содержит преобразование DataType, возможно, неявное, которое не может быть векторным. |
| 1102 | Цикл содержит неарифметические или другие невекторизуемые операции. |
| 1103 | Тело цикла содержит операции сдвига, размер которых может меняться внутри цикла. |
| 1104 | Тело цикла содержит скалярные переменные. |
| 1105 | Цикл включает нераспознанную операцию сокращения. |
| 1106 | Внешний цикл не векторизован. |

```cpp
void code_1100(int *A, int x)
{
    // Code 1100 is emitted when the compiler detects control flow
    // in the loop - for example, "if", the ternary operator "?", and
    // the like. Resolve this by flattening or removing control
    // flow in the loop body.

    // Not all control flow causes 1100; some is indeed
    // vectorized.

    for (int i=0; i<1000; ++i)
    {
        // straightline code is more amenable to vectorization
        if (x)
        {
            A[i] = A[i] + 1;
        }
    }
}

extern "C" int __readcr0();
void code_1102(int *A)
{
    // Code 1102 is emitted when the compiler is unable to vectorize
    // an operation in the loop body. For example, intrinsics and other
    // non-arithmetic, non-logical, and non-memory operations are not
    // vectorizable.

    // Resolve this by removing as many non-vectorizable operations
    // as possible from the loop body.

    for (int i=0; i<1000; ++i)
    {
        A[i] = __readcr0();
    }
}

void code_1103(int *A, int *B)
{
    // Code 1103 is emitted when the compiler is unable to vectorize
    // a "shift" operation. In this example, there are two shifts
    // that cannot be vectorized.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] >> B[i]; // not vectorizable

        int x = B[i];
        A[i] = A[i] >> x; // not vectorizable
    }

    // To resolve this, ensure that your shift amounts are loop
    // invariant. If the shift amounts cannot be loop invariant,
    // it may not be possible to vectorize this loop.

    int x = B[0];
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] >> x; // vectorizable
    }
}

int code_1104(int *A, int *B)
{
    // When it vectorizes a loop, the compiler must 'expand' scalar
    // variables to a vector size such that they can fit in
    // vector registers. Code 1104 is emitted when the compiler
    // cannot 'expand' such scalars.

    // In this example, we try to 'expand' x to be used in the
    // vectorized loop. However, there is a use of 'x'
    // beyond the loop body, which prohibits this expansion.

    // To resolve this, try to limit scalars to be used only in
    // the loop body and not beyond, and try to keep their types
    // consistent with the loop types.

    int x;
    for (int i=0; i<1000; ++i)
    {
        x = B[i];
        A[i] = A[i] + x;
    }

    return x;
}

int code_1105(int *A)
{
    // The compiler performs an optimization that's known as "reduction"
    // when it operates on each element of an array and computes
    // a resulting scalar value - for example, in this piece of code, which
    // computes the sum of each element in the array:

    int s = 0;
    for (int i=0; i<1000; ++i)
    {
        s += A[i]; // vectorizable
    }

    // The reduction pattern must resemble the loop in the example. The
    // compiler emits code 1105 if it cannot deduce the reduction
    // pattern, as shown in this example:

    for (int i=0; i<1000; ++i)
    {
        s += A[i] + s;  // code 1105
    }

    // Similarly, reductions of "float" or "double" types require
    // that the /fp:fast switch is thrown. Strictly speaking,
    // the reduction optimization that the compiler performs uses
    // "floating point reassociation". Reassociation is only
    // allowed when /fp:fast is thrown.

    return s;
}

void code_1106(int *A)
{
    // Code 1106 is emitted when the compiler tries to vectorize
    // an outer loop.

    for (int i=0; i<1000; ++i) // this loop is not vectorized
    {
        for (int j=0; j<1000; ++j) // this loop is vectorized
        {
            A[j] = A[j] + 1;
        }
    }
}
```

## <a name="12xx-reason-codes"></a><a name="BKMK_ReasonCode120x"></a> коды причин 12xx

Коды причин 12 *XX* относятся к векторизатора.

| Код причины | Объяснение |
|--|--|
| 1200 | Цикл содержит зависимости данных, перенесенные циклом, которые предотвращают векторную обработку. Разные итерации цикла взаимодействуют друг с другом, так как векторизинг цикл выдаст неверные ответы, а функция Auto-векторизатора не может доказать себе, что такая зависимость данных отсутствует. |
| 1201 | База массива изменяется в цикле. |
| 1202 | Поле в структуре не имеет 32 или 64 бит в ширину. |
| 1203 | Тело цикла содержит несмежный доступ к массиву. |
| 1204 | Достигнут предел внутренней структуры данных компилятора: слишком много границ зависимостей данных. |

```cpp
void fn();
void code_1200(int *A)
{
    // Code 1200 is emitted when data dependence is prohibiting
    // vectorization. This can only be resolved by rewriting the
    // loop, and considering the marking of loop function calls as
    // __forceinline.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i-1] + 1; // vectorization-prohibiting
        fn();               // vectorization-prohibiting
    }
}

void code_1201(int *A)
{
    // Code 1201 is emitted when an array base changes
    // in the loop body. Resolve this by rewriting your
    // code so that varying the array base is not necessary.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
        A++;
    }
}

struct S_1202
{
    short a;
    short b;
} s[1000];

short sA[1000], sB[1000], sC[1000];

void code_1202(S_1202 *s)
{
    // Code 1202 is emitted when non-vectorizable struct accesses
    // are present in the loop body. Only struct accesses
    // that are 32 or 64 bits are vectorized.

    for (int i=0; i<1000; ++i)
    {
        s[i].a = s[i].b + 1; // this 16 bit struct access is not vectorizable
        sA[i] += sB[i] * sC[i]; // this ensures we don't emit reason code '1300'
    }
}

void code_1203(int *A)
{
    // Code 1203 is emitted when non-vectorizable memory references
    // are present in the loop body. Vectorization of some non-contiguous
    // memory access is supported - for example, the gather/scatter pattern.

    for (int i=0; i<1000; ++i)
    {
        A[i] += A[0] + 1;       // constant memory access not vectorized
        A[i] += A[i*2+2] + 2;  // non-contiguous memory access not vectorized
    }
}

void code_1204(int *A)
{
    // Code 1204 is emitted when internal compiler data structures
    // hit a limit on the number of data dependence edges recorded.
    // Resolve this by moving the innermost loop to another function.

    for (int i=0; i<1000; i++)
        for (int j=0; j<1000; j++)
            for (int k=0; k<1000; k++)
                for (int l=0; l<1000; l++)
                {
                    for (int m=0; m<1000; m++)
                        A[m] = A[m+i] + A[m+j] + A[m+k] + A[m+l];
                }
}
```

## <a name="13xx-reason-codes"></a><a name="BKMK_ReasonCode130x"></a> коды причин 13xx

Коды причин 13 *XX* относятся к векторизатора.

| Код причины | Объяснение |
|--|--|
| 1300 | Тело цикла не содержит вычислений или объем вычислений очень мал. |
| 1301 | Шаг цикла не + 1. |
| 1302 | Loop — это " `do` - `while` ". |
| 1303 | Слишком мало итераций цикла для эффективной векторизации. |
| 1304 | Цикл содержит присваивания различных размеров. |
| 1305 | Недостаточно сведений о типе. |

```cpp
void code_1300(int *A, int *B)
{
    // Code 1300 is emitted when the compiler detects that there is
    // no computation in the loop body.

    for (int i=0; i<1000; ++i)
    {
        A[i] = B[i]; // Do not vectorize, instead emit memcpy
    }
}

void code_1301(int *A)
{
    // Code 1301 is emitted when the stride of a loop is not positive 1.
    // Only loops that have a stride of positive 1 are vectorized;
    // rewriting your loop may be required.

    for (int i=0; i<1000; i += 2)
    {
        A[i] = A[i] + 1;
    }
}

void code_1302(int *A)
{
    // Code 1302 is emitted for "do-while" loops. Only "while"
    // and "for" loops are vectorized.

    int i = 0;
    do
    {
        A[i] = A[i] + 1;
    } while (++i < 1000);
}

int code_1303(int *A, int *B)
{
    // Code 1303 is emitted when the compiler detects that
    // the number of iterations of the loop is too small to
    // make vectorization profitable.

    // If the loop computation fits perfectly in
    // vector registers - for example, the upperbound is 4, or 8 in
    // this case - then the loop _may_ be vectorized.

    // This loop is not vectorized because there are 5 iterations

    for (int i=0; i<5; ++i)
    {
        A[i] = A[i] + 1;
    }

    // This loop is vectorized

    for (int i=0; i<4; ++i)
    {
        A[i] = A[i] + 1;
    }

    // This loop is not vectorized because runtime pointer checks
    // are required to check that A and B don't overlap. It is not
    // worth it to vectorize this loop.

    for (int i=0; i<4; ++i)
    {
        A[i] = B[i] + 1;
    }

    // This loop is not vectorized because of the scalar reduction.

    int s = 0;
    for (int i=0; i<4; ++i)
    {
        s += A[i];
    }
    return s;
}

void code_1304(int *A, short *B)
{
    // Code 1304 is emitted when the compiler detects
    // different sized statements in the loop body.
    // In this case, there is an 32-bit statement and a
    // 16-bit statement.

    // In cases like this consider splitting the loop into loops to
    // maximize vector register utilization.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
        B[i] = B[i] + 1;
    }
}

typedef struct S_1305
{
    int a;
    int b;
} S_1305;

void code_1305( S_1305 *s, S_1305 x)
{
    // Code 1305 is emitted when the compiler can't discern
    // proper vectorizable type information for this loop.
    // This includes non-scalar loop types such as struct
    // assignments, as in this example.

    // Resolve this by ensuring that your loops have statements
    // that operate on integers or floating point types.

    for (int i=0; i<1000; ++i)
    {
        s[i] = x;
    }
}
```

## <a name="14xx-reason-codes"></a><a name="BKMK_ReasonCode140x"></a> коды причин 14xx

Коды причины 14 *XX* возникают, если задан какой-либо параметр, несовместимый с вектором.

| Код причины | Объяснение |
|--|--|
| 1400 | `#pragma loop(no_vector)`Указана директива . |
| 1401 | `/kernel`Для целевой архитектуры x86 или ARM указан ключ . |
| 1402 | `/arch:SSE2` при нацеливании на x86 параметр не указывается или выше. |
| 1403 | `/arch:ATOM` указан параметр, а цикл включает операции с Double. |
| 1404 | `/O1``/Os`указан параметр или. |
| 1405 | Векторизация отключается для упрощения оптимизации с переводом динамического инициализатора в статический. |

```cpp
void code_1400(int *A)
{
    // Code 1400 is emitted when the no_vector pragma
    // is specified.

#pragma loop(no_vector)
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /kernel
void code_1401(int *A)
{
    // Code 1401 is emitted when /kernel is specified.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /arch:IA32
void code_1402(int *A)
{
    // Code 1401 is emitted when /arch:IA32 is specified.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /favor:ATOM
void code_1403(double *A)
{
    // Code 1401 is emitted when /favor:ATOM is specified, and
    // the loop contains operations on "double" arrays.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /O1 or /Os
void code_1404(int *A)
{
    // Code 1401 is emitted when compiling for size.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}
```

## <a name="15xx-reason-codes"></a><a name="BKMK_ReasonCode150x"></a> коды причин 15xx

Коды причины 15 *XX* применяются к псевдонимам. Совмещение имен возникает, когда одно и тоже расположение в памяти доступно под двумя разными именами.

| Код причины | Объяснение |
|--|--|
| 1500 | Возможно совмещение имен для многомерных массивов. |
| 1501 | Возможно совмещение имен для массивов структур. |
| 1502 | Возможно совмещение имен, и индекс массива отличается от n + K. |
| 1503 | Возможно совмещение имен, и индекс массива имеет несколько смещений. |
| 1504 | Возможно совмещение имен; требуется слишком много проверок во время выполнения. |
| 1505 | Возможно совмещение имен, а проверки во время выполнения слишком сложные. |

```cpp
void code_1500(int A[100][100], int B[100][100])
{
    // Code 1500 is emitted when runtime pointer
    // disambiguation checks are required, and
    // there are multidimensional array references.

    for (int i=0; i<100; ++i)
    {
        for (int j=0; j<100; ++j)
        {
            A[i][j] = B[i][j] + 1;
        }
    }
}

typedef struct S_1501
{
    int a;
    int b;
} S_1501;

int iA[1000], iB[1000], iC[1000];

void code_1501(S_1501 *s1, S_1501 *s2)
{
    // Code 1501 is emitted when runtime pointer
    // disambiguation checks are required, and
    // there are array-of-struct accesses in the
    // loop body.

    for (int i=0; i<100; ++i)
    {
        s1[i].a = s2[i].b + 1;
        iA[i] += iB[i] * iC[i]; // this is to ensure we don't emit reason code '1300'
    }
}

void code_1502(int *A, int *B)
{
    // Code 1502 is emitted when runtime pointer
    // disambiguation checks are required, and
    // an array reference has an offset that varies
    // in the loop.

    int x = 0;
    for (int i=0; i<100; ++i)
    {
        A[i] = B[i + x] + 1;
        ++x;                   // 'x' varies in the loop
    }
}

void code_1503(int *A, int *B, int x, int y)
{
    // Code 1503 is emitted when runtime pointer
    // disambiguation checks are required, and
    // an array reference has multiple offsets.

    for (int i=0; i<100; ++i)
    {
        A[i] = B[i+x] + B[i+y] + 1;   // multiple offsets when addressing 'B': {x, y}
        A[i] = B[i+x] + B[i] + 1;     // multiple offsets when addressing 'B': {x, 0}
        A[i] = B[i+x] + B[i+x] + 1;   // this is vectorized
    }
}

void code_1504(int *A1, int *A2, int *A3, int *A4,
               int *A5, int *A6, int *A7, int *A8,
               int *A9, int *A10, int *A11, int *A12,
               int *A13, int *A14, int *A15, int *A16)
{
    // Code 1504 is emitted when too many runtime
    // pointer disambiguation checks are required.

    for (int i=0; i<100; ++i)
    {
        ++A1[i];
        ++A2[i];
        ++A3[i];
        ++A4[i];
        ++A5[i];
        ++A6[i];
        ++A7[i];
        ++A8[i];
        ++A9[i];
        ++A10[i];
        ++A11[i];
        ++A12[i];
        ++A13[i];
        ++A14[i];
        ++A15[i];
        ++A16[i];
    }
}

void code_1505(int *A, int *B)
{
    // Code 1505 is emitted when runtime pointer
    // disambiguation checks are required, but are
    // too complex for the compiler to discern.

    for (int i=0; i<100; ++i)
    {
        for (int j=0; j<100; ++j)
        {
            for (int k=0; k<100; ++k)
            {
                A[i+j-k] = B[i-j+k] * 2;
            }
        }
    }
}
```

## <a name="see-also"></a>См. также

[Ошибки и предупреждения для компилятора C/C++ и средств сборки](../compiler-errors-1/c-cpp-build-errors.md)\
[Автомасштабирование и автовектор](../../parallel/auto-parallelization-and-auto-vectorization.md)\
[Автоматическое векторизатора в Visual Studio 2012 — Обзор](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)\
[`#pragma loop()`](../../preprocessor/loop.md)\
[`/Q` Параметры (низкоуровневые операции)](../../build/reference/q-options-low-level-operations.md)\
[`/Qpar-report` (Auto-Параллелизатора Report Level)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)\
[`/Qvec-report` (Auto-векторизатора Report Level)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)
