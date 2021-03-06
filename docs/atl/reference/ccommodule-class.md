---
description: 'Дополнительные сведения о: CComModule Class'
title: Класс CComModule
ms.date: 08/19/2019
f1_keywords:
- CComModule
- ATLBASE/ATL::CComModule
- ATLBASE/ATL::CComModule::GetClassObject
- ATLBASE/ATL::CComModule::GetModuleInstance
- ATLBASE/ATL::CComModule::GetResourceInstance
- ATLBASE/ATL::CComModule::GetTypeLibInstance
- ATLBASE/ATL::CComModule::Init
- ATLBASE/ATL::CComModule::RegisterClassHelper
- ATLBASE/ATL::CComModule::RegisterClassObjects
- ATLBASE/ATL::CComModule::RegisterServer
- ATLBASE/ATL::CComModule::RegisterTypeLib
- ATLBASE/ATL::CComModule::RevokeClassObjects
- ATLBASE/ATL::CComModule::Term
- ATLBASE/ATL::CComModule::UnregisterClassHelper
- ATLBASE/ATL::CComModule::UnregisterServer
- ATLBASE/ATL::CComModule::UpdateRegistryClass
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceD
- ATLBASE/ATL::CComModule::UpdateRegistryFromResourceS
- ATLBASE/ATL::CComModule::m_csObjMap
- ATLBASE/ATL::CComModule::m_csTypeInfoHolder
- ATLBASE/ATL::CComModule::m_csWindowCreate
- ATLBASE/ATL::CComModule::m_hInst
- ATLBASE/ATL::CComModule::m_hInstResource
- ATLBASE/ATL::CComModule::m_hInstTypeLib
- ATLBASE/ATL::CComModule::m_pObjMap
helpviewer_keywords:
- CComModule class
- DLL modules [C++], ATL
ms.assetid: f5face2c-8fd8-40e6-9ec3-54ab74701769
ms.openlocfilehash: dd0ec6c6aa7d68374a90830b10815a9cbdd54aeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2020
ms.locfileid: "97152026"
---
# <a name="ccommodule-class"></a>Класс CComModule

Начиная с ATL 7,0, `CComModule` не рекомендуется. Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
> Этот класс и его члены не могут использоваться в приложениях, выполняемых в среда выполнения Windows.

## <a name="syntax"></a>Синтаксис

```
class CComModule : public _ATL_MODULE
```

## <a name="members"></a>Члены

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CComModule:: Жетклассобжект](#getclassobject)|Создает объект указанного идентификатора CLSID. Только для библиотек DLL.|
|[CComModule:: Жетмодулеинстанце](#getmoduleinstance)|Возвращает `m_hInst`.|
|[CComModule:: Жетресаурцеинстанце](#getresourceinstance)|Возвращает `m_hInstResource`.|
|[CComModule::GetTypeLibInstance](#gettypelibinstance)|Возвращает `m_hInstTypeLib`.|
|[CComModule:: init](#init)|Инициализирует элементы данных.|
|[CComModule:: Регистеркласшелпер](#registerclasshelper)|Вводит в системный реестр регистрацию стандартного класса объекта.|
|[CComModule:: Регистерклассобжектс](#registerclassobjects)|Регистрирует объект класса. Только для exe.|
|[CComModule:: Регистерсервер](#registerserver)|Обновляет системный реестр для каждого объекта в сопоставлении объектов.|
|[CComModule::RegisterTypeLib](#registertypelib)|Регистрирует библиотеку типов.|
|[CComModule:: Ревокеклассобжектс](#revokeclassobjects)|Отменяет объект класса. Только для exe.|
|[CComModule:: Term](#term)|Освобождает элементы данных.|
|[CComModule:: Унрегистеркласшелпер](#unregisterclasshelper)|Удаляет регистрацию стандартного класса объекта из системного реестра.|
|[CComModule:: Унрегистерсервер](#unregisterserver)|Отменяет регистрацию каждого объекта в сопоставлении объектов.|
|[CComModule:: Упдатерегистрикласс](#updateregistryclass)|Регистрирует или отменяет регистрацию стандартной регистрации класса объекта.|
|[CComModule::UpdateRegistryFromResourceD](#updateregistryfromresourced)|Запускает скрипт, содержащийся в указанном ресурсе, для регистрации или отмены регистрации объекта.|
|[CComModule:: Упдатерегистрифромресаурцес](#updateregistryfromresources)|Статические ссылки на компонент реестра ATL. Запускает скрипт, содержащийся в указанном ресурсе, для регистрации или отмены регистрации объекта.|

### <a name="public-data-members"></a>Открытые члены данных

|Имя|Описание|
|----------|-----------------|
|[CComModule:: m_csObjMap](#m_csobjmap)|Обеспечивает синхронизированный доступ к сведениям о сопоставлении объектов.|
|[CComModule:: m_csTypeInfoHolder](#m_cstypeinfoholder)|Обеспечивает синхронизированный доступ к сведениям библиотеки типов.|
|[CComModule::m_csWindowCreate](#m_cswindowcreate)|Обеспечивает синхронизированный доступ к сведениям о классе окна и статическим данным, используемым во время создания окна.|
|[CComModule:: m_hInst](#m_hinst)|Содержит маркер для экземпляра модуля.|
|[CComModule:: m_hInstResource](#m_hinstresource)|По умолчанию содержит описатель для экземпляра модуля.|
|[CComModule::m_hInstTypeLib](#m_hinsttypelib)|По умолчанию содержит описатель для экземпляра модуля.|
|[CComModule:: m_pObjMap](#m_pobjmap)|Указывает на карту объектов, поддерживаемую экземпляром модуля.|

## <a name="remarks"></a>Комментарии

> [!NOTE]
> Этот класс является устаревшим, и в мастерах создания кода ATL теперь используются производные классы [катлаутосреадмодуле](../../atl/reference/catlautothreadmodule-class.md) и [катлмодуле](../../atl/reference/catlmodule-class.md) . Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) . Приведенная ниже информация предназначена для использования с приложениями, созданными с помощью более старых версий ATL. `CComModule` по-прежнему является частью библиотеки ATL для обратной способности.

`CComModule` реализует модуль COM-сервера, позволяющий клиенту обращаться к компонентам модуля. `CComModule` поддерживает модули DLL (внутрипроцессный) и EXE (local).

`CComModule`Экземпляр использует карту объектов для обслуживания набора определений объектов класса. Эта схема объектов реализуется как массив `_ATL_OBJMAP_ENTRY` структур и содержит сведения для:

- Ввод и удаление описаний объектов в системном реестре.

- Создание экземпляров объектов с помощью фабрики классов.

- Установка связи между клиентом и корневым объектом в компоненте.

- Выполнение управления жизненным циклом объектов класса.

При запуске ATL COM помощью мастера мастер автоматически создает `_Module` глобальный экземпляр `CComModule` или производный от него класс. Дополнительные сведения о мастере проектов ATL см. в статье [Создание проекта ATL](../../atl/reference/creating-an-atl-project.md).

Кроме того `CComModule` , ATL предоставляет [ккомаутосреадмодуле](../../atl/reference/ccomautothreadmodule-class.md), который реализует модуль апартаментной модели для exe-и служб Windows. Производные модули от `CComAutoThreadModule` , если требуется создавать объекты в нескольких подразделениях.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[катлмодуле](../../atl/reference/catlmodule-class.md)

[катлмодулет](../../atl/reference/catlmodulet-class.md)

`CComModule`

## <a name="requirements"></a>Требования

**Заголовок:** atlbase. h

## <a name="ccommodulegetclassobject"></a><a name="getclassobject"></a> CComModule:: Жетклассобжект

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```

### <a name="parameters"></a>Параметры

*рклсид*<br/>
окне Идентификатор CLSID создаваемого объекта.

*riid*<br/>
окне IID запрашиваемого интерфейса.

*ппв*<br/>
заполняет Указатель на указатель интерфейса, идентифицируемый *riid*. Если объект не поддерживает этот интерфейс, *ППВ* имеет значение null.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Создает объект указанного идентификатора CLSID и получает указатель интерфейса на этот объект.

`GetClassObject` доступно только для библиотек DLL.

## <a name="ccommodulegetmoduleinstance"></a><a name="getmoduleinstance"></a> CComModule:: Жетмодулеинстанце

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetModuleInstance() throw();
```

### <a name="return-value"></a>Возвращаемое значение

Значение HINSTANCE, идентифицирующее этот модуль.

### <a name="remarks"></a>Комментарии

Возвращает элемент данных [m_hInst](#m_hinst) .

## <a name="ccommodulegetresourceinstance"></a><a name="getresourceinstance"></a> CComModule:: Жетресаурцеинстанце

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetResourceInstance() throw();
```

### <a name="return-value"></a>Возвращаемое значение

HINSTANCE.

### <a name="remarks"></a>Комментарии

Возвращает элемент данных [m_hInstResource](#m_hinstresource) .

## <a name="ccommodulegettypelibinstance"></a><a name="gettypelibinstance"></a> CComModule:: Жеттипелибинстанце

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE GetTypeLibInstance() const throw();
```

### <a name="return-value"></a>Возвращаемое значение

HINSTANCE.

### <a name="remarks"></a>Комментарии

Возвращает элемент данных [m_hInstTypeLib](#m_hinsttypelib) .

## <a name="ccommoduleinit"></a><a name="init"></a> CComModule:: init

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL) throw();
```

### <a name="parameters"></a>Параметры

*p*<br/>
окне Указатель на массив записей сопоставлений объектов.

*h*<br/>
окне Значение HINSTANCE, передаваемое в `DLLMain` или `WinMain` .

*плибид*<br/>
окне Указатель на идентификатор LIBID библиотеки типов, связанной с проектом.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Инициализирует все элементы данных.

## <a name="ccommodulem_csobjmap"></a><a name="m_csobjmap"></a> CComModule:: m_csObjMap

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csObjMap;
```

### <a name="remarks"></a>Комментарии

Обеспечивает синхронизированный доступ к карте объектов.

## <a name="ccommodulem_cstypeinfoholder"></a><a name="m_cstypeinfoholder"></a> CComModule:: m_csTypeInfoHolder

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csTypeInfoHolder;
```

### <a name="remarks"></a>Комментарии

Обеспечивает синхронизированный доступ к библиотеке типов.

## <a name="ccommodulem_cswindowcreate"></a><a name="m_cswindowcreate"></a> CComModule:: m_csWindowCreate

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
CRITICAL_SECTION m_csWindowCreate;
```

### <a name="remarks"></a>Комментарии

Обеспечивает синхронизированный доступ к сведениям о классе окна и статическим данным, используемым во время создания окна.

## <a name="ccommodulem_hinst"></a><a name="m_hinst"></a> CComModule:: m_hInst

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInst;
```

### <a name="remarks"></a>Комментарии

Содержит маркер для экземпляра модуля.

Метод [init](#init) задает `m_hInst` для обработчика, передаваемого в `DLLMain` или `WinMain` .

## <a name="ccommodulem_hinstresource"></a><a name="m_hinstresource"></a> CComModule:: m_hInstResource

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstResource;
```

### <a name="remarks"></a>Комментарии

По умолчанию содержит описатель для экземпляра модуля.

Метод [init](#init) задает `m_hInstResource` для обработчика, передаваемого в `DLLMain` или `WinMain` . Можно явно задать `m_hInstResource` для обработчика значение ресурса.

Метод [жетресаурцеинстанце](#getresourceinstance) Возвращает обработчик, хранящийся в `m_hInstResource` .

## <a name="ccommodulem_hinsttypelib"></a><a name="m_hinsttypelib"></a> CComModule:: m_hInstTypeLib

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HINSTANCE m_hInstTypeLib;
```

### <a name="remarks"></a>Комментарии

По умолчанию содержит описатель для экземпляра модуля.

Метод [init](#init) задает `m_hInstTypeLib` для обработчика, передаваемого в `DLLMain` или `WinMain` . Можно явно задать `m_hInstTypeLib` для обработчика библиотеку типов.

Метод [жеттипелибинстанце](#gettypelibinstance) Возвращает обработчик, хранящийся в `m_hInstTypeLib` .

## <a name="ccommodulem_pobjmap"></a><a name="m_pobjmap"></a> CComModule:: m_pObjMap

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
_ATL_OBJMAP_ENTRY* m_pObjMap;
```

### <a name="remarks"></a>Комментарии

Указывает на карту объектов, поддерживаемую экземпляром модуля.

## <a name="ccommoduleregisterclasshelper"></a><a name="registerclasshelper"></a> CComModule:: Регистеркласшелпер

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT RegisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags);
```

### <a name="parameters"></a>Параметры

*этому*<br/>
окне Идентификатор CLSID регистрируемого объекта.

*лпсзпрогид*<br/>
окне Идентификатор ProgID, связанный с объектом.

*лпсзвериндпрогид*<br/>
окне Независимый от версии идентификатор ProgID, связанный с объектом.

*ндесЦид*<br/>
окне Идентификатор строкового ресурса для описания объекта.

*dwFlags*<br/>
окне Указывает потоковую модель для ввода в реестр. Возможные значения: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH или АУТПРКСФЛАГ.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Вводит в системный реестр регистрацию стандартного класса объекта.

Метод [упдатерегистрикласс](#updateregistryclass) вызывает `RegisterClassHelper` .

## <a name="ccommoduleregisterclassobjects"></a><a name="registerclassobjects"></a> CComModule:: Регистерклассобжектс

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterClassObjects(DWORD dwClsContext, DWORD dwFlags) throw();
```

### <a name="parameters"></a>Параметры

*двклсконтекст*<br/>
окне Задает контекст, в котором будет выполняться объект класса. Возможные значения: CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER или CLSCTX_LOCAL_SERVER. Описание этих значений см. в разделе [клскткс](/windows/win32/api/wtypesbase/ne-wtypesbase-clsctx) в Windows SDK.

*dwFlags*<br/>
окне Определяет типы соединения с объектом класса. Возможные значения: REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE или REGCLS_MULTI_SEPARATE. Описание этих значений см. в разделе [регклс](/windows/win32/api/combaseapi/ne-combaseapi-regcls) в Windows SDK.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Регистрирует объект класса EXE в OLE, чтобы другие приложения могли подключаться к нему. Этот метод доступен только для exe.

## <a name="ccommoduleregisterserver"></a><a name="registerserver"></a> CComModule:: Регистерсервер

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```

### <a name="parameters"></a>Параметры

*брегтипелиб*<br/>
окне Указывает, будет ли зарегистрирована библиотека типов. Значение по умолчанию — FALSE.

*пклсид*<br/>
окне Указывает на идентификатор CLSID регистрируемого объекта. При значении NULL (значение по умолчанию) будут зарегистрированы все объекты в сопоставлении объектов.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

В зависимости от параметра *пклсид* обновляет системный реестр для одного объекта класса или для всех объектов в сопоставлении объектов.

Если *брегтипелиб* имеет значение true, сведения о библиотеке типов также будут обновлены.

Сведения о том, как добавить запись в карту объектов, см. в разделе [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

`RegisterServer` будет вызываться автоматически `DLLRegisterServer` для библиотеки DLL или для исполняемого `WinMain` файла с `/RegServer` параметром командной строки.

## <a name="ccommoduleregistertypelib"></a><a name="registertypelib"></a> CComModule:: Регистертипелиб

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT RegisterTypeLib() throw();
HRESULT RegisterTypeLib(LPCTSTR lpszIndex) throw();
```

### <a name="parameters"></a>Параметры

*лпсзиндекс*<br/>
окне Строка в формате `"\\N"` , где `N` — целочисленный индекс ресурса TypeLib.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Добавляет сведения о библиотеке типов в системный реестр.

Если экземпляр модуля содержит несколько библиотек типов, используйте вторую версию этого метода, чтобы указать, какую библиотеку типов следует использовать.

## <a name="ccommodulerevokeclassobjects"></a><a name="revokeclassobjects"></a> CComModule:: Ревокеклассобжектс

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT RevokeClassObjects() throw();
```

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Удаляет объект класса. Этот метод доступен только для exe.

## <a name="ccommoduleterm"></a><a name="term"></a> CComModule:: Term

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```cpp
void Term() throw();
```

### <a name="remarks"></a>Комментарии

Освобождает все элементы данных.

## <a name="ccommoduleunregisterclasshelper"></a><a name="unregisterclasshelper"></a> CComModule:: Унрегистеркласшелпер

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT UnregisterClassHelper(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID);
```

### <a name="parameters"></a>Параметры

*этому*<br/>
окне Идентификатор CLSID объекта, регистрация которого будет отменена.

*лпсзпрогид*<br/>
окне Идентификатор ProgID, связанный с объектом.

*лпсзвериндпрогид*<br/>
окне Независимый от версии идентификатор ProgID, связанный с объектом.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Удаляет регистрацию стандартного класса объекта из системного реестра.

Метод [упдатерегистрикласс](#updateregistryclass) вызывает `UnregisterClassHelper` .

## <a name="ccommoduleunregisterserver"></a><a name="unregisterserver"></a> CComModule:: Унрегистерсервер

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
HRESULT UnregisterServer(const CLSID* pCLSID = NULL) throw ();
inline HRESULT UnregisterServer(BOOL bUnRegTypeLib, const CLSID* pCLSID = NULL) throw ();
```

### <a name="parameters"></a>Параметры

*бунрегтипелиб*<br/>
Если значение — TRUE, то библиотека типов также не регистрируется.

*пклсид*<br/>
Указывает на CLSID объекта, регистрация которого будет отменена. Если NULL (значение по умолчанию), регистрация всех объектов в сопоставлении объектов будет отменена.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

В зависимости от параметра *пклсид* отменяет регистрацию либо одного объекта класса, либо всех объектов в сопоставлении объектов.

`UnregisterServer` будет вызываться автоматически `DLLUnregisterServer` для библиотеки DLL или для исполняемого `WinMain` файла с `/UnregServer` параметром командной строки.

Сведения о том, как добавить запись в карту объектов, см. в разделе [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) .

## <a name="ccommoduleupdateregistryclass"></a><a name="updateregistryclass"></a> CComModule:: Упдатерегистрикласс

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    UINT nDescID,
    DWORD dwFlags,
    BOOL bRegister);

ATL_DEPRECATED HRESULT UpdateRegistryClass(
    const CLSID& clsid,
    LPCTSTR lpszProgID,
    LPCTSTR lpszVerIndProgID,
    LPCTSTR szDesc,
    DWORD dwFlags,
    BOOL bRegister);
```

### <a name="parameters"></a>Параметры

*этому*<br/>
Идентификатор CLSID регистрируемого или незарегистрированного объекта.

*лпсзпрогид*<br/>
Идентификатор ProgID, связанный с объектом.

*лпсзвериндпрогид*<br/>
Независимый от версии идентификатор ProgID, связанный с объектом.

*ндесЦид*<br/>
Идентификатор строкового ресурса для описания объекта.

*сздеск*<br/>
Строка, содержащая описание объекта.

*dwFlags*<br/>
Указывает потоковую модель для ввода в реестр. Возможные значения: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH или АУТПРКСФЛАГ.

*брегистер*<br/>
Указывает, должен ли быть зарегистрирован объект.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Если *брегистер* имеет значение true, этот метод вводит в системный реестр регистрацию стандартного класса объекта.

Если *брегистер* имеет значение false, то удаляется регистрация объекта.

В зависимости от значения *брегистер* `UpdateRegistryClass` вызывает либо [регистеркласшелпер](#registerclasshelper) , либо [унрегистеркласшелпер](#unregisterclasshelper).

При указании [](registry-macros.md#declare_registry) макроса DECLARE_REGISTRY `UpdateRegistryClass` будет вызываться автоматически при обработке схемы объекта.

## <a name="ccommoduleupdateregistryfromresourced"></a><a name="updateregistryfromresourced"></a> CComModule:: Упдатерегистрифромресаурцед

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
virtual HRESULT UpdateRegistryFromResourceD(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceD(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw ();
```

### <a name="parameters"></a>Параметры

*лпсзрес*<br/>
окне Имя ресурса.

*нресид*<br/>
окне Идентификатор ресурса.

*брегистер*<br/>
окне Указывает, должен ли быть зарегистрирован объект.

*пмапентриес*<br/>
окне Указатель на заменяющую карту, в которой хранятся значения, связанные с заменяемыми параметрами скрипта. ATL автоматически использует `%MODULE%` . Чтобы использовать дополнительные заменяемые параметры, см. Дополнительные сведения в примечаниях. В противном случае используйте значение NULL по умолчанию.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Запускает скрипт, содержащийся в ресурсе, указанном параметром *лпсзрес* или *нресид*.

Если *брегистер* имеет значение true, этот метод регистрирует объект в системном реестре; в противном случае он отменяет регистрацию объекта.

При указании макроса [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) или [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) `UpdateRegistryFromResourceD` будет вызываться автоматически при обработке схемы объекта.

> [!NOTE]
> Чтобы заменить значения замены во время выполнения, не указывайте DECLARE_REGISTRY_RESOURCE или DECLARE_REGISTRY_RESOURCEID макрос. Вместо этого создайте массив `_ATL_REGMAP_ENTRIES` структур, где каждая запись содержит заполнитель переменной со значением для замены заполнителя во время выполнения. Затем вызовите `UpdateRegistryFromResourceD` , передав массив для параметра *пмапентриес* . При этом все значения замены в структурах добавляются в `_ATL_REGMAP_ENTRIES` карту замены регистратора.

> [!NOTE]
> Статическую ссылку на компонент реестра ATL (регистратор) см. в разделе [упдатерегистрифромресаурцес](#updateregistryfromresources).

Дополнительные сведения о заменяемых параметрах и сценариях см. в статье [компонент реестра ATL (регистратор)](../../atl/atl-registry-component-registrar.md).

## <a name="ccommoduleupdateregistryfromresources"></a><a name="updateregistryfromresources"></a> CComModule:: Упдатерегистрифромресаурцес

Начиная с ATL 7,0, `CComModule` является устаревшим: Дополнительные сведения см. в разделе [Классы модулей ATL](../../atl/atl-module-classes.md) .

```
virtual HRESULT UpdateRegistryFromResourceS(
    LPCTSTR lpszRes,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();

virtual HRESULT UpdateRegistryFromResourceS(
    UINT nResID,
    BOOL bRegister,
    struct _ATL_REGMAP_ENTRY* pMapEntries = NULL) throw();
```

### <a name="parameters"></a>Параметры

*лпсзрес*<br/>
окне Имя ресурса.

*нресид*<br/>
окне Идентификатор ресурса.

*брегистер*<br/>
окне Указывает, должен ли быть зарегистрирован скрипт ресурсов.

*пмапентриес*<br/>
окне Указатель на заменяющую карту, в которой хранятся значения, связанные с заменяемыми параметрами скрипта. ATL автоматически использует `%MODULE%` . Чтобы использовать дополнительные заменяемые параметры, см. Дополнительные сведения в примечаниях. В противном случае используйте значение NULL по умолчанию.

### <a name="return-value"></a>Возвращаемое значение

Стандартное значение HRESULT.

### <a name="remarks"></a>Комментарии

Аналогично [упдатерегистрифромресаурцед](#updateregistryfromresourced) , за исключением `UpdateRegistryFromResourceS` создания статической ссылки на компонент реестра ATL (регистратор).

`UpdateRegistryFromResourceS` будет вызываться автоматически при обработке схемы объекта, при условии, что вы добавили `#define _ATL_STATIC_REGISTRY` в *PCH. h* (*stdafx. h* в Visual Studio 2017 и более ранних версиях).

> [!NOTE]
> Чтобы заменить значения замены во время выполнения, не указывайте [DECLARE_REGISTRY_RESOURCE](registry-macros.md#declare_registry_resource) или [DECLARE_REGISTRY_RESOURCEID](registry-macros.md#declare_registry_resourceid) макрос. Вместо этого создайте массив `_ATL_REGMAP_ENTRIES` структур, где каждая запись содержит заполнитель переменной со значением для замены заполнителя во время выполнения. Затем вызовите `UpdateRegistryFromResourceS` , передав массив для параметра *пмапентриес* . При этом все значения замены в структурах добавляются в `_ATL_REGMAP_ENTRIES` карту замены регистратора.

Дополнительные сведения о заменяемых параметрах и сценариях см. в статье [компонент реестра ATL (регистратор)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>См. также раздел

[Общие сведения о классах](../../atl/atl-class-overview.md)
