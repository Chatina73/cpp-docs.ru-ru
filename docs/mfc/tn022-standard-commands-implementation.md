---
description: 'Дополнительные сведения о: TN022: реализация стандартных команд'
title: TN022. Реализация стандартных команд
ms.date: 11/04/2016
f1_keywords:
- vc.commands
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
ms.openlocfilehash: 7c8540dcf0e41e5f6d5f00a4f22568c4df0fcdbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215811"
---
# <a name="tn022-standard-commands-implementation"></a>TN022. Реализация стандартных команд

> [!NOTE]
> Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию. В результате некоторые процедуры и разделы могут быть устаревшими или неверными. Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.

В этом заметке описываются стандартные реализации команд, предоставляемые MFC 2,0. Ознакомьтесь с [техническим примечанием 21](../mfc/tn021-command-and-message-routing.md) сначала, поскольку в нем описываются механизмы, используемые для реализации многих стандартных команд.

В этом описании предполагается знание архитектур MFC, API-интерфейсов и распространенной практики программирования. Описаны и недокументированные API-интерфейсы только для реализации. Это не самое место для начала изучения функций и программирования в MFC. Дополнительные сведения о документированных API см. в Visual C++.

## <a name="the-problem"></a>Проблема

MFC определяет множество стандартных идентификаторов команд в файле заголовка AFXRES. H. Поддержка платформ для этих команд различается. Понимание того, где и как классы платформы обрабатывают эти команды, не только показывает, как работает платформа, но предоставит полезную информацию о настройке стандартных реализаций и о том, как настроить стандартные реализации и изучить несколько методов реализации собственных обработчиков команд.

## <a name="contents-of-this-technical-note"></a>Содержание этой технической заметки

Каждый идентификатор команды описан в двух разделах:

- Заголовок: символическое имя идентификатора команды (например, ID_FILE_SAVE), за которым следует назначение команды (например, "сохраняет текущий документ"), разделенные двоеточием.

- Один или несколько абзацев, описывающих, какие классы реализуют команду, и что делает реализация по умолчанию

Большинство реализаций команд по умолчанию предустановлены в схеме сообщений базового класса платформы. Существует несколько реализаций команд, требующих явной привязки в производном классе. Они описаны в разделе "Примечание". Если вы выбрали правильные параметры в помощью мастера, эти обработчики по умолчанию будут подключены в созданном приложении скелета.

## <a name="naming-convention"></a>Соглашение об именовании

Стандартные команды соответствуют простому соглашению об именовании, которое рекомендуется использовать по возможности. Большинство стандартных команд находятся в стандартных местах в строке меню приложения. Символическое имя команды начинается с "ID_", за которым следует стандартное имя всплывающего меню, за которым следует имя пункта меню. Символьное имя в верхнем регистре с разбиением на слова с подчеркиванием. Для команд, не имеющих стандартных имен элементов меню, имя логической команды определяется, начиная с "ID_" (например, ID_NEXT_PANE).

Префикс "ID_" используется для указания команд, предназначенных для привязки к элементам меню, кнопкам панели инструментов или другим объектам пользовательского интерфейса команды. Обработчики команд, обрабатывающие команды "ID_", должны использовать механизмы ON_COMMAND и ON_UPDATE_COMMAND_UI архитектуры команд MFC.

Мы рекомендуем использовать стандартный префикс "IDM_" для пунктов меню, которые не соответствуют архитектуре команд и нуждаются в коде для их включения и отключения в меню. Конечно, количество команд меню должно быть небольшим, так как в отличие от архитектуры команд MFC не только делает обработчики команд более мощными (так как они будут работать с панелями инструментов), но делают код обработчика команд пригодным для повторного использования.

## <a name="id-ranges"></a>Диапазоны ИДЕНТИФИКАТОРов

Дополнительные сведения об использовании диапазонов ИДЕНТИФИКАТОРов в MFC см. в [техническом примечании 20](../mfc/tn020-id-naming-and-numbering-conventions.md) .

Стандартные команды MFC попадают в диапазон 0xE000 в 0xEFFF. Не полагайтесь на конкретные значения этих идентификаторов, так как они могут быть изменены в будущих версиях библиотеки.

Приложение должно определить свои команды в диапазоне от 0x8000 до 0xDFFF.

## <a name="standard-command-ids"></a>Стандартные идентификаторы команд

Для каждого идентификатора команды существует стандартная строка запроса сообщения, которую можно найти в ЗАПРОСах файла. RC. Идентификатор строки для этого командного окна меню должен быть таким же, как и для идентификатора команды.

- ID_FILE_NEW создает новый или пустой документ.

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   `CWinApp::OnFileNew` реализует эту команду по-разному в зависимости от количества шаблонов документов в приложении. Если имеется только один `CDocTemplate` , `CWinApp::OnFileNew` создаст новый документ этого типа, а также правильный класс Frame и View.

   Если имеется более одного `CDocTemplate` , `CWinApp::OnFileNew` запросит у пользователя диалоговое окно (AFX_IDD_NEWTYPEDLG), позволяющее выбрать тип документа для использования. Выбранный объект `CDocTemplate` используется для создания документа.

   Одной из распространенных настроек ID_FILE_NEW является предоставление другого и более графического выбора типов документов. В этом случае можно реализовать собственный интерфейс `CMyApp::OnFileNew` и поместить его в схему сообщений вместо `CWinApp::OnFileNew` . Вызывать реализацию базового класса не требуется.

   Другой распространенной настройкой ID_FILE_NEW является предоставление отдельной команды для создания документа каждого типа. В этом случае следует определить новые идентификаторы команд, например ID_FILE_NEW_CHART и ID_FILE_NEW_SHEET.

- ID_FILE_OPEN открывает существующий документ.

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   `CWinApp::OnFileOpen` имеет очень простую реализацию вызова, `CWinApp::DoPromptFileName` за которым следует `CWinApp::OpenDocumentFile` имя файла или путь к файлу, который необходимо открыть. `CWinApp`Подпрограммы реализации `DoPromptFileName` открывает стандартное диалоговое окно FileOpen и заполняют его расширениями файлов, полученными из текущих шаблонов документов.

   Одной из распространенных настроек ID_FILE_OPEN является настройка диалогового окна FileOpen или добавление дополнительных фильтров файлов. Для этого рекомендуется заменить реализацию по умолчанию собственным диалоговым окном FileOpen и вызвать `CWinApp::OpenDocumentFile` с именем файла или путем к файлу документа. Нет необходимости вызывать базовый класс.

- ID_FILE_CLOSE закрывает открытый в данный момент документ.

   `CDocument::OnFileClose` вызывает метод, `CDocument::SaveModified` предлагающий пользователю сохранить документ, если он был изменен, а затем вызывает `OnCloseDocument` . Вся закрывающая логика, включая уничтожение документа, выполняется в `OnCloseDocument` подпрограммы.

    > [!NOTE]
    >  ID_FILE_CLOSE действует иначе из сообщения WM_CLOSE или команды SC_CLOSE системы, отправленной в окно фрейм документа. Закрытие окна приведет к закрытию документа только в том случае, если это окно последнего кадра, показывающее документ. Закрытие документа с ID_FILE_CLOSE не только закрывает документ, но и закрывает все окна фрейма, отображающие документ.

- ID_FILE_SAVE сохраняет текущий документ.

   В реализации используется вспомогательная подпрограммы `CDocument::DoSave` , которая используется как для `OnFileSave` , так и для `OnFileSaveAs` . Если сохранить документ, который не был сохранен ранее (т. е. он не имеет имени пути, например в случае Филенев) или был считан из документа, доступного только для чтения, `OnFileSave` логика будет действовать как команда ID_FILE_SAVE_AS и попросить пользователя предоставить новое имя файла. Фактический процесс открытия файла и выполнения сохранения осуществляется с помощью виртуальной функции `OnSaveDocument` .

   Существует две распространенные причины для настройки ID_FILE_SAVE. Для документов, которые не сохраняются, просто удалите элементы меню ID_FILE_SAVE и кнопки панели инструментов из пользовательского интерфейса. Кроме того, убедитесь, что документ не был изменен (т. е. не вызывается `CDocument::SetModifiedFlag` ), и платформа не будет вызывать сохранение документа. Для документов, которые сохраняются в другом файле, а не на диске, определите новую команду для этой операции.

   В случае `COleServerDoc` , ID_FILE_SAVE используется как для сохранения файлов (для обычных документов), так и для обновления файлов (для внедренных документов).

   Если данные документа хранятся в отдельных файлах на диске, но вы не хотите использовать реализацию сериализации по умолчанию `CDocument` , следует переопределить `CDocument::OnSaveDocument` вместо `OnFileSave` .

- ID_FILE_SAVE_AS сохраняет текущий документ под другим именем файла.

   `CDocument::OnFileSaveAs`Реализация использует ту же `CDocument::DoSave` вспомогательную подпрограммы, что и `OnFileSave` . `OnFileSaveAs`Команда обрабатывается так же, как ID_FILE_SAVE, если перед сохранением в документах не было имени файла. `COleServerDoc::OnFileSaveAs` реализует логику для сохранения обычного файла данных документа или для сохранения серверного документа, представляющего объект OLE, внедренный в другое приложение, в виде отдельного файла.

   Если вы настраиваете логику ID_FILE_SAVE, вам, вероятно, потребуется настроить ID_FILE_SAVE_AS подобным образом или операция "Сохранить как" может не применяться к документу. Вы можете удалить пункт меню из строки меню, если это не требуется.

- ID_FILE_SAVE_COPY_AS сохраняет текущий документ копии под новым именем.

   `COleServerDoc::OnFileSaveCopyAs`Реализация очень похожа на `CDocument::OnFileSaveAs` , за исключением того, что объект документа не прикрепляется к базовому файлу после сохранения. То есть, если документ в памяти был изменен перед сохранением, он все равно изменяется. Кроме того, эта команда не влияет на имя пути или заголовок, хранящиеся в документе.

- ID_FILE_UPDATE уведомляет контейнер о сохранении внедренного документа.

   `COleServerDoc::OnUpdateDocument`Реализация просто уведомляет контейнер о том, что внедрение должно быть сохранено. Затем контейнер вызывает соответствующие API-интерфейсы OLE, чтобы сохранить внедренный объект.

- ID_FILE_PAGE_SETUP вызывает диалоговое окно настройки страницы или макета для конкретного приложения.

   В настоящее время для этого диалогового окна нет стандартного стандарта, и у платформы нет реализации этой команды по умолчанию.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_FILE_PRINT_SETUP вызвать стандартное диалоговое окно настройки печати.

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   Эта команда вызывает стандартное диалоговое окно настройки печати, позволяющее пользователю настроить принтер и параметры печати по крайней мере для этого документа или для всех документов в этом приложении. Для изменения параметров принтера по умолчанию для всей системы необходимо использовать панель управления.

   `CWinApp::OnFilePrintSetup` имеет очень простую реализацию создания `CPrintDialog` объекта и вызова `CWinApp::DoPrintDialog` функции реализации. Задается настройка принтера по умолчанию для приложения.

   Общая необходимость в настройке этой команды заключается в том, чтобы разрешить параметры принтера для каждого документа, которые должны сохраняться вместе с документом при сохранении. Для этого необходимо добавить обработчик схемы сообщений в `CDocument` класс, который создает `CPrintDialog` объект, инициализирует его с соответствующими атрибутами принтера (обычно *хдевмоде* и *хдевнамес*), вызвать `CPrintDialog::DoModal` и сохранить измененные параметры принтера. Для надежной реализации следует рассмотреть реализацию `CWinApp::DoPrintDialog` для обнаружения ошибок и `CWinApp::UpdatePrinterSelection` для работы с разумными по умолчанию и отслеживания изменений в масштабах всей системы.

- ID_FILE_PRINT стандартной печати текущего документа

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CView` схеме сообщений производного класса.

   Эта команда выводит текущий документ или правильно, запускает процесс печати, который включает в себя вызов стандартного диалогового окна печати и запуск обработчика печати.

   `CView::OnFilePrint` реализует эту команду и главный цикл печати. Он вызывает виртуальную функцию `CView::OnPreparePrinting` для запроса пользователя в диалоговом окне печати. Затем он подготавливает выходной контроллер домена для перехода на принтер, открывает диалоговое окно хода выполнения печати (AFX_IDD_PRINTDLG) и отправляет Escape- `StartDoc` последовательность на принтер. `CView::OnFilePrint` также содержит главный цикл печати, ориентированный на страницы. Для каждой страницы вызывается виртуальный объект, `CView::OnPrepareDC` за которым следует `StartPage` escape-последовательность и вызов виртуальной функции `CView::OnPrint` для этой страницы. По завершении `CView::OnEndPrinting` вызывается виртуальный метод, и диалоговое окно хода выполнения печати закрывается.

   Архитектура печати MFC поддерживает различные способы печати и предварительного просмотра печати. Обычно `CView` для всех задач печати, ориентированных на страницы, можно найти различные функции, допускающие переопределение. Только в случае приложения, использующего принтер для вывода, не ориентированного на страницы, должно быть необходимо заменить реализацию ID_FILE_PRINT.

- ID_FILE_PRINT_PREVIEW войти в режим предварительного просмотра для текущего документа.

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CView` схеме сообщений производного класса.

   `CView::OnFilePrintPreview` запускает режим предварительного просмотра, вызывая задокументированную вспомогательную функцию `CView::DoPrintPreview` . `CView::DoPrintPreview` является основным механизмом для цикла предварительного просмотра печати, точно так же, как `OnFilePrint` основной механизм для цикла печати.

   Операцию предварительного просмотра можно настроить различными способами, передавая различные параметры в `DoPrintPreview` . См. [техническое примечание 30](../mfc/tn030-customizing-printing-and-print-preview.md), в котором обсуждаются некоторые сведения о предварительном просмотре печати и о том, как ее настроить.

- ID_FILE_MRU_FILE1... FILE16 диапазон идентификаторов команд для **списка** использованных файлов.

   `CWinApp::OnUpdateRecentFileMenu` — Это обработчик пользовательского интерфейса команды Update, который является одним из более сложных применений механизма ON_UPDATE_COMMAND_UI. В ресурсе меню необходимо определить только один элемент меню с ИДЕНТИФИКАТОРом ID_FILE_MRU_FILE1. Этот пункт меню остается изначально отключенным.

   По мере роста списка MRU в список добавляются дополнительные пункты меню. Стандартная `CWinApp` Реализация по умолчанию использует стандартный предел четырех последних использованных файлов. Вы можете изменить значение по умолчанию, вызвав его `CWinApp::LoadStdProfileSettings` с большим или меньшим значением. Список MRU хранится в приложении. INI-файл. Список загружается в `InitInstance` функцию приложения при вызове `LoadStdProfileSettings` и сохраняется при выходе из приложения. Обработчик пользовательского интерфейса команды обновления MRU также будет преобразовывать абсолютные пути в относительные пути для вывода в меню файл.

   `CWinApp::OnOpenRecentFile` обработчик ON_COMMAND, выполняющий фактическую команду. Он просто получает имя файла из списка MRU и вызывает `CWinApp::OpenDocumentFile` , который выполняет всю работу по открытию файла и обновлению списка MRU.

   Настройка этого обработчика команд не рекомендуется.

- ID_EDIT_CLEAR очистить текущее выделение

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды с помощью `CEdit::Clear` . Команда отключена, если нет текущего выбора.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_CLEAR_ALL очищает весь документ.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды. Пример реализации см. в примере учебника по MFC [Scribble](../overview/visual-cpp-samples.md) .

- ID_EDIT_COPY копирует текущий выделенный фрагмент в буфер обмена.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды, которая копирует текущий выделенный текст в буфер обмена, как CF_TEXT с помощью `CEdit::Copy` . Команда отключена, если нет текущего выбора.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_CUT вырезает выделенный фрагмент в буфер обмена.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды, которая вырезает выделенный текст в буфер обмена как CF_TEXT с помощью `CEdit::Cut` . Команда отключена, если нет текущего выбора.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_FIND начинает операцию поиска, вызывает немодальное диалоговое окно поиска.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды, которая вызывает вспомогательную функцию реализации `OnEditFindReplace` для использования и хранения предыдущих параметров поиска и замены в переменных реализации Private. `CFindReplaceDialog`Класс используется для управления немодальным диалоговым окном для запроса пользователя.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_PASTE Вставляет текущее содержимое буфера обмена.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды, которая копирует текущие данные буфера обмена, заменяя выделенный текст с помощью `CEdit::Paste` . Команда отключена, если в буфере обмена нет **CF_TEXT** .

   `COleClientDoc` просто предоставляет обработчик пользовательского интерфейса команды обновления для этой команды. Если буфер обмена не содержит внедренный OLE-элемент или объект, команда будет отключена. Вы несете ответственность за написание обработчика для фактической команды на выполнение фактического вставления. Если приложение OLE может также вставлять другие форматы, необходимо предоставить собственный обработчик пользовательского интерфейса для команды обновления в представлении или документе (то есть в другом месте `COleClientDoc` в маршрутизации целевого объекта команды).

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

   Для замены стандартной реализации OLE используйте `COleClientItem::CanPaste` .

- ID_EDIT_PASTE_LINK вставляет ссылку из текущего содержимого буфера обмена.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `COleDocument` просто предоставляет обработчик пользовательского интерфейса команды обновления для этой команды. Если буфер обмена не содержит OLE-элемент или объект, команда будет отключена. Вы несете ответственность за написание обработчика для фактической команды на выполнение фактического вставления. Если приложение OLE может также вставлять другие форматы, необходимо предоставить собственный обработчик пользовательского интерфейса для команды обновления в представлении или документе (то есть в другом месте `COleDocument` в маршрутизации целевого объекта команды).

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

   Для замены стандартной реализации OLE используйте `COleClientItem::CanPasteLink` .

- ID_EDIT_PASTE_SPECIAL Вставляет текущее содержимое буфера обмена с параметрами.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса. MFC не предоставляет это диалоговое окно.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_REPEAT повторяет последнюю операцию.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды для повторения последней операции поиска. Используются переменные закрытой реализации для последнего поиска. Команда отключена, если не удается выполнить поиск.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_REPLACE начинает операцию замены, открывает немодальное диалоговое окно замены.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды, которая вызывает вспомогательную функцию реализации `OnEditFindReplace` для использования и хранения предыдущих параметров поиска и замены в переменных реализации Private. `CFindReplaceDialog`Класс используется для управления немодальным диалоговым окном, предлагающим пользователю.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_SELECT_ALL выделяет весь документ.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды, которая выбирает весь текст в документе. Команда отключена, если нет текста для выбора.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_UNDO отменяет последнюю операцию.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   `CEditView` предоставляет реализацию этой команды с помощью `CEdit::Undo` . Команда отключена, если `CEdit::CanUndo` возвращает значение false.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_EDIT_REDO выполняет последнюю операцию.

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для каждого `CView` производного класса.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_WINDOW_NEW открывает другое окно в активном документе.

   `CMDIFrameWnd::OnWindowNew` реализует эту мощную функцию с помощью шаблона документа текущего документа для создания другого фрейма, содержащего другое представление текущего документа.

   Как и в большинстве команд меню окон многодокументного интерфейса (MDI), команда отключена, если нет активного дочернего окна MDI.

   Настройка этого обработчика команд не рекомендуется. Если вы хотите предоставить команду, которая создает дополнительные представления или окна фрейма, вы, вероятно, лучше будете использовать собственную команду. Можно клонировать код из `CMDIFrameWnd::OnWindowNew` и изменить его на конкретный кадр и просмотреть нужные классы.

- ID_WINDOW_ARRANGE упорядочивает значки в нижней части окна MDI.

   `CMDIFrameWnd` реализует эту стандартную команду MDI в вспомогательной функции реализации `OnMDIWindowCmd` . Этот вспомогательный модуль сопоставляет идентификаторы команд с сообщениями MDI Windows и может совместно использовать много кода.

   Как и большинство команд меню окон MDI, команда отключена, если нет активного дочернего окна MDI.

   Настройка этого обработчика команд не рекомендуется.

- ID_WINDOW_CASCADE расположить окна каскадом, чтобы они были перекрываться.

   `CMDIFrameWnd` реализует эту стандартную команду MDI в вспомогательной функции реализации `OnMDIWindowCmd` . Этот вспомогательный модуль сопоставляет идентификаторы команд с сообщениями MDI Windows и может совместно использовать много кода.

   Как и большинство команд меню окон MDI, команда отключена, если нет активного дочернего окна MDI.

   Настройка этого обработчика команд не рекомендуется.

- ID_WINDOW_TILE_HORZ окна мозаики по горизонтали.

   Эта команда реализуется `CMDIFrameWnd` так же, как ID_WINDOW_CASCADE, за исключением того, что для операции используется другое сообщение Windows MDI.

   Необходимо выбрать ориентацию плитки по умолчанию для приложения. Это можно сделать, изменив идентификатор для пункта меню "плитка" окна на ID_WINDOW_TILE_HORZ или ID_WINDOW_TILE_VERT.

- ID_WINDOW_TILE_VERT окна плиток по вертикали.

   Эта команда реализуется `CMDIFrameWnd` так же, как ID_WINDOW_CASCADE, за исключением того, что для операции используется другое сообщение Windows MDI.

   Необходимо выбрать ориентацию плитки по умолчанию для приложения. Это можно сделать, изменив идентификатор для пункта меню "плитка" окна на ID_WINDOW_TILE_HORZ или ID_WINDOW_TILE_VERT.

- ID_WINDOW_SPLIT интерфейс клавиатуры к разделителю.

   `CView` обрабатывает эту команду для `CSplitterWnd` реализации. Если представление является частью окна разделителя, эта команда будет делегировать функцию реализации `CSplitterWnd::DoKeyboardSplit` . При этом разделитель будет размещен в режиме, позволяющем пользователям с клавиатуры разбивать или разбивать окно разделителя.

   Эта команда недоступна, если представление не находится в разделителе.

   Настройка этого обработчика команд не рекомендуется.

- ID_APP_ABOUT вызывает диалоговое окно "о программе".

   Для приложения "о программе" нет стандартной реализации. Приложение по умолчанию, созданное помощью мастера, создаст пользовательский класс диалогового окна для приложения и будет использовать его как окно "о программе". Помощью мастера будет также писать тривиальный обработчик команд, который обрабатывает эту команду и вызывает диалоговое окно.

   Эта команда почти всегда реализуется.

- ID_APP_EXIT выйти из приложения.

   `CWinApp::OnAppExit` обрабатывает эту команду, отправляя сообщение WM_CLOSE в главное окно приложения. Стандартное завершение работы приложения (запрос «грязных» файлов и т. д.) обрабатывается `CFrameWnd` реализацией.

   Настройка этого обработчика команд не рекомендуется. Рекомендуется переопределение `CWinApp::SaveAllModified` или `CFrameWnd` закрытие логики.

   Если вы решили реализовать эту команду, мы рекомендуем использовать этот идентификатор команды.

- ID_HELP_INDEX список разделов справки из. Файл HLP.

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   `CWinApp::OnHelpIndex` обрабатывает эту команду простым вызовом `CWinApp::WinHelp` .

   Настройка этого обработчика команд не рекомендуется.

- ID_HELP_USING отображает справку по использованию справки.

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   `CWinApp::OnHelpUsing` обрабатывает эту команду простым вызовом `CWinApp::WinHelp` .

   Настройка этого обработчика команд не рекомендуется.

- ID_CONTEXT_HELP переходит в режим справки "SHIFT-F1".

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   `CWinApp::OnContextHelp` обрабатывает эту команду, настроив курсор режима справки, вводя модальный цикл и ожидая выбора пользователем окна для получения справки. Дополнительные сведения о реализации справки MFC см. в [технической заметке 28](../mfc/tn028-context-sensitive-help-support.md) .

   Настройка этого обработчика команд не рекомендуется.

- ID_HELP предоставляет справку по текущему контексту

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   `CWinApp::OnHelp` обрабатывает эту команду, получая верный контекст справки для текущего контекста приложения. Он обрабатывает простую справку F1, справку по окнам сообщений и т. д. Дополнительные сведения о реализации справки MFC см. в [технической заметке 28](../mfc/tn028-context-sensitive-help-support.md) .

   Настройка этого обработчика команд не рекомендуется.

- ID_DEFAULT_HELP отображает справку по умолчанию для контекста

    > [!NOTE]
    >  Чтобы включить эту функцию, необходимо подключить его к `CWinApp` схеме сообщений производного класса.

   Эта команда обычно сопоставляется с `CWinApp::OnHelpIndex` .

   Можно указать другой обработчик команд, если требуется различие между справкой по умолчанию и индексом справки.

- ID_NEXT_PANE переходит к следующей панели

   `CView` обрабатывает эту команду для `CSplitterWnd` реализации. Если представление является частью окна разделителя, эта команда будет делегировать функцию реализации `CSplitterWnd::OnNextPaneCmd` . Это приведет к перемещению активного представления на следующую панель в разделителе.

   Эта команда недоступна, если представление не находится в разделителе или отсутствует следующая панель для перехода.

   Настройка этого обработчика команд не рекомендуется.

- ID_PREV_PANE переход к предыдущей панели

   `CView` обрабатывает эту команду для `CSplitterWnd` реализации. Если представление является частью окна разделителя, эта команда будет делегировать функцию реализации `CSplitterWnd::OnNextPaneCmd` . Это приведет к перемещению активного представления на предыдущую панель в разделителе.

   Эта команда отключена, если представление не находится в разделителе или отсутствует Предыдущая панель для перехода.

   Настройка этого обработчика команд не рекомендуется.

- ID_OLE_INSERT_NEW вставляет новый OLE-объект

   В настоящее время для этой команды нет стандартной реализации. Его необходимо реализовать для `CView` класса, производного от, чтобы вставить новый объект OLE Item или Object в текущее выделение.

   Все клиентские приложения OLE должны реализовать эту команду. Помощью мастера с параметром OLE создаст скелет реализации `OnInsertObject` в классе представления, который потребуется выполнить.

   Полную реализацию этой команды см. в примере MFC OLE пример [OCLIENT](../overview/visual-cpp-samples.md) .

- ID_OLE_EDIT_LINKS изменяет связи OLE

   `COleDocument` обрабатывает эту команду с помощью реализации стандартного диалогового окна OLE-ссылок, предоставляемого MFC. Реализация этого диалогового окна доступна через `COleLinksDialog` класс. Если текущий документ не содержит ссылок, команда будет отключена.

   Настройка этого обработчика команд не рекомендуется.

- ID_OLE_VERB_FIRST... Последний диапазон ИДЕНТИФИКАТОРов для команд OLE

   `COleDocument` использует этот диапазон ИДЕНТИФИКАТОРов команд для команд, поддерживаемых текущим выбранным объектом OLE-элементом. Это должен быть диапазон, так как данный тип элемента или объекта OLE может поддерживать ноль или более пользовательских команд. В меню приложения должен быть один пункт меню с ИДЕНТИФИКАТОРом ID_OLE_VERB_FIRST. При запуске программы в меню будет добавлено соответствующее описание команды меню (или всплывающее меню со многими командами). Управление меню OLE обрабатывается с помощью `AfxOleSetEditMenu` обработчика пользовательского интерфейса команды обновления для этой команды.

   Нет явных обработчиков команд для обработки каждого идентификатора команды в этом диапазоне. `COleDocument::OnCmdMsg` переопределяется для перехвата всех идентификаторов команд в этом диапазоне, преобразования их в номера глаголов, начинающиеся с нуля, и запуска сервера для этой команды (с помощью `COleClientItem::DoVerb` ).

   Не рекомендуется настраивать или использовать этот диапазон ИДЕНТИФИКАТОРов команд.

- ID_VIEW_TOOLBAR включает и выключает панель инструментов

   `CFrameWnd` обрабатывает эту команду и обработчик пользовательского интерфейса команды обновления для переключения видимого состояния панели инструментов. Панель инструментов должна быть дочерним окном фрейма с ИДЕНТИФИКАТОРом дочернего окна AFX_IDW_TOOLBAR. Обработчик команд фактически переключает окно панели инструментов на видимость. `CFrameWnd::RecalcLayout` используется для перерисовки окна фрейма с помощью панели инструментов в новом состоянии. Обработчик пользовательского интерфейса команды Update — выполняет проверку элемента меню, когда панель инструментов отображается.

   Настройка этого обработчика команд не рекомендуется. Если вы хотите добавить дополнительные панели инструментов, необходимо клонировать и изменить обработчик команд, а также обработчик пользовательского интерфейса команды обновления для этой команды.

- ID_VIEW_STATUS_BAR включает и выключает строку состояния

   Эта команда реализуется `CFrameWnd` так же, как ID_VIEW_TOOLBAR, за исключением того, что используется другой идентификатор дочернего окна (AFX_IDW_STATUS_BAR).

## <a name="update-only-command-handlers"></a>Обработчики команд Update-Only

В качестве индикаторов в строках состояния используются несколько стандартных идентификаторов команд. Они используют один и тот же механизм обработки пользовательского интерфейса команды обновления для отображения текущего визуального состояния во время простоя приложения. Поскольку пользователь не может выбрать пользователя (т. е. невозможно отправить панель строки состояния), нет смысла иметь обработчик ON_COMMAND для этих идентификаторов команд.

- ID_INDICATOR_CAPS: индикатор блокировки CAP.

- ID_INDICATOR_NUM: индикатор NUM LOCK.

- ID_INDICATOR_SCRL: индикатор блокировки SCRL.

- ID_INDICATOR_KANA: индикатор блокировки японской азбуки (применим только к японским системам).

Все три из них реализуются в `CFrameWnd::OnUpdateKeyIndicator` , вспомогательный метод реализации, который использует идентификатор команды для соотнесения с соответствующим виртуальным ключом. Распространенная реализация включает или отключает (для панелей состояния Disabled = без текста) `CCmdUI` объект в зависимости от того, заблокирован ли соответствующий виртуальный ключ.

Настройка этого обработчика команд не рекомендуется.

- ID_INDICATOR_EXT: Расширенный индикатор SELECT.

- ID_INDICATOR_OVR: перечеркивание индикатора.

- ID_INDICATOR_REC: индикатор записи.

В настоящее время нет стандартной реализации этих индикаторов.

Если вы решили реализовать эти индикаторы, мы рекомендуем использовать эти идентификаторы индикаторов и поддерживать порядок индикаторов в строке состояния (т. е. в таком порядке: EXT, CAP, NUM, SCRL, ОВР, REC).

## <a name="see-also"></a>См. также раздел

[Технические примечания по номеру](../mfc/technical-notes-by-number.md)<br/>
[Технические примечания по категориям](../mfc/technical-notes-by-category.md)
