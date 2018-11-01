---
title: ptr::ptr
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ptr::ptr
- ptr.ptr
- msclr.com.ptr.ptr
- msclr::com::ptr::ptr
helpviewer_keywords:
- ptr::ptr
ms.assetid: 4f5883b4-7c0a-46c6-aa9f-4e49eed463eb
ms.openlocfilehash: 097cfe7a030c2ae9f1727b6655384de050f0f221
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622460"
---
# <a name="ptrptr"></a>ptr::ptr

Создает `com::ptr` программы-оболочки COM-объекта.

## <a name="syntax"></a>Синтаксис

```
ptr();
ptr(
   _interface_type * p
);
```

#### <a name="parameters"></a>Параметры

*P*<br/>
Указатель интерфейса COM.

## <a name="remarks"></a>Примечания

Конструктор без аргументов присваивает `nullptr` на базовый дескриптор объекта. Последующие вызовы `com::ptr` будут проверены внутренний объект и автоматически ошибкой, пока не будет фактически создан или присоединенного объекта.

Один аргумент конструктора добавляет ссылку на COM-объекта, но не освобождает ссылку вызывающей стороны, чтобы вызывающий объект должен вызвать `Release` для COM-объекта по-настоящему теряете контроль. При `com::ptr`его деструктор вызывается автоматически освобождает ссылки COM-объекта.

Передача `NULL` в этот конструктор является таким же, как вызывать версию без аргументов.

## <a name="example"></a>Пример

Этот пример реализует класс CLR, который использует `com::ptr` программы-оболочки для его закрытого члена `IXMLDOMDocument` объекта. Он демонстрирует использование обеих версий конструктора.

```
// comptr_ptr.cpp
// compile with: /clr /link msxml2.lib
#include <msxml2.h>
#include <msclr\com\ptr.h>

#import <msxml3.dll> raw_interfaces_only

using namespace System;
using namespace System::Runtime::InteropServices;
using namespace msclr;

// a ref class that uses a com::ptr to contain an
// IXMLDOMDocument object
ref class XmlDocument {
public:
   // construct the internal com::ptr with a null interface
   // and use CreateInstance to fill it
   XmlDocument(String^ progid) {
      m_ptrDoc.CreateInstance(progid);
   }

   // construct the internal com::ptr with a COM object
   XmlDocument(IXMLDOMDocument* pDoc) : m_ptrDoc(pDoc) {}

   // note that the destructor will call the com::ptr destructor
   // and automatically release the reference to the COM object

private:
   com::ptr<IXMLDOMDocument> m_ptrDoc;
};

// use the ref class to handle an XML DOM Document object
int main() {
   IXMLDOMDocument* pDoc = NULL;

   try {
      // create an XML DOM document object
      Marshal::ThrowExceptionForHR(CoCreateInstance(CLSID_DOMDocument30, NULL,
         CLSCTX_ALL, IID_IXMLDOMDocument, (void**)&pDoc));
      // construct the ref class with the COM object
      XmlDocument doc1(pDoc);

      // or create the class from a progid string
      XmlDocument doc2("Msxml2.DOMDocument.3.0");
   }
   // doc1 and doc2 destructors are called when they go out of scope
   // and the internal com::ptr releases its reference to the COM object
   catch (Exception^ e) {
      Console::WriteLine(e);
   }
   finally {
      if (NULL != pDoc) {
         pDoc->Release();
      }
   }
}
```

## <a name="requirements"></a>Требования

**Файл заголовка** \<msclr\com\ptr.h >

**Пространство имен** msclr::com

## <a name="see-also"></a>См. также

[Члены ptr](../dotnet/ptr-members.md)<br/>
[ptr::CreateInstance](../dotnet/ptr-createinstance.md)<br/>
[ptr::~ptr](../dotnet/ptr-tilde-ptr.md)