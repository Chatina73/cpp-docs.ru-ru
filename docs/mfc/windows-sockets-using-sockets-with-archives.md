---
description: 'Дополнительные сведения: сокеты Windows: Использование сокетов с архивами'
title: Сокеты Windows. Использование сокетов с архивами
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: bd5f239a0fdcee4bf6c6141994c4ca5002bdc6b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331337"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Сокеты Windows. Использование сокетов с архивами

В этой статье описывается [модель программирования CSocket](#_core_the_csocket_programming_model). Класс [CSocket](../mfc/reference/csocket-class.md) предоставляет поддержку сокетов на более высоком уровне абстракции, чем класс [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket` использует версию протокола сериализации MFC для передачи данных в объект сокета и обратно через объект MFC [CArchive](../mfc/reference/carchive-class.md) . `CSocket` обеспечивает блокировку (при управлении фоновой обработкой сообщений Windows) и предоставляет доступ к `CArchive` , который управляет множеством аспектов взаимодействия, которые необходимо выполнить самостоятельно с помощью необработанного API или класса `CAsyncSocket` .

> [!TIP]
> Класс можно использовать в `CSocket` качестве более удобной версии `CAsyncSocket` , но простейшая модель программирования — использовать `CSocket` с `CArchive` объектом.

Дополнительные сведения о том, как работает реализация сокетов с архивами, см. в разделе [сокеты Windows: как работают сокеты с архивами](../mfc/windows-sockets-how-sockets-with-archives-work.md). Пример кода см. в разделе [сокеты Windows: последовательность операций](../mfc/windows-sockets-sequence-of-operations.md) и [сокеты Windows: пример сокетов с использованием архивов](../mfc/windows-sockets-example-of-sockets-using-archives.md). Дополнительные сведения о некоторых функциях, которые можно получить, путем наследования собственных классов из классов Sockets, см. в разделе [сокеты Windows: наследование от классов сокетов](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> При написании клиентской программы MFC для взаимодействия с установленными серверами (не MFC) не отправляйте объекты C++ через архив. Если сервер не является приложением MFC, которое понимает типы объектов, которые требуется отправить, он не сможет получать и десериализовать объекты. Дополнительные сведения о теме взаимодействия с приложениями, не относящимися к MFC, см. в статье [порядок следования байтов в Windows Sockets](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a> Модель программирования CSocket

Использование `CSocket` объекта включает в себя создание и связывание нескольких объектов классов MFC. В описанной ниже процедуре каждый шаг принимается как сокет сервера, так и клиентский сокет, за исключением шага 3, в котором каждый тип сокета требует другого действия.

> [!TIP]
> Во время выполнения серверное приложение, как правило, запускается первым и ожидает, когда клиентское приложение ищет подключение. Если сервер не готов, когда клиент пытается подключиться, пользовательское приложение обычно попытается повторить попытку подключения позже.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>Настройка обмена данными между сокетом сервера и сокетом клиента

1. Создайте объект [CSocket](../mfc/reference/csocket-class.md) .

1. Используйте объект для создания базового маркера **сокета** .

   Для `CSocket` клиентского объекта обычно следует использовать параметры по умолчанию для [создания](../mfc/reference/casyncsocket-class.md#create), если только не требуется сокет датаграммы. Для `CSocket` объекта сервера необходимо указать порт в `Create` вызове.

    > [!NOTE]
    >  `CArchive` не работает с сокетами датаграмм. Если вы хотите использовать `CSocket` для сокета датаграмм, необходимо использовать класс так же, как и при использовании `CAsyncSocket` , то есть без архива. Так как датаграммы ненадежны (не гарантированно поступают и могут быть повторены или получены из последовательности), они не совместимы с сериализацией через архив. Предполагается, что операция сериализации будет надежно и последовательно завершена. При попытке использовать `CSocket` с `CArchive` объектом для датаграммы утверждение MFC завершается ошибкой.

1. Если сокет является клиентом, вызовите [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect) , чтобы подключить объект сокета к сокету сервера.

     -или-

   Если сокет является сервером, вызовите метод [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen) , чтобы начать прослушивание попыток подключения от клиента. После получения запроса на подключение примите его, вызвав [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

    > [!NOTE]
    >  `Accept`Функция-член принимает ссылку на новый пустой `CSocket` объект в качестве параметра. Этот объект необходимо создать перед вызовом метода `Accept` . Если этот объект сокета выходит за пределы области действия, соединение закрывается. Не вызывайте `Create` этот новый объект сокета.

1. Создайте объект [CSocketFile](../mfc/reference/csocketfile-class.md) , связав `CSocket` с ним объект.

1. Создайте объект [CArchive](../mfc/reference/carchive-class.md) для загрузки (получения) или хранения (отправки) данных. Архив связан с `CSocketFile` объектом.

   Помните, что не `CArchive` работает с сокетами датаграмм.

1. Используйте `CArchive` объект для передачи данных между клиентскими и серверными сокетами.

   Помните, что данный `CArchive` объект перемещает данные только в одном направлении: для загрузки (получения) или сохранения (отправки). В некоторых случаях будут использоваться два `CArchive` объекта: один для отправки данных, другой — для получения подтверждений.

   После принятия подключения и настройки архива можно выполнять такие задачи, как проверка паролей.

1. Удалите архив, файл сокета и объекты сокета.

    > [!NOTE]
    >  Класс `CArchive` предоставляет `IsBufferEmpty` функцию члена, специально предназначенную для использования с классом `CSocket` . Если буфер содержит несколько сообщений с данными, например, необходимо выполнить цикл до тех пор, пока все они не будут считаны и буфер не будет сброшен. В противном случае следующее уведомление о том, что данные для получения могут быть неограниченно отложенными. Используйте, `IsBufferEmpty` чтобы гарантировать получение всех данных.

В статье [сокеты Windows: последовательность операций](../mfc/windows-sockets-sequence-of-operations.md) иллюстрирует обе стороны этого процесса с примером кода.

Дополнительные сведения см. в разделе:

- [Сокеты Windows: сокеты потоков](../mfc/windows-sockets-stream-sockets.md)

- [Сокеты Windows: сокеты датаграммы](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>См. также раздел

[Сокеты Windows в MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket:: Create](../mfc/reference/csocket-class.md#create)
