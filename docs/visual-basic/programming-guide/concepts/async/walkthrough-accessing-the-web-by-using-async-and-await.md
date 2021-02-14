---
description: Дополнительные сведения см. в разделе Пошаговое руководство. доступ к Интернету с помощью Async и await (Visual Basic)
title: Пошаговое руководство. Получение доступа к Интернету с помощью модификатора Async и оператора Await
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 08488d4909e4fbc40cc11213eb293c2693fdec71
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474165"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="337af-103">Пошаговое руководство. Получение доступа к Интернету с помощью модификатора Async и оператора Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="337af-103">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="337af-104">Возможности Async и Await упрощают создание асинхронных программ.</span><span class="sxs-lookup"><span data-stu-id="337af-104">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="337af-105">Можно написать асинхронный код, который выглядит как синхронный, и позволить компилятору обрабатывать трудные функции обратного вызова и продолжения, которые обычно включает асинхронный код.</span><span class="sxs-lookup"><span data-stu-id="337af-105">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="337af-106">Дополнительные сведения о функции Async см. в разделе [Асинхронное программирование с использованием Async и await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="337af-106">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="337af-107">Это пошаговое руководство начинается с создания синхронного приложения Windows Presentation Foundation (WPF), которое суммирует число байтов в списке веб-сайтов.</span><span class="sxs-lookup"><span data-stu-id="337af-107">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="337af-108">Затем в рамках руководства приложение преобразуется в асинхронное решение с помощью новых возможностей.</span><span class="sxs-lookup"><span data-stu-id="337af-108">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="337af-109">Если вы не хотите создавать приложение самостоятельно, вы можете скачать пример "Пример Async. Пошаговое руководство по доступу к интернету (C# и Visual Basic)" со страницы [примеров кода для разработчиков](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="337af-109">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="337af-110">В этом пошаговом руководстве выполняются следующие задачи.</span><span class="sxs-lookup"><span data-stu-id="337af-110">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="337af-111">Создание приложения WPF</span><span class="sxs-lookup"><span data-stu-id="337af-111">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="337af-112">Разработка простого окна MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="337af-112">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="337af-113">Добавление ссылки</span><span class="sxs-lookup"><span data-stu-id="337af-113">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="337af-114">Добавление необходимых операторов Imports</span><span class="sxs-lookup"><span data-stu-id="337af-114">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="337af-115">Создание синхронного приложения</span><span class="sxs-lookup"><span data-stu-id="337af-115">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="337af-116">Тестирование синхронного решения</span><span class="sxs-lookup"><span data-stu-id="337af-116">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="337af-117">Преобразование GetURLContents в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="337af-117">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="337af-118">Преобразование SumPageSizes в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="337af-118">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="337af-119">Преобразование startButton_Click в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="337af-119">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="337af-120">Тестирование асинхронного решения</span><span class="sxs-lookup"><span data-stu-id="337af-120">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="337af-121">Замените метод GetURLContentsAsync методом платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="337af-121">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="337af-122">Полный пример асинхронной работы см. в разделе " [Пример](#example) ".</span><span class="sxs-lookup"><span data-stu-id="337af-122">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="337af-123">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="337af-123">Prerequisites</span></span>

<span data-ttu-id="337af-124">На компьютере должна быть установлена среда Visual Studio 2012 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="337af-124">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="337af-125">Дополнительные сведения см. на странице [загрузки](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="337af-125">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="337af-126">Создание приложения WPF</span><span class="sxs-lookup"><span data-stu-id="337af-126">Create a WPF application</span></span>

1. <span data-ttu-id="337af-127">Запустите Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="337af-127">Start Visual Studio.</span></span>

2. <span data-ttu-id="337af-128">В строке меню выберите **Файл**, **Создать**, **Проект**.</span><span class="sxs-lookup"><span data-stu-id="337af-128">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="337af-129">Откроется диалоговое окно **Новый проект** .</span><span class="sxs-lookup"><span data-stu-id="337af-129">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="337af-130">В области **Установленные шаблоны** выберите Visual Basic, а затем выберите **приложение WPF** в списке типов проектов.</span><span class="sxs-lookup"><span data-stu-id="337af-130">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="337af-131">В текстовом поле **Имя** введите `AsyncExampleWPF` и нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="337af-131">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="337af-132">В **обозревателе решений** появится новый проект.</span><span class="sxs-lookup"><span data-stu-id="337af-132">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="337af-133">Разработка простого окна MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="337af-133">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="337af-134">В редакторе кода Visual Studio перейдите на вкладку **MainWindow.xaml** .</span><span class="sxs-lookup"><span data-stu-id="337af-134">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="337af-135">Если окно **панель элементов** не отображается, откройте меню **вид** и выберите пункт **панель элементов**.</span><span class="sxs-lookup"><span data-stu-id="337af-135">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="337af-136">Добавьте элементы управления **Button** и **TextBox** в окно **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="337af-136">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="337af-137">Выделите элемент управления **TextBox** и в окне **Свойства** задайте указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="337af-137">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="337af-138">Задайте для свойства **Имя** значение `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="337af-138">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="337af-139">Задайте для свойства **Высота** значение 250.</span><span class="sxs-lookup"><span data-stu-id="337af-139">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="337af-140">Задайте для свойства **Ширина** значение 500.</span><span class="sxs-lookup"><span data-stu-id="337af-140">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="337af-141">На вкладке **Текст** укажите моноширинный шрифт, например Lucida Console или Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="337af-141">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="337af-142">Выделите элемент управления **Button** и в окне **Свойства** задайте указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="337af-142">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="337af-143">Задайте для свойства **Имя** значение `startButton`.</span><span class="sxs-lookup"><span data-stu-id="337af-143">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="337af-144">Измените значение свойства **Содержимое** с **Button** на **Start**.</span><span class="sxs-lookup"><span data-stu-id="337af-144">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="337af-145">Поместите текстовое поле и кнопку так, чтобы оба элемента управления отображались в окне **MainWindow**.</span><span class="sxs-lookup"><span data-stu-id="337af-145">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="337af-146">Дополнительные сведения о конструкторе XAML WPF см. в разделе [Создание пользовательского интерфейса с помощью конструктора XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="337af-146">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="337af-147">Добавление ссылки</span><span class="sxs-lookup"><span data-stu-id="337af-147">Add a reference</span></span>

1. <span data-ttu-id="337af-148">В **обозревателе решений** выделите имя проекта.</span><span class="sxs-lookup"><span data-stu-id="337af-148">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="337af-149">В строке меню выберите **Проект**, **Добавить ссылку**.</span><span class="sxs-lookup"><span data-stu-id="337af-149">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="337af-150">Откроется диалоговое окно **Диспетчер ссылок**.</span><span class="sxs-lookup"><span data-stu-id="337af-150">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="337af-151">Вверху диалогового окна убедитесь в том, что проект предназначен для платформы .NET Framework 4.5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="337af-151">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="337af-152">В области **Сборки** выберите **Платформа**, если этот вариант еще не выбран.</span><span class="sxs-lookup"><span data-stu-id="337af-152">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="337af-153">В списке имен установите флажок **System.Net.Http**.</span><span class="sxs-lookup"><span data-stu-id="337af-153">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="337af-154">Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="337af-154">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="337af-155">Добавление необходимых операторов Imports</span><span class="sxs-lookup"><span data-stu-id="337af-155">Add necessary Imports statements</span></span>

1. <span data-ttu-id="337af-156">В **Обозреватель решений** откройте контекстное меню файла MainWindow. XAML. vb и выберите пункт **Просмотреть код**.</span><span class="sxs-lookup"><span data-stu-id="337af-156">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="337af-157">Добавьте следующие `Imports` инструкции в начало файла кода, если они еще не установлены.</span><span class="sxs-lookup"><span data-stu-id="337af-157">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="337af-158">Создание синхронного приложения</span><span class="sxs-lookup"><span data-stu-id="337af-158">Create a synchronous application</span></span>

1. <span data-ttu-id="337af-159">В окне конструктора MainWindow. XAML дважды щелкните кнопку **Пуск** , чтобы создать `startButton_Click` обработчик событий в файле MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="337af-159">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="337af-160">В файле MainWindow. XAML. vb скопируйте следующий код в текст `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="337af-160">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="337af-161">Код вызывает метод, который управляет приложением `SumPageSizes` и выводит на экран сообщение, когда элемент управления возвращается к `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="337af-161">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="337af-162">Код для синхронного решения содержит следующие четыре метода:</span><span class="sxs-lookup"><span data-stu-id="337af-162">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="337af-163">`SumPageSizes`, который получает список URL-адресов веб-страниц из `SetUpURLList`, а затем вызывает метод `GetURLContents` и `DisplayResults` для обработки каждого URL-адреса;</span><span class="sxs-lookup"><span data-stu-id="337af-163">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="337af-164">`SetUpURLList`, который создает и возвращает список веб-адресов;</span><span class="sxs-lookup"><span data-stu-id="337af-164">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="337af-165">`GetURLContents`, который загружает содержимое каждого веб-сайта и возвращает содержимое в виде массива байтов;</span><span class="sxs-lookup"><span data-stu-id="337af-165">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="337af-166">`DisplayResults`, который показывает число байтов в массиве байтов для каждого URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="337af-166">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="337af-167">Скопируйте следующие четыре метода и вставьте их в `startButton_Click` обработчик событий в MainWindow. XAML. vb:</span><span class="sxs-lookup"><span data-stu-id="337af-167">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
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
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="337af-168">Тестирование синхронного решения</span><span class="sxs-lookup"><span data-stu-id="337af-168">Test the synchronous solution</span></span>

1. <span data-ttu-id="337af-169">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="337af-169">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="337af-170">Программа должна выдать результаты, похожие на следующий список:</span><span class="sxs-lookup"><span data-stu-id="337af-170">Output that resembles the following list should appear:</span></span>

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    <span data-ttu-id="337af-171">Обратите внимание, что вывод результатов на экран занимает несколько секунд.</span><span class="sxs-lookup"><span data-stu-id="337af-171">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="337af-172">В течение этого времени поток пользовательского интерфейса заблокирован, пока он ожидает загрузку запрошенных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="337af-172">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="337af-173">Соответственно, после нажатия кнопки **Start** окно нельзя перемещать, разворачивать, сворачивать или даже закрывать.</span><span class="sxs-lookup"><span data-stu-id="337af-173">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="337af-174">Эти действия будут завершаться сбоем, пока не появятся результаты подсчета.</span><span class="sxs-lookup"><span data-stu-id="337af-174">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="337af-175">Если веб-сайт не отвечает, вы не можете определить, на каком сайте произошел сбой.</span><span class="sxs-lookup"><span data-stu-id="337af-175">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="337af-176">Трудно даже остановить ожидание и закрыть программу.</span><span class="sxs-lookup"><span data-stu-id="337af-176">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="337af-177">Преобразование GetURLContents в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="337af-177">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="337af-178">Для преобразования синхронного решения в асинхронное решение лучше начать с `GetURLContents` того, что вызовы <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> метода и <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> метода — это место, где приложение обращается к веб-приложению.</span><span class="sxs-lookup"><span data-stu-id="337af-178">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="337af-179">Платформа .NET Framework упрощает преобразование путем предоставления асинхронных версий этих методов.</span><span class="sxs-lookup"><span data-stu-id="337af-179">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="337af-180">Дополнительные сведения о методах, которые используются в `GetURLContents`, см. в разделе <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="337af-180">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="337af-181">По мере выполнения шагов в этом пошаговом руководстве возникают различные ошибки компилятора.</span><span class="sxs-lookup"><span data-stu-id="337af-181">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="337af-182">Их можно игнорировать и продолжить процедуры пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="337af-182">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="337af-183">Измените метод, который вызывается в третьей строке `GetURLContents` из `GetResponse`, асинхронным методом <xref:System.Net.WebRequest.GetResponseAsync%2A>, основанным на задачах.</span><span class="sxs-lookup"><span data-stu-id="337af-183">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="337af-184">`GetResponseAsync` возвращает значение типа <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="337af-184">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="337af-185">В этом случае *переменная, возвращаемая задачей*, `TResult`, имеет тип <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="337af-185">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="337af-186">Задача является обещанием создать фактический объект `WebResponse` после загрузки запрошенных данных и выполнения задачи до завершения.</span><span class="sxs-lookup"><span data-stu-id="337af-186">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="337af-187">Чтобы получить `WebResponse` значение из задачи, примените оператор [await](../../../language-reference/operators/await-operator.md) к вызову `GetResponseAsync` , как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="337af-187">To retrieve the `WebResponse` value from the task, apply an [Await](../../../language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="337af-188">Оператор `Await` приостанавливает выполнение текущего метода `GetURLContents`, пока не будет завершена ожидаемая задача.</span><span class="sxs-lookup"><span data-stu-id="337af-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="337af-189">На это время управление возвращается вызывающему объекту текущего метода.</span><span class="sxs-lookup"><span data-stu-id="337af-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="337af-190">В этом примере текущим методом является `GetURLContents`, а вызывающим объектом — `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="337af-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="337af-191">После завершения задачи создается обещанный объект `WebResponse` в качестве значения ожидаемой задачи, который присваивается переменной `response`.</span><span class="sxs-lookup"><span data-stu-id="337af-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="337af-192">Предыдущий оператор можно разделить на следующие два оператора для уточнения выполняемых операций.</span><span class="sxs-lookup"><span data-stu-id="337af-192">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="337af-193">Вызов `webReq.GetResponseAsync` возвращает `Task(Of WebResponse)` или `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="337af-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="337af-194">Затем к `Await` задаче применяется оператор для получения `WebResponse` значения.</span><span class="sxs-lookup"><span data-stu-id="337af-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="337af-195">Если асинхронный метод выполняет какие-то действия, это не зависит от выполнения задачи, метод может продолжать свои действия между выполнениями этих двух операторов: после вызова асинхронного метода и перед применением оператора await.</span><span class="sxs-lookup"><span data-stu-id="337af-195">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="337af-196">Примеры см. [в разделе Практическое руководство. Параллельное выполнение нескольких веб-запросов с помощью инструкций Async и await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) и [Практическое руководство. расширение асинхронного пошагового руководства с помощью Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="337af-196">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="337af-197">Из-за добавления оператора `Await` в предыдущем шаге возникает ошибка компилятора.</span><span class="sxs-lookup"><span data-stu-id="337af-197">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="337af-198">Оператор можно использовать только в методах, помеченных модификатором [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="337af-198">The operator can be used only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="337af-199">Пропустите ошибку, повторяя действия по замене вызова `CopyTo` вызовом метода `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="337af-199">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="337af-200">Измените имя метода, вызывающего <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="337af-200">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="337af-201">Метод `CopyTo` или `CopyToAsync` копирует байты в свой аргумент `content` и не возвращает осмысленное значение.</span><span class="sxs-lookup"><span data-stu-id="337af-201">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="337af-202">В синхронной версии вызов метода `CopyTo` — это просто оператор, который не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="337af-202">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="337af-203">Асинхронная версия — `CopyToAsync` — возвращает <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="337af-203">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="337af-204">Задача работает как Task(void) и позволяет ожидать метод.</span><span class="sxs-lookup"><span data-stu-id="337af-204">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="337af-205">Примените `Await` или `await` к вызову `CopyToAsync`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="337af-205">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="337af-206">Предыдущий оператор сокращает две следующие строки кода.</span><span class="sxs-lookup"><span data-stu-id="337af-206">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="337af-207">Все, что остается сделать в `GetURLContents`, — это изменить подпись метода.</span><span class="sxs-lookup"><span data-stu-id="337af-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="337af-208">Оператор можно использовать `Await` только в методах, помеченных модификатором [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="337af-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="337af-209">Добавьте модификатор, чтобы пометить метод как *асинхронный*, как показано в приведенном ниже примере кода.</span><span class="sxs-lookup"><span data-stu-id="337af-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="337af-210">Возвращаемый тип асинхронного метода может иметь только значение <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="337af-210">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="337af-211">В Visual Basic метод должен являться функцией `Function`, возвращающей `Task` или `Task(Of T)`, либо он должен быть `Sub`.</span><span class="sxs-lookup"><span data-stu-id="337af-211">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="337af-212">Как правило, `Sub` метод используется только в асинхронном обработчике событий, где `Sub` требуется.</span><span class="sxs-lookup"><span data-stu-id="337af-212">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="337af-213">В других случаях используется, `Task(T)` Если завершенный метод имеет оператор [return](../../../language-reference/statements/return-statement.md) , возвращающий значение типа T, и используется, `Task` Если завершенный метод не возвращает осмысленное значение.</span><span class="sxs-lookup"><span data-stu-id="337af-213">In other cases, you use `Task(T)` if the completed method has a [Return](../../../language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="337af-214">Дополнительные сведения см. в разделе [асинхронные типы возвращаемых данных (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="337af-214">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

    <span data-ttu-id="337af-215">Метод `GetURLContents` имеет оператор return, который возвращает массив байтов.</span><span class="sxs-lookup"><span data-stu-id="337af-215">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="337af-216">Таким образом, тип возвращаемого значения асинхронной версии — Task(T), где T — массив байтов.</span><span class="sxs-lookup"><span data-stu-id="337af-216">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="337af-217">Внесите следующие изменения в подпись метода.</span><span class="sxs-lookup"><span data-stu-id="337af-217">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="337af-218">Измените тип возвращаемого значения на `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="337af-218">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="337af-219">По соглашению об именовании асинхронные методы имеют имена, заканчивающиеся на Async, поэтому переименуйте метод в `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="337af-219">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="337af-220">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="337af-220">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="337af-221">После внесения этих изменений преобразование `GetURLContents` в асинхронный метод завершено.</span><span class="sxs-lookup"><span data-stu-id="337af-221">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="337af-222">Преобразование SumPageSizes в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="337af-222">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="337af-223">Повторите шаги из предыдущей процедуры для `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="337af-223">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="337af-224">Во-первых, преобразуйте вызов метода `GetURLContents` в вызов асинхронного метода.</span><span class="sxs-lookup"><span data-stu-id="337af-224">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="337af-225">Измените имя вызываемого метода с `GetURLContents` на `GetURLContentsAsync`, если это еще не сделано.</span><span class="sxs-lookup"><span data-stu-id="337af-225">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="337af-226">Примените оператор `Await` к задаче, возвращаемой методом `GetURLContentsAsync`, для получения значения байтового массива.</span><span class="sxs-lookup"><span data-stu-id="337af-226">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="337af-227">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="337af-227">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="337af-228">Предыдущее назначение сокращает две следующие строки кода.</span><span class="sxs-lookup"><span data-stu-id="337af-228">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="337af-229">Внесите следующие изменения в подпись метода.</span><span class="sxs-lookup"><span data-stu-id="337af-229">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="337af-230">Пометьте метод модификатором `Async`.</span><span class="sxs-lookup"><span data-stu-id="337af-230">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="337af-231">Добавьте в имя метода Async.</span><span class="sxs-lookup"><span data-stu-id="337af-231">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="337af-232">В настоящее время нет возвращаемой переменной задачи, т. е `SumPageSizesAsync` . не возвращает значение для t. (метод не имеет `Return` оператора.) Однако метод должен возвращать, `Task` чтобы быть ожидающим.</span><span class="sxs-lookup"><span data-stu-id="337af-232">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="337af-233">Поэтому измените тип метода с `Sub` на `Function` .</span><span class="sxs-lookup"><span data-stu-id="337af-233">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="337af-234">Тип значения, возвращаемого функцией, — `Task`.</span><span class="sxs-lookup"><span data-stu-id="337af-234">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="337af-235">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="337af-235">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="337af-236">Преобразование `SumPageSizes` в `SumPageSizesAsync` завершено.</span><span class="sxs-lookup"><span data-stu-id="337af-236">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="337af-237">Преобразование startButton_Click в асинхронный метод</span><span class="sxs-lookup"><span data-stu-id="337af-237">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="337af-238">В обработчике событий измените имя вызываемого метода с `SumPageSizes` на `SumPageSizesAsync`, если это еще не сделано.</span><span class="sxs-lookup"><span data-stu-id="337af-238">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="337af-239">Поскольку `SumPageSizesAsync` является асинхронным методом, измените код в обработчике событий для ожидания результата.</span><span class="sxs-lookup"><span data-stu-id="337af-239">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="337af-240">Вызов `SumPageSizesAsync` отражает вызов `CopyToAsync` в `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="337af-240">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="337af-241">Вызов возвращает `Task`, а не `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="337af-241">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="337af-242">Как и в предыдущих процедурах, вызов можно преобразовать, используя один или два оператора.</span><span class="sxs-lookup"><span data-stu-id="337af-242">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="337af-243">В следующем примере кода показаны эти изменения.</span><span class="sxs-lookup"><span data-stu-id="337af-243">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="337af-244">Чтобы предотвратить случайное повторное введение операции, добавьте следующий оператор в верхней части `startButton_Click`, чтобы отключить кнопку **Start**.</span><span class="sxs-lookup"><span data-stu-id="337af-244">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="337af-245">Можно снова включить кнопку в конце обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="337af-245">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="337af-246">Дополнительные сведения о повторном входе см. в статье обработка повторного [входа в асинхронных приложениях (Visual Basic)](handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="337af-246">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="337af-247">Наконец, добавьте модификатор `Async` в объявление, чтобы обработчик событий мог ожидать `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="337af-247">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="337af-248">Как правило, имена обработчиков событий не изменяются.</span><span class="sxs-lookup"><span data-stu-id="337af-248">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="337af-249">Тип возвращаемого значения не изменен на, `Task` так как обработчики событий должны быть `Sub` процедурами в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="337af-249">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="337af-250">Преобразование проекта из синхронного в асинхронный завершено.</span><span class="sxs-lookup"><span data-stu-id="337af-250">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="337af-251">Тестирование асинхронного решения</span><span class="sxs-lookup"><span data-stu-id="337af-251">Test the asynchronous solution</span></span>

1. <span data-ttu-id="337af-252">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="337af-252">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="337af-253">Появившиеся результаты должны напоминать результаты синхронного решения.</span><span class="sxs-lookup"><span data-stu-id="337af-253">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="337af-254">Однако имеются следующие различия.</span><span class="sxs-lookup"><span data-stu-id="337af-254">However, notice the following differences.</span></span>

    - <span data-ttu-id="337af-255">Все результаты не отображаются одновременно после завершения обработки.</span><span class="sxs-lookup"><span data-stu-id="337af-255">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="337af-256">Например, обе программы содержат строку в `startButton_Click`, которая очищает текстовое поле.</span><span class="sxs-lookup"><span data-stu-id="337af-256">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="337af-257">Ее цель состоит в том, чтобы очистить текстовое поле между запусками при нажатии кнопки **Start** во второй раз после появления одного набора результатов.</span><span class="sxs-lookup"><span data-stu-id="337af-257">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="337af-258">В синхронной версии текстовое поле очищается перед отображением данных во второй раз, после завершения загрузки и высвобождения потока пользовательского интерфейса для выполнения других операций.</span><span class="sxs-lookup"><span data-stu-id="337af-258">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="337af-259">В асинхронной версии текстовое поле очищается сразу же после нажатия кнопки **Start**.</span><span class="sxs-lookup"><span data-stu-id="337af-259">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="337af-260">И что самое главное, поток пользовательского интерфейса не блокируется во время загрузки.</span><span class="sxs-lookup"><span data-stu-id="337af-260">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="337af-261">Можно перемещать окно или изменять его размер во время загрузки, подсчета и отображения веб-ресурсов.</span><span class="sxs-lookup"><span data-stu-id="337af-261">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="337af-262">Если один из веб-сайтов работает медленно или не отвечает, можно отменить операцию, нажав кнопку **Закрыть** (красный крестик в правом верхнем углу окна).</span><span class="sxs-lookup"><span data-stu-id="337af-262">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="337af-263">Замените метод GetURLContentsAsync методом платформа .NET Framework</span><span class="sxs-lookup"><span data-stu-id="337af-263">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="337af-264">Платформа .NET Framework предоставляет множество асинхронных методов, которые можно использовать.</span><span class="sxs-lookup"><span data-stu-id="337af-264">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="337af-265">Один из них, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> метод, делает то, что нужно для этого пошагового руководства.</span><span class="sxs-lookup"><span data-stu-id="337af-265">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="337af-266">Его можно использовать вместо метода `GetURLContentsAsync`, созданного в предыдущей процедуре.</span><span class="sxs-lookup"><span data-stu-id="337af-266">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="337af-267">Первым шагом является создание <xref:System.Net.Http.HttpClient> объекта в `SumPageSizesAsync` методе.</span><span class="sxs-lookup"><span data-stu-id="337af-267">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="337af-268">Добавьте следующее объявление в начале метода.</span><span class="sxs-lookup"><span data-stu-id="337af-268">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="337af-269">В `SumPageSizesAsync,` замените вызов метода `GetURLContentsAsync` вызовом метода `HttpClient`.</span><span class="sxs-lookup"><span data-stu-id="337af-269">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="337af-270">Удалите или прокомментируйте метод `GetURLContentsAsync`, который вы написали.</span><span class="sxs-lookup"><span data-stu-id="337af-270">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="337af-271">Нажмите клавишу F5, чтобы запустить программу, а затем нажмите кнопку **Start** .</span><span class="sxs-lookup"><span data-stu-id="337af-271">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="337af-272">Поведение этой версии проекта должно соответствовать поведению, которое описывается в процедуре "Тестирование асинхронного решения"; при этом с вашей стороны требуется даже меньше усилий.</span><span class="sxs-lookup"><span data-stu-id="337af-272">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="337af-273">Пример</span><span class="sxs-lookup"><span data-stu-id="337af-273">Example</span></span>

<span data-ttu-id="337af-274">Ниже приведен полный пример преобразованного асинхронного решения, использующего асинхронный `GetURLContentsAsync` метод.</span><span class="sxs-lookup"><span data-stu-id="337af-274">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="337af-275">Обратите внимание, что он очень напоминает исходное синхронное решение.</span><span class="sxs-lookup"><span data-stu-id="337af-275">Notice that it strongly resembles the original, synchronous solution.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
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

<span data-ttu-id="337af-276">Следующий код содержит полный пример решения, использующего метод `HttpClient`, `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="337af-276">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
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

## <a name="see-also"></a><span data-ttu-id="337af-277">См. также</span><span class="sxs-lookup"><span data-stu-id="337af-277">See also</span></span>

- [<span data-ttu-id="337af-278">Пример использования Async. Пошаговое руководство. Обращение к веб-сайтам (C# и Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="337af-278">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="337af-279">Оператор Await</span><span class="sxs-lookup"><span data-stu-id="337af-279">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="337af-280">Асинхронный режим</span><span class="sxs-lookup"><span data-stu-id="337af-280">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="337af-281">Асинхронное программирование с использованием ключевых слов Async и Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="337af-281">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- <span data-ttu-id="337af-282">[Async Return Types (Visual Basic)](async-return-types.md) (Типы возвращаемых значений Async (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="337af-282">[Async Return Types (Visual Basic)](async-return-types.md)</span></span>
- [<span data-ttu-id="337af-283">Асинхронное программирование на основе задач (TAP)</span><span class="sxs-lookup"><span data-stu-id="337af-283">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- <span data-ttu-id="337af-284">[How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md) (Практическое руководство. Расширение пошагового руководства по асинхронным процедурам с использованием метода Task.WhenAll (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="337af-284">[How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)</span></span>
- <span data-ttu-id="337af-285">[How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) (Практическое руководство. Параллельное выполнение нескольких веб-запросов с использованием Async и Await (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="337af-285">[How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span></span>
