---
title: Функции LoadLibrary и AfxLoadLibrary
ms.date: 05/24/2018
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: 7c0b63d80a8b4b03b55d6e50af6c08a8de0937de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596556"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>Функции LoadLibrary и AfxLoadLibrary

Обрабатывает вызов [LoadLibraryExA](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexa) или [LoadLibraryExW](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibraryexw)(или [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary)) для явного связывания с библиотекой DLL. Если функция выполняется успешно, он сопоставляет указанную библиотеку DLL с адресным пространством вызывающего процесса и возвращает дескриптор библиотеки DLL, который можно использовать с другими функциями для явного связывания — например, `GetProcAddress` и `FreeLibrary`.

`LoadLibrary` пытается обнаружить библиотеку DLL с помощью той же последовательности поиска, который используется для неявного связывания. Если системе не удается найти библиотеку DLL или функция точки входа возвращает значение FALSE, `LoadLibrary` возвращает значение NULL. Если вызов `LoadLibrary` указан модуль DLL, уже сопоставленный с адресным пространством вызывающего процесса, функция возвращает дескриптор библиотеки DLL и увеличивает счетчик ссылок модуля.

Если библиотеки DLL есть функция точки входа, операционная система вызывает функцию в контексте потока, который вызвал `LoadLibrary`. Функция точки входа не вызывается, если библиотека DLL уже присоединена к процессу из-за предыдущего вызова `LoadLibrary` , имеющий не последовал вызов `FreeLibrary` функции.

Для приложений MFC, загружающих библиотеки расширений DLL MFC, мы рекомендуем использовать `AfxLoadLibrary` вместо `LoadLibrary`. `AfxLoadLibrary` обрабатывает синхронизацию потока перед вызовом метода `LoadLibrary`. Интерфейс (прототип функции) `AfxLoadLibrary` совпадает со значением `LoadLibrary`.

Если Windows не удается загрузить библиотеку DLL, процесс может попытаться восстановить выполнение после ошибки. Например процесс может уведомить пользователя об ошибке и попросите пользователя указать другой путь к библиотеке DLL.

> [!IMPORTANT]
> Не забудьте указать полный путь для всех библиотек DLL. Текущий каталог выполняется поиск при загрузке файлов. Если вы не рассматриваются как предназначенные путь к файлу, файл, который не является тот могут быть загружены. Другой способ избежать этого, — с помощью [/DEPENDENTLOADFLAG](../build/reference/dependentloadflag.md) параметр компоновщика.

## <a name="what-do-you-want-to-do"></a>Выберите действие

- [Неявное связывание с библиотекой DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)

- [Определение подходящего метода связывания](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Дополнительные сведения

- [Порядок поиска библиотеки динамической компоновки](/windows/desktop/Dlls/dynamic-link-library-search-order)

- [Функции FreeLibrary и AfxFreeLibrary](../build/freelibrary-and-afxfreelibrary.md)

- [Функция GetProcAddress](../build/getprocaddress.md)

## <a name="see-also"></a>См. также

- [DLL в Visual C++](../build/dlls-in-visual-cpp.md)
