---
description: 'Дополнительные сведения: _com_error:: ErrorInfo'
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: 36092ae9287352d421bf502ad24c054cf3b7a907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296047"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Блок, относящийся только к системам Microsoft**

Получает объект `IErrorInfo`, переданный конструктору.

## <a name="syntax"></a>Синтаксис

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Возвращаемое значение

Необработанный элемент `IErrorInfo`, переданный в конструктор.

## <a name="remarks"></a>Комментарии

Извлекает инкапсулированный `IErrorInfo` элемент в `_com_error` объекте или значение null, если элемент не `IErrorInfo` записан. Вызывающий объект должен вызвать `Release` для возвращенного объекта, когда он завершил использовать его.

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Класс _com_error](../cpp/com-error-class.md)
