---
title: Класс CMFCAcceleratorKey
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: 169530b213e9201dd59782aad05b71c73c62c596
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461663"
---
# <a name="cmfcacceleratorkey-class"></a>Класс CMFCAcceleratorKey

Вспомогательный класс, реализующий виртуальное ключевое сопоставление и форматирование.

## <a name="syntax"></a>Синтаксис

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|Имя|Описание|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Создает объект `CMFCAcceleratorKey`.|

### <a name="public-methods"></a>Открытые методы

|Имя|Описание|
|----------|-----------------|
|[CMFCAcceleratorKey::Format](#format)|Преобразует структуру УСКОРЕНИЕ, визуальное представление.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Задает сочетание клавиш для `CMFCAcceleratorKey` объекта.|

## <a name="remarks"></a>Примечания

Сочетания клавиш также называются сочетания клавиш. Если вы хотите отобразить сочетания клавиш, вводимые пользователем, [класс CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) maps сочетания клавиш, таких как Alt + Shift + S, в пользовательский текстовый формат, например «Alt + Shift + S». Каждый `CMFCAcceleratorKey` объект сопоставляется одному сочетанию клавиш текстовом формате.

Дополнительные сведения об использовании сочетаний клавиш и таблицы сочетаний клавиш см. в разделе [класс CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Пример

В следующем примере демонстрируется создание `CMFCAcceleratorKey` объекта и как использовать его `Format` метод.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Требования

**Заголовок:** afxacceleratorkey.h

##  <a name="cmfcacceleratorkey"></a>  CMFCAcceleratorKey::CMFCAcceleratorKey

Создает [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) объекта.

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Параметры

*lpAccel*<br/>
[in] Указатель на сочетания клавиш.

### <a name="remarks"></a>Примечания

Если вы не укажете сочетания клавиш при создании `CMFCAccleratorKey`, использовать [CMFCAcceleratorKey::SetAccelerator](#setaccelerator) метод, чтобы связать сочетания клавиш с вашей `CMFCAcceleratorKey` объекта.

##  <a name="format"></a>  CMFCAcceleratorKey::Format

Преобразует структуру УСКОРЕНИЕ связанные строковому значению.

```
void Format(CString& str) const;
```

### <a name="parameters"></a>Параметры

*str*<br/>
[out] Ссылку на `CString` объекта, где метод записывает переведенные сочетания клавиш.

### <a name="remarks"></a>Примечания

Этот метод извлекает формат строки для сочетанием клавиш. Можно задать формат строки [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) объекта с помощью конструктора или метода [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

##  <a name="setaccelerator"></a>  CMFCAcceleratorKey::SetAccelerator

Задает сочетание клавиш для [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) объекта.

```
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Параметры

*lpAccel*<br/>
[in] Указатель на сочетания клавиш.

### <a name="remarks"></a>Примечания

Этот метод позволяет задать сочетание клавиш для `CMFCAcceleratorKey` Если вы не указали сочетания клавиш при создании `CMFCAcceleratorKey`.

## <a name="see-also"></a>См. также

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
