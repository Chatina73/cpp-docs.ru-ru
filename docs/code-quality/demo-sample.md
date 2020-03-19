---
title: Пример проекта C++ для анализа кода
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: 1966e9cec5825ae37728bbf28c0f21ff4eed62fc
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467223"
---
# <a name="sample-c-project-for-code-analysis"></a>Пример проекта C++ для анализа кода

В следующих процедурах показано, как создать пример для [пошагового руководства: анализC++ C/Code для дефектов](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Эти процедуры создают следующее:

- Решение Visual Studio с именем CppDemo.

- Проект статической библиотеки CodeDefects.

- Проект статической библиотеки Annotations.

Кроме того, эти процедуры предоставляют код для заголовка и *CPP*-файлов для статических библиотек.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Создание решения CppDemo и проекта CodeDefects

1. Откройте Visual Studio и выберите **создать новый проект** .

1. Изменить языковой фильтр на **C++**

1. Выберите **Пустой проект** и нажмите кнопку **Далее**

1. В текстовом поле **Имя проекта** введите **CodeDefects**.

1. В текстовом поле **Имя решения** введите **CppDemo**.

1. Нажмите кнопку **Создать**.

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Настройка проекта CodeDefects в качестве статической библиотеки

1. В обозревателе решений щелкните правой кнопкой мыши проект **CodeDefects** и выберите пункт **Свойства**.

1. Разверните пункт **Свойства конфигурации** и выберите **Общие**.

1. В списке **Общее** измените **тип конфигурации** на **Статическая библиотека (.lib)** .

1. В списке **Дополнительно** измените **целевое расширение файла** на **.lib**

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Добавление заголовка и исходного файла в проект CodeDefects

1. В обозревателе решений разверните **CodeDefects**, щелкните правой кнопкой мыши элемент **Файлы заголовков**, выберите пункт **Добавить**, а затем пункт **Новый элемент**.

1. В диалоговом окне **Добавление нового элемента** щелкните **Код** и выберите **Файл заголовка (.h)** .

1. В поле **Имя** введите **Bug.h** и нажмите кнопку **Добавить**.

1. Скопируйте приведенный ниже код и вставьте его в файл *Bug.h* в редакторе.

    ```cpp
    #pragma once

    #include <windows.h>

    // These functions are consumed by the sample
    // but are not defined. This project cannot be linked!
    bool CheckDomain(LPCTSTR);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. В обозревателе решений щелкните правой кнопкой мыши **Исходные файлы** и последовательно выберите пункты **Создать** и **Новый элемент**.

1. В окне **Добавление нового элемента** щелкните **Файл C++ (.cpp)** .

1. В поле **Имя** введите **Bug.cpp** и нажмите кнопку **Добавить**.

1. Скопируйте приведенный ниже код и вставьте его в файл *Bug.cpp* в редакторе.

    ```cpp
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == '\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = '\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. Откройте меню **Файл** и щелкните пункт **Сохранить все**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Добавление проекта Annotations и его настройка в качестве статической библиотеки

1. В обозревателе решений щелкните **CppDemo** и последовательно выберите пункты **Добавить** и **Новый проект**.

1. В диалоговом окне **Добавить новый проект** измените языковой фильтр на **C++** и выберите **Пустой проект**, а затем нажмите кнопку **Далее**.

1. В текстовом поле **Имя проекта** введите **Аннотации** и нажмите кнопку **Создать**.

1. В обозревателе решений щелкните правой кнопкой мыши проект **Annotations** и выберите пункт **Свойства**.

1. Разверните пункт **Свойства конфигурации** и выберите **Общие**.

1. В списке **Общее** измените **тип конфигурации** на "Статическая библиотека (.lib)", а затем щелкните **Статическая библиотека (.lib)** .

1. В списке **Дополнительно** выберите текст в столбце рядом с полем **Расширение целевого файла**, а затем введите **.lib**.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Добавление файла заголовка и исходного файла в проект Annotations

1. В обозревателе решений разверните **Annotations**, щелкните правой кнопкой мыши элемент **Файлы заголовков**, выберите пункт **Добавить**, а затем пункт **Новый элемент**.

1. В окне **Добавление нового элемента** щелкните **Файл заголовка (.h)** .

1. В поле **Имя** введите **annotations.h** и нажмите кнопку **Добавить**.

1. Скопируйте приведенный ниже код и вставьте его в файл *annotations.h* в редакторе.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. В обозревателе решений щелкните правой кнопкой мыши **Исходные файлы** и последовательно выберите пункты **Создать** и **Новый элемент**.

1. В диалоговом окне **Добавление нового элемента** щелкните **Код** и выберите **Файл C++ (.cpp)** .

1. В поле **Имя** введите **annotations.cpp** и нажмите кнопку **Добавить**.

1. Скопируйте приведенный ниже код и вставьте его в файл *annotations.cpp* в редакторе.

    ```cpp
    #include "annotations.h"

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. Откройте меню **Файл** и щелкните пункт **Сохранить все**.

Теперь решение завершено и должно создаться без ошибок.
