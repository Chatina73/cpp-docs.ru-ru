---
title: A.19   Примеры неправильного вложения директив совместной работы
ms.date: 11/04/2016
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
ms.openlocfilehash: 5be09dd3282260dabc2ef30dafc249539d6a6418
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501950"
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19   Примеры неправильного вложения директив совместной работы

В примерах в этом разделе показаны директив вложенности правила. Дополнительные сведения о директива nesting, см. в разделе [раздела 2.9](../../parallel/openmp/2-9-directive-nesting.md) на стр. 33.

Следующий пример не соответствует требованиям из-за внутренней и внешней `for` директивы являются вложенными и привязать к тому же `parallel` директивы:

```
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

Следующая версия динамически вложенных в предыдущем примере также соответствует требованиям:

```
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

Следующий пример не соответствует требованиям поскольку `for` и `single` используются вложенные директивы, и их привязки к одной и той же параллельной области:

```
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

Следующий пример не соответствует требованиям поскольку `barrier` директив внутри `for` может вызвать взаимоблокировку:

```
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

Следующий пример не соответствует требованиям поскольку `barrier` приводит к взаимоблокировке тем, что только один поток за раз можно входить в критический раздел:

```
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

Следующий пример не соответствует требованиям поскольку `barrier` приводит к взаимоблокировке тем, что только один поток выполняет `single` раздел:

```
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```