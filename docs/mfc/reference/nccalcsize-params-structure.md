---
title: Структура NCCALCSIZE_PARAMS
ms.date: 11/04/2016
f1_keywords:
- NCCALCSIZE_PARAMS
helpviewer_keywords:
- NCCALCSIZE_PARAMS structure [MFC]
ms.assetid: 3424cd9f-806a-4089-82fb-414187589edf
ms.openlocfilehash: 3dbe1fcdb941a94876dd95a0eed86d6f4a3e15c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443775"
---
# <a name="nccalcsizeparams-structure"></a>Структура NCCALCSIZE_PARAMS

`NCCALCSIZE_PARAMS` Структура содержит сведения, что приложение может использовать при обработке сообщения WM_NCCALCSIZE для расчета размера, положения и допустимое содержимое клиентской области окна.

## <a name="syntax"></a>Синтаксис

```
typedef struct tagNCCALCSIZE_PARAMS {
    RECT rgrc[3];
    PWINDOWPOS lppos;
} NCCALCSIZE_PARAMS;
```

#### <a name="parameters"></a>Параметры

*rgrc*<br/>
Указывает массив прямоугольников. Первый содержит новые координаты, перемещения или изменения размера окна. Второй содержит координаты окна, прежде чем он был перемещен или изменении размера. Третий содержит координаты клиентской области окна, прежде чем он был перемещен или изменении размера. Если окно дочернего окна, координаты указываются относительно клиентской области родительского окна. Если окно является окном верхнего уровня, координаты указываются относительно экрана.

*lppos*<br/>
Указывает на [WINDOWPOS](../../mfc/reference/windowpos-structure1.md) структуру, содержащую размер и положение значения, указанные в операции, которая вызвала окне, чтобы быть перемещения или изменения размера.

## <a name="requirements"></a>Требования

**Заголовок:** winuser.h

## <a name="see-also"></a>См. также

[Структуры, стили, обратные вызовы и схемы сообщений](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CWnd::OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)

