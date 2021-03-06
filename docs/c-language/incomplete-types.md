---
description: 'Подробнее о следующем: Неполные типы'
title: Неполные типы
ms.date: 11/04/2016
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
ms.openlocfilehash: b85d7a703d6687ad7ec1b0476b8b8a43930330dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243579"
---
# <a name="incomplete-types"></a>Неполные типы

*Неполный тип* — это тип, который описывает идентификатор, но не содержит информацию, необходимую для определения размера идентификатора. Неполным типом может быть:

- Тип структуры, для которой еще не были определены члены.

- Тип объединения для которого еще не были определены члены.

- Тип массива, для которого еще не были определены размерности.

Тип **`void`** является неполным типом, который невозможно сделать полным. Чтобы дополнить неполный тип, укажите отсутствующие данные. В следующих примерах показано, как создать и дополнить неполные типы.

- Чтобы создать неполный тип структуры, объявите тип структуры, не указывая ее члены. В этом примере указатель `ps` указывает на неполный тип структуры с именем `student`.

    ```C
    struct student *ps;
    ```

- Чтобы дополнить неполный тип структуры, объявите тот же самый тип структуры ниже в той же самой области видимости и задайте его члены, как в следующем примере:

    ```C
    struct student
    {
        int num;
    }                   /* student structure now completed */
    ```

- Чтобы создать неполный тип массива, объявите тип массива, не указывая для него число повторений. Пример:

    ```C
    char a[];  /* a has incomplete type */
    ```

- Чтобы дополнить неполный тип массива, объявите то же самое имя ниже в той же самой области видимости и задайте его число повторений, как в следующем примере:

    ```C
    char a[25]; /* a now has complete type */
    ```

## <a name="see-also"></a>См. также

[Объявления и типы](../c-language/declarations-and-types.md)
