---
description: Дополнительные сведения см. в статье поток управления в асинхронных программах (Visual Basic)
title: Поток управления в асинхронных программах
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: bf0ca6a083971cb02cfb6dff2dfcaaabd5405b36
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100428250"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="f72e9-103">Control Flow in Async Programs (Visual Basic) (Поток управления в асинхронных программах (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="f72e9-103">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="f72e9-104">Можно намного проще создавать и обслуживать асинхронные программы с помощью ключевых слов `Async` и `Await`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-104">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="f72e9-105">Однако при непонимании механизма работы асинхронной программы результаты могут удивить.</span><span class="sxs-lookup"><span data-stu-id="f72e9-105">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="f72e9-106">В этом разделе выполняется трассировка потока управления с помощью простой асинхронной программы, чтобы продемонстрировать переход потока управления от одного метода к другому, включая данные, передаваемые в каждом случае.</span><span class="sxs-lookup"><span data-stu-id="f72e9-106">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="f72e9-107">Ключевые слова `Async` и `Await` появились в Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f72e9-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="f72e9-108">Как правило, методы, содержащие асинхронный код, помечаются модификатором [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="f72e9-108">In general, you mark methods that contain asynchronous code with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f72e9-109">В методе, помеченном модификатором Async, можно использовать оператор [await (Visual Basic)](../../../language-reference/operators/await-operator.md) , чтобы указать место приостановки метода для ожидания завершения вызванного асинхронного процесса.</span><span class="sxs-lookup"><span data-stu-id="f72e9-109">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="f72e9-110">Дополнительные сведения см. [в разделе Асинхронное программирование с использованием Async и await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="f72e9-110">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="f72e9-111">В следующем примере асинхронные методы используются для загрузки содержимого указанного веб-сайта в виде строки и отображения длины строки.</span><span class="sxs-lookup"><span data-stu-id="f72e9-111">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="f72e9-112">Пример содержит следующие два метода:</span><span class="sxs-lookup"><span data-stu-id="f72e9-112">The example contains the following two methods.</span></span>

- <span data-ttu-id="f72e9-113">`startButton_Click`, который вызывает метод `AccessTheWebAsync` и выводит результат;</span><span class="sxs-lookup"><span data-stu-id="f72e9-113">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="f72e9-114">`AccessTheWebAsync`, который загружает содержимое веб-сайта в виде строки и возвращает длину строки.</span><span class="sxs-lookup"><span data-stu-id="f72e9-114">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="f72e9-115">`AccessTheWebAsync` использует для загрузки содержимого асинхронный метод <xref:System.Net.Http.HttpClient><xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="f72e9-115">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="f72e9-116">Выводимые строки помечены номерами на стратегических этапах программы, чтобы помочь вам понять, как работает программа и что происходит на каждом отмеченном этапе.</span><span class="sxs-lookup"><span data-stu-id="f72e9-116">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="f72e9-117">Выводимые строки обозначены номерами от ONE (один) до SIX (шесть).</span><span class="sxs-lookup"><span data-stu-id="f72e9-117">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="f72e9-118">Метки представляют порядок, в котором программа достигает эти строки кода.</span><span class="sxs-lookup"><span data-stu-id="f72e9-118">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="f72e9-119">В следующем примере кода показана структура программы.</span><span class="sxs-lookup"><span data-stu-id="f72e9-119">The following code shows an outline of the program.</span></span>

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

<span data-ttu-id="f72e9-120">Каждое из расположений, обозначенное от одного до шести, отображает сведения о текущем состоянии программы.</span><span class="sxs-lookup"><span data-stu-id="f72e9-120">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="f72e9-121">Выводятся следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="f72e9-121">The following output is produced:</span></span>

```console
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="f72e9-122">Настройка программы</span><span class="sxs-lookup"><span data-stu-id="f72e9-122">Set Up the Program</span></span>

<span data-ttu-id="f72e9-123">Можно загрузить используемый в этом разделе код из MSDN, или же можно создать его самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="f72e9-123">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="f72e9-124">Для выполнения этого примера на компьютере должен быть установлен Visual Studio 2012 или более поздней версии, а также платформа .NET Framework 4,5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="f72e9-124">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="f72e9-125">Скачайте программу</span><span class="sxs-lookup"><span data-stu-id="f72e9-125">Download the Program</span></span>

<span data-ttu-id="f72e9-126">Вы можете скачать приложение для этого раздела на странице примеров [Пример Async: поток управления в асинхронных программах](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="f72e9-126">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="f72e9-127">Следующие шаги описывают процесс открытия и запуска программы.</span><span class="sxs-lookup"><span data-stu-id="f72e9-127">The following steps open and run the program.</span></span>

1. <span data-ttu-id="f72e9-128">Распакуйте загруженный файл, а затем запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f72e9-128">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="f72e9-129">В строке меню выберите **Файл**, **Открыть**, **Проект/Решение**.</span><span class="sxs-lookup"><span data-stu-id="f72e9-129">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="f72e9-130">Перейдите к папке, содержащей распакованный пример кода, откройте файл решения (SLN), а затем нажмите клавишу F5 для сборки и выполнения проекта.</span><span class="sxs-lookup"><span data-stu-id="f72e9-130">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="f72e9-131">Самостоятельное построение программы</span><span class="sxs-lookup"><span data-stu-id="f72e9-131">Build the Program Yourself</span></span>

<span data-ttu-id="f72e9-132">Следующий проект Windows Presentation Foundation (WPF) содержит примеры кода для этого раздела.</span><span class="sxs-lookup"><span data-stu-id="f72e9-132">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="f72e9-133">Чтобы запустить проект, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="f72e9-133">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="f72e9-134">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f72e9-134">Start Visual Studio.</span></span>

2. <span data-ttu-id="f72e9-135">В строке меню выберите **Файл**, **Создать**, **Проект**.</span><span class="sxs-lookup"><span data-stu-id="f72e9-135">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="f72e9-136">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="f72e9-136">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="f72e9-137">В области **Установленные шаблоны** выберите **Visual Basic**, а затем выберите **приложение WPF** в списке типов проектов.</span><span class="sxs-lookup"><span data-stu-id="f72e9-137">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="f72e9-138">Введите `AsyncTracer` в качестве имени проекта и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="f72e9-138">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="f72e9-139">В **обозревателе решений** появится новый проект.</span><span class="sxs-lookup"><span data-stu-id="f72e9-139">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="f72e9-140">В редакторе кода Visual Studio перейдите на вкладку **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="f72e9-140">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="f72e9-141">Если вкладка не отображается, откройте контекстное меню для MainWindow.xaml в **обозревателе решений** и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="f72e9-141">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="f72e9-142">Замените код в представлении **XAML** файла MainWindow.xaml на следующий.</span><span class="sxs-lookup"><span data-stu-id="f72e9-142">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    <span data-ttu-id="f72e9-143">В представлении **Конструктор** файла MainWindow.xaml появится простое окно, содержащее кнопку и текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="f72e9-143">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="f72e9-144">Добавьте ссылку для <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="f72e9-144">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="f72e9-145">В **Обозреватель решений** откройте контекстное меню файла MainWindow. XAML. vb и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="f72e9-145">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="f72e9-146">В файле MainWindow. XAML. vb замените код следующим кодом.</span><span class="sxs-lookup"><span data-stu-id="f72e9-146">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. <span data-ttu-id="f72e9-147">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="f72e9-147">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="f72e9-148">Должны отобразиться следующие выходные данные:</span><span class="sxs-lookup"><span data-stu-id="f72e9-148">The following output should appear:</span></span>

    ```console
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="f72e9-149">Трассировка программы</span><span class="sxs-lookup"><span data-stu-id="f72e9-149">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="f72e9-150">Шаги ОДИН и ДВА</span><span class="sxs-lookup"><span data-stu-id="f72e9-150">Steps ONE and TWO</span></span>

<span data-ttu-id="f72e9-151">В первых двух строках прослеживается путь по мере того, как метод `startButton_Click` вызывает `AccessTheWebAsync`, а `AccessTheWebAsync` вызывает асинхронный метод <xref:System.Net.Http.HttpClient><xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="f72e9-151">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="f72e9-152">Ниже показаны вызовы из метода в метод.</span><span class="sxs-lookup"><span data-stu-id="f72e9-152">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="f72e9-153">![Шаги ОДИН и ДВА](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="f72e9-153">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="f72e9-154">Типом возвращаемого значения и для `AccessTheWebAsync`, и для `client.GetStringAsync` является <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f72e9-154">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f72e9-155">Для `AccessTheWebAsync` значение TResult является целым числом.</span><span class="sxs-lookup"><span data-stu-id="f72e9-155">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="f72e9-156">Для `GetStringAsync` значение TResult является строкой.</span><span class="sxs-lookup"><span data-stu-id="f72e9-156">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="f72e9-157">Дополнительные сведения о типах возвращаемых асинхронных методов см. в разделе [асинхронные типы возвращаемых данных (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f72e9-157">For more information about async method return types, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

<span data-ttu-id="f72e9-158">Асинхронный метод, возвращающий задачи, возвращает экземпляр задачи, когда контроль управления возвращается к вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="f72e9-158">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="f72e9-159">Управление передается от асинхронного метода его вызывающему методу, когда в вызванном методе обнаруживается оператор `Await` или когда вызванный метод завершается.</span><span class="sxs-lookup"><span data-stu-id="f72e9-159">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="f72e9-160">Отображаемые строки, которые помечены от трёх до шести, отслеживают эту часть процесса.</span><span class="sxs-lookup"><span data-stu-id="f72e9-160">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="f72e9-161">Шаг ТРИ</span><span class="sxs-lookup"><span data-stu-id="f72e9-161">Step THREE</span></span>

<span data-ttu-id="f72e9-162">В `AccessTheWebAsync` для загрузки содержимого целевой веб-страницы вызывается асинхронный метод <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="f72e9-162">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="f72e9-163">Управление передается от `client.GetStringAsync` методу `AccessTheWebAsync` при возвращении результатов методом `client.GetStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-163">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="f72e9-164">Метод `client.GetStringAsync` возвращает задачу строки, назначенной переменной `getStringTask` в `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-164">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f72e9-165">Следующая строка в примере программы демонстрирует вызов `client.GetStringAsync` и назначение.</span><span class="sxs-lookup"><span data-stu-id="f72e9-165">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="f72e9-166">Можно представить себе задачу как обещание `client.GetStringAsync` создать в конечном итоге фактическую строку.</span><span class="sxs-lookup"><span data-stu-id="f72e9-166">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="f72e9-167">В то же время, если у `AccessTheWebAsync` есть работа, не зависящая от обещанной строки, от `client.GetStringAsync`, эта работа будет продолжена во время ожидания `client.GetStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-167">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="f72e9-168">В этом примере следующие строки вывода, которые обозначены как "THREE", представляют возможность сделать независимую работу.</span><span class="sxs-lookup"><span data-stu-id="f72e9-168">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="f72e9-169">Следующая инструкция приостанавливает ход выполнения в `AccessTheWebAsync` при ожидании `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-169">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="f72e9-170">На следующем рисунке показан поток управления путем `client.GetStringAsync` к назначению `getStringTask` и из создания `getStringTask` в приложение оператора await.</span><span class="sxs-lookup"><span data-stu-id="f72e9-170">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="f72e9-171">![Шаг ТРИ](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="f72e9-171">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="f72e9-172">Выражение await приостанавливает `AccessTheWebAsync` до возвращения результатов `client.GetStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-172">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="f72e9-173">На это время управление возвращается вызывающему объекту метода `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-173">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="f72e9-174">Как правило, ожидание вызова асинхронного метода выполняется немедленно.</span><span class="sxs-lookup"><span data-stu-id="f72e9-174">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="f72e9-175">Например, следующее присвоение может заменить предыдущий код, который создает, а затем ожидает `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="f72e9-175">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="f72e9-176">В этом разделе оператор await применяется позже для размещения строк, которые отмечают поток управления в программе.</span><span class="sxs-lookup"><span data-stu-id="f72e9-176">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="f72e9-177">Шаг ЧЕТЫРЕ</span><span class="sxs-lookup"><span data-stu-id="f72e9-177">Step FOUR</span></span>

<span data-ttu-id="f72e9-178">Объявленный тип возвращаемого значения `AccessTheWebAsync` — `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-178">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="f72e9-179">Таким образом, когда выполнение `AccessTheWebAsync` приостанавливается, он возвращает задачу целого числа в `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-179">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="f72e9-180">Следует понимать, что возвращаемая задача — не `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-180">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="f72e9-181">Возвращаемая задача — это новая задача целого числа, представляющая оставшуюся работу в приостановленном методе `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-181">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="f72e9-182">Задача является обещанием `AccessTheWebAsync` создать фактическое целое число после завершения задачи.</span><span class="sxs-lookup"><span data-stu-id="f72e9-182">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="f72e9-183">Следующий оператор назначает эту задачу переменной `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-183">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="f72e9-184">Как и в `AccessTheWebAsync`, `startButton_Click` может продолжать работу, которая не зависит от результатов асинхронной задачи (`getLengthTask`), во время ожидания задачи.</span><span class="sxs-lookup"><span data-stu-id="f72e9-184">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="f72e9-185">Следующие выходные строки представляют эту работу:</span><span class="sxs-lookup"><span data-stu-id="f72e9-185">The following output lines represent that work:</span></span>

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="f72e9-186">Выполнение в `startButton_Click` приостанавливается при ожидании `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-186">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="f72e9-187">Следующая инструкция назначения приостанавливает `startButton_Click` до завершения `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-187">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="f72e9-188">На следующем рисунке стрелками показан поток управления из выражения await в `AccessTheWebAsync` к назначению значения `getLengthTask`, за которым следует обычная обработка в методе `startButton_Click` до ожидания `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-188">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="f72e9-189">![Шаг ЧЕТЫРЕ](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="f72e9-189">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="f72e9-190">Шаг ПЯТЬ</span><span class="sxs-lookup"><span data-stu-id="f72e9-190">Step FIVE</span></span>

<span data-ttu-id="f72e9-191">Когда `client.GetStringAsync` уведомляет о завершении, обработка в `AccessTheWebAsync` возобновляется и может продолжаться после оператора await.</span><span class="sxs-lookup"><span data-stu-id="f72e9-191">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="f72e9-192">Следующие строки выходных данных представляют возобновление обработки:</span><span class="sxs-lookup"><span data-stu-id="f72e9-192">The following lines of output represent the resumption of processing:</span></span>

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="f72e9-193">Операнд оператора return, `urlContents.Length`, хранится в задаче, возвращаемой `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-193">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="f72e9-194">Выражение await получает это значение из `getLengthTask` в `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-194">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="f72e9-195">На следующем рисунке показана передача управления после завершения `client.GetStringAsync` (и `getStringTask`).</span><span class="sxs-lookup"><span data-stu-id="f72e9-195">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="f72e9-196">![Шаг ПЯТЬ](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="f72e9-196">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="f72e9-197">`AccessTheWebAsync` выполняется до завершения, и управление возвращается к `startButton_Click`, который ожидает завершения.</span><span class="sxs-lookup"><span data-stu-id="f72e9-197">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="f72e9-198">Шаг ШЕСТЬ</span><span class="sxs-lookup"><span data-stu-id="f72e9-198">Step SIX</span></span>

<span data-ttu-id="f72e9-199">Когда `AccessTheWebAsync` уведомляет о завершении, обработка может продолжаться после оператора await в `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-199">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="f72e9-200">Фактически, на этом работа программы завершается.</span><span class="sxs-lookup"><span data-stu-id="f72e9-200">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="f72e9-201">Приведенные ниже строки выходных данных представляют возобновление обработки в `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="f72e9-201">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="f72e9-202">Выражение await получает из `getLengthTask` целое значение, представляющее операнд оператора return в `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-202">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="f72e9-203">Следующий оператор назначает это значение переменной `contentLength`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-203">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="f72e9-204">На следующем рисунке показано возвращение управления от `AccessTheWebAsync` к `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="f72e9-204">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="f72e9-205">![Шаг ШЕСТЬ](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="f72e9-205">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="f72e9-206">См. также</span><span class="sxs-lookup"><span data-stu-id="f72e9-206">See also</span></span>

- [<span data-ttu-id="f72e9-207">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f72e9-207">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- <span data-ttu-id="f72e9-208">[Async Return Types (Visual Basic)](async-return-types.md) (Типы возвращаемых значений Async (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="f72e9-208">[Async Return Types (Visual Basic)](async-return-types.md)</span></span>
- [<span data-ttu-id="f72e9-209">Пошаговое руководство. Получение доступа к Интернету с помощью модификатора Async и оператора Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f72e9-209">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="f72e9-210">Пример использования Async. Поток управления в асинхронных программах (C# и Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f72e9-210">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
