---
title: 'CWinApp: Класс Application'
ms.date: 11/04/2016
f1_keywords:
- CWinApp
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
ms.openlocfilehash: d9f0d4f5ba6b6b070b23ce98ecda8c7accf44934
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241566"
---
# <a name="cwinapp-the-application-class"></a>CWinApp: Класс Application

Главный класс приложения в MFC инкапсулирует инициализации, выполнения и завершения приложения для операционной системы Windows. Приложения, созданного на платформе должен иметь один и только один объект класса, производный от [CWinApp](../mfc/reference/cwinapp-class.md). Этот объект собран перед созданием windows.

`CWinApp` является производным от `CWinThread`, который представляет основной поток выполнения для приложения, который может содержать один или несколько потоков. В последних версиях MFC `InitInstance`, **запуска**, `ExitInstance`, и `OnIdle` функции-члены являются фактически в классе `CWinThread`. Эти функции описаны здесь, как если бы они были `CWinApp` членов вместо этого, поскольку относится роль объекта как объект приложения, а не как основной поток.

> [!NOTE]
>  Класса приложения является основной поток выполнения приложения. С помощью функций Win32 API, можно также создать второстепенных потоков выполнения. Эти потоки могут использовать библиотеку MFC. Дополнительные сведения см. в разделе [многопоточность](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Как и любой программы для операционной системы Windows, приложения framework имеет `WinMain` функции. В приложении framework, однако не написать `WinMain`. Он предоставляется библиотекой классов и вызывается при запуске приложения. `WinMain` выполняет стандартных служб, таких как Регистрация классов окон. Затем он вызывает член функции объекта приложения для инициализации и запуска приложения. (Вы можете настроить `WinMain` путем переопределения `CWinApp` функции-члены, `WinMain` вызовов.)

Для инициализации этого приложения `WinMain` вызывает объект приложения `InitApplication` и `InitInstance` функций-членов. Чтобы запустить цикл обработки сообщений приложения, `WinMain` вызовы **запуска** функция-член. При прерывании `WinMain` вызывает объект приложения `ExitInstance` функция-член.

> [!NOTE]
>  Имена, показанных в **полужирным** в этой документации, обозначающих элементы, предоставляемые библиотеки классов Microsoft Foundation и Visual C++. Имена, показанных в `monospaced` типа указывают элементы, которые можно создать или переопределить.

## <a name="see-also"></a>См. также

[Общие разделы по MFC](../mfc/general-mfc-topics.md)<br/>
[CWinApp и мастер приложений MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)<br/>
[Переопределяемые функции-члены CWinApp](../mfc/overridable-cwinapp-member-functions.md)<br/>
[Специальные службы CWinApp](../mfc/special-cwinapp-services.md)
