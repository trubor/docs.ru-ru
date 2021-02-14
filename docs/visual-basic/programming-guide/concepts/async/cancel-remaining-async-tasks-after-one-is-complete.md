---
description: 'Дополнительные сведения: отмена оставшихся асинхронных задач после завершения одной операции (Visual Basic)'
title: Отмена оставшихся асинхронных задач после завершения одной из них
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 6f7fc8af707c6c0d69fcf88e511b84b31ba75a82
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438896"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="f7ffa-103">Cancel Remaining Async Tasks after One Is Complete (Visual Basic) (Отмена оставшихся асинхронных задач после завершения одной из них в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7ffa-103">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>

<span data-ttu-id="f7ffa-104">Используя метод <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> вместе с <xref:System.Threading.CancellationToken>, можно отменить все оставшиеся задачи после выполнения отдельной задачи.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-104">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="f7ffa-105">Метод `WhenAny` принимает аргумент, который представляет собой коллекцию задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-105">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="f7ffa-106">Метод запускает все задачи и возвращает одну задачу.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-106">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="f7ffa-107">Одна задача считается завершенной, когда завершена любая задача в коллекции.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-107">The single task is complete when any task in the collection is complete.</span></span>

<span data-ttu-id="f7ffa-108">В этом примере показано, как использовать маркер отмены в сочетании с `WhenAny` для приостановки завершения первой задачи из коллекции задач и отмены оставшихся задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-108">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="f7ffa-109">Каждая задача загружает содержимое веб-сайта.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-109">Each task downloads the contents of a website.</span></span> <span data-ttu-id="f7ffa-110">Пример отображает длину содержимого первой завершаемой загрузки и отменяет другие загрузки.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-110">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>

> [!NOTE]
> <span data-ttu-id="f7ffa-111">Для выполнения примеров необходимо, чтобы на компьютере были установлены Visual Studio 2012 или более поздняя версия и .NET Framework 4.5 или более поздняя версия.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-111">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="f7ffa-112">Загрузка примера</span><span class="sxs-lookup"><span data-stu-id="f7ffa-112">Downloading the Example</span></span>

<span data-ttu-id="f7ffa-113">Скачать полный проект Windows Presentation Foundation (WPF) можно со страницы [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea). Затем выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-113">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="f7ffa-114">Распакуйте загруженный файл, а затем запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-114">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="f7ffa-115">В строке меню выберите **Файл**, **Открыть**, **Проект/Решение**.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-115">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="f7ffa-116">В диалоговом окне **Открытие проекта** откройте папку с примером кода, который вы распаковали, а затем откройте файл решения (с разрешением .sln) для AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-116">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="f7ffa-117">В **обозревателе решений** откройте контекстное меню проекта **CancelAfterOneTask** и выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-117">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="f7ffa-118">Нажмите клавишу F5, чтобы запустить проект.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-118">Choose the F5 key to run the project.</span></span>

    <span data-ttu-id="f7ffa-119">Нажмите сочетание клавиш CTRL+F5, чтобы запустить проект без отладки.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-119">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="f7ffa-120">Запустите программу несколько раз, чтобы убедиться, что разные задачи завершаются первыми.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-120">Run the program several times to verify that different downloads finish first.</span></span>

<span data-ttu-id="f7ffa-121">Если вы не хотите скачивать проект, можете просмотреть файл MainWindow.xaml.vb в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-121">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="f7ffa-122">Построение примера</span><span class="sxs-lookup"><span data-stu-id="f7ffa-122">Building the Example</span></span>

<span data-ttu-id="f7ffa-123">Пример в этом разделе добавляет в проект, разработанный при [отмене асинхронной задачи, или список задач](cancel-an-async-task-or-a-list-of-tasks.md) для отмены списка задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-123">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="f7ffa-124">В примере используется тот же пользовательский интерфейс, хотя кнопка **Отмена** не используется явно.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-124">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="f7ffa-125">Для самостоятельной сборки примера шаг за шагом следуйте инструкциям в разделе "Загрузка примера", но выберите в качестве **запускаемого проекта** проект **CancelAfterOneTask**.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-125">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="f7ffa-126">Добавьте изменения, приведенные в данном разделе, в этот проект.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-126">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="f7ffa-127">В файле MainWindow. XAML проекта **CancelAListOfTasks** запустите переход, переместив шаги обработки для каждого веб-сайта из цикла в `AccessTheWebAsync` следующий асинхронный метод.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-127">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>

```vb
' ***Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

<span data-ttu-id="f7ffa-128">В `AccessTheWebAsync` в этом примере используются запрос, метод <xref:System.Linq.Enumerable.ToArray%2A> и метод `WhenAny` для создания и запуска массива задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-128">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="f7ffa-129">Применение `WhenAny` к массиву возвращает одну задачу, которая, если ожидается, вычисляется как первая завершившаяся задача в массиве задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-129">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>

<span data-ttu-id="f7ffa-130">Внесите следующие изменения в `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-130">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f7ffa-131">Звездочками отмечены изменения в файле кода.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-131">Asterisks mark the changes in the code file.</span></span>

1. <span data-ttu-id="f7ffa-132">Закомментируйте или удалите цикл.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-132">Comment out or delete the loop.</span></span>

2. <span data-ttu-id="f7ffa-133">Создайте запрос, который во время выполнения создает коллекцию общих заданий.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-133">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="f7ffa-134">Каждый вызов `ProcessURLAsync` возвращает <xref:System.Threading.Tasks.Task%601>, где `TResult` — это целое число.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-134">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. <span data-ttu-id="f7ffa-135">Вызовите `ToArray` для выполнения запроса и запуска задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="f7ffa-136">Применение метода `WhenAny` в следующем шаге будет выполнять запрос и запускать задачи без использования `ToArray`, однако этот режим может быть недоступен для других методов.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="f7ffa-137">Наиболее безопасным способом является явное принудительное выполнения запроса.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-137">The safest practice is to force execution of the query explicitly.</span></span>

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. <span data-ttu-id="f7ffa-138">Вызовите `WhenAny` для коллекции задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-138">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="f7ffa-139">`WhenAny` возвращает `Task(Of Task(Of Integer))` или `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-139">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="f7ffa-140">То есть `WhenAny` возвращает задачу, которая вычисляется как одна задача `Task(Of Integer)` или `Task<int>`, если она ожидается.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-140">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="f7ffa-141">Одна задача — это первая завершившаяся задача в коллекции.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-141">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="f7ffa-142">Задача, которая завершается первой, назначается `finishedTask`.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-142">The task that finished first is assigned to `finishedTask`.</span></span> <span data-ttu-id="f7ffa-143">`finishedTask` имеет тип <xref:System.Threading.Tasks.Task%601>, где `TResult` является целым числом, поскольку это возвращаемый тип `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-143">The type of `finishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to finishedTask.
    Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. <span data-ttu-id="f7ffa-144">В этом примере нас интересует только та задача, которая завершается первой.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-144">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="f7ffa-145">Таким образом, используйте <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> для отмены оставшихся задач.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-145">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. <span data-ttu-id="f7ffa-146">Наконец, мы ожидаем `finishedTask` для получения длины скачанного содержимого.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-146">Finally, await `finishedTask` to retrieve the length of the downloaded content.</span></span>

    ```vb
    Dim length = Await finishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

<span data-ttu-id="f7ffa-147">Запустите программу несколько раз, чтобы убедиться, что разные задачи завершаются первыми.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-147">Run the program several times to verify that different downloads finish first.</span></span>

## <a name="complete-example"></a><span data-ttu-id="f7ffa-148">Полный пример</span><span class="sxs-lookup"><span data-stu-id="f7ffa-148">Complete Example</span></span>

<span data-ttu-id="f7ffa-149">Следующий код представляет собой полный файл MainWindow. XAML. vb или MainWindow.xaml.cs для примера.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-149">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="f7ffa-150">Звездочками помечаются элементы, добавленные для этого примера.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-150">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="f7ffa-151">Обратите внимание на то, что необходимо добавить ссылку для <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f7ffa-151">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="f7ffa-152">Вы можете скачать проект из статьи [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="f7ffa-152">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' ***Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' ***Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' ***Call WhenAny and then await the result. The task that finishes
        ' first is assigned to finishedTask.
        Dim finishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' ***Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' ***Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await finishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' ***Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a><span data-ttu-id="f7ffa-153">См. также</span><span class="sxs-lookup"><span data-stu-id="f7ffa-153">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- <span data-ttu-id="f7ffa-154">[Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) (Настройка асинхронного приложения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="f7ffa-154">[Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md)</span></span>
- [<span data-ttu-id="f7ffa-155">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7ffa-155">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="f7ffa-156">Пример использования Async. Настройка приложения</span><span class="sxs-lookup"><span data-stu-id="f7ffa-156">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
