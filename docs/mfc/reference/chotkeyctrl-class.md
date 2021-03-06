---
description: 'Дополнительные сведения о: CHotKeyCtrl Class'
title: Класс CHotKeyCtrl
ms.date: 11/04/2016
f1_keywords:
- CHotKeyCtrl
- AFXCMN/CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::CHotKeyCtrl
- AFXCMN/CHotKeyCtrl::Create
- AFXCMN/CHotKeyCtrl::CreateEx
- AFXCMN/CHotKeyCtrl::GetHotKey
- AFXCMN/CHotKeyCtrl::GetHotKeyName
- AFXCMN/CHotKeyCtrl::GetKeyName
- AFXCMN/CHotKeyCtrl::SetHotKey
- AFXCMN/CHotKeyCtrl::SetRules
helpviewer_keywords:
- CHotKeyCtrl [MFC], CHotKeyCtrl
- CHotKeyCtrl [MFC], Create
- CHotKeyCtrl [MFC], CreateEx
- CHotKeyCtrl [MFC], GetHotKey
- CHotKeyCtrl [MFC], GetHotKeyName
- CHotKeyCtrl [MFC], GetKeyName
- CHotKeyCtrl [MFC], SetHotKey
- CHotKeyCtrl [MFC], SetRules
ms.assetid: 896f9766-0718-4f58-aab2-20325e118ca6
ms.openlocfilehash: 875b35c2c683cc8502c1bc2668aad5b4a0326757
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331780"
---
# <a name="chotkeyctrl-class"></a>Класс CHotKeyCtrl

Предоставляет функциональные возможности стандартного элемента управления "горячая клавиша" Windows.

## <a name="syntax"></a>Синтаксис

```
class CHotKeyCtrl : public CWnd
```

## <a name="members"></a>Члены

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[CHotKeyCtrl:: CHotKeyCtrl](#chotkeyctrl)|Формирует объект `CHotKeyCtrl`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CHotKeyCtrl:: Create](#create)|Создает элемент управления горячим ключом и прикрепляет его к `CHotKeyCtrl` объекту.|
|[CHotKeyCtrl:: Креатикс](#createex)|Создает активный элемент управления ключами с указанными расширенными стилями Windows и прикрепляет его к `CHotKeyCtrl` объекту.|
|[CHotKeyCtrl:: насочетание клавиш](#gethotkey)|Получает виртуальный код ключа и флаги модификатора для сочетания клавиш из элемента управления горячими ключами.|
|[CHotKeyCtrl:: Жесоткэйнаме](#gethotkeyname)|Возвращает имя ключа в локальной кодировке, назначенное горячей клавише.|
|[CHotKeyCtrl:: Жеткэйнаме](#getkeyname)|Возвращает имя ключа в локальной кодировке, назначенное указанному виртуальному коду клавиши.|
|[CHotKeyCtrl:: Сесоткэй](#sethotkey)|Задает сочетание горячих клавиш для элемента управления "горячий ключ".|
|[CHotKeyCtrl:: Сетрулес](#setrules)|Определяет недопустимые сочетания и сочетание модификатора по умолчанию для элемента управления горячего ключа.|

## <a name="remarks"></a>Комментарии

«Элемент управления горячей клавиши» — это окно, которое позволяет пользователю создать сочетание клавиш. "Горячая" клавиша — это сочетание клавиш, которое пользователь может нажать для быстрого выполнения действия. (Например, пользователь может создать горячую клавишу, которая активирует заданное окно и переводит его в начало Z-порядка). Элемент управления горячими ключами отображает варианты выбора пользователя и гарантирует, что пользователь выбрал допустимое сочетание клавиш.

Этот элемент управления (и, следовательно, `CHotKeyCtrl` класс) доступен только для программ, работающих под управлением windows 95/98 и Windows NT версии 3,51 и более поздних версий.

Когда пользователь выбрал сочетание клавиш, приложение может извлечь указанное сочетание клавиш из элемента управления и использовать сообщение WM_SETHOTKEY, чтобы настроить горячую клавишу в системе. Каждый раз, когда пользователь нажимает горячую клавишу, в любой части системы окно, указанное в WM_SETHOTKEY сообщении, получает сообщение WM_SYSCOMMAND, указывающее SC_HOTKEY. Это сообщение активирует окно, которое его получает. Сочетание клавиш остается действительным до тех пор, пока приложение, которое вызвало WM_SETHOTKEY, не завершит работу.

Этот механизм отличается от поддержки горячих клавиш, которая зависит от WM_HOTKEY сообщения и функций Windows [RegisterHotKey](/windows/win32/api/winuser/nf-winuser-registerhotkey) и [унрегистерхоткэй](/windows/win32/api/winuser/nf-winuser-unregisterhotkey) .

Дополнительные сведения об использовании см `CHotKeyCtrl` . в разделе [элементы управления](../../mfc/controls-mfc.md) и [Использование CHotKeyCtrl](../../mfc/using-chotkeyctrl.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHotKeyCtrl`

## <a name="requirements"></a>Требования

**Заголовок:** afxcmn.h

## <a name="chotkeyctrlchotkeyctrl"></a><a name="chotkeyctrl"></a> CHotKeyCtrl:: CHotKeyCtrl

Формирует объект `CHotKeyCtrl`.

```
CHotKeyCtrl();
```

## <a name="chotkeyctrlcreate"></a><a name="create"></a> CHotKeyCtrl:: Create

Создает элемент управления горячим ключом и прикрепляет его к `CHotKeyCtrl` объекту.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Параметры

*двстиле*<br/>
Задает стиль элемента управления горячей клавиши. Примените любое сочетание стилей элементов управления. Дополнительные сведения см. в разделе [общие стили элементов управления](/windows/win32/Controls/common-control-styles) в Windows SDK.

*rect*<br/>
Задает размер и расположение элемента управления горячей клавиши. Это может быть либо объект [крект](../../atl-mfc-shared/reference/crect-class.md) , либо [Структура Rect](/windows/win32/api/windef/ns-windef-rect).

*ппарентвнд*<br/>
Указывает родительское окно элемента управления "горячая клавиша", обычно [CDialog](../../mfc/reference/cdialog-class.md). Оно не должно иметь значение NULL.

*nID*<br/>
Указывает идентификатор элемента управления горячей клавиши.

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если инициализация прошла успешно; в противном случае — 0.

### <a name="remarks"></a>Комментарии

`CHotKeyCtrl`Объект создается в два этапа. Сначала вызовите конструктор, а затем вызовите метод `Create` , который создает элемент управления горячей клавиши и присоединяет его к `CHotKeyCtrl` объекту.

Если вы хотите использовать расширенные стили Windows с элементом управления, вызовите [креатикс](#createex) вместо `Create` .

## <a name="chotkeyctrlcreateex"></a><a name="createex"></a> CHotKeyCtrl:: Креатикс

Вызовите эту функцию, чтобы создать элемент управления (дочернее окно) и связать его с `CHotKeyCtrl` объектом.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Параметры

*двексстиле*<br/>
Задает расширенный стиль создаваемого элемента управления. Список расширенных стилей Windows см. в разделе параметр *двексстиле* для [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) в Windows SDK.

*двстиле*<br/>
Задает стиль элемента управления горячей клавиши. Примените любое сочетание стилей элементов управления. Дополнительные сведения см. в разделе [общие стили элементов управления](/windows/win32/Controls/common-control-styles) в Windows SDK.

*rect*<br/>
Ссылка на структуру [Rect](/windows/win32/api/windef/ns-windef-rect) , описывающую размер и расположение создаваемого окна в клиентских координатах *ппарентвнд*.

*ппарентвнд*<br/>
Указатель на окно, которое является родительским элементом управления.

*nID*<br/>
Идентификатор дочернего окна элемента управления.

### <a name="return-value"></a>Возвращаемое значение

Имеет ненулевое значение в случае успешного выполнения, иначе — 0.

### <a name="remarks"></a>Комментарии

Используйте `CreateEx` вместо [CREATE](#create) , чтобы применить расширенные стили Windows, заданные **WS_EX_** в расширенном стиле Windows.

## <a name="chotkeyctrlgethotkey"></a><a name="gethotkey"></a> CHotKeyCtrl:: насочетание клавиш

Получает виртуальный код клавиши и флаги модификатора сочетания клавиш из элемента управления горячими ключами.

```
DWORD GetHotKey() const;

void GetHotKey(
    WORD& wVirtualKeyCode,
    WORD& wModifiers) const;
```

### <a name="parameters"></a>Параметры

*ввиртуалкэйкоде*<br/>
заполняет Виртуальный ключевой код сочетания клавиш. Список стандартных виртуальных клавиш см. в разделе Winuser. h.

*вмодифиерс*<br/>
заполняет Побитовое сочетание (или) флагов, указывающих клавиши-модификаторы в сочетаниях клавиш.

Ниже перечислены флаги модификатора.

|Флаг|Соответствующий ключ|
|----------|-----------------------|
|HOTKEYF_ALT|ALT - клавиша|
|HOTKEYF_CONTROL|Клавиша CTRL|
|HOTKEYF_EXT|Расширенный ключ|
|HOTKEYF_SHIFT|Клавиша SHIFT|

### <a name="return-value"></a>Возвращаемое значение

В первом перегруженном методе DWORD, содержащий виртуальный код ключа и флаги модификатора. Младший байт слова нижнего порядка содержит виртуальный код ключа, старший байт слова нижнего порядка содержит флаги модификатора, а высокое значение — ноль.

### <a name="remarks"></a>Комментарии

Код виртуального ключа и клавиши модификатора вместе определяют сочетание клавиш.

## <a name="chotkeyctrlgethotkeyname"></a><a name="gethotkeyname"></a> CHotKeyCtrl:: Жесоткэйнаме

Вызовите эту функцию члена, чтобы получить локализованное имя сочетания клавиш.

```
CString GetHotKeyName() const;
```

### <a name="return-value"></a>Возвращаемое значение

Локализованное имя выбранной в данный момент горячей клавиши. Если не выбрана ни одна горячая клавиша, `GetHotKeyName` возвращает пустую строку.

### <a name="remarks"></a>Комментарии

Имя, возвращаемое этой функцией члена, берется из драйвера клавиатуры. Нелокализованный драйвер клавиатуры можно установить в локализованной версии Windows, и наоборот.

## <a name="chotkeyctrlgetkeyname"></a><a name="getkeyname"></a> CHotKeyCtrl:: Жеткэйнаме

Вызовите эту функцию-член, чтобы получить локализованное имя ключа, присвоенное указанному виртуальному ключу.

```
static CString GetKeyName(
    UINT vk,
    BOOL fExtended);
```

### <a name="parameters"></a>Параметры

*VK*<br/>
Код виртуального ключа.

*фекстендед*<br/>
Если код виртуального ключа является расширенным ключом, значение TRUE; в противном случае — FALSE.

### <a name="return-value"></a>Возвращаемое значение

Локализованное имя ключа, заданное параметром *VK* . Если у ключа нет сопоставленного имени, `GetKeyName` возвращает пустую строку.

### <a name="remarks"></a>Комментарии

Имя ключа, которое возвращает эта функция, поступает от драйвера клавиатуры, поэтому можно установить нелокализованный драйвер клавиатуры в локализованной версии Windows и наоборот.

### <a name="example"></a>Пример

[!code-cpp[NVC_MFCControlLadenDialog#69](../../mfc/codesnippet/cpp/chotkeyctrl-class_1.cpp)]

## <a name="chotkeyctrlsethotkey"></a><a name="sethotkey"></a> CHotKeyCtrl:: Сесоткэй

Задает сочетание клавиш для элемента управления "горячая клавиша".

```cpp
void SetHotKey(
    WORD wVirtualKeyCode,
    WORD wModifiers);
```

### <a name="parameters"></a>Параметры

*ввиртуалкэйкоде*<br/>
окне Виртуальный ключевой код сочетания клавиш. Список стандартных виртуальных клавиш см. в разделе Winuser. h.

*вмодифиерс*<br/>
окне Побитовое сочетание (или) флагов, указывающих клавиши-модификаторы в сочетаниях клавиш.

Ниже перечислены флаги модификатора.

|Флаг|Соответствующий ключ|
|----------|-----------------------|
|HOTKEYF_ALT|ALT - клавиша|
|HOTKEYF_CONTROL|Клавиша CTRL|
|HOTKEYF_EXT|Расширенный ключ|
|HOTKEYF_SHIFT|Клавиша SHIFT|

### <a name="remarks"></a>Комментарии

Код виртуального ключа и клавиши модификатора вместе определяют сочетание клавиш.

## <a name="chotkeyctrlsetrules"></a><a name="setrules"></a> CHotKeyCtrl:: Сетрулес

Вызовите эту функцию, чтобы определить недопустимые сочетания и сочетание модификатора по умолчанию для элемента управления "горячая клавиша".

```cpp
void SetRules(
    WORD wInvalidComb,
    WORD wModifiers);
```

### <a name="parameters"></a>Параметры

*винвалидкомб*<br/>
Массив флагов, задающий недопустимые сочетания клавиш. Это может быть сочетание следующих значений:

- HKCOMB_A ALT

- HKCOMB_C CTRL

- HKCOMB_CA CTRL + ALT

- HKCOMB_NONE неизмененных ключей

- HKCOMB_S SHIFT

- HKCOMB_SA SHIFT + ALT

- HKCOMB_SC SHIFT + CTRL

- HKCOMB_SCA SHIFT + CTRL + ALT

*вмодифиерс*<br/>
Массив флагов, указывающий сочетание клавиш, которое будет использоваться при вводе пользователем недопустимого сочетания. Дополнительные сведения о флагах модификатора см. в разделе " [сочетание клавиш](#gethotkey)".

### <a name="remarks"></a>Комментарии

Когда пользователь вводит недопустимое сочетание клавиш, как определено флагами, указанными в *винвалидкомб*, система использует оператор OR для объединения вводимых пользователем ключей с флагами, указанными в *вмодифиерс*. Полученное сочетание клавиш преобразуется в строку и затем отображается в элементе управления "горячая клавиша".

## <a name="see-also"></a>См. также раздел

[CWnd, класс](../../mfc/reference/cwnd-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)
