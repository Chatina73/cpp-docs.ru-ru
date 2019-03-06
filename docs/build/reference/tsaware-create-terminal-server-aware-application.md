---
title: /TSAWARE (создание приложения, поддерживающего сервер терминалов)
ms.date: 11/04/2016
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
ms.openlocfilehash: fe31763c5da21a724f0c9242e6eb8429a2379ecd
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421503"
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (создание приложения, поддерживающего сервер терминалов)

```
/TSAWARE[:NO]
```

## <a name="remarks"></a>Примечания

Параметр/TSAWARE устанавливает флаг в поле IMAGE_OPTIONAL_HEADER DllCharacteristics в необязательном заголовке образа программы. Если этот флаг установлен, сервер терминалов не будет вносить определенные изменения в приложение.

Если приложение не поддерживает сервер терминалов (также известный как приложение прежних версий), сервер терминалов выполняет определенные изменения в приложении, чтобы оно работало должным образом в многопользовательской среде. Например сервер терминалов создаст виртуальную папку Windows, таким образом, что каждый пользователь получит в папку Windows, вместо получения directory системы Windows. Это предоставляет пользователям доступ к собственным файлам INI. Кроме того сервер терминалов вносит ряд изменений в реестр приложения прежних версий. Эти изменения снижают скорость загрузки устаревшее приложение на сервере терминалов.

Если приложение поддерживает сервер терминалов, он должен полагаться на ini-файлы и не записи **HKEY_CURRENT_USER** реестра во время установки.

При использовании/TSAWARE, и приложение по-прежнему использует ini-файлы, файлы будут совместно использоваться всеми пользователями системы. Если допустима, по-прежнему можно связать приложение с/TSAWARE; в противном случае необходимо использовать: No.

Параметр/TSAWARE включена по умолчанию для Windows и консольных приложений. См. в разделе [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) и [/Version](../../build/reference/version-version-information.md) сведения.

/ TSAWARE не является допустимым для драйверов, VxD или DLL.

Если приложение было скомпоновано с/TSAWARE, DUMPBIN [/Headers](../../build/reference/headers.md) будут отображаться сведения об этом.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Задание данного параметра компоновщика в среде разработки Visual Studio

1. Откройте диалоговое окно **Страницы свойств** проекта. Дополнительные сведения см. в разделе [свойств проекта Visual C++ параметр](../../ide/working-with-project-properties.md).

1. Нажмите кнопку **компоновщика** папки.

1. Нажмите кнопку **системы** страницу свойств.

1. Изменить **сервера терминалов** свойство.

### <a name="to-set-this-linker-option-programmatically"></a>Задание данного параметра компоновщика программным способом

- См. раздел <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)<br/>
[Хранить сведения о пользователе](/windows/desktop/TermServ/storing-user-specific-information)<br/>
[Устаревшие приложения в среде служб терминалов](https://msdn.microsoft.com/library/aa382957.aspx)
