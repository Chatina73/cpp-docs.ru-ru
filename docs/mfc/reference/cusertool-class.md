---
title: Класс CUserTool
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: 5bb0ae073b722c97e8e30158f8f7832fd88b2fbc
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2019
ms.locfileid: "58779044"
---
# <a name="cusertool-class"></a>Класс CUserTool

Пользовательский инструмент — это пункт меню, который запускает внешнее приложение. **Средства** вкладке **Настройка** диалоговое окно ( [класс CMFCToolBarsCustomizeDialog](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)) позволяет пользователю добавить пользовательские средства, а также указать имя, команду, аргументы, и исходный каталог для каждого пользовательского средства.

## <a name="syntax"></a>Синтаксис

```
class CUserTool : public CObject
```

## <a name="members"></a>Участники

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CUserTool::CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::DrawToolIcon](#drawtoolicon)|Значок средства пользователь рисует в заданном прямоугольнике.|
|[CUserTool::GetCommand](#getcommand)|Возвращает строку, содержащую текст команды, связанные со средством пользователя.|
|[CUserTool::GetCommandId](#getcommandid)|Возвращает идентификатор пункта меню средства пользовательской команды.|
|[CUserTool::Invoke](#invoke)|Выполняет команду, связанную с средство пользовательской среды.|
|[CUserTool::Serialize](#serialize)|Считывает этот объект из архива или записывает в него. (Переопределяет [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|
|[CUserTool::SetCommand](#setcommand)|Задает команду, связанную с средство пользовательской среды.|
|[CUserTool::SetToolIcon](#settoolicon)|Загружает значок для пользовательского средства из приложения, связанного с помощью инструмента.|

### <a name="protected-methods"></a>Защищенные методы

|name|Описание|
|----------|-----------------|
|[CUserTool::LoadDefaultIcon](#loaddefaulticon)|Загружает значок по умолчанию для пользовательского средства.|

### <a name="data-members"></a>Элементы данных

|name|Описание|
|----------|-----------------|
|[CUserTool::m_strArguments](#m_strarguments)|Аргументы командной строки для пользовательского средства.|
|[CUserTool::m_strInitialDirectory](#m_strinitialdirectory)|Исходный каталог для пользовательского средства.|
|[CUserTool::m_strLabel](#m_strlabel)|Имя инструмента, который отображается в пункте меню для средства.|

## <a name="remarks"></a>Примечания

Дополнительные сведения о включении средства пользователя в приложении см. в разделе [класс CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md).

## <a name="example"></a>Пример

Следующий пример демонстрирует создание средство, разработанное `CUserToolsManager` установите `m_strLabel` переменной-члена, а также набор приложение, которое запускает средство пользовательской среды. Этот фрагмент кода является частью [Visual Studio демонстрационного](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>Требования

**Заголовок:** afxusertool.h

##  <a name="copyicontoclipboard"></a>  CUserTool::CopyIconToClipboard

Дополнительные сведения см. в исходном коде, расположенном в папке **VC\\atlmfc\\src\\mfc** каталога установки Visual Studio.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>Возвращаемое значение

### <a name="remarks"></a>Примечания

##  <a name="drawtoolicon"></a>  CUserTool::DrawToolIcon

Значок средства пользователь рисует лежащий в заданном прямоугольнике.

```
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>Параметры

*основного контроллера домена*<br/>
[in] Указатель на контекст устройства.

*rectImage*<br/>
[in] Задает координаты области для отображения значка.

##  <a name="getcommand"></a>  CUserTool::GetCommand

Возвращает строку, содержащую текст команды, связанные со средством пользователя.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>Возвращаемое значение

Ссылку на `CString` , содержащий текст команды, связанные со средством пользователя.

##  <a name="getcommandid"></a>  CUserTool::GetCommandId

Возвращает идентификатор команды инструмента пользователя.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>Возвращаемое значение

Идентификатор команды этого пользователя средства.

##  <a name="invoke"></a>  CUserTool::Invoke

Выполняет команду, связанную с средство пользовательской среды.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если команда была выполнена успешно; в противном случае 0.

### <a name="remarks"></a>Примечания

Вызовы [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) для выполнения команды, связанной с средство пользовательской среды. Функция завершается с ошибкой, если команда является пустым или [ShellExecute](/windows/desktop/api/shellapi/nf-shellapi-shellexecutea) завершается ошибкой.

##  <a name="loaddefaulticon"></a>  CUserTool::LoadDefaultIcon

Загружает значок по умолчанию для пользовательского средства.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>Возвращаемое значение

Дескриптор загруженных значка (HICON), или значение NULL, если не удается загрузить значок по умолчанию.

### <a name="remarks"></a>Примечания

Этот метод вызывается платформой, когда не удается загрузить значок для инструмента, определенного пользователем из исполняемого файла средства.

Переопределите этот метод, чтобы предоставить собственный значок по умолчанию средство.

##  <a name="m_strarguments"></a>  CUserTool::m_strArguments

Аргументы командной строки для пользовательского средства.

```
CString m_strArguments;
```

### <a name="remarks"></a>Примечания

Эта строка передается в средство, при вызове [CUserTool::Invoke](#invoke) или когда пользователь щелкает команду, связанную с помощью этого средства.

##  <a name="m_strinitialdirectory"></a>  CUserTool::m_strInitialDirectory

Указывает исходный каталог для пользовательского средства.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>Примечания

Эта переменная указывает начальный каталог, эта программа выполняется в, при вызове [CUserTool::Invoke](#invoke) или когда пользователь щелкает команду, связанную с помощью этого средства.

##  <a name="m_strlabel"></a>  CUserTool::m_strLabel

Метка, которая отображается в пункте меню для средства.

```
CString m_strLabel;
```

##  <a name="serialize"></a>  CUserTool::Serialize

Дополнительные сведения см. в исходном коде, расположенном в папке **VC\\atlmfc\\src\\mfc** каталога установки Visual Studio.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>Параметры

[in] *ar*<br/>

### <a name="remarks"></a>Примечания

##  <a name="setcommand"></a>  CUserTool::SetCommand

Задает приложение, которое запускает средство пользовательской среды.

```
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>Параметры

*lpszCmd*<br/>
[in] Указывает новое приложение, должны быть сопоставлены средство пользовательской среды.

### <a name="remarks"></a>Примечания

Вызовите этот метод для установки нового приложения, которое запускает средство пользовательской среды. Метод уничтожает старый значок и загружает новый значок из данного приложения. Если значок не удалось загрузить из приложения, он загружает значок по умолчанию для пользовательского средства, вызвав [CUserTool::LoadDefaultIcon](#loaddefaulticon).

##  <a name="settoolicon"></a>  CUserTool::SetToolIcon

Загружает значок для пользовательского средства из приложения, который используется средством.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>Возвращаемое значение

Дескриптор загрузить значок.

### <a name="remarks"></a>Примечания

Вызовите этот метод, чтобы загрузить значок для отображения пункта меню. Этот метод осуществляет поиск значок в исполняемом файле, который используется средством. Если он имеет значок по умолчанию, предоставляемые значок [CUserTool::LoadDefaultIcon](#loaddefaulticon) вместо него используется.

## <a name="see-also"></a>См. также

[Диаграмма иерархии](../../mfc/hierarchy-chart.md)<br/>
[Классы](../../mfc/reference/mfc-classes.md)<br/>
[Класс CWinAppEx](../../mfc/reference/cwinappex-class.md)<br/>
[Класс CUserToolsManager](../../mfc/reference/cusertoolsmanager-class.md)
