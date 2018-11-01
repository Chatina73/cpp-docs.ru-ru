---
title: /INTEGRITYCHECK (требование проверки подписи)
ms.date: 11/04/2016
ms.assetid: 9e738825-2c98-40cd-8ad2-5d0d9c14893e
ms.openlocfilehash: 8530175cd5bc0ed5dced7f92e5f67a1576bb43e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50578351"
---
# <a name="integritycheck-require-signature-check"></a>/INTEGRITYCHECK (требование проверки подписи)

Указывает, что цифровая подпись бинарного образа должна быть проверена во время загрузки.

```
/INTEGRITYCHECK[:NO]
```

## <a name="remarks"></a>Примечания

По умолчанию **/INTEGRITYCHECK** отключен.

**/INTEGRITYCHECK** наборы параметров, в заголовке PE исполняемого файла или файла DLL, флаг для диспетчера памяти для проверки цифровой подписи для загрузки образа в Windows. Этот параметр, должно быть задано для 32-разрядных и 64-разрядных библиотек DLL, реализующих кода режима ядра, загруженного некоторыми компонентами Windows и рекомендуется для всех драйверов устройств в Windows Vista, Windows 7, Windows 8, Windows Server 2008 и Windows Server 2012. Версии Windows до Windows Vista игнорируют этот флажок. Дополнительные сведения см. в разделе [принудительно целостности подписи из переносимых исполняемых (PE) файлов](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx).

### <a name="to-set-this-linker-option-in-visual-studio"></a>Настройка этого параметра компоновщика в Visual Studio

1. Откройте диалоговое окно **Окна свойств** проекта. Дополнительные сведения см. в разделе [Работа со свойствами проекта](../../ide/working-with-project-properties.md).

1. Разверните узел **Свойства конфигурации**.

1. Разверните **компоновщика** узла.

1. Выберите **командной строки** страницу свойств.

1. В **Дополнительные параметры**, введите `/INTEGRITYCHECK` или `/INTEGRITYCHECK:NO`.

## <a name="see-also"></a>См. также

[Настройка параметров компоновщика](../../build/reference/setting-linker-options.md)<br/>
[Параметры компоновщика](../../build/reference/linker-options.md)<br/>
[Принудительная целостность подписи из переносимых исполняемых (PE) файлов](http://social.technet.microsoft.com/wiki/contents/articles/255.forced-integrity-signing-of-portable-executable-pe-files.aspx)<br/>
[Пошаговое руководство о подписи кода режима ядра](https://msdn.microsoft.com/windows/hardware/gg487328.aspx)<br/>
[Библиотеки DLL инициализации приложений в Windows 7 и Windows Server 2008](https://msdn.microsoft.com/windows/hardware/gg463040.aspx)