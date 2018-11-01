---
title: _set_new_handler
ms.date: 11/04/2016
apiname:
- _set_new_handler
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: bc7718503f59c69868a75cac9383286a548fc307
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640314"
---
# <a name="setnewhandler"></a>_set_new_handler

Передает управление механизму обработки ошибок, если оператору **new** не удается выделить память.

## <a name="syntax"></a>Синтаксис

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>Параметры

*pNewHandler*<br/>
Указатель на предоставленную приложением функцию обработки памяти. Аргумент 0 вызывает удаление нового обработчика.

## <a name="return-value"></a>Возвращаемое значение

Возвращает указатель на предыдущее исключение, обработка функцию, зарегистрированную функцией **_set_new_handler**, таким образом, чтобы можно было впоследствии восстановить предыдущую функцию. Если предыдущая функция не задана, возвращаемое значение может использоваться для восстановления поведения по умолчанию; Это значение может быть **NULL**.

## <a name="remarks"></a>Примечания

C++ **_set_new_handler** функция указывает функцию обработки исключений, которая получает управление, если **новый** оператор не удается выделить память. Если **новый** завершается ошибкой, система времени выполнения автоматически вызывает функцию обработки исключений, которая была передана в качестве аргумента для **_set_new_handler**. **_PNH**, определенный в New.h, является указателем на функцию, возвращающую тип **int** и принимает аргумент типа **size_t**. Используйте **size_t** указывает объем выделяемого пространства.

Обработчик по умолчанию отсутствует.

**_set_new_handler** — по сути это схема сбора мусора. Система времени выполнения делает попытку выделения памяти каждый раз, когда пользовательская функция возвращает ненулевое значение, и завершается неудачей, если пользовательская функция возвращает 0.

Вхождение **_set_new_handler** функция в программе регистрирует функцию обработки исключений, указанную в списке аргументов с системой времени выполнения:

```cpp
// set_new_handler1.cpp
#include <new.h>

int handle_program_memory_depletion( size_t )
{
   // Your code
}

int main( void )
{
   _set_new_handler( handle_program_memory_depletion );
   int *pi = new int[BIG_NUMBER];
}
```

Можно сохранить адрес функции, которая была передан последней в **_set_new_handler** функцию и восстановить ее позже:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

Функция [_set_new_mode](set-new-mode.md) C++ задает новый режим обработчика для [malloc](malloc.md). Новый режим обработки указывает, что в случае сбоя **malloc** должен вызывать новую подпрограмму обработчика, заданную функцией **_set_new_handler**. По умолчанию **malloc** не вызывает новую подпрограмму обработчика в случае сбоя процесса выделения памяти. Можно переопределить это поведение по умолчанию, чтобы, когда **malloc** не удается выделить память, **malloc** вызывала новую подпрограмму обработчика таким же образом, как **новый** делает оператор При сбое по той же причине. Чтобы переопределить значение по умолчанию, вызовите:

```cpp
_set_new_mode(1);
```

на ранних этапах программы или выполните компоновку с использованием Newmode.obj.

Если определяемый пользователем `operator new` не указан, новые функции обработчика не вызываются автоматически в случае сбоя.

Дополнительные сведения см. в разделе [new](../../cpp/new-operator-cpp.md) и [delete](../../cpp/delete-operator-cpp.md) в *Справочнике по языку C++*.

Будет только один **_set_new_handler** обработчик для всех динамически связанных файлов DLL или исполняемых файлов; даже если вы вызываете **_set_new_handler** Ваш обработчик может быть заменен другим или вы заменяете обработчик, заданный другой библиотекой DLL или исполняемый файл.

## <a name="requirements"></a>Требования

|Подпрограмма|Обязательный заголовок|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

Дополнительные сведения о совместимости см. в разделе [Совместимость](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Пример

В этом примере если выделение памяти завершается сбоем, управление передается обработчику MyNewHandler. Аргумент, переданный обработчику MyNewHandler, представляет собой запрошенное количество байтов. Значение, возвращаемое из MyNewHandler, представляет собой флаг, указывающий, нужна ли повторная попытка выделения памяти: ненулевое значение указывает, что выделение должно быть повторено, нулевое значение указывает, что произошла ошибка выделения памяти.

```cpp
// crt_set_new_handler.cpp
// compile with: /c
#include <stdio.h>
#include <new.h>
#define BIG_NUMBER 0x1fffffff

int coalesced = 0;

int CoalesceHeap()
{
   coalesced = 1;  // Flag RecurseAlloc to stop
   // do some work to free memory
   return 0;
}
// Define a function to be called if new fails to allocate memory.
int MyNewHandler( size_t size )
{
   printf("Allocation failed. Coalescing heap.\n");

   // Call a function to recover some heap space.
   return CoalesceHeap();
}

int RecurseAlloc() {
   int *pi = new int[BIG_NUMBER];
   if (!coalesced)
      RecurseAlloc();
   return 0;
}

int main()
{
   // Set the failure handler for new to be MyNewHandler.
   _set_new_handler( MyNewHandler );
   RecurseAlloc();
}
```

```Output
Allocation failed. Coalescing heap.

This application has requested the Runtime to terminate it in an unusual way.
Please contact the application's support team for more information.
```

## <a name="see-also"></a>См. также

[Выделение памяти](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
