---
description: 'Дополнительные сведения о: TN065: Dual-Interface поддержка серверов OLE Automation'
title: TN065. Поддержка сдвоенных интерфейсов для серверов автоматизации OLE
ms.date: 06/28/2018
f1_keywords:
- vc.ole
helpviewer_keywords:
- dual interfaces [MFC], OLE Automation
- TN065 [MFC]
- ACDUAL sample [MFC]
- Automation servers [MFC], dual-interface support
ms.assetid: b5c8ed09-2f7f-483c-80fc-2a47ad896063
ms.openlocfilehash: 9add7b42c832944c10b4b607f26b6ca8f23ae300
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214576"
---
# <a name="tn065-dual-interface-support-for-ole-automation-servers"></a>TN065. Поддержка сдвоенных интерфейсов для серверов автоматизации OLE

> [!NOTE]
> Следующее техническое примечание не было обновлено, поскольку сначала оно было включено в электронную документацию. В результате некоторые процедуры и разделы могут быть устаревшими или неверными. Для получения последних сведений рекомендуется выполнить поиск интересующей темы в алфавитном указателе документации в Интернете.

В этом заметке описывается добавление поддержки двух интерфейсов в серверное приложение OLE-автоматизации на основе MFC. Образец [ACDUAL](../overview/visual-cpp-samples.md) иллюстрирует поддержку сдвоенных интерфейсов, а пример кода в этой заметке ВЗЯТ из ACDual. Макросы, описанные в этом примечании, такие как DECLARE_DUAL_ERRORINFO, DUAL_ERRORINFO_PART и IMPLEMENT_DUAL_ERRORINFO, являются частью примера ACDUAL и находятся в МФКДУАЛ. H.

## <a name="dual-interfaces"></a>Сдвоенные интерфейсы

Хотя OLE-автоматизация позволяет реализовать `IDispatch` интерфейс, интерфейс VTBL или сдвоенный интерфейс (который охватывает оба), корпорация Майкрософт настоятельно рекомендует реализовать сдвоенные интерфейсы для всех предоставляемых объектов OLE-автоматизации. Сдвоенные интерфейсы обладают значительными преимуществами только для интерфейсов, исключающих только `IDispatch` VTBL.

- Привязка может выполняться во время компиляции через интерфейс VTBL или во время выполнения с помощью `IDispatch` .

- Использование контроллеров OLE Automation, которые могут использовать интерфейс VTBL, может повысить производительность.

- Существующие контроллеры OLE Automation, использующие `IDispatch` интерфейс, продолжат работать.

- Интерфейс VTBL проще вызывать из C++.

- Сдвоенные интерфейсы необходимы для обеспечения совместимости с функциями поддержки Visual Basic объектов.

## <a name="adding-dual-interface-support-to-a-ccmdtarget-based-class"></a>Добавление поддержки Dual-Interface в класс CCmdTarget-Based

Сдвоенный интерфейс — это просто пользовательский интерфейс, производный от `IDispatch` . Самый простой способ реализовать поддержку двух интерфейсов в `CCmdTarget` классе на основе — сначала реализовать стандартный интерфейс диспетчеризации для класса с помощью MFC и ClassWizard, а затем добавить настраиваемый интерфейс позже. В большинстве случаев ваша реализация пользовательского интерфейса будет просто делегировать `IDispatch` реализацию MFC.

Сначала измените файл ODL для своего сервера, чтобы определить сдвоенные интерфейсы для объектов. Для определения сдвоенного интерфейса необходимо использовать инструкцию Interface, а не `DISPINTERFACE` инструкцию, создаваемую мастером Visual C++. Вместо удаления существующей `DISPINTERFACE` инструкции добавьте новую инструкцию интерфейса. Сохраняя `DISPINTERFACE` форму, можно продолжить использовать ClassWizard для добавления свойств и методов к объекту, но необходимо добавить эквивалентные свойства и методы в оператор интерфейса.

Оператор интерфейса для сдвоенного интерфейса должен иметь атрибуты *oleautomation* и *Dual* , и интерфейс должен быть производным от `IDispatch` . Пример [Guidgen](../overview/visual-cpp-samples.md) можно использовать для создания **идентификатора IID** для сдвоенного интерфейса:

```IDL
[ uuid(0BDD0E81-0DD7-11cf-BBA8-444553540000), // IID_IDualAClick
    oleautomation,
    dual
]
interface IDualAClick : IDispatch
    {
    };
```

Получив оператор Interface, начните добавлять записи для методов и свойств. Для сдвоенных интерфейсов необходимо изменить порядок списков параметров так, чтобы методы и функции доступа к свойствам в сдвоенном интерфейсе возвращали **HRESULT** и передавали их возвращаемые значения в качестве параметров с атрибутами `[retval,out]` . Помните, что для свойств необходимо добавить `propget` функцию доступа Read () и Write ( `propput` ) с одним и тем же идентификатором. Например:

```IDL
[propput, id(1)] HRESULT text([in] BSTR newText);
[propget, id(1)] HRESULT text([out, retval] BSTR* retval);
```

После определения методов и свойств необходимо добавить ссылку на инструкцию Interface в операторе coclass. Пример:

```IDL
[ uuid(4B115281-32F0-11cf-AC85-444553540000) ]
coclass Document
{
    dispinterface IAClick;
    [default] interface IDualAClick;
};
```

После обновления ODL Используйте механизм карты интерфейсов MFC, чтобы определить класс реализации для сдвоенного интерфейса в классе объектов и сделать соответствующие записи в `QueryInterface` механизме MFC. Вам потребуется одна запись в `INTERFACE_PART` блоке для каждой записи в операторе Interface интерфейса ODL, а также записи для интерфейса диспетчеризации. Каждой записи ODL с атрибутом *propput* требуется функция с именем `put_propertyname` . Каждой записи с атрибутом *propget* требуется функция с именем `get_propertyname` .

Чтобы определить класс реализации для сдвоенного интерфейса, добавьте `DUAL_INTERFACE_PART` блок в определение класса объекта. Пример:

```cpp
BEGIN_DUAL_INTERFACE_PART(DualAClick, IDualAClick)
    STDMETHOD(put_text)(THIS_ BSTR newText);
    STDMETHOD(get_text)(THIS_ BSTR FAR* retval);
    STDMETHOD(put_x)(THIS_ short newX);
    STDMETHOD(get_x)(THIS_ short FAR* retval);
    STDMETHOD(put_y)(THIS_ short newY);
    STDMETHOD(get_y)(THIS_ short FAR* retval);
    STDMETHOD(put_Position)(THIS_ IDualAutoClickPoint FAR* newPosition);
    STDMETHOD(get_Position)(THIS_ IDualAutoClickPoint FAR* FAR* retval);
    STDMETHOD(RefreshWindow)(THIS);
    STDMETHOD(SetAllProps)(THIS_ short x, short y, BSTR text);
    STDMETHOD(ShowWindow)(THIS);
END_DUAL_INTERFACE_PART(DualAClick)
```

Чтобы подключить сдвоенный интерфейс к механизму [QueryInterface](/windows/win32/com/queryinterface--navigating-in-an-object) библиотеки MFC, добавьте `INTERFACE_PART` запись в карту интерфейса:

```cpp
BEGIN_INTERFACE_MAP(CAutoClickDoc, CDocument)
    INTERFACE_PART(CAutoClickDoc, DIID_IAClick, Dispatch)
    INTERFACE_PART(CAutoClickDoc, IID_IDualAClick, DualAClick)
END_INTERFACE_MAP()
```

Далее необходимо заполнить реализацию интерфейса. В большинстве случаев вы сможете делегировать существующую `IDispatch` реализацию MFC. Пример:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XDualAClick::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XDualAClick::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfoCount(
    UINT FAR* pctinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);
    return lpDispatch->GetTypeInfoCount(pctinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetTypeInfo(
    UINT itinfo,
    LCID lcid,
    ITypeInfo FAR* FAR* pptinfo)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetTypeInfo(itinfo, lcid, pptinfo);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::GetIDsOfNames(
    REFIID riid,
    OLECHAR FAR* FAR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID FAR* rgdispid)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->GetIDsOfNames(riid, rgszNames, cNames, lcid, rgdispid);
}

STDMETHODIMP CAutoClickDoc::XDualAClick::Invoke(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS FAR* pdispparams,
    VARIANT FAR* pvarResult,
    EXCEPINFO FAR* pexcepinfo,
    UINT FAR* puArgErr)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDispatch = pThis->GetIDispatch(FALSE);
    ASSERT(lpDispatch != NULL);

    return lpDispatch->Invoke(dispidMember, riid, lcid,
        wFlags, pdispparams, pvarResult, pexcepinfo, puArgErr);
}
```

Для методов объекта и функций методов доступа к свойствам необходимо заполнить реализацию. Функции методов и свойств могут в целом делегироваться обратно методам, созданным с помощью ClassWizard. Однако при настройке свойств для прямого доступа к переменным необходимо написать код, чтобы получить или поместить значение в переменную. Пример:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Unicode BSTR to
    // Ansi CString, if necessary...
    pThis->m_str = newText;
    return NOERROR;
}

STDMETHODIMP CAutoClickDoc::XDualAClick::get_text(BSTR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    // MFC automatically converts from Ansi CString to
    // Unicode BSTR, if necessary...
    pThis->m_str.SetSysString(retval);
    return NOERROR;
}
```

## <a name="passing-dual-interface-pointers"></a>Передача Dual-Interfaceных указателей

Передача указателя сдвоенного интерфейса не является достаточно простой, особенно если необходимо вызвать `CCmdTarget::FromIDispatch` . `FromIDispatch` работает только с `IDispatch` указателями MFC. Один из способов обойти это — запросить исходный `IDispatch` указатель, настроенный MFC, и передать этот указатель в функции, которым он необходим. Пример:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::put_Position(
    IDualAutoClickPoint FAR* newPosition)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp = NULL;
    newPosition->QueryInterface(IID_IDispatch, (LPVOID*)&lpDisp);
    pThis->SetPosition(lpDisp);
    lpDisp->Release();
    return NOERROR;
}
```

Перед передачей указателя обратно через метод с двумя интерфейсами может потребоваться преобразовать его из `IDispatch` указателя MFC в указатель сдвоенного интерфейса. Пример:

```
STDMETHODIMP CAutoClickDoc::XDualAClick::get_Position(
    IDualAutoClickPoint FAR* FAR* retval)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    LPDISPATCH lpDisp;
    lpDisp = pThis->GetPosition();
    lpDisp->QueryInterface(IID_IDualAutoClickPoint, (LPVOID*)retval);
    return NOERROR;
}
```

## <a name="registering-the-applications-type-library"></a>Регистрация библиотеки типов приложения

Помощью мастера не создает код для регистрации библиотеки типов серверного приложения OLE Automation в системе. Хотя существует и другие способы регистрации библиотеки типов, приложение может зарегистрировать библиотеку типов при обновлении сведений о типе OLE, то есть при каждом запуске приложения в автономном режиме.

Регистрация библиотеки типов приложения каждый раз, когда приложение запускается автономно:

- Включить AFXCTL. H в стандарте включает файл заголовка STDAFX. З, чтобы получить доступ к определению `AfxOleRegisterTypeLib` функции.

- В `InitInstance` функции приложения нахождение вызова `COleObjectFactory::UpdateRegistryAll` . После этого вызова добавьте вызов `AfxOleRegisterTypeLib` , указав **идентификатор LIBID** , соответствующий вашей библиотеке типов, а также имя библиотеки типов:

    ```cpp
    // When a server application is launched stand-alone, it is a good idea
    // to update the system registry in case it has been damaged.
    m_server.UpdateRegistry(OAT_DISPATCH_OBJECT);

    COleObjectFactory::UpdateRegistryAll();

    // DUAL_SUPPORT_START
        // Make sure the type library is registered or dual interface won't work.
        AfxOleRegisterTypeLib(AfxGetInstanceHandle(),
            LIBID_ACDual,
            _T("AutoClik.TLB"));
    // DUAL_SUPPORT_END
    ```

## <a name="modifying-project-build-settings-to-accommodate-type-library-changes"></a>Изменение параметров сборки проекта для поддержки изменений библиотеки типов

Чтобы изменить параметры сборки проекта таким образом, чтобы файл заголовка, содержащий определения **UUID** , создавался MkTypLib всякий раз при перестроении библиотеки типов:

1. В меню **Сборка** выберите пункт **Параметры**, а затем выберите файл ODL из списка файлов для каждой конфигурации.

2. Перейдите на вкладку **типы OLE** и укажите имя файла в поле **выходной заголовок** имя файла. Используйте имя файла, которое еще не используется проектом, так как MkTypLib перезапишет существующий файл. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **параметры сборки** .

Чтобы добавить определения **UUID** из файла заголовка, созданного MkTypLib, в проект:

1. Включите в стандартный файл заголовка, созданного MkTypLib, в файле заголовка *stdafx. h*.

2. Создайте новый файл ИНИТИИДС. CPP и добавьте его в проект. В этом файле добавьте созданный MkTypLib файл заголовка после включения OLE2. H и ИНИТГУИД. Высоты

    ```cpp
    // initIIDs.c: defines IIDs for dual interfaces
    // This must not be built with precompiled header.
    #include <ole2.h>
    #include <initguid.h>
    #include "acdual.h"
    ```

3. В меню **Сборка** выберите пункт **Параметры**, а затем выберите инитиидс. CPP из списка файлов для каждой конфигурации.

4. Перейдите на вкладку **C++** , щелкните Категория **предварительно скомпилированные заголовки** и установите переключатель **не использовать предкомпилированные заголовки** . Нажмите кнопку ОК, чтобы закрыть диалоговое окно **параметры сборки** .

## <a name="specifying-the-correct-object-class-name-in-the-type-library"></a>Указание правильного имени класса объекта в библиотеке типов

Мастера, поставляемые с Visual C++ неправильно используют имя класса реализации для указания компонентного класса в ODL-файле сервера для классов, создаваемых OLE. Хотя это и будет работать, имя класса реализации, скорее всего, не является именем класса, которое должны использовать пользователи объекта. Чтобы указать правильное имя, откройте файл ODL, перейдите к каждой инструкции coclass и замените имя класса реализации правильным внешним именем.

Обратите внимание, что при изменении оператора coclass имена переменных **CLSID** в файле заголовка, созданном MkTypLib, изменятся соответствующим образом. Вам потребуется обновить код, чтобы использовать новые имена переменных.

## <a name="handling-exceptions-and-the-automation-error-interfaces"></a>Обработка исключений и интерфейсов ошибок службы автоматизации

Методы и функции доступа к свойству объекта автоматизации могут вызывать исключения. В этом случае следует обрабатывать их в реализации сдвоенного интерфейса и передавать сведения об исключении обратно в контроллер через интерфейс обработки ошибок OLE-автоматизации `IErrorInfo` . Этот интерфейс предоставляет подробные и контекстные сведения об ошибках с помощью `IDispatch` интерфейсов и таблицы VTBL. Чтобы указать, что обработчик ошибок доступен, следует реализовать `ISupportErrorInfo` интерфейс.

Чтобы проиллюстрировать механизм обработки ошибок, предположим, что создаваемые ClassWizard функции, используемые для реализации стандартной поддержки диспетчеризации, создают исключения. Реализация MFC `IDispatch::Invoke` обычно перехватывает эти исключения и преобразует их в структуру ексцептинфо, возвращаемую через `Invoke` вызов. Однако, когда используется интерфейс VTBL, вы несете ответственность за перехват исключений самостоятельно. В качестве примера защиты методов с двумя интерфейсами:

```cpp
STDMETHODIMP CAutoClickDoc::XDualAClick::put_text(BSTR newText)
{
    METHOD_PROLOGUE(CAutoClickDoc, DualAClick)
    TRY_DUAL(IID_IDualAClick)
    {
        // MFC automatically converts from Unicode BSTR to
        // Ansi CString, if necessary...
        pThis->m_str = newText;
        return NOERROR;
    }
    CATCH_ALL_DUAL
}
```

`CATCH_ALL_DUAL` следит за возвратом правильного кода ошибки при возникновении исключения. `CATCH_ALL_DUAL` Преобразует исключение MFC в сведения об обработке ошибок OLE-автоматизации с помощью `ICreateErrorInfo` интерфейса. (Пример `CATCH_ALL_DUAL` макроса находится в файле мфкдуал. H в образце [ACDUAL](../overview/visual-cpp-samples.md) . Функция, которую она вызывает для обработчика исключений, `DualHandleException` находится в файле мфкдуал. CPP.) `CATCH_ALL_DUAL` определяет возвращаемый код ошибки в зависимости от типа возникшего исключения:

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) — в этом случае `HRESULT` создается с помощью следующего кода:

    ```cpp
    hr = MAKE_HRESULT(SEVERITY_ERROR, FACILITY_ITF, (e->m_wCode + 0x200));
    ```

   При этом создается `HRESULT` конкретный интерфейс, который вызывал исключение. Код ошибки смещается на 0x200, чтобы избежать конфликтов с определяемыми системой параметрами `HRESULT` для стандартных интерфейсов OLE.

- [CMemoryException](../mfc/reference/cmemoryexception-class.md) — в этом случае `E_OUTOFMEMORY` возвращается.

- В этом случае возвращается любое другое исключение `E_UNEXPECTED` .

Чтобы указать, что используется обработчик ошибок OLE-автоматизации, необходимо также реализовать `ISupportErrorInfo` интерфейс.

Сначала добавьте код в определение класса службы автоматизации, чтобы отобразить его поддержку `ISupportErrorInfo` .

Во вторых, добавьте код в карту интерфейса класса службы автоматизации, чтобы связать `ISupportErrorInfo` класс реализации с `QueryInterface` механизмом MFC. `INTERFACE_PART`Оператор соответствует классу, определенному для `ISupportErrorInfo` .

Наконец, Реализуйте класс, определенный для поддержки `ISupportErrorInfo` .

(Пример [ACDUAL](../overview/visual-cpp-samples.md) содержит три макроса, которые помогут выполнить эти три шага,, `DECLARE_DUAL_ERRORINFO` `DUAL_ERRORINFO_PART` и `IMPLEMENT_DUAL_ERRORINFO` , все они содержатся в мфкдуал. H.)

В следующем примере реализуется класс, определенный для поддержки `ISupportErrorInfo` . `CAutoClickDoc` — Это имя класса автоматизации, а `IID_IDualAClick` — **идентификатор IID** для интерфейса, который является источником ошибок, передаваемых через объект ошибки OLE-автоматизации:

```cpp
STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::AddRef()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalAddRef();
}

STDMETHODIMP_(ULONG) CAutoClickDoc::XSupportErrorInfo::Release()
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalRelease();
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::QueryInterface(
    REFIID iid,
    LPVOID* ppvObj)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return pThis->ExternalQueryInterface(&iid, ppvObj);
}

STDMETHODIMP CAutoClickDoc::XSupportErrorInfo::InterfaceSupportsErrorInfo(
    REFIID iid)
{
    METHOD_PROLOGUE(CAutoClickDoc, SupportErrorInfo)
    return (iid == IID_IDualAClick) S_OK : S_FALSE;
}
```

## <a name="see-also"></a>См. также раздел

[Технические примечания по номеру](../mfc/technical-notes-by-number.md)<br/>
[Технические примечания по категориям](../mfc/technical-notes-by-category.md)
