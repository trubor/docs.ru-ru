---
description: 'Дополнительные сведения о: Практическое руководство. расширение асинхронного пошагового руководства с помощью Task. WhenAll (Visual Basic)'
title: Практическое руководство. Оптимизация производительности асинхронных процедур с использованием метода Task.WhenAll
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: fc303d6b2ed64cb2003c06724fcd21000d0b3abf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474386"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="b83d0-103">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic) (Практическое руководство. Расширение пошагового руководства по асинхронным процедурам с использованием метода Task.WhenAll (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="b83d0-103">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>

<span data-ttu-id="b83d0-104">Вы можете повысить производительность асинхронного решения в [пошаговом руководстве: доступ к Интернету с помощью методов async и await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) с помощью <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> метода.</span><span class="sxs-lookup"><span data-stu-id="b83d0-104">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b83d0-105">Этот метод асинхронно ожидает несколько асинхронных операций, которые представлены в виде коллекции задач.</span><span class="sxs-lookup"><span data-stu-id="b83d0-105">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="b83d0-106">Как вы могли заметить в этом пошаговом руководстве, веб-сайты загружаются с разной скоростью.</span><span class="sxs-lookup"><span data-stu-id="b83d0-106">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="b83d0-107">Иногда один из веб-сайтов работает слишком медленно, что задерживает все остальные загрузки.</span><span class="sxs-lookup"><span data-stu-id="b83d0-107">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="b83d0-108">Во время работы асинхронных программ, созданных в этом пошаговом руководстве, программу можно с легкостью завершить, если нет необходимости в ожидании, но было бы лучше начать все загрузки одновременно и дать возможность более быстрым загрузкам продолжаться без ожидания более медленных.</span><span class="sxs-lookup"><span data-stu-id="b83d0-108">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="b83d0-109">Метод `Task.WhenAll` можно применить к коллекции задач.</span><span class="sxs-lookup"><span data-stu-id="b83d0-109">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="b83d0-110">Метод `WhenAll`, примененный к коллекции, возвращает одну задачу, которая остается незавершенной до тех пор, пока не будет выполнена каждая задача из коллекции.</span><span class="sxs-lookup"><span data-stu-id="b83d0-110">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="b83d0-111">Как видим, задачи выполняются параллельно, однако дополнительные потоки не создаются.</span><span class="sxs-lookup"><span data-stu-id="b83d0-111">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="b83d0-112">Задачи могут выполняться в любом порядке.</span><span class="sxs-lookup"><span data-stu-id="b83d0-112">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b83d0-113">Следующие процедуры описывают расширения для асинхронных приложений, разработанных в [пошаговом руководстве: доступ к Интернету с помощью Async и await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="b83d0-113">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="b83d0-114">Вы можете разработать приложения, выполнив пошаговое руководство или скачав код на странице [Примеры кода от разработчиков](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="b83d0-114">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="b83d0-115">Для выполнения этого примера на компьютере должна быть установлена среда Visual Studio 2012 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="b83d0-115">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="b83d0-116">Добавление метода Task.WhenAll в решение GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="b83d0-116">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="b83d0-117">Добавьте `ProcessURLAsync` метод в первое приложение, разработанное в [пошаговом руководстве: доступ к Интернету с помощью Async и Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="b83d0-117">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="b83d0-118">Если вы скачали код из  [примеров кода разработчика](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), откройте проект асинквалксраугх, а затем добавьте `ProcessURLAsync` в файл MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="b83d0-118">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="b83d0-119">Если вы разработали код, выполнив пошаговое руководство, добавьте `ProcessURLAsync` в приложение, которое включает метод `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-119">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="b83d0-120">Файл MainWindow. XAML. vb для этого приложения является первым примером в разделе «полные примеры кода из пошагового руководства».</span><span class="sxs-lookup"><span data-stu-id="b83d0-120">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="b83d0-121">Метод `ProcessURLAsync` объединяет действия в теле цикла `For Each` в `SumPageSizesAsync` в исходном пошаговом руководстве.</span><span class="sxs-lookup"><span data-stu-id="b83d0-121">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="b83d0-122">Метод асинхронно скачивает содержимое указанного веб-сайта в виде массива байтов и затем отображает и возвращает длину массива байтов.</span><span class="sxs-lookup"><span data-stu-id="b83d0-122">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="b83d0-123">Закомментируйте или удалите цикл `For Each` в `SumPageSizesAsync`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="b83d0-123">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList

    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

    '    ' The previous line abbreviates the following two assignment statements.

    '    ' GetURLContentsAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="b83d0-124">Создайте коллекцию задач.</span><span class="sxs-lookup"><span data-stu-id="b83d0-124">Create a collection of tasks.</span></span> <span data-ttu-id="b83d0-125">Следующий код определяет [запрос](../linq/index.md), который при выполнении метода <xref:System.Linq.Enumerable.ToArray%2A> создает коллекцию задач, скачивающих содержимое каждого веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="b83d0-125">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="b83d0-126">Задачи запускаются при вычислении запроса.</span><span class="sxs-lookup"><span data-stu-id="b83d0-126">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="b83d0-127">Добавьте следующий код в метод `SumPageSizesAsync` после объявления `urlList`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-127">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="b83d0-128">Примените `Task.WhenAll` к коллекции задач, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-128">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="b83d0-129">`Task.WhenAll` возвращает одну задачу, которая завершается после завершения всех задач в коллекции задач.</span><span class="sxs-lookup"><span data-stu-id="b83d0-129">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="b83d0-130">В следующем примере выражение `Await` ожидает завершения одной задачи, возвращаемой `WhenAll`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-130">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="b83d0-131">Результат этого выражения – массив целых чисел, каждое из которых – размер загруженного веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="b83d0-131">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="b83d0-132">Добавьте следующий код в `SumPageSizesAsync` сразу после кода, добавленного на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="b83d0-132">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="b83d0-133">И, наконец, используйте метод <xref:System.Linq.Enumerable.Sum%2A> для вычисления суммы длин всех веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="b83d0-133">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="b83d0-134">Добавьте следующую строку в `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-134">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="b83d0-135">Добавление метода Task.WhenAll в решение HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="b83d0-135">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="b83d0-136">Добавьте следующую версию `ProcessURLAsync` во второе приложение, разработанное в [пошаговом руководстве: доступ к Интернету с помощью Async и Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="b83d0-136">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="b83d0-137">Если вы скачали код из [примеров кода разработчика](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), откройте проект AsyncWalkthrough_HttpClient, а затем добавьте `ProcessURLAsync` в файл MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="b83d0-137">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>

    - <span data-ttu-id="b83d0-138">Если вы разработали код, выполнив пошаговое руководство, добавьте `ProcessURLAsync` в приложение, которое использует метод `HttpClient.GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-138">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="b83d0-139">Файл MainWindow. XAML. vb для этого приложения является вторым примером в разделе «полные примеры кода из пошагового руководства».</span><span class="sxs-lookup"><span data-stu-id="b83d0-139">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

     <span data-ttu-id="b83d0-140">Метод `ProcessURLAsync` объединяет действия в теле цикла `For Each` в `SumPageSizesAsync` в исходном пошаговом руководстве.</span><span class="sxs-lookup"><span data-stu-id="b83d0-140">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="b83d0-141">Метод асинхронно скачивает содержимое указанного веб-сайта в виде массива байтов и затем отображает и возвращает длину массива байтов.</span><span class="sxs-lookup"><span data-stu-id="b83d0-141">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

     <span data-ttu-id="b83d0-142">Единственное отличие от метода `ProcessURLAsync` из предыдущей процедуры заключается в использовании экземпляра <xref:System.Net.Http.HttpClient>, `client`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-142">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```vb
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function
    ```

2. <span data-ttu-id="b83d0-143">Закомментируйте или удалите цикл `For Each` в `SumPageSizesAsync`, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="b83d0-143">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```vb
    'Dim total = 0
    'For Each url In urlList
    '    ' GetByteArrayAsync returns a task. At completion, the task
    '    ' produces a byte array.
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

    '    ' The following two lines can replace the previous assignment statement.
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
    '    'Dim urlContents As Byte() = Await getContentsTask

    '    DisplayResults(url, urlContents)

    '    ' Update the total.
    '    total += urlContents.Length
    'Next
    ```

3. <span data-ttu-id="b83d0-144">Определите [запрос](../linq/index.md), который при выполнении метода <xref:System.Linq.Enumerable.ToArray%2A> создает коллекцию задач, скачивающих содержимое каждого веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="b83d0-144">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="b83d0-145">Задачи запускаются при вычислении запроса.</span><span class="sxs-lookup"><span data-stu-id="b83d0-145">The tasks are started when the query is evaluated.</span></span>

     <span data-ttu-id="b83d0-146">Добавьте следующий код в метод `SumPageSizesAsync` после объявления `client` и `urlList`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-146">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```vb
    ' Create a query.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client)

    ' Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="b83d0-147">Затем примените `Task.WhenAll` к коллекции задач, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-147">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="b83d0-148">`Task.WhenAll` возвращает одну задачу, которая завершается после завершения всех задач в коллекции задач.</span><span class="sxs-lookup"><span data-stu-id="b83d0-148">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

     <span data-ttu-id="b83d0-149">В следующем примере выражение `Await` ожидает завершения одной задачи, возвращаемой `WhenAll`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-149">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="b83d0-150">Результат выражения `Await` — массив целых чисел, каждое из которых представляет размер скачанного веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="b83d0-150">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="b83d0-151">Добавьте следующий код в `SumPageSizesAsync` сразу после кода, добавленного на предыдущем шаге.</span><span class="sxs-lookup"><span data-stu-id="b83d0-151">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```vb
    ' Await the completion of all the running tasks.
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

    '' The previous line is equivalent to the following two statements.
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
    'Dim lengths As Integer() = Await whenAllTask
    ```

5. <span data-ttu-id="b83d0-152">И, наконец, используйте метод <xref:System.Linq.Enumerable.Sum%2A> для получения суммы длин всех веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="b83d0-152">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="b83d0-153">Добавьте следующую строку в `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="b83d0-153">Add the following line to `SumPageSizesAsync`.</span></span>

    ```vb
    Dim total = lengths.Sum()
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="b83d0-154">Тестирование решений Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="b83d0-154">To test the Task.WhenAll solutions</span></span>

<span data-ttu-id="b83d0-155">Для любого из решений нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Запуск**.</span><span class="sxs-lookup"><span data-stu-id="b83d0-155">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="b83d0-156">Выходные данные должны быть похожи на выходные данные асинхронных решений в [пошаговом руководстве: доступ к Интернету с использованием Async и await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="b83d0-156">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="b83d0-157">Тем не менее обратите внимание, что веб-сайты каждый раз отображаются в другом порядке.</span><span class="sxs-lookup"><span data-stu-id="b83d0-157">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="b83d0-158">Пример</span><span class="sxs-lookup"><span data-stu-id="b83d0-158">Example</span></span>

<span data-ttu-id="b83d0-159">В следующем коде показано расширение для проекта, использующее метод `GetURLContentsAsync` для скачивания содержимого из Интернета.</span><span class="sxs-lookup"><span data-stu-id="b83d0-159">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        'Dim total = 0
        'For Each url In urlList

        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)

        '    ' The previous line abbreviates the following two assignment statements.

        '    ' GetURLContentsAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    ' The actions from the foreach loop are moved to this async method.
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)

        Dim byteArray = Await GetURLContentsAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                ' CopyToAsync returns a Task, not a Task<T>.
                Await responseStream.CopyToAsync(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="example"></a><span data-ttu-id="b83d0-160">Пример</span><span class="sxs-lookup"><span data-stu-id="b83d0-160">Example</span></span>

<span data-ttu-id="b83d0-161">В следующем коде показано расширение для проекта, использующее метод `HttpClient.GetByteArrayAsync` для скачивания содержимого из Интернета.</span><span class="sxs-lookup"><span data-stu-id="b83d0-161">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        '' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' Create a query.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client)

        ' Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' You can do other work here before awaiting.

        ' Await the completion of all the running tasks.
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)

        '' The previous line is equivalent to the following two statements.
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)
        'Dim lengths As Integer() = Await whenAllTask

        Dim total = lengths.Sum()

        ''<snippet7>
        'Dim total = 0
        'For Each url In urlList
        '    ' GetByteArrayAsync returns a task. At completion, the task
        '    ' produces a byte array.
        '    '<snippet31>
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
        '    '</snippet31>

        '    ' The following two lines can replace the previous assignment statement.
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
        '    'Dim urlContents As Byte() = Await getContentsTask

        '    DisplayResults(url, urlContents)

        '    ' Update the total.
        '    total += urlContents.Length
        'NextNext

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://www.msdn.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)

        Dim byteArray = Await client.GetByteArrayAsync(url)
        DisplayResults(url, byteArray)
        Return byteArray.Length
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="b83d0-162">См. также</span><span class="sxs-lookup"><span data-stu-id="b83d0-162">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b83d0-163">Пошаговое руководство. Получение доступа к Интернету с помощью модификатора Async и оператора Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b83d0-163">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
