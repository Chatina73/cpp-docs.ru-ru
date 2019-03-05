---
title: Макросы сообщений Windows
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 7bb5e2fa265c3a5dcabcc16d8343d5b86a4aaf42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273932"
---
# <a name="windows-messages-macros"></a>Макросы сообщений Windows

Этот макрос пересылает сообщения окна.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Используйте для пересылки сообщения окном на другое окно для обработки.|

## <a name="requirements"></a>Требования

**Заголовок:** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

Этот макрос пересылает сообщение, полученное центром окна в другое окно для обработки.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если сообщение было обработано, ноль Если это не так.

### <a name="remarks"></a>Примечания

Используйте WM_FORWARDMSG на пересылку сообщений, полученных в окне другого окна для обработки. Параметры LPARAM и WPARAM используются следующим образом:

|Параметр|Использование|
|---------------|-----------|
|WPARAM|Данные, определенные пользователем|
|LPARAM|Указатель на `MSG` структуру, содержащую сведения о сообщении|

### <a name="example"></a>Пример

В следующем примере `m_hWndOther` представляет другое окно, которое получает это сообщение.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>См. также

[Макросы](../../atl/reference/atl-macros.md)
