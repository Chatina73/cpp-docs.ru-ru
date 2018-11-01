---
title: Шаги для организации типичного клиентского приложения Gopher
ms.date: 11/04/2016
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
ms.openlocfilehash: 123b8abd2ca65356c584fa52f9415504bcb701c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486428"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>Шаги для организации типичного клиентского приложения Gopher

Ниже приведены шаги, которые необходимо выполнять в организации типичного клиентского приложения gopher.

|Ваша цель|Выполняемые действия|Произведенный эффект|
|---------------|----------------------|-------------|
|Запустить сеанс gopher.|Создание [CInternetSession](../mfc/reference/cinternetsession-class.md) объекта.|Инициализирует WinInet и подключается к серверу.|
|Подключитесь к серверу gopher.|Используйте [CInternetSession::GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection).|Возвращает [CGopherConnection](../mfc/reference/cgopherconnection-class.md) объекта.|
|Найти первый ресурс в gopher.|Используйте [CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile).|Находит первый файл. Возвращает значение FALSE, если файлы не найдены.|
|Поиск следующего ресурса в gopher.|Используйте [CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile).|Находит следующий файл. Возвращает значение FALSE, если файл не найден.|
|Откройте файл обнаруженных `FindFile` или `FindNextFile` для чтения.|Получить с помощью указателя gopher [CGopherFileFind::GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator). Используйте [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Открывает файл, указанный параметром указателя. `OpenFile` Возвращает [CGopherFile](../mfc/reference/cgopherfile-class.md) объекта.|
|Откройте файл с помощью указателя gopher, указанные вами.|Создание с помощью указателя gopher [CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator). Используйте [CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile).|Открывает файл, указанный параметром указателя. `OpenFile` Возвращает [CGopherFile](../mfc/reference/cgopherfile-class.md) объекта.|
|Чтение из файла.|Используйте [CGopherFile](../mfc/reference/cgopherfile-class.md).|Считывает указанное число байтов, с помощью буфера указанные вами.|
|Обработка исключений.|Используйте [CInternetException](../mfc/reference/cinternetexception-class.md) класса.|Обрабатывает все общие типы исключений Интернет.|
|Завершите сеанс gopher.|Избавиться от [CInternetSession](../mfc/reference/cinternetsession-class.md) объекта.|Автоматически очищает открытые дескрипторы файлов и подключений.|

## <a name="see-also"></a>См. также

[Расширения Интернета Win32 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[Необходимые компоненты для клиентских классов в Интернете](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[Создание клиентских приложений в Интернете с использованием классов MFC WinInet](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
