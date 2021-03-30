---
description: 'Дополнительные сведения: _variant_t:: operator ='
title: '_variant_t:: operator ='
ms.date: 03/23/2021
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.openlocfilehash: c1cd581b386a3cf5d551fe8341ba588fc56b9c2e
ms.sourcegitcommit: bb35a6c22d896c4640cff00a7321442c544ca219
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2021
ms.locfileid: "105744768"
---
# `_variant_t::operator=`

Присваивает новое значение `_variant_t` экземпляру.

`_variant_t`Класс и его `operator=` член являются **специфичными для Microsoft**.

## <a name="syntax"></a>Синтаксис

```cpp
_variant_t& operator=( const VARIANT& varSrc );
_variant_t& operator=( const VARIANT* pVarSrc );
_variant_t& operator=( const _variant_t& var_t_Src );
_variant_t& operator=( short sSrc );
_variant_t& operator=( long lSrc );
_variant_t& operator=( float fltSrc );
_variant_t& operator=( double dblSrc );
_variant_t& operator=( const CY& cySrc );
_variant_t& operator=( const _bstr_t& bstrSrc );
_variant_t& operator=( const wchar_t* wstrSrc );
_variant_t& operator=( const char* strSrc );
_variant_t& operator=( IDispatch* pDispSrc );
_variant_t& operator=( bool bSrc );
_variant_t& operator=( IUnknown* pSrc );
_variant_t& operator=( const DECIMAL& decSrc );
_variant_t& operator=( BYTE byteSrc );
_variant_t& operator=( char cSrc );
_variant_t& operator=( unsigned short usSrc );
_variant_t& operator=( unsigned long ulSrc );
_variant_t& operator=( int iSrc );
_variant_t& operator=( unsigned int uiSrc );
_variant_t& operator=( __int64 i8Src );
_variant_t& operator=( unsigned __int64 ui8Src );
```

### <a name="parameters"></a>Параметры

*`varSrc`*\
Ссылка на объект, `VARIANT` из которого копируются содержимое и `VT_*` тип.

*`pVarSrc`*\
Указатель на объект, `VARIANT` из которого копируются содержимое и `VT_*` тип.

*`var_t_Src`*\
Ссылка на объект, `_variant_t` из которого копируются содержимое и `VT_*` тип.

*`sSrc`*\
**`short`** Целочисленное значение для копирования. Заданный тип, `VT_BOOL` Если `*this` имеет тип `VT_BOOL` . В противном случае задается тип `VT_I2` .

*`lSrc`*\
**`long`** Целочисленное значение для копирования. Заданный тип, `VT_BOOL` Если `*this` имеет тип `VT_BOOL` . Заданный тип, `VT_ERROR` Если `*this` имеет тип `VT_ERROR` . В противном случае заданный тип `VT_I4` .

*`fltSrc`*\
**`float`** Числовое значение для копирования. Заданный тип `VT_R4` .

*`dblSrc`*\
**`double`** Числовое значение для копирования. Заданный тип, `VT_DATE` Если `this` имеет тип `VT_DATE` . В противном случае заданный тип `VT_R8` .

*`cySrc`*\
Объект `CY` для копирования. Заданный тип `VT_CY` .

*`bstrSrc`*\
Объект `BSTR` для копирования. Заданный тип `VT_BSTR` .

*`wstrSrc`*\
Строка в Юникоде для копирования, хранимая как `BSTR` и заданный тип `VT_BSTR` .

*`strSrc`*\
Многобайтовая строка для копирования, хранимая как `BSTR` и заданный тип `VT_BSTR` .

*`pDispSrc`*\
`IDispatch`Указатель, который нужно скопировать с помощью вызова `AddRef` . Заданный тип `VT_DISPATCH` .

*`bSrc`*\
**`bool`** Копируемое значение. Заданный тип `VT_BOOL` .

*`pSrc`*\
`IUnknown`Указатель, который нужно скопировать с помощью вызова `AddRef` . Заданный тип  `VT_UNKNOWN` .

*`decSrc`*\
Объект `DECIMAL` для копирования. Заданный тип `VT_DECIMAL` .

*`byteSrc`*\
`BYTE`Копируемое значение. Заданный тип `VT_UI1` .

*`cSrc`*\
**`char`** Копируемое значение. Заданный тип `VT_I1` .

*`usSrc`*\
**`unsigned short`** Копируемое значение. Заданный тип `VT_UI2` .

*`ulSrc`*\
**`unsigned long`** Копируемое значение. Заданный тип `VT_UI4` .

*`iSrc`*\
**`int`** Копируемое значение. Заданный тип `VT_INT` .

*`uiSrc`*\
**`unsigned int`** Копируемое значение. Заданный тип `VT_UINT` .

*`i8Src`*\
**`__int64`** **`long long`** Копируемое значение или. Заданный тип `VT_I8` .

*`ui8Src`*\
**`unsigned __int64`** **`unsigned long long`** Копируемое значение или. Заданный тип `VT_UI8` .

## <a name="remarks"></a>Замечания

`operator=`Оператор присваивания очищает любое существующее значение, которое удаляет типы объектов или вызывает `Release` `IDispatch*` `IUnknown*` типы и. Затем он копирует новое значение в `_variant_t` объект. Он изменяет `_variant_t` тип так, чтобы он соответствовал назначенному значению, за исключением случаев, указанных для **`short`** **`long`** аргументов, и **`double`** . Типы значений копируются напрямую. `VARIANT`Указатель или `_variant_t` ссылочный аргумент или копирует содержимое и тип назначенного объекта. Другие аргументы указателя или ссылочного типа создают копию назначенного объекта. Оператор присваивания вызывает `AddRef` `IDispatch*` аргументы и `IUnknown*` .

`operator=` вызывается [`_com_raise_error`](../cpp/com-raise-error.md) при возникновении ошибки.

`operator=` Возвращает ссылку на обновленный `_variant_t` объект.

## <a name="see-also"></a>См. также

[Класс `_variant_t`](../cpp/variant-t-class.md)
