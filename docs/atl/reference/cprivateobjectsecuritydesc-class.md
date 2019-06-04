---
title: Класс CPrivateObjectSecurityDesc
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: cc726892515ea38a559bdf182affa96f84be3449
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503307"
---
# <a name="cprivateobjectsecuritydesc-class"></a>Класс CPrivateObjectSecurityDesc

Этот класс представляет объект дескриптора безопасности закрытый объект.

## <a name="syntax"></a>Синтаксис

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>Участники

### <a name="public-constructors"></a>Открытые конструкторы

|name|Описание|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|Конструктор.|
|[CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc](#dtor)|Деструктор|

### <a name="public-methods"></a>Открытые методы

|name|Описание|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|Этот метод используется для преобразования в формат, который поддерживает автоматическое распространение наследуемых управления доступом (ACE) в дескрипторе безопасности и его списки управления доступом (ACL).|
|[CPrivateObjectSecurityDesc::Create](#create)|Этот метод используется для выделения и инициализировать дескриптор безопасности в относительный для закрытого объекта, созданные с помощью вызова диспетчера ресурсов.|
|[CPrivateObjectSecurityDesc::Get](#get)|Этот метод используется для получения сведений из дескриптора безопасности закрытый объект.|
|[CPrivateObjectSecurityDesc::Set](#set)|Вызовите этот метод, чтобы изменить дескриптор безопасности закрытый объект.|

### <a name="operators"></a>Операторы

|||
|-|-|
|[оператор =](#operator_eq)|Оператор присвоения.|

## <a name="remarks"></a>Примечания

Этот класс производным от [CSecurityDesc](../../atl/reference/csecuritydesc-class.md), предоставляет методы для создания и управления дескриптор безопасности закрытого объекта.

Введение в модель управления доступом в Windows, см. в разделе [контроля доступа](/windows/desktop/SecAuthZ/access-control) в пакете Windows SDK.

## <a name="inheritance-hierarchy"></a>Иерархия наследования

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>Требования

**Заголовок:** atlsecurity.h

##  <a name="converttoautoinherit"></a>  CPrivateObjectSecurityDesc::ConvertToAutoInherit

Этот метод используется для преобразования в формат, который поддерживает автоматическое распространение наследуемых управления доступом (ACE) в дескрипторе безопасности и его списки управления доступом (ACL).

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Параметры

*pParent*<br/>
Указатель на [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) объекта, ссылающегося на родительский контейнер объекта. Если родительского контейнера нет, этот параметр имеет значение NULL.

*Тип объекта*<br/>
Указатель на `GUID` структура, определяющая тип объекта, связанного с текущим объектом. Задайте *ObjectType* значение NULL, если объект не является идентификатором GUID.

*bIsDirectoryObject*<br/>
Указывает, является ли новый объект может содержать другие объекты. Значение true указывает, что новый объект является контейнером. Значение false указывает, что новый объект не является контейнером.

*GenericMapping*<br/>
Указатель на [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) структуру, которая задает сопоставление каждой универсального направо особые права для объекта.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение true, если операция выполнена успешно; в противном случае — значение false.

### <a name="remarks"></a>Примечания

Этот метод пытается определить, перечислены ли записи ACE в управления доступом (DACL) и системный список управления доступом (SACL) текущего дескриптора безопасности, унаследованные из родительского дескриптора безопасности. Он вызывает [ConvertToAutoInheritPrivateObjectSecurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity) функции.

##  <a name="cprivateobjectsecuritydesc"></a>  CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc

Конструктор.

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Примечания

Инициализирует `CPrivateObjectSecurityDesc` объекта.

##  <a name="dtor"></a>  CPrivateObjectSecurityDesc::~CPrivateObjectSecurityDesc

Деструктор

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Примечания

Деструктор освобождает все выделенные ресурсы и удаляет закрытый объект дескриптора безопасности.

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

Этот метод используется для выделения и инициализировать дескриптор безопасности в относительный для закрытого объекта, созданные с помощью вызова диспетчера ресурсов.

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>Параметры

*pParent*<br/>
Указатель на [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) объекта, ссылающегося на родительский каталог, в которой создается новый объект. Задайте значение NULL, если нет родительского каталога.

*pCreator*<br/>
Указатель на дескриптор безопасности, предоставляемые создателю объекта. Если создатель объекта явным образом не передает сведения о безопасности для нового объекта, этот параметр равен NULL.

*bIsDirectoryObject*<br/>
Указывает, является ли новый объект может содержать другие объекты. Значение true указывает, что новый объект является контейнером. Значение false указывает, что новый объект не является контейнером.

*Маркер*<br/>
Ссылка на [CAccessToken](../../atl/reference/caccesstoken-class.md) объекта для процесса клиента, от имени которого создается объект.

*GenericMapping*<br/>
Указатель на [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) структуру, которая задает сопоставление каждой универсального направо особые права для объекта.

*Тип объекта*<br/>
Указатель на `GUID` структура, определяющая тип объекта, связанного с текущим объектом. Задайте *ObjectType* значение NULL, если объект не является идентификатором GUID.

*bIsContainerObject*<br/>
Указывает, является ли новый объект может содержать другие объекты. Значение true указывает, что новый объект является контейнером. Значение false указывает, что новый объект не является контейнером.

*AutoInheritFlags*<br/>
Набор битовые флаги, определяющие, как элементы управления доступом (ACE) наследуются от *pParent*. См. в разделе [CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) для получения дополнительных сведений.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение true, если операция выполнена успешно; в противном случае — значение false.

### <a name="remarks"></a>Примечания

Этот метод вызывает метод [CreatePrivateObjectSercurity](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity) или [CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex).

Второй метод позволяет указать идентификатор GUID типа объекта нового объекта или управление как элементы управления доступом наследуются.

> [!NOTE]
>  Дескриптор безопасности в относительный является дескриптор безопасности, в котором хранится вся информация безопасности в непрерывном блоке памяти.

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

Этот метод используется для получения сведений из дескриптора безопасности закрытый объект.

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>Параметры

*SI*<br/>
Набор битовых флагов, указывающие части для получения дескриптора безопасности. Это значение может представлять собой сочетание [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) битовые флаги.

*pResult*<br/>
Указатель на [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) , получающий копию запрошенные сведения из указанного дескриптора безопасности.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение true, если операция выполнена успешно; в противном случае — значение false.

### <a name="remarks"></a>Примечания

Дескриптор безопасности — это структуры и связанных данных, содержащий сведения о безопасности для защищаемого объекта.

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

Оператор присвоения.

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>Параметры

*rhs*<br/>
`CPrivateObjectSecurityDesc` Объект текущему объекту.

### <a name="return-value"></a>Возвращаемое значение

Возвращает обновленный `CPrivateObjectSecurityDesc` объекта.

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

Вызовите этот метод, чтобы изменить дескриптор безопасности закрытый объект.

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>Параметры

*SI*<br/>
Набор битовых флагов, указывающие части дескриптора безопасности. Это значение может представлять собой сочетание [SECURITY_INFORMATION](/windows/desktop/SecAuthZ/security-information) битовые флаги.

*Изменения*<br/>
Указатель на [CSecurityDesc](../../atl/reference/csecuritydesc-class.md) объекта. Указывает части данного дескриптора безопасности *si* параметра применяются в дескрипторе безопасности объекта.

*GenericMapping*<br/>
Указатель на [GENERIC_MAPPING](/windows/desktop/api/winnt/ns-winnt-_generic_mapping) структуру, которая задает сопоставление каждой универсального направо особые права для объекта.

*Маркер*<br/>
Ссылка на [CAccessToken](../../atl/reference/caccesstoken-class.md) объекта для процесса клиента, от имени которого создается объект.

*AutoInheritFlags*<br/>
Набор битовые флаги, определяющие, как элементы управления доступом (ACE) наследуются от *pParent*. См. в разделе [CreatePrivateObjectSecurityEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) для получения дополнительных сведений.

### <a name="return-value"></a>Возвращаемое значение

Возвращает значение true, если операция выполнена успешно; в противном случае — значение false.

### <a name="remarks"></a>Примечания

Второй метод позволяет указать идентификатор GUID типа объекта объекта или управление как элементы управления доступом наследуются.

## <a name="see-also"></a>См. также

[SECURITY_DESCRIPTOR](/windows/desktop/api/winnt/ns-winnt-_security_descriptor)<br/>
[Общие сведения о классе](../../atl/atl-class-overview.md)<br/>
[Глобальные функции безопасности](../../atl/reference/security-global-functions.md)<br/>
[Класс CSecurityDesc](../../atl/reference/csecuritydesc-class.md)
