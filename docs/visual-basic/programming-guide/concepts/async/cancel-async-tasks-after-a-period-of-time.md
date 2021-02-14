---
description: 'Дополнительные сведения: отмена асинхронных задач по истечении определенного периода времени (Visual Basic)'
title: Отмена асинхронных задач после определенного периода времени
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: fa1711017128dd32f29adfd87a540676371d02cf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431637"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="d2dde-103">Отмена асинхронных задач после определенного периода времени (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2dde-103">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>

<span data-ttu-id="d2dde-104">Если не нужно дожидаться, пока завершится выполнение асинхронной операции, ее можно отменить по истечении определенного периода времени с помощью метода <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2dde-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="d2dde-105">Этот метод планирует отмену всех связанных задач, не завершенных в течение времени, установленного выражением `CancelAfter`.</span><span class="sxs-lookup"><span data-stu-id="d2dde-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="d2dde-106">В этом примере добавляется код, написанный в статье [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) (Отмена асинхронной задачи или списка задач (Visual Basic)), для скачивания списка веб-сайтов и отображения длины содержимого каждого из них.</span><span class="sxs-lookup"><span data-stu-id="d2dde-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="d2dde-107">Для выполнения примеров необходимо, чтобы на компьютере были установлены Visual Studio версии 2012 и выше и .NET Framework версии 4.5 и выше.</span><span class="sxs-lookup"><span data-stu-id="d2dde-107">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>

## <a name="downloading-the-example"></a><span data-ttu-id="d2dde-108">Загрузка примера</span><span class="sxs-lookup"><span data-stu-id="d2dde-108">Downloading the Example</span></span>

<span data-ttu-id="d2dde-109">Скачать полный проект Windows Presentation Foundation (WPF) можно со страницы [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea). Затем выполните следующие шаги.</span><span class="sxs-lookup"><span data-stu-id="d2dde-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="d2dde-110">Распакуйте загруженный файл, а затем запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2dde-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="d2dde-111">В строке меню выберите **Файл**, **Открыть**, **Проект/Решение**.</span><span class="sxs-lookup"><span data-stu-id="d2dde-111">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="d2dde-112">В диалоговом окне **Открытие проекта** откройте папку с примером кода, который вы распаковали, а затем откройте файл решения (с разрешением .sln) для AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="d2dde-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>

4. <span data-ttu-id="d2dde-113">В **обозревателе решений** откройте контекстное меню проекта **CancelAfterTime** и выберите команду **Назначить запускаемым проектом**.</span><span class="sxs-lookup"><span data-stu-id="d2dde-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="d2dde-114">Нажмите клавишу F5, чтобы запустить проект.</span><span class="sxs-lookup"><span data-stu-id="d2dde-114">Choose the F5 key to run the project.</span></span>

     <span data-ttu-id="d2dde-115">Нажмите сочетание клавиш CTRL+F5, чтобы запустить проект без отладки.</span><span class="sxs-lookup"><span data-stu-id="d2dde-115">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>

6. <span data-ttu-id="d2dde-116">Выполните программу несколько раз, чтобы убедиться, что ее выходные данные могут содержать выходные данные по всем веб-сайтам, по некоторым из них или не содержать никакие данные по веб-сайтам.</span><span class="sxs-lookup"><span data-stu-id="d2dde-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

 <span data-ttu-id="d2dde-117">Если вы не хотите скачивать проект, можете просмотреть файл MainWindow.xaml.vb в конце этого раздела.</span><span class="sxs-lookup"><span data-stu-id="d2dde-117">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>

## <a name="building-the-example"></a><span data-ttu-id="d2dde-118">Построение примера</span><span class="sxs-lookup"><span data-stu-id="d2dde-118">Building the Example</span></span>

<span data-ttu-id="d2dde-119">Пример в этом разделе добавляется в проект, созданный в статье [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) (Отмена асинхронной задачи или списка задач (Visual Basic)).</span><span class="sxs-lookup"><span data-stu-id="d2dde-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="d2dde-120">В примере используется тот же пользовательский интерфейс, хотя кнопка **Отмена** не используется явно.</span><span class="sxs-lookup"><span data-stu-id="d2dde-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="d2dde-121">Для самостоятельной сборки примера шаг за шагом следуйте инструкциям в разделе "Загрузка примера", но выберите в качестве **запускаемого проекта** проект **CancelAfterOneTask**.</span><span class="sxs-lookup"><span data-stu-id="d2dde-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="d2dde-122">Добавьте изменения, приведенные в данном разделе, в этот проект.</span><span class="sxs-lookup"><span data-stu-id="d2dde-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="d2dde-123">Чтобы задать максимальный период времени, по истечении которого задачи будут отмечены как отмененные, добавьте вызов `CancelAfter` в `startButton_Click`, как показано в приведенном ниже примере.</span><span class="sxs-lookup"><span data-stu-id="d2dde-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="d2dde-124">Добавления помечены звездочками.</span><span class="sxs-lookup"><span data-stu-id="d2dde-124">The addition is marked with asterisks.</span></span>

```vb
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

    ' Instantiate the CancellationTokenSource.
    cts = New CancellationTokenSource()

    resultsTextBox.Clear()

    Try
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        ' can adjust the time.)
        cts.CancelAfter(2500)

        Await AccessTheWebAsync(cts.Token)
        resultsTextBox.Text &= vbCrLf & "Downloads complete."

    Catch ex As OperationCanceledException
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

    Catch ex As Exception
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
    End Try

    ' Set the CancellationTokenSource to Nothing when the download is complete.
    cts = Nothing
End Sub
```

<span data-ttu-id="d2dde-125">Выполните программу несколько раз, чтобы убедиться, что ее выходные данные могут содержать выходные данные по всем веб-сайтам, по некоторым из них или не содержать никакие данные по веб-сайтам.</span><span class="sxs-lookup"><span data-stu-id="d2dde-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="d2dde-126">Ниже приведен пример выходных данных.</span><span class="sxs-lookup"><span data-stu-id="d2dde-126">The following output is a sample:</span></span>

```console
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="d2dde-127">Полный пример</span><span class="sxs-lookup"><span data-stu-id="d2dde-127">Complete Example</span></span>

<span data-ttu-id="d2dde-128">Приведенный ниже код — полный текст файла MainWindow.xaml.vb для примера.</span><span class="sxs-lookup"><span data-stu-id="d2dde-128">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="d2dde-129">Звездочками помечаются элементы, добавленные для этого примера.</span><span class="sxs-lookup"><span data-stu-id="d2dde-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="d2dde-130">Обратите внимание на то, что необходимо добавить ссылку для <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="d2dde-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="d2dde-131">Вы можете скачать проект из статьи [Пример асинхронности. Тонкая настройка приложения](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="d2dde-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
            ' can adjust the time.)
            cts.CancelAfter(2500)

            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
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

        ' Process each element in the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
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

' Length of the downloaded string: 35990.

' Length of the downloaded string: 407399.

' Length of the downloaded string: 226091.

' Downloads canceled.
```

## <a name="see-also"></a><span data-ttu-id="d2dde-132">См. также</span><span class="sxs-lookup"><span data-stu-id="d2dde-132">See also</span></span>

- [<span data-ttu-id="d2dde-133">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2dde-133">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="d2dde-134">Пошаговое руководство. Получение доступа к Интернету с помощью модификатора Async и оператора Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2dde-134">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- <span data-ttu-id="d2dde-135">[Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md) (Отмена асинхронной задачи или списка задач в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2dde-135">[Cancel an Async Task or a List of Tasks (Visual Basic)](cancel-an-async-task-or-a-list-of-tasks.md)</span></span>
- <span data-ttu-id="d2dde-136">[Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) (Настройка асинхронного приложения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="d2dde-136">[Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md)</span></span>
- [<span data-ttu-id="d2dde-137">Пример использования Async. Настройка приложения</span><span class="sxs-lookup"><span data-stu-id="d2dde-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
