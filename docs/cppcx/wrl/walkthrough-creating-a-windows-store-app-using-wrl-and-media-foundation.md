---
description: 'Дополнительные сведения: создание приложения UWP с помощью WRL и Media Foundation'
title: Пошаговое руководство. Создание приложения UWP с использованием WRL и Media Foundation
ms.date: 04/15/2021
ms.topic: reference
ms.openlocfilehash: 823d5d53da5d67f79cb4f79e24560d6d581772c3
ms.sourcegitcommit: d531c567c268b676b44abbc8416ba7e20d22044b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2021
ms.locfileid: "107539288"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Пошаговое руководство. Создание приложения UWP с использованием WRL и Media Foundation

> [!NOTE]
> Для новых приложений и компонентов UWP рекомендуется использовать [c++/WinRT](/windows/uwp/cpp-and-winrt-apis/)— новую стандартную проекцию c++ 17 для Среда выполнения Windows API. C++/WinRT доступна в пакете SDK для Windows 10, начиная с версии 1803. C++/WinRT реализована полностью в файлах заголовков и предназначена для предоставления доступа к современным API Windows через первый класс.

В этом руководстве вы узнаете, как использовать библиотеку шаблонов C++ среда выполнения Windows (WRL) для создания приложения универсальная платформа Windows (UWP), использующего [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk).

В этом примере создается настраиваемое преобразование Media Foundation. Он применяет к изображениям, захваченным с веб-камеры, эффекты в градациях серого. Приложение использует C++ для определения пользовательского преобразования и C# для использования компонента и выполнения преобразования захваченного изображения.

> [!NOTE]
> Чтобы воспользоваться пользовательским компонентом преобразования вместо C# можно также использовать JavaScript, Visual Basic или C++.

Для создания среда выполнения Windows компонентов обычно можно использовать C++/CX. Однако иногда необходимо использовать WRL. Например, при создании расширения мультимедиа для Microsoft Media Foundation необходимо создать компонент, реализующий интерфейсы COM и среда выполнения Windows. Так как C++/CX может создавать только объекты среда выполнения Windows, для создания расширения мультимедиа необходимо использовать WRL. Это обусловлено тем, что позволяет реализовать интерфейсы COM и среда выполнения Windows.

> [!NOTE]
> Хотя этот пример кода является объемным, он показывает минимум, необходимый для создания полезных преобразований Media Foundation. Его можно использовать в качестве отправной точки для собственного пользовательского преобразования. Этот пример адаптируется из [примера расширений мультимедиа](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples), в котором используются расширения мультимедиа для применения эффектов к видео, расшифровки видео и создания обработчиков схем, создающих потоки мультимедиа.

## <a name="prerequisites"></a>Предварительные требования

- В Visual Studio 2017 и более поздних версиях поддержка UWP является дополнительным компонентом. Чтобы установить его, откройте Visual Studio Installer из меню "Пуск" Windows и найдите свою версию Visual Studio. Выберите **изменить** и убедитесь, что выбран элемент **Разработка универсальная платформа Windows** . В разделе **необязательные компоненты** проверьте **инструменты c++ для UWP (V141)** для Visual Studio 2017 или **инструменты c++ для UWP (v142)** для Visual Studio 2019. Затем проверьте версию Windows SDK, которую вы хотите использовать.

- Опыт работы с [Среда выполнения Windows](/uwp/api/).

- опыт работы с моделью COM;

- Веб-камера,

## <a name="key-points"></a>Ключевые моменты

- Для создания пользовательского компонента Media Foundation используйте файл определения языка MIDL, чтобы определить и реализовать интерфейс, а затем сделать его активируемым из других компонентов.

- `namespace`Атрибуты и `runtimeclass` , а также `NTDDI_WIN8` значение атрибута [Version](/windows/win32/Midl/version) являются важными частями определения MIDL для Media Foundation компонента, использующего WRL.

- [`Microsoft::WRL::RuntimeClass`](runtimeclass-class.md) является базовым классом для пользовательского компонента Media Foundation. `Microsoft::WRL::RuntimeClassType::WinRtClassicComMix]`Значение перечисления [(runtimeclasstype-Enumeration.md), которое указывается в качестве аргумента шаблона, помечает класс для использования в качестве класса среда выполнения Windows и классического класса среды выполнения COM.

- [`InspectableClass`](inspectableclass-macro.md)Макрос реализует базовые функциональные возможности com, такие как подсчет ссылок и `QueryInterface` метод, и задает имя класса среды выполнения и уровень доверия.

- Используйте [`Microsoft::WRL::Module`](module-class.md) класс для реализации функций точки входа DLL, таких как [`DllGetActivationFactory`](/windows/win32/winrt/functions) , [`DllCanUnloadNow`](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow) и [`DllGetClassObject`](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject) .

- Свяжите библиотеку DLL компонента с *`runtimeobject.lib`* . Также укажите [`/WINMD`](../../cppcx/compiler-and-linker-options-c-cx.md) в строке компоновщика, чтобы создать метаданные Windows.

- Используйте ссылки проекта, чтобы сделать компоненты WRL доступными для приложений UWP.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>Использование WRL для создания компонента преобразования в градациях серого Media Foundation

1. В Visual Studio создайте пустой проект **решения** . Присвойте проекту имя, например *медиакаптуре*.

1. Добавьте в решение проект **DLL (универсальный Windows)** . Присвойте проекту имя, например *грайскалетрансформ*.

1. Добавьте в проект файл **MIDL (. IDL)** . Присвойте файлу имя, например *`GrayscaleTransform.idl`* .

1. Добавьте следующий код в Грайскалетрансформ. IDL:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Используйте следующий код, чтобы заменить содержимое *`pch.h`* :

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Добавьте новый файл заголовка в проект, присвойте ему имя *`BufferLock.h`* , а затем замените содержимое следующим кодом:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. *`GrayscaleTransform.h`* не используется в этом примере. Его можно удалить из проекта при необходимости.

1. Используйте следующий код, чтобы заменить содержимое *`GrayscaleTransform.cpp`* :

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Добавьте новый файл определения модуля в проект, присвойте ему имя *`GrayscaleTransform.def`* , а затем добавьте следующий код:

   ```idl
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Используйте следующий код, чтобы заменить содержимое `dllmain.cpp` :

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. В диалоговом окне **страницы свойств** проекта задайте следующие свойства **компоновщика** .

   1. В разделе **входные данные** для **файла определения модуля** укажите `GrayScaleTransform.def` .

   1. Кроме того, в разделе **входные данные** добавьте `runtimeobject.lib` , `mfuuid.lib` и `mfplat.lib` в свойство **Дополнительные зависимости** .

   1. В разделе **метаданные Windows** задайте для параметра **создать метаданные Windows** значение **Да (/WinMD)**.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>Использование WRL компонента пользовательского Media Foundation из приложения C#

1. Добавьте в решение новый проект **пустое приложение C# (универсальный Windows)** `MediaCapture` . Присвойте проекту имя, например *медиакаптуре*.

1. В проекте **медиакаптуре** добавьте ссылку на `GrayscaleTransform` проект. Дополнительные сведения см. в разделе [как добавить или удалить ссылки с помощью диспетчера ссылок](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. В *`Package.appxmanifest`* на вкладке **возможности** выберите **микрофон** и **веб-камера**. Обе возможности необходимы для получения фотографий с веб-камеры.

1. В *`MainPage.xaml`* добавьте следующий код в корневой [`Grid`](/uwp/api/windows.ui.xaml.controls.grid) элемент:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Используйте следующий код, чтобы заменить содержимое `MainPage.xaml.cs` :

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

На следующем рисунке показан `MediaCapture app` .

![Снимок экрана приложения Медиакаптуре, записывающего фотографию.](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Next Steps

Пример показывает способ записи фотографий (по одной) с веб-камеры по умолчанию. [Пример расширений мультимедиа](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples) выполняет больше возможностей. Здесь показано, как перечислять видеокамеры и работать с локальными обработчиками схем. В этом примере также демонстрируются другие эффекты мультимедиа, которые работают как с отдельными фотографиями, так и с потоками видео.

## <a name="see-also"></a>См. также раздел

[Библиотека шаблонов C++ среда выполнения Windows (WRL)](windows-runtime-cpp-template-library-wrl.md)\
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)
