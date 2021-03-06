---
description: 'Дополнительные сведения: отправка и получение сообщений'
title: Отправка и получение сообщений
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 3a61346c51ce035f6fd5a53b8c329ef81154b089
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97203215"
---
# <a name="message-sending-and-receiving"></a>Отправка и получение сообщений

Рассмотрим отправную часть процесса и реакцию платформы.

Большинство сообщений выводятся при взаимодействии пользователя с программой. Команды создаются щелчками мыши в пунктах меню или на кнопках панели инструментов или с помощью клавиш быстрого вызова. Пользователь также создает сообщения Windows, например, перемещая или изменяя размер окна. Другие сообщения Windows отправляются при возникновении таких событий, как запуск или завершение программы, в результате чего Windows получает или теряет фокус и т. д. Сообщения контрольных уведомлений создаются щелчками мыши или другими пользователями с помощью элемента управления, например кнопки или элемента управления "список" в диалоговом окне.

`Run`Функция члена класса `CWinApp` извлекает сообщения и отправляет их в соответствующее окно. Большинство командных сообщений отправляются в основное окно фрейма приложения. `WindowProc`Предопределенный классом библиотека классов получает сообщения и направляет их по-разному в зависимости от категории полученных сообщений.

Теперь рассмотрим принимающую часть процесса.

Первоначальный получатель сообщения должен быть объектом окна. Сообщения Windows обычно обрабатываются непосредственно этим объектом окна. Командные сообщения, обычно создаваемые в главном окне фрейма приложения, перенаправляются в цепочку команд, описанную в разделе [Маршрутизация команд](command-routing.md).

Каждый объект, способный получать сообщения или команды, имеет собственную схему сообщений, которая сопоставляет сообщение или команду с именем обработчика.

Когда целевой объект команды получает сообщение или команду, он выполняет поиск соответствия в соответствующей схеме сообщений. Если обнаруживает обработчик для сообщения, он вызывает обработчик. Дополнительные сведения о поиске в картах сообщений см. [в разделе как платформа ищет схемы сообщений](how-the-framework-searches-message-maps.md). Снова ознакомьтесь с [командами](user-interface-objects-and-command-ids.md)на рис.

## <a name="see-also"></a>См. также раздел

[Как платформа вызывает обработчик](how-the-framework-calls-a-handler.md)
