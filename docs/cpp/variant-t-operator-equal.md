---
description: 'Дополнительные сведения: _variant_t:: operator ='
title: _variant_t::operator =
ms.date: 11/04/2016
f1_keywords:
- _variant_t::operator=
helpviewer_keywords:
- operator= [C++], variant
- operator = [C++], variant
- = operator [C++], with specific Visual C++ objects
ms.assetid: 77622723-6e49-4dec-9e0f-fa74028f1a3c
ms.openlocfilehash: 3218d15f5b787709f1759bfda3a2501bcdda5406
ms.sourcegitcommit: d775eac25552bd0fb7276703efa6931d6a1a59fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105099688"
---
# <a name="_variant_toperator-"></a>_variant_t::operator =

**Блок, относящийся только к системам Microsoft**

## <a name="syntax"></a>Синтаксис

```
_variant_t& operator=(
   const VARIANT& varSrc
);

_variant_t& operator=(
   const VARIANT* pVarSrc
);

_variant_t& operator=(
   const _variant_t& var_t_Src
);

_variant_t& operator=(
   short sSrc
);

_variant_t& operator=(
   long lSrc
);

_variant_t& operator=(
   float fltSrc
);

_variant_t& operator=(
   double dblSrc
);

_variant_t& operator=(
   const CY& cySrc
);

_variant_t& operator=(
   const _bstr_t& bstrSrc
);

_variant_t& operator=(
   const wchar_t* wstrSrc
);

_variant_t& operator=(
   const char* strSrc
);

_variant_t& operator=(
   IDispatch* pDispSrc
);

_variant_t& operator=(
   bool bSrc
);

_variant_t& operator=(
   IUnknown* pSrc
);

_variant_t& operator=(
   const DECIMAL& decSrc
);

_variant_t& operator=(
   BYTE bSrc
);

_variant_t& operator=(
   char cSrc
);

_variant_t& operator=(
   unsigned short usSrc
);

_variant_t& operator=(
   unsigned long ulSrc
);

_variant_t& operator=(
   int iSrc
);

_variant_t& operator=(
   unsigned int uiSrc
);

_variant_t& operator=(
   __int64 i8Src
);

_variant_t& operator=(
   unsigned __int64 ui8Src
);
```

## <a name="remarks"></a>Remarks

Оператор присваивает новое значение объекту `_variant_t`.

- **operator = (**  *варсрк*  **)** Присваивает существующий `VARIANT` `_variant_t` объект объекту.

- **operator = (**  *пварсрк*  **)** Присваивает существующий `VARIANT` `_variant_t` объект объекту.

- **operator = (**  *var_t_Src*  **)** Присваивает существующий `_variant_t` объект `_variant_t` объекту.

- **operator = (**  *ССРК*  **)** Присваивает **`short`** целочисленное значение `_variant_t` объекту.

- **operator = (** `lSrc` **)** присваивает **`long`** объекту целочисленное значение `_variant_t` .    

- **operator = (**  *флтсрк*  **)** Присваивает **`float`** числовое значение `_variant_t` объекту.

- **operator = (**  *дблсрк*  **)** Присваивает **`double`** числовое значение `_variant_t` объекту.

- **operator = (**  *цисрк*  **)** Присваивает объект объекту `CY` `_variant_t` .

- **operator = (**  *бстрсрк*  **)** Присваивает объект объекту `BSTR` `_variant_t` .

- **operator = (**  *встрсрк*  **)** Присваивает строку Юникода `_variant_t` объекту.

- **operator = (** `strSrc` **)** присваивает объекту многобайтовую строку `_variant_t` .    

- **operator = (** `bSrc` **)** присваивает **`bool`** значение `_variant_t` объекту.  

- **operator = (**  *пдиспсрк*  **)** Присваивает `IDispatch*` объект `_variant_t` объекту и вызывает метод `AddRef` .

- **operator = (**  *пиункновнсрк*  **)** Присваивает `IUnknown*` объект `_variant_t` объекту и вызывает метод `AddRef` .

- **operator = (**  *дексрк*  **)** Присваивает `DECIMAL` значение `_variant_t` объекту.

- **operator = (** `bSrc` **)** присваивает `BYTE` значение `_variant_t` объекту.  

**Завершение блока, относящегося только к системам Майкрософт**

## <a name="see-also"></a>См. также

[Класс _variant_t](../cpp/variant-t-class.md)
