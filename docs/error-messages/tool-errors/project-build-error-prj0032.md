---
description: 'Дополнительные сведения: ошибка сборки проекта PRJ0032'
title: Ошибка построения проекта PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 25c8f9480e63a8afee23c880912e17632111a4c2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241148"
---
# <a name="project-build-error-prj0032"></a>Ошибка построения проекта PRJ0032

Свойство "Outputs" для настраиваемого этапа сборки уровня проекта содержит "макрос", результатом которого является "macro_expansion".

Пользовательский этап сборки в проекте имел неправильные выходные данные, вероятно, из-за проблемы с оценкой макроса. Эта ошибка также может означать, что путь неправильно сформирован, содержит символы или сочетания символов, которые не являются допустимыми в пути к файлу.

Чтобы устранить эту ошибку, исправьте макрос или исправьте спецификацию пути. Вычисленный путь представляет собой абсолютный путь из каталога проекта.
