---
description: 'Подробнее о следующем: Правила и ограничения dllimport/dllexport'
title: Правила и ограничения dllimport и dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: 6d7de92b7d58eacc9334859a865e0e1456fffcb9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97292888"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Правила и ограничения dllimport/dllexport

**Блок, относящийся только к системам Microsoft**

- Если функция объявлена без атрибута **`dllimport`** или `dllexport`, то она не считается частью интерфейса DLL. Поэтому определение функции должно находиться в том же самом модуле или в другом модуле той же программы. Для того чтобы включить функцию в интерфейс DLL, необходимо в другом модуле объявить определение функции, указав для нее атрибут `dllexport`. В противном случае при сборке клиента возникнет ошибка компоновщика.

- Если в одном и том же модуле вашей программы содержатся объявления одной и той же функции с атрибутами **`dllimport`** и `dllexport`, то атрибут `dllexport` имеет приоритет над **`dllimport`** . Однако компилятор создает предупреждение. Пример:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Вы не можете инициализировать указатель на статические данные с адресом объекта данных, объявленного с атрибутом **`dllimport`** . Например, следующий код вызывает ошибки:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport int i;
       .
       .
       .
       int *pi = &i;                           /* Error */

       void func2()
       {
          static int *pi = &i;                   /* Error */
       }

    ```

- Если при инициализации указателя на статическую функцию вы присвоите ему адрес функции, объявленной с атрибутом **`dllimport`** , то указатель будет ссылаться не на адрес функции, а на адрес преобразователя импорта DLL (это заглушка, которая передает управление функции). Следующее присваивание не порождает сообщения об ошибке:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void
       .
       .
       .
       static void ( *pf )( void ) = &func1;   /* No Error */

       void func2()
       {
          static void ( *pf )( void ) = &func1;  /* No Error */
       }

    ```

- Поскольку программа с атрибутом `dllexport` в объявлении объекта должна содержать определение этого объекта, то указатель на глобальную или локальную статическую функцию можно инициализировать с адресом функции с атрибутом `dllexport`. Аналогичным образом указатель на глобальные или локальные статические данные можно инициализировать с адресом объекта данных с атрибутом `dllexport`. Пример:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllImport int i;

       DllExport void func1( void );
       DllExport int i;
       .
       .
       .
       int *pi = &i;                            /* Okay */
       static void ( *pf )( void ) = &func1;    /* Okay */

       void func2()
       {
          static int *pi = i;                     /* Okay */
          static void ( *pf )( void ) = &func1;   /* Okay */
       }

    ```

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Функции импорта и экспорта DLL](../c-language/dll-import-and-export-functions.md)
