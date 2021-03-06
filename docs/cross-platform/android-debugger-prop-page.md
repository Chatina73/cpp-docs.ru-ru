---
description: 'Дополнительные сведения: Свойства отладчика Android'
title: Свойства отладчика Android (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 27068b56421860b1e77b6cacf7e2ef4fae147a24
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97136530"
---
# <a name="android-debugger-properties"></a>Свойства отладчика Android

| Свойство | Описание | Варианты |
|--|--|--|
| Тип отладчика | Указывает тип кода для отладки. | **Только машинный код**<br /><br />**Только Java** |
| Целевой объект отладки | Указывает эмулятор или устройство для использования при отладке. Если эмуляторы не запущены, используйте "Диспетчер виртуальных устройств Android (AVD)" для запуска устройства. |
| Пакет для запуска | Указывает расположение *apk* , который будет отлажен. Этот параметр запускает пакет (APK) при отладке приложения. |
| Действие запуска | Действие Android для запуска приложения должно соответствовать использованному в манифесте. Нажмите кнопку Применить, чтобы получить список из *AndroidManifest.xml* и заполните его динамически. |
| Дополнительные пути поиска символов | Дополнительный путь поиска для символов отладки. |
| Дополнительные пути поиска исходных файлов Java | Дополнительные пути поиска для исходных файлов Java (применяется исключительно для типа отладчика "Только Java"). |
