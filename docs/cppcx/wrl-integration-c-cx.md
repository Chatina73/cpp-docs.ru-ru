---
description: 'Дополнительные сведения о: WRL Integration (C++/CX)'
title: Интеграция с WRL (C++/CX)
ms.date: 01/22/2017
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
ms.openlocfilehash: ecf0bec03fedc0e860bb4f546d4ef067db681139
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287961"
---
# <a name="wrl-integration-ccx"></a>Интеграция с WRL (C++/CX)

Вы можете свободно сочетать код WRL с кодом среда выполнения Windows библиотеки шаблонов C++ (WRL). В той же записи преобразования можно использовать объекты, объявленные с нотацией WRL Handle-to-Object ( `^` ), и WRL с помощью смарт-указателя ( `ComPtr<T>` ). Однако необходимо вручную управлять возвращаемыми значениями, а также WRL коды ошибок HRESULT и исключения WRL.

## <a name="wrl-development"></a>Разработка WRL

Дополнительные сведения о создании и использовании компонентов WRL см. в разделе [Библиотека шаблонов C++ среда выполнения Windows (WRL)](./wrl/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Пример

В следующем фрагменте кода показано использование WRL и WRL для использования классов среда выполнения Windows и проверки файла метаданных.

Пример взят из фрагмента кода на форуме создание Microsoft Store приложений. Автор этого фрагмента кода приводит следующие замечания и оговорки:

1. C++ не предоставляет определенные API для отражения среда выполнения Windows типов, но файлы метаданных Windows (. winmd) для типа полностью соответствуют файлам метаданных CLR. Windows предоставляет новые API обнаружения метаданных (RoGetMetaDataFile), позволяющие получить WINMD-файл для указанного типа. Однако возможности применения этих API при разработке в C++ ограничены, поскольку пользователь не может создать экземпляр класса.

1. После компиляции кода необходимо передать файлы Runtimeobject.lib и Rometadata.lib компоновщику.

1. Этот фрагмент предоставляется на условиях "как есть". В принципе он должен работать правильно, однако возможность ошибок не исключена.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}
```

## <a name="see-also"></a>См. также раздел

[Взаимодействие с другими языками](interoperating-with-other-languages-c-cx.md)
