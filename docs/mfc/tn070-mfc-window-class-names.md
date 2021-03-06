---
description: 'Дополнительные сведения о: TN070: имена классов окон MFC'
title: TN070. Имена классов окна MFC
ms.date: 11/04/2016
helpviewer_keywords:
- window class names [MFC]
- TN070 [MFC]
ms.assetid: 90617912-dd58-4a7c-9082-ced71736d7cd
ms.openlocfilehash: 963f343f480a5805a3c1ec3cf5499583a17535ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214524"
---
# <a name="tn070-mfc-window-class-names"></a>TN070. Имена классов окна MFC

> [!NOTE]
> Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию. В результате некоторые процедуры и разделы могут быть устаревшими или неверными. Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.

В окнах MFC используется динамически создаваемое имя класса, отражающее возможности окна. MFC динамически создает имена классов для окон фрейма, представлений и всплывающих окон, создаваемых приложением. В диалоговых окнах и элементах управления, создаваемых приложением MFC, имеется имя класса окна, предоставленное Windows.

Можно заменить динамически предоставляемое имя класса, зарегистрировав собственный класс окна и используя его в переопределении [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow). Имена классов, предоставляемые MFC, соответствуют одной из двух следующих форм:

```
Afx:%x:%x
Afx:%x:%x:%x:%x:%x
```

Шестнадцатеричные цифры, заменяющие `%x` символы, заполняются из данных из структуры [вндкласс](/windows/win32/api/winuser/ns-winuser-wndclassw) . MFC использует этот метод, чтобы несколько классов C++, которым требуются идентичные структуры **вндкласс** , могли совместно использовать один и тот же зарегистрированный класс окна. В отличие от большинства простых приложений Win32, приложения MFC имеют только одно приложение **WndProc**, поэтому вы можете легко использовать структуры **вндкласс** для экономии времени и памяти. Ниже приведены заменяемые значения для приведенных `%x` выше символов.

- **ВНДКЛАСС. hInstance**

- **ВНДКЛАСС. Style**

- **ВНДКЛАСС. Хкурсор**

- **ВНДКЛАСС. Хбрбаккграунд**

- **ВНДКЛАСС. Хикон**

Первая форма ( `Afx:%x:%x` ) используется, если значения **хкурсор**, **Хбрбаккграунд** и **Хикон** равны **null**.

## <a name="see-also"></a>См. также раздел

[Технические примечания по номеру](../mfc/technical-notes-by-number.md)<br/>
[Технические примечания по категориям](../mfc/technical-notes-by-category.md)<br/>
[TN020: соглашения об именовании и нумерации ИДЕНТИФИКАТОРов](../mfc/tn020-id-naming-and-numbering-conventions.md)
