---
title: 3.1.1 Функция omp_set_num_threads
ms.date: 11/04/2016
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
ms.openlocfilehash: 20b6b6ced2b4031696f1d019604842ae9b91bda2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663285"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 Функция omp_set_num_threads

`omp_set_num_threads` Функция задает количество потоков, используемых для последующих параллельных регионов не указано, по умолчанию `num_threads` предложение. Он следующий:

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Значение параметра *num_threads* должно быть положительным целым числом. Ее результат зависит от того, включен ли динамическую настройку количество потоков. Доступен широкий набор правил о взаимодействии между `omp_set_num_threads` функция и динамическую настройку потоков, см. в разделе 2.3 раздел на странице "8".

Эта функция имеет эффекты, описанных выше, при вызове из части программы где `omp_in_parallel` функция возвращает нуль. Если он вызывается из части программы где `omp_in_parallel` функция возвращает ненулевое значение, то поведение этой функции не определено.

Этот вызов имеет приоритет над `OMP_NUM_THREADS` переменной среды. Значение по умолчанию для количества потоков, которые могут быть установлены, вызвав `omp_set_num_threads` или задав `OMP_NUM_THREADS` переменной среды, можно явно переопределить на отдельном **параллельных** директив, указав `num_threads` предложение.

## <a name="cross-references"></a>Перекрестные ссылки:

- `omp_set_dynamic` функции, см. в разделе [разделе 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) на стр. 39.

- `omp_get_dynamic` функции, см. в разделе [разделе 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) на странице 40.

- `OMP_NUM_THREADS` переменной, см. в разделе среды [разделе 4.2](../../parallel/openmp/4-2-omp-num-threads.md) на стр. 48 и разделе 2.3 на странице "8".

- `num_threads` предложение, см. в разделе [разделе 2.3](../../parallel/openmp/2-3-parallel-construct.md) на странице "8"