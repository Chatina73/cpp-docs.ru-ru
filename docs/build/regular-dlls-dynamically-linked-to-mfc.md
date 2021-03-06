---
description: 'Подробнее о следующем: Обычные библиотеки DLL MFC, динамически связанные с MFC'
title: Обычные библиотеки DLL MFC, динамически связанные с MFC
ms.date: 11/04/2016
helpviewer_keywords:
- regular MFC DLLs [C++], dynamically linked to MFC
- AFX_MANAGE_STATE macro
- DLLs [C++], regular
- shared DLL versions [C++]
- dynamically linked DLLs [C++]
ms.assetid: b4f7ab92-8723-42a5-890e-214f4e29dcd0
ms.openlocfilehash: a16320427d881e2d37dd2afedc0566a759d59b9a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273869"
---
# <a name="regular-mfc-dlls-dynamically-linked-to-mfc"></a>Обычные библиотеки DLL MFC, динамически связанные с MFC

Обычная библиотека DLL MFC, динамически связанная с MFC, — это библиотека DLL, которая использует MFC на внутреннем уровне, а экспортированные функции в библиотеке DLL могут вызываться исполняемыми файлами MFC или не MFC. Как понятно из названия, такие библиотеки DLL создаются с помощью библиотеки динамической компоновки MFC (также известной как общая версия MFC). Как правило, функции экспортируются из обычной библиотеки DLL MFC с использованием стандартного интерфейса C.

Необходимо добавить макрос `AFX_MANAGE_STATE` в начало всех экспортированных функций в обычных библиотеках DLL MFC, которые динамически связываются с MFC, чтобы установить текущее состояние модуля в качестве значения для библиотеки DLL. Это можно сделать, добавив следующую строку кода в начало функций, экспортированных из библиотеки DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Обычная библиотека DLL MFC, динамически связанная с MFC, предоставляет следующие возможности.

- Это новый тип библиотеки DLL, представленный в Visual C++ 4.0.

- Клиентский исполняемый файл может быть написан на любом языке, поддерживающем использование библиотек DLL (C, C++, Pascal, Visual Basic и т. д.). Он необязательно должен быть приложением MFC.

- В отличие от статически связанных обычных библиотек DLL MFC библиотеки DLL этого типа динамически связываются с библиотекой DLL MFC (также называемой общей библиотекой DLL MFC).

- Библиотека импорта MFC, связанная с этим типом библиотек DLL, аналогична той, которая используется для библиотек DLL расширения MFC или приложений, использующих библиотеку DLL MFC: MFCxx(D).lib.

Обычная библиотека DLL MFC, динамически связанная с MFC, имеет следующие требования.

- Эти библиотеки DLL компилируются с **_AFXDLL**, как и исполняемый файл, динамически связываемый с библиотекой DLL MFC. Но также определяется **_USRDLL**, как и обычная библиотека DLL MFC, которая статически связана с MFC.

- Этот тип библиотеки DLL должен создавать экземпляр класса, производного от `CWinApp`.

- Этот тип библиотеки DLL использует `DllMain`, предоставляемый MFC. Весь код инициализации, относящийся к библиотеке DLL, следует размещать в функции-члене `InitInstance`, а код завершения — в `ExitInstance`, как в обычном приложении MFC.

Поскольку этот тип библиотеки DLL использует версию библиотеки динамической компоновки MFC, необходимо явным образом задать для текущего модуля библиотеку DLL. Для этого используйте макрос [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) в начале каждой функции, экспортированной из библиотеки DLL.

Обычные библиотеки DLL MFC должны иметь класс, производный от `CWinApp`, и один объект этого класса приложения так же, как и приложение MFC. Однако у объекта `CWinApp` библиотеки DLL (в отличие от объекта `CWinApp` приложения) нет основного генератора сообщений.

Обратите внимание, что механизм `CWinApp::Run` не применяется к библиотеке DLL, так как в приложении есть основной генератор сообщений. Если ваша библиотека DLL открывает немодальные диалоговые окна или имеет собственное окно фрейма, основной конвейер сообщений приложения должен вызвать подпрограммы, экспортируемые из библиотеки DLL, которые вызывают `CWinApp::PreTranslateMessage`.

Весь код инициализации, относящийся к библиотеке DLL, следует размещать в функции-члене `CWinApp::InitInstance`, как в обычном приложении MFC. Функция-член `CWinApp::ExitInstance` производного класса `CWinApp` вызывается из библиотеки MFC, предоставленной `DllMain`, перед выгрузкой библиотеки DLL.

Необходимо распространить общие библиотеки MFCx0.dll и Msvcr*0.dll (или аналогичные файлы) с приложением.

Библиотека DLL, динамически связанная с MFC, не может быть статически связана с MFC. Приложения ссылаются на обычные библиотеки DLL MFC, динамически связываемые с MFC, так же как и любые другие библиотеки DLL.

Как правило, символы экспортируются из обычной библиотеки DLL MFC с использованием стандартного интерфейса C. Объявление функции, экспортированной из обычной библиотеки DLL MFC, выглядит примерно следующим образом:

```
extern "C" __declspec(dllexport) MyExportedFunction( );
```

Все выделения памяти в обычной библиотеке DLL MFC должны оставаться в этой библиотеке. Библиотека DLL не должна передавать в вызывающий исполняемый файл или получать из него следующие объекты:

- указатели на объекты MFC;

- указатели на память, выделенную с помощью MFC.

Если необходимо выполнить какие-либо из указанных выше действий или между вызывающим исполняемым файлом и библиотекой DLL нужно передать объекты, производные от MFC, следует создать библиотеку DLL расширения MFC.

Безопасно передавать указатели на память, которая была выделена библиотеками времени выполнения C, между приложением и DLL можно только в том случае, если сделана копия данных. Нельзя удалять эти указатели, изменять их размер или использовать их без создания копии памяти.

При создании обычной библиотеки DLL MFC, которая динамически связывается с MFC, необходимо использовать макрос [AFX_MANAGE_STATE](../mfc/reference/extension-dll-macros.md#afx_manage_state) для правильного переключения состояния модуля MFC. Это можно сделать, добавив следующую строку кода в начало функций, экспортированных из библиотеки DLL:

```
AFX_MANAGE_STATE(AfxGetStaticModuleState( ))
```

Макрос **AFX_MANAGE_STATE** не следует использовать в обычных библиотеках DLL MFC, которые статически связываются с MFC или в библиотеках DLL расширения MFC. Дополнительные сведения см. в статье [Управление данными состояния модулей MFC](../mfc/managing-the-state-data-of-mfc-modules.md).

Пример создания, сборки и использования обычной библиотеки DLL MFC см. в примере [DLLScreenCap](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/advanced/DllScreenCap). Дополнительные сведения об обычных библиотеках DLL MFC, которые динамически связываются с MFC, см. в разделе "Преобразование DLLScreenCap в динамическую компоновку с библиотекой DLL MFC" в аннотации в качестве примера.

## <a name="what-do-you-want-to-do"></a>Выберите действие

- [Инициализация обычных библиотек DLL MFC](run-time-library-behavior.md#initializing-regular-dlls)

## <a name="what-do-you-want-to-know-more-about"></a>Дополнительные сведения

- [Состояния модулей обычной библиотеки DLL MFC, динамически связанной с MFC](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)

- [Управление данными состояния модулей MFC](../mfc/managing-the-state-data-of-mfc-modules.md)

- [Использование библиотек DLL расширений MFC для баз данных, OLE и сокетов в обычных DLL-библиотеках MFC](using-database-ole-and-sockets-extension-dlls-in-regular-dlls.md)

- [Использование MFC как части библиотеки DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)

## <a name="see-also"></a>См. также

[Типы библиотек DLL](kinds-of-dlls.md)
