---
description: Дополнительные сведения о облачном и веб-программировании см. в Visual C++
title: Облачное и веб-программирование в Visual C++
ms.date: 05/14/2019
ms.assetid: b63611f1-9723-44d0-ba7f-c3ebef341313
ms.topic: overview
ms.openlocfilehash: 3d845ea89507440c07747314c24ff01bd848cf37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151623"
---
# <a name="cloud-and-web-programming-in-visual-c"></a>Облачное и веб-программирование в Visual C++

В C++ имеются несколько параметров для соединения с веб-узлом и облаком.

## <a name="microsoft-azure-sdks-and-rest-services"></a>Пакеты SDK для Microsoft Azure и службы REST

- [Клиентская библиотека службы хранилища Microsoft Azure для C++](https://azure.github.io/azure-storage-cpp/)

  Клиентская библиотека службы хранилища Azure для C++ предоставляет полноценный интерфейс API для работы со службой хранилища Azure, включая следующие возможности.

  - Создание, чтение, удаление и выведение списка контейнеров больших двоичных объектов, таблиц и очередей.
  - Создание, чтение, удаление, выведение списка и копирование больших двоичных объектов, а также чтение и запись диапазонов больших двоичных объектов.
  - Вставка, удаление, замена, слияние и запрос сущностей в таблице Azure.
  - Постановка в очередь и вывод сообщений из очереди Azure.
  - Отложенное выведение списка контейнеров, больших двоичных объектов, таблиц и очередей и отложенный запрос сущностей

- [Пакеты SDK для Центра Интернета вещей Azure](/azure/iot-hub/iot-hub-devguide-sdks) ANSI C99 для Интернета вещей позволяют выполнять IoT-приложения на устройстве или на внутреннем сервере.

- [OneDrive и SharePoint в Microsoft Graph](https://dev.onedrive.com/README.htm)

  API OneDrive предоставляет набор служб HTTP для подключения приложения к файлам и папкам в Microsoft 365 и SharePoint Server 2016.

## <a name="windows-and-cross-platform-networking-apis"></a>Windows и кроссплатформенные сетевые API

- [Пакет SDK для C++ REST (кодовое имя Casablanca)](https://github.com/Microsoft/cpprestsdk)

  Предоставляет современный кроссплатформенный асинхронный API для взаимодействия со службами REST.

  - Выполнение вызовов REST к любому HTTP-серверу со встроенной поддержкой синтаксического анализа документов JSON и сериализации
  - Поддерживает OAuth 1 и 2, в том числе локальный прослушиватель перенаправления
  - Установление подключений Websockets для удаленных служб
  - Полностью асинхронная задача API на основе PPL, включая встроенный пул потоков

  Поддерживает Windows Desktop (7 +), Windows Server (2012 или более поздних версий), универсальную платформу Windows, Linux, OSX, Android и iOS.

- [Windows::Web::Http::HttpClient](/uwp/api/windows.web.http.httpclient)

  Клиентский класс HTTP среды выполнения Windows, основанный на классе .NET Framework с тем же именем в пространстве имен System.Web. `HttpClient` полностью поддерживает асинхронной отправку и загрузку по протоколу HTTP, а также фильтры конвейера, позволяющие вставлять пользовательские обработчики HTTP в конвейер. Пакет Windows SDK содержит примеры фильтров для лимитных сетей, проверки подлинности OAuth и т. д. Для приложений, предназначенных для универсальной платформы Windows, мы рекомендуем использовать класс `Windows::Web:HttpClient`.

- [Интерфейс IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2)

  Предоставляет собственный интерфейс COM, который можно использовать в приложениях среды выполнения Windows или классических приложениях Windows для подключения к Интернету по протоколу HTTP или вызова команд GET, PUT и других команд HTTP. Дополнительные сведения см. в разделе [Пошаговое руководство. подключение с помощью задач и HTTP-запросов XML](../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md).

- [Windows Internet (WinInet)](/windows/win32/WinInet/portal)

  Windows API, который можно использовать в классических приложениях Windows для подключения к Интернету.

## <a name="see-also"></a>См. также раздел

[C++ в Visual Studio](../overview/visual-cpp-in-visual-studio.md) <br/>
[Центр разработчиков Microsoft Azure C и C++](https://azure.microsoft.com/develop/cpp/) <br/>
[Сети и веб-службы (UWP)](/windows/uwp/networking/)
