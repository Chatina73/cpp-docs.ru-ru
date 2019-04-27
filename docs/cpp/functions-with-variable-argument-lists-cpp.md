---
title: Функции с переменным аргументом списками (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: 1f366af6f4058ffb8356017d59a7c176a978b860
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153857"
---
# <a name="functions-with-variable-argument-lists--c"></a>Функции с переменным аргументом списками (C++)

Функции, в объявлениях которых в качестве последнего члена указано многоточие (...), могут принимать переменное число аргументов. В таких случаях C++ обеспечивает проверку типа только для явно объявленных аргументов. Переменные списки аргументов можно использовать, если функция должна быть настолько универсальной, что могут изменяться даже количество и типы аргументов. Семейство функций является примером функций, которые используются переменные списки аргументов. `printf` *список объявлений аргументов*

## <a name="functions-with-variable-arguments"></a>Функции с переменными аргументами

Для доступа к аргументам после объявленных, используйте макрос, содержащийся в стандартном включаемом файле \<stdarg.h > как описано ниже.

**Блок, относящийся только к системам Microsoft**

Microsoft C++ допускает указывать многоточие в качестве аргумента, если это последний аргумент и перед многоточием стоит запятая. Поэтому объявление `int Func( int i, ... );` допускается, а объявление `int Func( int i ... );` — нет.

**Завершение блока, относящегося только к системам Майкрософт**

В объявлении функции, которая принимает переменное число аргументов, требуется по крайней мере один аргумент-местозаполнитель, даже если он не используется. Если этот аргумент-местозаполнитель не указан, доступ к остальным аргументам невозможен.

Если аргументы типа **char** передаются как переменные аргументы, они преобразуются в тип **int**. Аналогичным образом, если аргументы типа **float** передаются как переменные аргументы, они преобразуются в тип **двойные**. Для аргументов остальных типов могут выполняться обычные восходящие приведения целочисленных типов и типов с плавающей запятой. См. в разделе [стандартные преобразования](standard-conversions.md) Дополнительные сведения.

Функции, которым необходимы списки с переменным количеством аргументов, объявляются с многоточием (...) в списках аргументов. Использование типов и макросы, описанные в \<stdarg.h > включаемый файл для доступа к аргументам, которые передаются по списка переменных. Дополнительные сведения об этих макросах см. в разделе [va_arg, va_copy, va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). в документации по библиотеке времени выполнения C.

В следующем примере показано, каким образом макросы взаимодействуют с типом (объявлены в \<stdarg.h >):

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

Приведенный выше пример иллюстрирует следующие важные правила:

1. Перед тем как обращаться к аргументам из списка переменной длины, необходимо установить его маркер в качестве переменной типа `va_list`. В приведенном выше примере этот маркер имеет имя `vl`.

1. К отдельным аргументам можно обращаться при помощи макроса `va_arg`. Макросу `va_arg` необходимо указать тип получаемых аргументов, чтобы он мог перенести из стека нужное количество байтов. Если вы ошибетесь и укажете другой тип, а его размер не будет совпадать с типом, который вызывающая программа передает макросу `va_arg`, это может привести к непредсказуемым результатам.

1. Результат, полученный при помощи макроса `va_arg`, необходимо явным образом преобразовывать в нужный вам тип.

Для завершения обработки списка с переменным количеством аргументов необходимо вызвать макрос.`va_end`