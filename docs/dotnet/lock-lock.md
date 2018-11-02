---
title: lock::lock
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- lock::lock
- lock.lock
- msclr.lock.lock
- msclr::lock::lock
helpviewer_keywords:
- lock constructor
ms.assetid: c9ad6c71-36ec-49c5-8ebd-f5c3a0cc94f0
ms.openlocfilehash: 480e4f6604adc0a6bd0b3b5fff32f37c811a16a4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2018
ms.locfileid: "50470581"
---
# <a name="locklock"></a>lock::lock

Создает `lock` объекта, при необходимости ожидает получения блокировки неограниченно долго, в течение определенного времени или вообще не.

## <a name="syntax"></a>Синтаксис

```
template<class T> lock(
   T ^ _object
);
template<class T> lock(
   T ^ _object,
   int _timeout
);
template<class T> lock(
   T ^ _object,
   System::TimeSpan _timeout
);
template<class T> lock(
   T ^ _object,
   lock_later
);
```

#### <a name="parameters"></a>Параметры

*_Object*<br/>
Блокируемый объект.

*_время ожидания*<br/>
Значение времени ожидания в миллисекундах, или как <xref:System.TimeSpan>.

## <a name="exceptions"></a>Исключения

Создает <xref:System.ApplicationException> Если получение блокировки не происходит до истечения времени ожидания.

## <a name="remarks"></a>Примечания

Попытка получения блокировки на первые три формы конструктора `_object` в пределах заданного периода ожидания (или <xref:System.Threading.Timeout.Infinite> Если ничего не указано).

Четвертый конструктор в форме не получения блокировки на `_object`. `lock_later` является членом [перечисление lock_when](../dotnet/lock-when-enum.md). Используйте [lock::acquire](../dotnet/lock-acquire.md) или [lock::try_acquire](../dotnet/lock-try-acquire.md) таким образом получить блокировку.

Блокировка будет выпущена автоматически в том случае, когда вызывается деструктор.

Параметр `_object` не может иметь значение <xref:System.Threading.ReaderWriterLock>.  Если это так, приведет к ошибке компилятора.

## <a name="example"></a>Пример

В этом примере используется один экземпляр класса в нескольких потоках.  Этот класс использует блокировку на себя для обеспечения согласованности для каждого потока, доступ к ее внутренним данным.  Основного потока приложения использует блокировку на том же экземпляре класса для периодической проверки любого рабочих потоков по-прежнему существовать, и ожиданий, чтобы завершить работу, пока все потоки исполнителей выполнили свои задачи.

```
// msl_lock_lock.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="requirements"></a>Требования

**Файл заголовка** \<msclr\lock.h >

**Пространство имен** msclr

## <a name="see-also"></a>См. также

[Члены lock](../dotnet/lock-members.md)<br/>
[lock::~lock](../dotnet/lock-tilde-lock.md)<br/>
[lock::acquire](../dotnet/lock-acquire.md)<br/>
[lock::try_acquire](../dotnet/lock-try-acquire.md)