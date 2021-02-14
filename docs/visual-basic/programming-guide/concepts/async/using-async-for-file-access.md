---
description: 'Дополнительные сведения: использование Async для доступа к файлам (Visual Basic)'
title: Использование метода Async для доступа к файлам
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: f065ef8d8672569921e1652e62d24c10a506f828
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474217"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="14328-103">Использование метода Async для доступа к файлам (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14328-103">Using Async for File Access (Visual Basic)</span></span>

<span data-ttu-id="14328-104">Для доступа к файлам можно использовать функцию Async.</span><span class="sxs-lookup"><span data-stu-id="14328-104">You can use the Async feature to access files.</span></span> <span data-ttu-id="14328-105">С помощью возможности Async можно вызывать асинхронные методы, не прибегая к использованию обратных вызовов или разделению кода между несколькими методами или лямбда-выражениями.</span><span class="sxs-lookup"><span data-stu-id="14328-105">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="14328-106">Для выполнения последовательного кода асинхронно просто вызовите асинхронный метод вместо синхронного метода и добавьте несколько ключевых слов в код.</span><span class="sxs-lookup"><span data-stu-id="14328-106">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="14328-107">Можно рассмотреть следующие причины для добавления асинхронности для вызовов для доступа к файлам.</span><span class="sxs-lookup"><span data-stu-id="14328-107">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="14328-108">Асинхронность делает приложения пользовательского интерфейса более отзывчивыми, потому что поток пользовательского интерфейса, который запускает операцию, может продолжать выполнять и другую работу.</span><span class="sxs-lookup"><span data-stu-id="14328-108">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="14328-109">Если поток пользовательского интерфейса должен выполнять код, который занимает много времени (например, более 50 миллисекунд), пользовательский интерфейс можно приостановить до тех пор, пока не будет завершен ввод-вывод, и затем пользовательский интерфейс сможет снова обрабатывать ввод с клавиатуры, мыши и другие события.</span><span class="sxs-lookup"><span data-stu-id="14328-109">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="14328-110">Асинхронность улучшает масштабируемость ASP.NET и других серверных приложений за счет уменьшения необходимости использования потоков.</span><span class="sxs-lookup"><span data-stu-id="14328-110">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="14328-111">Если приложение использует выделенный поток на ответ и тысяча запросов приходит одновременно, тысяча потоков не потребуется.</span><span class="sxs-lookup"><span data-stu-id="14328-111">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="14328-112">Асинхронные операции часто не нуждаются в пользовании потоком во время ожидания.</span><span class="sxs-lookup"><span data-stu-id="14328-112">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="14328-113">Они пользуются существующим потоком завершения ввода-вывода короткое время в конце.</span><span class="sxs-lookup"><span data-stu-id="14328-113">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="14328-114">Задержка операции доступа к файлу может быть очень низкой при текущих условиях, но может значительно увеличиться в будущем.</span><span class="sxs-lookup"><span data-stu-id="14328-114">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="14328-115">Например, файл может быть перемещен на сервер через Интернет.</span><span class="sxs-lookup"><span data-stu-id="14328-115">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="14328-116">Добавленные издержки при использовании функции Async являются малыми.</span><span class="sxs-lookup"><span data-stu-id="14328-116">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="14328-117">Асинхронные задачи могут легко выполняться параллельно.</span><span class="sxs-lookup"><span data-stu-id="14328-117">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="14328-118">Выполнение примеров</span><span class="sxs-lookup"><span data-stu-id="14328-118">Running the Examples</span></span>  

 <span data-ttu-id="14328-119">Чтобы выполнить примеры в этом разделе, вы можете создать **приложение WPF** или **приложение Windows Forms**, а затем добавить **кнопку**.</span><span class="sxs-lookup"><span data-stu-id="14328-119">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="14328-120">В событии `Click` кнопки добавьте вызов к первому методу в каждом примере.</span><span class="sxs-lookup"><span data-stu-id="14328-120">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="14328-121">В следующие примеры добавьте указанные ниже операторы`Imports`.</span><span class="sxs-lookup"><span data-stu-id="14328-121">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="14328-122">Использование класса FileStream</span><span class="sxs-lookup"><span data-stu-id="14328-122">Use of the FileStream Class</span></span>  

 <span data-ttu-id="14328-123">В приведенных в этой статье примерах используется класс <xref:System.IO.FileStream>, содержащий параметр, который вызывает асинхронный ввод-вывод на уровне операционной системы.</span><span class="sxs-lookup"><span data-stu-id="14328-123">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="14328-124">С помощью этого параметра можно избежать блокирования пула потоков во многих случаях.</span><span class="sxs-lookup"><span data-stu-id="14328-124">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="14328-125">Чтобы включить этот параметр, необходимо добавить в вызов конструктора аргумент `useAsync=true` или `options=FileOptions.Asynchronous`.</span><span class="sxs-lookup"><span data-stu-id="14328-125">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="14328-126">Этот параметр нельзя использовать с классами <xref:System.IO.StreamReader> и <xref:System.IO.StreamWriter>, если вы открываете их напрямую (указав путь к файлу).</span><span class="sxs-lookup"><span data-stu-id="14328-126">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="14328-127">При этом параметр можно использовать, если им предоставлен <xref:System.IO.Stream>, открытый классом <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="14328-127">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="14328-128">Обратите внимание, что асинхронные вызовы выполняются быстрее в приложениях пользовательского интерфейса, даже если поток в пуле потоков блокирован, поскольку поток пользовательского интерфейса не блокирован во время ожидания.</span><span class="sxs-lookup"><span data-stu-id="14328-128">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="14328-129">Запись текста</span><span class="sxs-lookup"><span data-stu-id="14328-129">Writing Text</span></span>  

 <span data-ttu-id="14328-130">Следующие примеры записывают текст в файл.</span><span class="sxs-lookup"><span data-stu-id="14328-130">The following example writes text to a file.</span></span> <span data-ttu-id="14328-131">На каждой точке await происходит немедленный выход из метода.</span><span class="sxs-lookup"><span data-stu-id="14328-131">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="14328-132">После завершения файлового ввода-вывода метод возобновляет работу с пункта, следующего за await.</span><span class="sxs-lookup"><span data-stu-id="14328-132">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="14328-133">Обратите внимание, что модификатор async в определении методов требует наличия await в теле метода.</span><span class="sxs-lookup"><span data-stu-id="14328-133">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="14328-134">Первоначальная строка с оператором `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` является сокращенной формой записи двух следующих операторов:</span><span class="sxs-lookup"><span data-stu-id="14328-134">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="14328-135">Первый оператор возвращает задачу и вызывает запуск обработки файла.</span><span class="sxs-lookup"><span data-stu-id="14328-135">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="14328-136">Вторая строка с await немедленно оставляет метод и возвращается в другую задачу.</span><span class="sxs-lookup"><span data-stu-id="14328-136">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="14328-137">При окончании обработки файла выполнение возвращается в точку выполнения, которая следует за await.</span><span class="sxs-lookup"><span data-stu-id="14328-137">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="14328-138">Дополнительные сведения см.  [в разделе поток управления в асинхронных программах (Visual Basic)](control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="14328-138">For more information, see  [Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="14328-139">Чтение текста</span><span class="sxs-lookup"><span data-stu-id="14328-139">Reading Text</span></span>  

 <span data-ttu-id="14328-140">Следующий пример считывает текст из файла.</span><span class="sxs-lookup"><span data-stu-id="14328-140">The following example reads text from a file.</span></span> <span data-ttu-id="14328-141">Текст добавляется в буфер обмена, а затем, в данном случае, помещается в <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="14328-141">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="14328-142">В отличие от предыдущего примера await выдаёт в результате значение.</span><span class="sxs-lookup"><span data-stu-id="14328-142">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="14328-143">Метод <xref:System.IO.Stream.ReadAsync%2A> возвращает <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>, поэтому по завершении операции оценка await выдает значение `Int32` (`numRead`).</span><span class="sxs-lookup"><span data-stu-id="14328-143">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="14328-144">Дополнительные сведения см. в разделе [асинхронные типы возвращаемых данных (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="14328-144">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="14328-145">Параллельный асинхронный ввод-вывод</span><span class="sxs-lookup"><span data-stu-id="14328-145">Parallel Asynchronous I/O</span></span>  

 <span data-ttu-id="14328-146">В следующем примере показана параллельная обработка при записи 10 текстовых файлов.</span><span class="sxs-lookup"><span data-stu-id="14328-146">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="14328-147">Для каждого файла метод <xref:System.IO.Stream.WriteAsync%2A> возвращает задачу, которая затем добавляется в список задач.</span><span class="sxs-lookup"><span data-stu-id="14328-147">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="14328-148">Оператор `Await Task.WhenAll(tasks)` существует и возобновляется в методе, как только завершается обработка файла для всех задач.</span><span class="sxs-lookup"><span data-stu-id="14328-148">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="14328-149">Пример закрывает все экземпляры <xref:System.IO.FileStream> в блоке `Finally` после завершения всех задач.</span><span class="sxs-lookup"><span data-stu-id="14328-149">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="14328-150">Если бы вместо этого каждый `FileStream` был бы создан в операторе `Imports`, то `FileStream` можно было бы удалить до завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="14328-150">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="14328-151">Обратите внимание, что любое увеличение производительности зависит почти полностью от параллельной, а не асинхронной обработки.</span><span class="sxs-lookup"><span data-stu-id="14328-151">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="14328-152">Преимущества асинхронности в том, что она не привязана к количеству потоков и не связана с потоком пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="14328-152">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="14328-153">При использовании методов <xref:System.IO.Stream.WriteAsync%2A> и <xref:System.IO.Stream.ReadAsync%2A> можно указать <xref:System.Threading.CancellationToken>, который позволяет отменить операцию в середине потока.</span><span class="sxs-lookup"><span data-stu-id="14328-153">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="14328-154">Дополнительные сведения см. в разделе [Точная настройка асинхронного приложения (Visual Basic)](fine-tuning-your-async-application.md) и [Отмена в управляемых потоках](../../../../standard/threading/cancellation-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="14328-154">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14328-155">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="14328-155">See also</span></span>

- [<span data-ttu-id="14328-156">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14328-156">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- <span data-ttu-id="14328-157">[Async Return Types (Visual Basic)](async-return-types.md) (Типы возвращаемых значений Async (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="14328-157">[Async Return Types (Visual Basic)](async-return-types.md)</span></span>
- <span data-ttu-id="14328-158">[Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md) (Поток управления в асинхронных программах (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="14328-158">[Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md)</span></span>
