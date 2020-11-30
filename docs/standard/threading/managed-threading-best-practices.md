---
title: Рекомендации по работе с потоками
description: Ознакомьтесь с рекомендациями по работе с управляемыми потоками в .NET. Реализуйте сложные ситуации, такие как координация работы нескольких потоков или обработка потоков, вызывающих блокировку.
ms.date: 10/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET], design guidelines
- threading [.NET], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: 88cbf266d15a10ff7c56e07a30161e0a800989d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708053"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="b3d3d-104">Рекомендации по работе с потоками</span><span class="sxs-lookup"><span data-stu-id="b3d3d-104">Managed threading best practices</span></span>

<span data-ttu-id="b3d3d-105">Многопоточность требует тщательного программирования.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-105">Multithreading requires careful programming.</span></span> <span data-ttu-id="b3d3d-106">Большинство задач можно упростить, поместив запросы на выполнение в очередь по потокам пулов потоков.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-106">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="b3d3d-107">В этом разделе рассматриваются более сложные ситуации, такие как координация работы нескольких потоков или обработка потоков, вызывающих блокировку.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-107">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3d3d-108">Начиная с версии .NET Framework 4, библиотека параллельных задач и PLINQ предоставляют интерфейсы API, которые несколько снижают сложность и риски многопоточного программирования.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-108">Starting with .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="b3d3d-109">Дополнительные сведения см. в статье [Параллельное программирование в .NET](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-109">For more information, see [Parallel Programming in .NET](../parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="b3d3d-110">Взаимоблокировки и состояние гонки</span><span class="sxs-lookup"><span data-stu-id="b3d3d-110">Deadlocks and race conditions</span></span>  

 <span data-ttu-id="b3d3d-111">Многопоточность позволяет решить проблемы с пропускной способностью и скоростью реагирования, но при этом возникают новые проблемы: взаимоблокировки и конфликты.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-111">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="b3d3d-112">Взаимоблокировки</span><span class="sxs-lookup"><span data-stu-id="b3d3d-112">Deadlocks</span></span>  

 <span data-ttu-id="b3d3d-113">Взаимоблокировка происходит, когда каждый из двух потоков пытается заблокировать ресурс, уже заблокированный другим потоком.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-113">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="b3d3d-114">Ни один из потоков не может продолжить работу.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-114">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="b3d3d-115">Многие методы классов управляемых потоков предоставляют значения времени ожидания для обнаружения взаимоблокировок.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-115">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="b3d3d-116">Например, следующий код пытается получить блокировку для объекта с именем `lockObject`.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-116">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="b3d3d-117">Если блокировка не будет получена в течение 300 миллисекунд, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> возвратит `false`.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-117">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="b3d3d-118">Состояние гонки</span><span class="sxs-lookup"><span data-stu-id="b3d3d-118">Race conditions</span></span>  

 <span data-ttu-id="b3d3d-119">Конфликт — это ошибка, которая возникает, когда результат программы зависит от того, какой из двух или более потоков первым достигнет определенного блока кода.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-119">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="b3d3d-120">Выполнение программы часто дает различные результаты, и предсказать результат выполнения конкретного запуска невозможно.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-120">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="b3d3d-121">Простой пример состояния гонки — увеличение поля.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-121">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="b3d3d-122">Предположим, что класс содержит закрытое поле **static** (**Shared** в Visual Basic), которое увеличивается всякий раз при создании класса с помощью кода, например `objCt++;` (в C#) или `objCt += 1` (в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-122">Suppose a class has a private **static** field (**Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="b3d3d-123">Для этой операции необходимо загрузить значение из `objCt` в регистр, увеличить или уменьшить это значение и сохранить его в `objCt`.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-123">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="b3d3d-124">В многопоточных приложениях поток, загружающий и увеличивающий значение, может быть вытеснен другим потоком, который выполняет все три эти действия; если первый поток возобновляет выполнение и сохраняет его значение, он переопределяет `objCt`, не принимая во внимание тот факт, что в промежутке значение изменилось.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-124">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="b3d3d-125">Конкретно этого состояния гонки можно легко избежать, применяя методы класса <xref:System.Threading.Interlocked>, например <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-125">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b3d3d-126">Сведения о других технологиях синхронизации данных между несколькими потоками см. в разделе [Синхронизация данных для многопоточности](synchronizing-data-for-multithreading.md).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-126">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="b3d3d-127">Конфликты могут также возникать при синхронизации действий различных потоков.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-127">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="b3d3d-128">При написании каждой строки кода необходимо учитывать, что может произойти, если поток будет вытеснен другим потоком до ее выполнения (или до одной из индивидуальных машинных команд, составляющих эту строку).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-128">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="b3d3d-129">Статические члены и статические конструкторы</span><span class="sxs-lookup"><span data-stu-id="b3d3d-129">Static members and static constructors</span></span>  

 <span data-ttu-id="b3d3d-130">Класс не инициализируется, пока не завершится выполнение его конструктора (конструктор `static` в C# `Shared Sub New` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-130">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="b3d3d-131">Чтобы предотвратить выполнение кода в еще не инициализированном типе, CLR блокирует все вызовы из других потоков для членов класса `static` (члены `Shared` в Visual Basic) до тех пор, пока выполнение конструктора класса не будет завершено.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-131">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="b3d3d-132">Например, если конструктор класса запускает новый поток, а процедура потока вызывает член `static` класса, новый поток блокируется до завершения конструктора класса.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-132">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="b3d3d-133">Это относится к любому типу, который может иметь конструктор `static`.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-133">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="b3d3d-134">Число процессоров</span><span class="sxs-lookup"><span data-stu-id="b3d3d-134">Number of processors</span></span>

<span data-ttu-id="b3d3d-135">Наличие нескольких процессоров или только одного процессора в системе может повлиять на многопоточную архитектуру.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-135">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="b3d3d-136">Дополнительные сведения см. в разделе [Количество процессоров](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-136">For more information, see [Number of Processors](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).</span></span>

<span data-ttu-id="b3d3d-137">Используйте свойство <xref:System.Environment.ProcessorCount?displayProperty=nameWithType>, чтобы определить количество процессоров, доступных во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-137">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at run time.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="b3d3d-138">Основные рекомендации</span><span class="sxs-lookup"><span data-stu-id="b3d3d-138">General recommendations</span></span>  

 <span data-ttu-id="b3d3d-139">При использовании нескольких потоков соблюдайте следующие рекомендации:</span><span class="sxs-lookup"><span data-stu-id="b3d3d-139">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="b3d3d-140">Не используйте <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> для завершения других потоков.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-140">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="b3d3d-141">Вызов метода **Abort** для другого потока аналогичен вызову исключения в этом потоке, когда неизвестно, на каком этапе находится обработка этого потока.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-141">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="b3d3d-142">Не используйте <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> и <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> для синхронизации действий между потоками.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-142">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="b3d3d-143">Используйте вместо этого <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent> и <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-143">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="b3d3d-144">Не контролируйте выполнение рабочих потоков из основной программы (например, с помощью событий).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-144">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="b3d3d-145">Вместо этого составьте программу так, чтобы рабочие потоки ожидали доступности задания, выполняли его и оповещали другие части программы о его завершении.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-145">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="b3d3d-146">Если рабочие потоки не блокируются, можно использовать потоки из пула потоков.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-146">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="b3d3d-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> можно использовать в ситуациях, когда рабочие потоки блокируются.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="b3d3d-148">Не используйте типы как объекты блокировки.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-148">Don't use types as lock objects.</span></span> <span data-ttu-id="b3d3d-149">Это означает, что следует избегать кода `lock(typeof(X))` в C# или `SyncLock(GetType(X))` в Visual Basic, а также использования <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> с объектами <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-149">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="b3d3d-150">Для каждого конкретного типа существует только один экземпляр <xref:System.Type?displayProperty=nameWithType> в каждом домене приложения.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-150">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="b3d3d-151">Если блокируемый тип является открытым, его может заблокировать чужой код, вызвав тем самым взаимоблокировку.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-151">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="b3d3d-152">Дополнительные вопросы см. [Рекомендации по обеспечению надежности](../../framework/performance/reliability-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-152">For additional issues, see [Reliability Best Practices](../../framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="b3d3d-153">Будьте внимательны при блокировке экземпляров, например `lock(this)` в C# или `SyncLock(Me)` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-153">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="b3d3d-154">Если другой код в приложении, который является внешним для типа, заблокирует объект, может возникнуть взаимоблокировка.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-154">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="b3d3d-155">Следите за тем, чтобы каждый поток, который входит в монитор, обязательно вышел из этого монитора, даже если за время, пока поток находится в мониторе, возникает исключение.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-155">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="b3d3d-156">Оператор C# [lock](../../csharp/language-reference/keywords/lock-statement.md) и оператор Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) делают это автоматически, обеспечивая вызов метода <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> с помощью блока **finally**.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-156">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="b3d3d-157">Если вы не можете проконтролировать вызов метода **Exit**, включите в свое приложение **мьютекс**.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-157">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="b3d3d-158">Мьютекс автоматически освобождается, как только прекращается выполнение владеющего им потока.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-158">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="b3d3d-159">Для задач, которые требуют различных ресурсов, используйте несколько потоков и старайтесь не назначать несколько потоков одному ресурсу.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-159">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="b3d3d-160">Например, любая задача с использованием ввода-вывода выигрывает от наличия собственного потока, поскольку во время операций ввода-вывода этот поток блокируется и, таким образом, разрешает выполнение других потоков.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-160">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="b3d3d-161">Входные данные пользователя — еще один ресурс, которому пойдет на пользу выделенный поток.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-161">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="b3d3d-162">На однопроцессорном компьютере задача, требующая активных вычислений, сосуществует с входными данными пользователя и задачами, которые предусматривают операции ввода-вывода, однако несколько ресурсоемких задач могут конкурировать друг с другом.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-162">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="b3d3d-163">Вместо оператора `lock` (`SyncLock` в Visual Basic) для простого изменения состояния лучше использовать методы класса <xref:System.Threading.Interlocked>.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-163">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="b3d3d-164">Оператор `lock` — хороший универсальный инструмент, но класс <xref:System.Threading.Interlocked> обеспечивает высокую производительность для обновлений, которые должны быть атомарными.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-164">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="b3d3d-165">Если конкуренции нет, он выполняет внутри единственный префикс lock.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-165">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="b3d3d-166">При проверке кода ищите код, похожий на показанный в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-166">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="b3d3d-167">В первом примере увеличивается переменная состояния:</span><span class="sxs-lookup"><span data-stu-id="b3d3d-167">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="b3d3d-168">Вы можете повысить производительность, применяя метод <xref:System.Threading.Interlocked.Increment%2A> вместо оператора `lock`, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-168">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="b3d3d-169">Используйте метод <xref:System.Threading.Interlocked.Add%2A> для атомарных приращений более 1.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-169">Use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="b3d3d-170">Во втором примере переменная ссылочного типа обновляется только в том случае, если она является пустой ссылкой (`Nothing` в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b3d3d-170">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     <span data-ttu-id="b3d3d-171">Чтобы повысить производительность, применяйте вместо этого метод <xref:System.Threading.Interlocked.CompareExchange%2A>, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-171">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="b3d3d-172">Перегрузка метода <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> предоставляет типобезопасную альтернативу для ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-172">The <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="b3d3d-173">Рекомендации для библиотек классов</span><span class="sxs-lookup"><span data-stu-id="b3d3d-173">Recommendations for class libraries</span></span>  

 <span data-ttu-id="b3d3d-174">При разработке библиотек классов для многопоточности необходимо учитывать следующие рекомендации.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-174">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="b3d3d-175">Старайтесь не создавать потребность в синхронизации.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-175">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="b3d3d-176">Особенно это относится к коду, который используется наиболее часто.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-176">This is especially true for heavily used code.</span></span> <span data-ttu-id="b3d3d-177">Например, алгоритм можно скорректировать таким образом, чтобы он допускал конфликты, а не устранял их.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-177">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="b3d3d-178">Ненужная синхронизация снижает производительность и может привести к взаимоблокировке и конфликтам.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-178">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="b3d3d-179">Сделайте статические данные (`Shared` в Visual Basic) по умолчанию потокобезопасными.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-179">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="b3d3d-180">Данные экземпляров не должны быть потокобезопасными по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-180">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="b3d3d-181">Добавление блокировок для создания потокобезопасного кода снижает производительность, увеличивает конфликт блокировки и создает условия для возникновения взаимоблокировок.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-181">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="b3d3d-182">В обычных моделях приложений пользовательский код одновременно выполняется только одним потоком, что уменьшает необходимость потокобезопасности.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-182">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="b3d3d-183">По этой причине библиотеки классов .NET не являются потокобезопасными по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-183">For this reason, the .NET class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="b3d3d-184">Не предоставляйте статические методы, изменяющие статическое состояние.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-184">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="b3d3d-185">В обычных сценариях сервера статическое состояние используется запросами совместно, а значит, код одновременно могут выполнять сразу несколько потоков.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-185">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="b3d3d-186">Это открывает возможность для появления потоковых ошибок.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-186">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="b3d3d-187">Попробуйте применить конструктивный шаблон, инкапсулирующий данные в экземпляры, которые не являются общими для запросов.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-187">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="b3d3d-188">Кроме того, если статические данные синхронизируются, вызовы между статическими методами, изменяющие состояние, могут приводить к взаимоблокировкам или избыточной синхронизации, что, в свою очередь, снижает производительность.</span><span class="sxs-lookup"><span data-stu-id="b3d3d-188">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d3d-189">См. также</span><span class="sxs-lookup"><span data-stu-id="b3d3d-189">See also</span></span>

- [<span data-ttu-id="b3d3d-190">Работа с потоками</span><span class="sxs-lookup"><span data-stu-id="b3d3d-190">Threading</span></span>](index.md)
- [<span data-ttu-id="b3d3d-191">Потоки и работа с потоками</span><span class="sxs-lookup"><span data-stu-id="b3d3d-191">Threads and Threading</span></span>](threads-and-threading.md)
