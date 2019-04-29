---
title: noalias
ms.date: 02/09/2018
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 2eceffd10f97615859918991320ceebf577d094c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377443"
---
# <a name="noalias"></a>noalias

**Блок, относящийся только к системам Microsoft**

**noalias** означает, что вызов функции не изменять или видимое глобальное состояние и изменяет только памяти, на которую *непосредственно* , параметры-указатели (косвенные обращения первого уровня).

Если функция отмечена как **noalias**, оптимизатор может считать, что, помимо самих параметров, косвенные обращения первого уровня только для параметров-указателей или ссылаться на изменения внутри функции. Видимое глобальное состояние — это набор всех данных, который не определяются и на которые нет ссылок за пределами области компиляции, и адрес которых не берется. Область компиляции — это все исходные файлы ([/LTCG (Создание кода во время компоновки)](../build/reference/ltcg-link-time-code-generation.md) сборок) или один исходный файл (отличным от **/LTCG** сборки).

**Noalias** Аннотация применяется только в теле функции аннотирования. Функция отмечена как **__declspec(noalias)** не влияет на присвоение псевдонимов указателей, возвращаемый функцией.

Другой заметки, которые могут повлиять на присвоение псевдонимов, см. в разделе [__declspec(restrict)](../cpp/restrict.md).

## <a name="example"></a>Пример

В следующем образце показано использование **__declspec(noalias)**.

Когда функция `multiply` помечается что обращений к памяти **__declspec(noalias)**, он сообщает компилятору, что эта функция не изменяет глобальное состояние только через указатели из своего списка параметров.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>См. также

[__declspec](../cpp/declspec.md)<br/>
[Ключевые слова](../cpp/keywords-cpp.md)<br/>
[__declspec(restrict)](../cpp/restrict.md)
