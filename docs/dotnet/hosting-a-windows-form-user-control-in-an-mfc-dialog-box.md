---
description: 'Дополнительные сведения: размещение пользовательского элемента управления формы Windows Forms в диалоговом окне MFC'
title: Размещение пользовательского элемента управления формы Windows Forms в диалоговом окне MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- hosting Windows Forms control [C++]
- Windows Forms [C++], MFC support
ms.assetid: 9f66ee52-b7cb-4ffd-8306-392a5da990d8
ms.openlocfilehash: 1bd1db9d9805c10247840ca6043c94d4e3e3abe7
ms.sourcegitcommit: c20734f18d3d49bb38b1628c68b53b54b3eeeb03
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2021
ms.locfileid: "99522811"
---
# <a name="hosting-a-windows-form-user-control-in-an-mfc-dialog-box"></a>Размещение пользовательского элемента управления формы Windows Forms в диалоговом окне MFC

MFC размещает элемент управления Windows Forms как Специальный тип элемента управления ActiveX и взаимодействует с элементом управления с помощью интерфейсов ActiveX, а также свойств и методов <xref:System.Windows.Forms.Control> класса. Для работы с элементом управления рекомендуется использовать свойства и методы платформа .NET Framework.

> [!NOTE]
> В текущем выпуске `CDialogBar` объект не может содержать элементы управления Windows Forms.

## <a name="in-this-section"></a>В этом разделе

[Как создать пользовательский элемент управления и узел в диалоговом окне](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)

[Инструкции. Привязка данных DDX/DDV с помощью Windows Forms](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)

[Как приемник Windows Forms событий из собственных классов C++](../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

## <a name="reference"></a>Справочник

Класс [квинформсконтрол](../mfc/reference/cwinformscontrol-class.md) &#124; класс [CDialog](../mfc/reference/cdialog-class.md) &#124; [Класс CWnd](../mfc/reference/cwnd-class.md) &#124;<xref:System.Windows.Forms.Control>

## <a name="see-also"></a>См. также

[Использование пользовательского элемента управления формы Windows Forms в MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)<br/>
[Отличия в программировании Windows Forms и MFC](../dotnet/windows-forms-mfc-programming-differences.md)<br/>
[Размещение пользовательского элемента управления формы Windows Forms в качестве представления MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Размещение пользовательского элемента управления формы Windows Forms в виде диалогового окна MFC](../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)
