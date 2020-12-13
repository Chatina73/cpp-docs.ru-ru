---
description: 'Дополнительные сведения о: CDocTemplate Class'
title: Класс CDocTemplate
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: e97e2d00f5ad847555ae951433c327cc861917b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184898"
---
# <a name="cdoctemplate-class"></a>Класс CDocTemplate

Абстрактный базовый класс, который определяет базовую функциональность шаблонов документов.

## <a name="syntax"></a>Синтаксис

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>Члены

### <a name="protected-constructors"></a>Защищенные конструкторы

|Имя|Описание|
|----------|-----------------|
|[CDocTemplate:: CDocTemplate](#cdoctemplate)|Формирует объект `CDocTemplate`.|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CDocTemplate:: Адддокумент](#adddocument)|Добавляет документ в шаблон.|
|[CDocTemplate:: Клосеаллдокументс](#closealldocuments)|Закрывает все документы, связанные с этим шаблоном.|
|[CDocTemplate:: Креатеневдокумент](#createnewdocument)|Создает новый документ.|
|[CDocTemplate:: CreateNewFrame](#createnewframe)|Создает новое окно фрейма, содержащее документ и представление.|
|[CDocTemplate:: Креатеолефраме](#createoleframe)|Создает окно фрейма с поддержкой OLE.|
|[CDocTemplate:: Креатепревиевфраме](#createpreviewframe)|Создает дочерний фрейм, используемый для расширенного просмотра.|
|[CDocTemplate:: Жетдокстринг](#getdocstring)|Извлекает строку, связанную с типом документа.|
|[CDocTemplate:: Жетфирстдокпоситион](#getfirstdocposition)|Извлекает расположение первого документа, связанного с этим шаблоном.|
|[CDocTemplate:: Жетнекстдок](#getnextdoc)|Извлекает документ и его расположение.|
|[CDocTemplate:: Инитиалупдатефраме](#initialupdateframe)|Инициализирует окно фрейма и при необходимости делает его видимым.|
|[CDocTemplate:: Лоадтемплате](#loadtemplate)|Загружает ресурсы для заданного `CDocTemplate` или производного класса.|
|[CDocTemplate:: Матчдоктипе](#matchdoctype)|Определяет степень достоверности в совпадении между типом документа и этим шаблоном.|
|[CDocTemplate:: Опендокументфиле](#opendocumentfile)|Открывает файл, заданный параметром PathName.|
|[CDocTemplate:: Ремоведокумент](#removedocument)|Удаляет документ из шаблона.|
|[CDocTemplate:: Савеаллмодифиед](#saveallmodified)|Сохраняет все документы, связанные с этим шаблоном, которые были изменены.|
|[CDocTemplate:: Сетконтаинеринфо](#setcontainerinfo)|Определяет ресурсы для контейнеров OLE при редактировании элемента OLE на месте.|
|[CDocTemplate:: Сетдефаулттитле](#setdefaulttitle)|Отображает заголовок по умолчанию в заголовке окна документа.|
|[CDocTemplate:: Сетпревиевинфо](#setpreviewinfo)|Программа установки выходит из обработчика предварительного просмотра.|
|[CDocTemplate:: Сетсерверинфо](#setserverinfo)|Определяет ресурсы и классы, когда серверный документ внедряется или редактируется на месте.|

## <a name="remarks"></a>Комментарии

Обычно создается один или несколько шаблонов документов в реализации `InitInstance` функции приложения. В шаблоне документа определяются отношения между тремя типами классов:

- Класс документа, производный от `CDocument` .

- Класс представления, который отображает данные из указанного выше класса документа. Этот класс можно наследовать от `CView` ,, `CScrollView` `CFormView` или `CEditView` . (Можно также использовать `CEditView` напрямую.)

- Класс окна фрейма, который содержит представление. Для приложения с одним документом (SDI) Этот класс наследуется от класса `CFrameWnd` . Для приложения с многодокументным интерфейсом (MDI) Этот класс наследуется от класса `CMDIChildWnd` . Если не требуется настраивать поведение окна фрейма, можно использовать `CFrameWnd` или `CMDIChildWnd` напрямую, не создавая собственный класс.

Приложение имеет один шаблон документа для каждого типа документов, которые он поддерживает. Например, если приложение поддерживает как электронные таблицы, так и текстовые документы, приложение будет иметь два объекта шаблона документа. Каждый шаблон документа отвечает за создание и управление всеми документами типа.

В шаблоне документа хранятся указатели на `CRuntimeClass` объекты для классов документов, представлений и окон фрейма. Эти `CRuntimeClass` объекты указываются при создании шаблона документа.

Шаблон документа содержит ИДЕНТИФИКАТОРы ресурсов, используемых с типом документа (например, меню, значок или ресурсы таблицы ускорителя). Шаблон документа также содержит строки, содержащие дополнительные сведения о типе документа. К ним относятся имя типа документа (например, "лист") и расширение файла (например, ". xls"). При необходимости оно может содержать другие строки, используемые пользовательским интерфейсом приложения, диспетчером файлов Windows и поддержкой связывания и внедрения объектов (OLE).

Если приложение является контейнером OLE или сервером, шаблон документа также определяет идентификатор меню, используемого при активации на месте. Если приложение является сервером OLE, шаблон документа определяет идентификатор панели инструментов и меню, используемые при активации на месте. Эти дополнительные ресурсы OLE указываются путем вызова методов `SetContainerInfo` и `SetServerInfo` .

Поскольку `CDocTemplate` является абстрактным классом, вы не можете напрямую использовать класс. Типичное приложение использует один из двух `CDocTemplate` производных классов, предоставляемых Библиотека Microsoft Foundation Class: `CSingleDocTemplate` , который реализует SDI, и `CMultiDocTemplate` , который реализует интерфейс MDI. Дополнительные сведения об использовании шаблонов документов см. в этих классах.

Если приложению требуется парадигма пользовательского интерфейса, которая фундаментально отличается от SDI или MDI, можно создать собственный класс из `CDocTemplate` .

Дополнительные сведения о см `CDocTemplate` . в разделе [шаблоны документов и процесс создания документа/представления](../../mfc/document-templates-and-the-document-view-creation-process.md).

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>Требования

**Заголовок:** afxwin.h

## <a name="cdoctemplateadddocument"></a><a name="adddocument"></a> CDocTemplate:: Адддокумент

Эта функция используется для добавления документа в шаблон.

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Параметры

*pDoc*<br/>
Указатель на добавляемый документ.

### <a name="remarks"></a>Комментарии

Производные классы [кмултидоктемплате](../../mfc/reference/cmultidoctemplate-class.md) и [ксингледоктемплате](../../mfc/reference/csingledoctemplate-class.md) переопределяют эту функцию. Если вы наследуете собственный класс шаблона документа из `CDocTemplate` , производный класс должен переопределить эту функцию.

## <a name="cdoctemplatecdoctemplate"></a><a name="cdoctemplate"></a> CDocTemplate:: CDocTemplate

Формирует объект `CDocTemplate`.

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>Параметры

*нидресаурце*<br/>
Указывает идентификатор ресурсов, используемых с типом документа. Это может быть меню, значок, таблица сочетаний клавиш и строковые ресурсы.

Строковый ресурс состоит из до семи подстрок, разделенных символом "\n" (символ "\n" необходим в качестве заполнителя, если подстрока не включена; Однако замыкающие символы "\n" не требуются); эти подстроки описывают тип документа. Сведения о подстроках см. в разделе [жетдокстринг](#getdocstring). Этот строковый ресурс находится в файле ресурсов приложения. Пример:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

Обратите внимание, что строка начинается с символа "\n"; Это происходит потому, что первая подстрока не используется для приложений MDI и поэтому не включается. Эту строку можно изменить с помощью редактора строк. вся строка отображается в виде одной записи в редакторе строк, а не в виде семи отдельных записей.

*пдоккласс*<br/>
Указывает на `CRuntimeClass` объект класса Document. Этот класс является производным от класса, `CDocument` который определяется для представления документов.

*пфрамекласс*<br/>
Указывает на `CRuntimeClass` объект класса фрейм окна. Этот класс может быть `CFrameWnd` производным от класса или, `CFrameWnd` Если требуется поведение по умолчанию для основного окна фрейма.

*пвиевкласс*<br/>
Указывает на `CRuntimeClass` объект класса представления. Этот класс является производным от класса, `CView` который определяется для вывода документов.

### <a name="remarks"></a>Комментарии

Используйте эту функцию-член для создания `CDocTemplate` объекта. Динамически выделяйте `CDocTemplate` объект и передайте его в функцию [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) из `InitInstance` функции-члена класса приложения.

## <a name="cdoctemplateclosealldocuments"></a><a name="closealldocuments"></a> CDocTemplate:: Клосеаллдокументс

Вызовите эту функцию члена, чтобы закрыть все открытые документы.

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Параметры

*бендсессион*<br/>
Не используется.

### <a name="remarks"></a>Комментарии

Эта функция-член обычно используется как часть команды выхода из файла. Реализация по умолчанию этой функции вызывает функцию члена [CDocument::D елетеконтентс](../../mfc/reference/cdocument-class.md#deletecontents) для удаления данных документа, а затем закрывает окна фрейма для всех представлений, присоединенных к документу.

Переопределите эту функцию, если требуется, чтобы пользователь выполнял специальную очистку перед закрытием документа. Например, если документ представляет запись в базе данных, может потребоваться переопределить эту функцию, чтобы закрыть базу данных.

## <a name="cdoctemplatecreatenewdocument"></a><a name="createnewdocument"></a> CDocTemplate:: Креатеневдокумент

Вызовите эту функцию-член, чтобы создать новый документ типа, связанного с этим шаблоном документа.

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на только что созданный документ или значение NULL при возникновении ошибки.

## <a name="cdoctemplatecreatenewframe"></a><a name="createnewframe"></a> CDocTemplate:: CreateNewFrame

Создает новое окно фрейма, содержащее документ и представление.

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>Параметры

*pDoc*<br/>
Документ, на который должно ссылаться новое окно фрейма. Может иметь значение NULL.

*посер*<br/>
Окно фрейма, на котором должно быть основано новое окно фрейма. Может иметь значение NULL.

### <a name="return-value"></a>Возвращаемое значение

Указатель на только что созданное окно фрейма или значение NULL при возникновении ошибки.

### <a name="remarks"></a>Комментарии

`CreateNewFrame` использует `CRuntimeClass` объекты, передаваемые конструктору, для создания нового окна фрейма с присоединенным представлением и документом. Если параметр *pDoc* имеет значение null, платформа выводит сообщение трассировки.

Параметр *посер* используется для реализации команды Window New. Она предоставляет окно фрейма, в котором можно моделировать новое окно фрейма. Новое окно фрейма обычно создается невидимым. Эта функция вызывается для создания окон фрейма за пределами стандартной платформы создания файлов и открытия файлов.

## <a name="cdoctemplatecreateoleframe"></a><a name="createoleframe"></a> CDocTemplate:: Креатеолефраме

Создает окно фрейма OLE.

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>Параметры

*ппарентвнд*<br/>
Указатель на родительское окно фрейма.

*pDoc*<br/>
Указатель на документ, на который должно ссылаться новое окно фрейма OLE.

*бкреатевиев*<br/>
Определяет, создается ли представление вместе с фреймом.

### <a name="return-value"></a>Возвращаемое значение

Указатель на окно фрейма в случае успеха; в противном случае — NULL.

### <a name="remarks"></a>Комментарии

Если *бкреатевиев* равен нулю, создается пустой фрейм.

## <a name="cdoctemplategetdocstring"></a><a name="getdocstring"></a> CDocTemplate:: Жетдокстринг

Извлекает строку, связанную с типом документа.

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>Параметры

*rStr*<br/>
Ссылка на `CString` объект, который будет содержать строку при возврате функции.

*index*<br/>
Индекс подстроки, извлекаемой из строки, описывающей тип документа. Этот параметр может принимать одно из следующих значений:

- `CDocTemplate::windowTitle` Имя, которое отображается в заголовке окна приложения (например, Microsoft Excel). Представляется только в шаблоне документа для приложений SDI.

- `CDocTemplate::docName` Корневой каталог для имени документа по умолчанию (например, "лист"). Этот корень и число используются для имени по умолчанию нового документа этого типа, когда пользователь выбирает новую команду из меню «файл» (например, «Лист1» или «Лист2»). Если не указано, в качестве значения по умолчанию используется "без названия".

- `CDocTemplate::fileNewName` Имя этого типа документа. Если приложение поддерживает несколько типов документов, эта строка отображается в диалоговом окне Создать файл (например, "лист"). Если не указано, тип документа становится недоступным при помощи команды File New.

- `CDocTemplate::filterName` Описание типа документа и фильтра с подстановочными знаками, соответствующих документам этого типа. Эта строка отображается в раскрывающемся списке "список файлов типа" в диалоговом окне открытия файла (например, "листы (*. xls)"). Если не указано, тип документа недоступен при помощи команды File Open.

- `CDocTemplate::filterExt` Расширение для документов этого типа (например, ". xls"). Если не указано, тип документа недоступен при помощи команды File Open.

- `CDocTemplate::regFileTypeId` Идентификатор для типа документа, который должен храниться в базе данных регистрации, обслуживаемой Windows. Эта строка предназначена только для внутреннего использования (например, "Ексцелворкшит"). Если не указано, тип документа не может быть зарегистрирован в диспетчере файлов Windows.

- `CDocTemplate::regFileTypeName` Имя типа документа, который будет сохранен в базе данных регистрации. Эта строка может отображаться в диалоговых окнах приложений, обращающихся к базе данных регистрации (например, «лист Microsoft Excel»).

### <a name="return-value"></a>Возвращаемое значение

Ненулевое значение, если указанная подстрока найдена; в противном случае — 0.

### <a name="remarks"></a>Комментарии

Вызовите эту функцию, чтобы получить конкретную подстроку, описывающую тип документа. Строка, содержащая эти подстроки, хранится в шаблоне документа и является производной от строки в файле ресурсов для приложения. Платформа вызывает эту функцию для получения строк, необходимых для пользовательского интерфейса приложения. Если вы указали расширение имени файла для документов приложения, платформа также вызывает эту функцию при добавлении записи в базу данных регистрации Windows. Это позволяет открывать документы из диспетчера файлов Windows.

Вызывайте эту функцию только в том случае, если ваш собственный класс является производным от `CDocTemplate` .

## <a name="cdoctemplategetfirstdocposition"></a><a name="getfirstdocposition"></a> CDocTemplate:: Жетфирстдокпоситион

Извлекает расположение первого документа, связанного с этим шаблоном.

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Значение расположения, которое можно использовать для прохода по списку документов, связанных с этим шаблоном документа; или значение NULL, если список пуст.

### <a name="remarks"></a>Комментарии

Используйте эту функцию, чтобы получить расположение первого документа в списке документов, связанных с этим шаблоном. Используйте значение value в качестве аргумента для [CDocTemplate:: жетнекстдок](#getnextdoc) , чтобы выполнить итерацию по списку документов, связанных с шаблоном.

[Ксингледоктемплате](../../mfc/reference/csingledoctemplate-class.md) и [кмултидоктемплате](../../mfc/reference/cmultidoctemplate-class.md) переопределяют эту чисто виртуальную функцию. Любой класс, производный от, `CDocTemplate` должен также переопределить эту функцию.

## <a name="cdoctemplategetnextdoc"></a><a name="getnextdoc"></a> CDocTemplate:: Жетнекстдок

Извлекает элемент List, определенный параметром *RPO*, а затем устанавливает *RPO* в значение value следующей записи в списке.

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>Возвращаемое значение

Указатель на следующий документ в списке документов, связанных с этим шаблоном.

### <a name="parameters"></a>Параметры

*RPO*<br/>
Ссылка на значение значения value, возвращенное предыдущим вызовом [жетфирстдокпоситион](#getfirstdocposition) или `GetNextDoc` .

### <a name="remarks"></a>Комментарии

Если извлеченный элемент является последним в списке, новое значение *RPO* устанавливается в NULL.

Можно использовать `GetNextDoc` в цикле прямой итерации, если исходное расположение устанавливается с вызовом [жетфирстдокпоситион](#getfirstdocposition).

Необходимо убедиться, что значение координаты представляет допустимую точку в списке. Если он является недопустимым, отладочная версия библиотека Microsoft Foundation Class утверждается.

## <a name="cdoctemplateinitialupdateframe"></a><a name="initialupdateframe"></a> CDocTemplate:: Инитиалупдатефраме

Инициализирует окно фрейма и при необходимости делает его видимым.

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>Параметры

*пфраме*<br/>
Окно фрейма, требующее первоначального обновления.

*pDoc*<br/>
Документ, с которым связана рамка. Может иметь значение NULL.

*бмакевисибле*<br/>
Указывает, должна ли рамка быть видимой и активной.

### <a name="remarks"></a>Комментарии

Вызов `IntitialUpdateFrame` после создания новой рамки с помощью `CreateNewFrame` . Вызов этой функции приводит к тому, что представления в этом окне фрейма получают свои `OnInitialUpdate` вызовы. Кроме того, если ранее не было активное представление, основное представление окна фрейма становится активным; первичное представление — это представление с ИДЕНТИФИКАТОРом дочернего элемента AFX_IDW_PANE_FIRST. Наконец, окно фрейма становится видимым, если *бмакевисибле* не равен нулю. Если *бмакевисибле* равен нулю, текущее фокус и видимое состояние окна фрейма останутся без изменений.

Не обязательно вызывать эту функцию при использовании реализации файла New и Open в платформе.

## <a name="cdoctemplateloadtemplate"></a><a name="loadtemplate"></a> CDocTemplate:: Лоадтемплате

Загружает ресурсы для заданного `CDocTemplate` или производного класса.

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Комментарии

Эта функция-член вызывается платформой для загрузки ресурсов для данного `CDocTemplate` или производного класса. Обычно он вызывается во время создания, за исключением случаев, когда шаблон создается глобально. В этом случае вызов метода `LoadTemplate` откладывается до вызова [CWinApp:: AddDocTemplate](../../mfc/reference/cwinapp-class.md#adddoctemplate) .

## <a name="cdoctemplatematchdoctype"></a><a name="matchdoctype"></a> CDocTemplate:: Матчдоктипе

Определяет степень достоверности в совпадении между типом документа и этим шаблоном.

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>Параметры

*лпсзпаснаме*<br/>
Путь к файлу, тип которого необходимо определить.

*рпдокматч*<br/>
Указатель на документ, которому назначен соответствующий документ, если уже открыт файл, заданный параметром *лпсзпаснаме* .

### <a name="return-value"></a>Возвращаемое значение

Значение из перечисления **достоверности** , которое определяется следующим образом:

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>Комментарии

Эта функция используется для определения типа шаблона документа, используемого для открытия файла. Если приложение поддерживает несколько типов файлов, можно использовать эту функцию, чтобы определить, какой из доступных шаблонов документов подходит для данного файла, вызвав `MatchDocType` для каждого шаблона, в свою очередь, и выбрав шаблон в соответствии с возвращаемым значением достоверности.

Если файл, указанный параметром *лпсзпаснаме* , уже открыт, эта функция возвращает `CDocTemplate::yesAlreadyOpen` и копирует объект файла `CDocument` в объект по адресу *рпдокматч*.

Если файл не открыт, но расширение в *лпсзпаснаме* соответствует расширению, заданному `CDocTemplate::filterExt` , эта функция возвращает `CDocTemplate::yesAttemptNative` и ЗАДАЕТ для *рпдокматч* значение null. Дополнительные сведения о `CDocTemplate::filterExt` см. в разделе [CDocTemplate:: жетдокстринг](#getdocstring).

Если ни одно из вариантов не равно true, функция возвращает `CDocTemplate::yesAttemptForeign` .

Реализация по умолчанию не возвращает `CDocTemplate::maybeAttemptForeign` или `CDocTemplate::maybeAttemptNative` . Переопределите эту функцию, чтобы реализовать логику сопоставления типов, подходящую для вашего приложения, возможно, используя эти два значения из перечисления **достоверности** .

## <a name="cdoctemplateopendocumentfile"></a><a name="opendocumentfile"></a> CDocTemplate:: Опендокументфиле

Открывает файл, заданный путем.

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>Параметры

*лпсзпаснаме*<br/>
окне Указатель на путь к файлу, содержащему открываемый документ.

*баддтомру*<br/>
окне Значение TRUE указывает, что документ является одним из самых последних файлов; Значение FALSE указывает, что документ не является одним из самых последних файлов.

### <a name="return-value"></a>Возвращаемое значение

Указатель на документ, имя файла которого имеет значение *лпсзпаснаме*; NULL, если это не удалось.

### <a name="remarks"></a>Комментарии

Открывает файл, путь к которому задается параметром *лпсзпаснаме*. Если *лпсзпаснаме* имеет значение null, создается новый файл, содержащий документ типа, связанного с этим шаблоном.

## <a name="cdoctemplateremovedocument"></a><a name="removedocument"></a> CDocTemplate:: Ремоведокумент

Удаляет документ, на который указывает *pDoc* , из списка документов, связанных с этим шаблоном.

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>Параметры

*pDoc*<br/>
Указатель на документ, который необходимо удалить.

### <a name="remarks"></a>Комментарии

Производные классы `CMultiDocTemplate` и `CSingleDocTemplate` переопределяют эту функцию. Если вы наследуете собственный класс шаблона документа из `CDocTemplate` , производный класс должен переопределить эту функцию.

## <a name="cdoctemplatesaveallmodified"></a><a name="saveallmodified"></a> CDocTemplate:: Савеаллмодифиед

Сохраняет все измененные документы.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Возвращаемое значение

Не равно нулю в случае успешного выполнения; в противном случае — 0.

## <a name="cdoctemplatesetcontainerinfo"></a><a name="setcontainerinfo"></a> CDocTemplate:: Сетконтаинеринфо

Определяет ресурсы для контейнеров OLE при редактировании элемента OLE на месте.

```cpp
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>Параметры

*нидолеинплацеконтаинер*<br/>
ИДЕНТИФИКАТОР ресурсов, используемых при активации внедренного объекта.

### <a name="remarks"></a>Комментарии

Вызовите эту функцию, чтобы задать ресурсы, которые будут использоваться при активации объекта OLE на месте. Эти ресурсы могут включать меню и таблицы сочетаний клавиш. Эта функция обычно вызывается в функции [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) приложения.

Меню, связанное с *нидолеинплацеконтаинер* , содержит разделители, которые позволяют меню активируемого на месте элемента выполнить слияние с меню приложения-контейнера. Дополнительные сведения о слиянии серверов и меню контейнеров см. в [меню и ресурсах (OLE)](../../mfc/menus-and-resources-ole.md)статьи.

## <a name="cdoctemplatesetdefaulttitle"></a><a name="setdefaulttitle"></a> CDocTemplate:: Сетдефаулттитле

Вызовите эту функцию, чтобы загрузить заголовок документа по умолчанию и отобразить его в строке заголовка документа.

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>Параметры

*пдокумент*<br/>
Указатель на документ, заголовок которого должен быть установлен.

### <a name="remarks"></a>Комментарии

Сведения о заголовке по умолчанию см. в описании `CDocTemplate::docName` в [CDocTemplate:: жетдокстринг](#getdocstring).

## <a name="cdoctemplatesetserverinfo"></a><a name="setserverinfo"></a> CDocTemplate:: Сетсерверинфо

Определяет ресурсы и классы, когда серверный документ внедряется или редактируется на месте.

```cpp
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>Параметры

*нидолимбеддинг*<br/>
ИДЕНТИФИКАТОР ресурсов, используемых при открытии внедренного объекта в отдельном окне.

*нидолеинплацесервер*<br/>
ИДЕНТИФИКАТОР ресурсов, используемых при активации внедренного объекта на месте.

*полефрамекласс*<br/>
Указатель на структуру [крунтимекласс](../../mfc/reference/cruntimeclass-structure.md) , содержащую сведения о классе для объекта окна фрейма, созданного при активации на месте.

*полевиевкласс*<br/>
Указатель на `CRuntimeClass` структуру, содержащую сведения о классе для объекта представления, созданного при активации на месте.

### <a name="remarks"></a>Комментарии

Вызовите эту функцию члена для обнаружения ресурсов, которые будут использоваться серверным приложением, когда пользователь запрашивает активацию внедренного объекта. Эти ресурсы состоят из меню и таблиц сочетаний клавиш. Эта функция обычно вызывается в `InitInstance` приложении.

Меню, связанное с *нидолеинплацесервер* , содержит разделители, позволяющие меню сервер выполнить слияние с меню контейнера. Дополнительные сведения о слиянии серверов и меню контейнеров см. в [меню и ресурсах (OLE)](../../mfc/menus-and-resources-ole.md)статьи.

## <a name="cdoctemplatecreatepreviewframe"></a><a name="createpreviewframe"></a> CDocTemplate:: Креатепревиевфраме

Создает дочерний фрейм, используемый для расширенного просмотра.

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>Параметры

*ппарентвнд*<br/>
Указатель на родительское окно (обычно предоставляется оболочкой).

*pDoc*<br/>
Указатель на объект документа, содержимое которого будет предварительно представлено.

### <a name="return-value"></a>Возвращаемое значение

Допустимый указатель на `CFrameWnd` объект или значение null, если создание завершается ошибкой.

### <a name="remarks"></a>Комментарии

## <a name="cdoctemplatesetpreviewinfo"></a><a name="setpreviewinfo"></a> CDocTemplate:: Сетпревиевинфо

Настраивает обработчик незавершенного просмотра.

```cpp
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>Параметры

*нидпревиевфраме*<br/>
Указывает идентификатор ресурса для предварительной версии кадра.

*ппревиевфрамекласс*<br/>
Указывает указатель на структуру сведений о классе среды выполнения предварительной версии кадра.

*ппревиеввиевкласс*<br/>
Указывает указатель на структуру сведений о классе среды выполнения в представлении предварительного просмотра.

### <a name="remarks"></a>Комментарии

## <a name="see-also"></a>См. также раздел

[Класс от CCmdTarget](../../mfc/reference/ccmdtarget-class.md)<br/>
[Иерархическая диаграмма](../../mfc/hierarchy-chart.md)<br/>
[Класс Ксингледоктемплате](../../mfc/reference/csingledoctemplate-class.md)<br/>
[Класс Кмултидоктемплате](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[Класс CDocument](../../mfc/reference/cdocument-class.md)<br/>
[Класс CView](../../mfc/reference/cview-class.md)<br/>
[Класс Кскроллвиев](../../mfc/reference/cscrollview-class.md)<br/>
[Класс CEditView](../../mfc/reference/ceditview-class.md)<br/>
[Класс CFormView](../../mfc/reference/cformview-class.md)<br/>
[Класс CFrameWnd](../../mfc/reference/cframewnd-class.md)<br/>
[Класс CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)
