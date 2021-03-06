---
description: Дополнительные сведения см. в статье обработка уведомлений о настройке.
title: Обработка уведомлений о настройке
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: b5e104f118ac0eeff96965692615ce9143c5c178
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254967"
---
# <a name="handling-customization-notifications"></a>Обработка уведомлений о настройке

Стандартный элемент управления панели инструментов Windows имеет встроенную функциональность настройки, в том числе системное диалоговое окно настроек, которое позволяет пользователю вставлять, удалять и переупорядочивать кнопки панели управления. Приложение определяет, доступны ли функции настройки, и контролирует степень, в которой пользователь может настроить панель инструментов.

Можно сделать эти функции настройки доступными для пользователя, предоставив панели инструментов стиль **CCS_ADJUSTABLE** . Функции настройки позволяют пользователю перетащить кнопку на новую позицию или удалить ее, перетащив с панели инструментов. Кроме того, пользователь может дважды щелкнуть панель инструментов, чтобы открыть диалоговое окно **Настройка панели инструментов** , которое позволяет пользователю добавить, удалить и переупорядочить кнопки панели инструментов. Приложение может отобразить диалоговое окно, используя функцию-член [Customize](reference/ctoolbarctrl-class.md#customize) .

Элемент управления "Панель инструментов" отправляет сообщения уведомления в родительское окно на каждом шаге процесса настройки. Если пользователь удерживает клавишу SHIFT и начинает перетаскивать кнопку, панель инструментов автоматически обработает операцию перетаскивания. Панель инструментов отправляет уведомление **TBN_QUERYDELETE** в родительское окно, чтобы определить, можно ли удалить кнопку. Операция перетаскивания завершается, если родительское окно возвращает **FALSE**. В противном случае панель инструментов захватывает ввод мыши и ждет, пока пользователь отпустит кнопку мыши.

Когда пользователь отпускает кнопку мыши, элемент управления "Панель инструментов" определяет положение указателя мыши. Если указатель находится за пределами панели инструментов, кнопка будет удалена. Если курсор наведен на другую кнопку панели инструментов, панель инструментов отправляет сообщение уведомления **TBN_QUERYINSERT** в родительское окно, чтобы определить, можно ли вставить кнопку слева от указанной кнопки. Кнопка будет вставлена, если родительское окно возвращает **TRUE**; в противном случае этого не произойдет. Панель инструментов отправляет сообщение уведомления **TBN_TOOLBARCHANGE** , чтобы сообщить об окончании операции перетаскивания.

Если пользователь начинает операцию перетаскивания, не удерживая клавишу SHIFT, элемент управления "Панель инструментов" отправляет сообщение уведомления **TBN_BEGINDRAG** окну-владельцу. Приложение, которое реализует собственный код перетаскивания кнопок, может воспринимать это сообщение в качестве сигнала к началу операции перетаскивания. Панель инструментов отправляет сообщение уведомления **TBN_ENDDRAG** , чтобы сообщить об окончании операции перетаскивания.

Элемент управления "Панель инструментов" отправляет сообщение уведомления, когда пользователь настраивает панель инструментов в диалоговом окне **Настройка панели инструментов** . Панель инструментов отправляет сообщение уведомления **TBN_BEGINADJUST** после того, как пользователь дважды щелкает панель инструментов, но перед созданием диалогового окна. Далее панель инструментов начинает отправлять ряд сообщений уведомления **TBN_QUERYINSERT** , чтобы определить, допускает ли панель инструментов вставку кнопок. Если родительское окно возвращает **TRUE**, панель инструментов останавливает отправку сообщений уведомления **TBN_QUERYINSERT** . Если родительское окно не возвращает значение **TRUE** для какой-либо из кнопок, панель инструментов удаляет диалоговое окно.

Далее элемент управления "Панель инструментов" определяет, можно ли удалить какие-нибудь кнопки из панели инструментов, отправляя одно сообщение уведомления **TBN_QUERYDELETE** для каждой кнопки в панели инструментов. Родительское окно возвращает **TRUE** , чтобы указать, что кнопку можно удалить; в противном случае возвращается значение **FALSE**. Панель инструментов добавляет все кнопки панели инструментов в диалоговое окно, но отключает те, которые невозможно удалить.

Каждый раз, когда элементу управления "Панель инструментов" требуются сведения о кнопке в диалоговом окне "Настройка панели инструментов", он отправляет сообщение уведомления **TBN_GETBUTTONINFO** , в котором указан индекс кнопки, для которой ему требуются сведения, и адрес структуры **TBNOTIFY** . Родительское окно должно заполнить структуру актуальной информацией.

В диалоговом окне **Настройка панели инструментов** есть кнопки "Справка" и "Сбросить". Когда пользователь нажимает кнопку "Справка", элемент управления "Панель инструментов" отправляет сообщение уведомления **TBN_CUSTHELP** . Родительское окно должно отвечать путем отображения справочной информации. Диалоговое окно отправляет сообщение уведомления **TBN_RESET** , когда пользователь нажимает кнопку "Сбросить". Это сообщение указывает на то, что панель инструментов собирается повторно инициализировать диалоговое окно.

Все эти сообщения являются сообщениями **WM_NOTIFY** , и их можно обрабатывать в окне-владельце путем добавления следующей формы записей карты сообщений для окна-владельца:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   Код идентификатора сообщения уведомления, например **TBN_BEGINADJUST**.

- **идконтрол**

   Идентификатор элемента управления, отправляющего уведомление.

- **мемберфксн**

   Функция-член, которая должна быть вызвана при получении этого уведомления.

Функция-член должна быть объявлена со следующим прототипом:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Если обработчик сообщений уведомления возвращает значение, то он должен помещать его в **LRESULT** , на который указывает *result*.

Для каждого сообщения `pNotifyStruct` указывает на структуру **NMHDR** или **TBNOTIFY** . Эти структуры описаны ниже.

Структура **NMHDR** содержит следующие члены:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Дескриптор окна элемента управления, который отправляет уведомление. Чтобы преобразовать этот дескриптор в указатель `CWnd` , используйте [CWnd::FromHandle](reference/cwnd-class.md#fromhandle).

- **idFrom**

   Идентификатор элемента управления, отправляющего уведомление.

- **code**

   Код уведомления. Этот член может иметь значение, относящимся к конкретному типу элемента управления, например **TBN_BEGINADJUST** или **TTN_NEEDTEXT**, либо он может иметь одно из общих значений уведомлений, перечисленных ниже:

  - **NM_CLICK** Пользователь щелкнул элемент управления левой кнопкой мыши.

  - **NM_DBLCLK** Пользователь дважды щелкнул элемент управления левой кнопкой мыши.

  - **NM_KILLFOCUS** Элемент управления потерял фокус ввода.

  - **NM_OUTOFMEMORY** Элементу управления не удалось выполнить операцию из-за нехватки памяти.

  - **NM_RCLICK** Пользователь щелкнул элемент управления правой кнопкой мыши.

  - **NM_RDBLCLK** Пользователь дважды щелкнул элемент управления правой кнопкой мыши.

  - **NM_RETURN** Элемент управления имеет фокус ввода, и пользователь нажал клавишу ВВОД.

  - **NM_SETFOCUS** Элемент управления получил фокус ввода.

Структура **TBNOTIFY** содержит следующие члены:

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   Общие сведения для всех сообщений **WM_NOTIFY** .

- **iItem**

   Индекс кнопки, связанной с уведомлением.

- **tbButton**

   Структура **тббуттон** , содержащая сведения о кнопке панели инструментов, связанной с уведомлением.

- **cchText**

   Число символов в тексте кнопки.

- **lpszText**

   Указатель на текст кнопки.

Уведомления, которые отправляет панель инструментов:

- **TBN_BEGINADJUST**

   Посылается, когда пользователь начинает настраивать элемент управления ToolBar. Указатель указывает на структуру **NMHDR** , которая содержит сведения об уведомлении. Обработчику не нужно возвращать конкретное значение.

- **TBN_BEGINDRAG**

   Посылается, когда пользователь начинает перетаскивать кнопку в элементе управления ToolBar. Указатель указывает на структуру **TBNOTIFY** . Член **iItem** содержит отсчитываемый от нуля индекс перетаскиваемой кнопки. Обработчику не нужно возвращать конкретное значение.

- **TBN_CUSTHELP**

   Посылается, когда пользователь нажимает кнопку "Справка" в диалоговом окне "Настройка панели инструментов". Нет возвращаемого значения. Указатель указывает на структуру **NMHDR** , которая содержит сведения о сообщении уведомления. Обработчику не нужно возвращать конкретное значение.

- **TBN_ENDADJUST**

   Посылается, когда пользователь останавливает настройку элемента управления ToolBar. Указатель указывает на структуру **NMHDR** , которая содержит сведения о сообщении уведомления. Обработчику не нужно возвращать конкретное значение.

- **TBN_ENDDRAG**

   Посылается, когда пользователь останавливает перетаскивание кнопки в элементе управления ToolBar. Указатель указывает на структуру **TBNOTIFY** . Член **iItem** содержит отсчитываемый от нуля индекс перетаскиваемой кнопки. Обработчику не нужно возвращать конкретное значение.

- **TBN_GETBUTTONINFO**

   Посылается, когда пользователь настраивает элемент управления ToolBar. Панель инструментов использует это сообщение уведомления для извлечения информации, необходимой диалоговому окну "Настройка панели инструментов". Указатель указывает на структуру **TBNOTIFY** . Член **iItem** указывает отсчитываемый от нуля индекс кнопки. Члены **pszText** и **cchText** указывают адрес и длину в символах текущего текста кнопки. Приложение должно заполнить структуру сведениями о кнопке. Возвращает **TRUE** , если сведения о кнопке скопированы в структуру; в противном случае — **FALSE** .

- **TBN_QUERYDELETE**

   Посылается, когда пользователь настраивает панель инструментов, чтобы определить, можно ли удалить кнопку из элемента управления ToolBar. Указатель указывает на структуру **TBNOTIFY** . Член **iItem** содержит отсчитываемый от нуля индекс удаляемой кнопки. Возвращает **TRUE** , чтобы разрешить удаление кнопки, или **FALSE** , чтобы предотвратить удаление кнопки.

- **TBN_QUERYINSERT**

   Посылается, когда пользователь настраивает элемент управления ToolBar, чтобы определить, можно ли вставить кнопку слева от данной кнопки. Указатель указывает на структуру **TBNOTIFY** . Член **iItem** содержит отсчитываемый от нуля индекс вставляемой кнопки. Возвращает **TRUE** , чтобы разрешить вставить кнопку перед указанной кнопкой, или **FALSE** , чтобы предотвратить вставку кнопки.

- **TBN_RESET**

   Посылается, когда пользователь сбрасывает содержимое диалогового окна "Настройка панели инструментов". Указатель указывает на структуру **NMHDR** , которая содержит сведения о сообщении уведомления. Обработчику не нужно возвращать конкретное значение.

- **TBN_TOOLBARCHANGE**

   Посылается после того, как пользователь настроил элемент управления ToolBar. Указатель указывает на структуру **NMHDR** , которая содержит сведения о сообщении уведомления. Обработчику не нужно возвращать конкретное значение.

## <a name="see-also"></a>См. также раздел

[Использование CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Элементы управления](controls-mfc.md)
