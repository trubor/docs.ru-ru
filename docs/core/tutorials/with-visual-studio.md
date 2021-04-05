---
title: Создание консольного приложения .NET в Visual Studio
description: Узнайте, как создать консольное приложение .NET с помощью C# или Visual Basic в Visual Studio.
ms.date: 03/26/2021
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperf-fy21q3
ms.openlocfilehash: e55927080ab30e7a24c54656b7f11a94a023bd65
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105636809"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="f7196-103">Учебник. Создание консольного приложения .NET в Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7196-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="f7196-104">В этом учебнике показано, как создать и запустить консольное приложение .NET с помощью Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="f7196-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7196-105">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="f7196-105">Prerequisites</span></span>

- <span data-ttu-id="f7196-106">[Visual Studio 2019 версии 16.9.2 или более поздней](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) с установленной рабочей нагрузкой **Кроссплатформенная разработка .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="f7196-106">[Visual Studio 2019 version 16.9.2 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="f7196-107">Пакет SDK для .NET 5.0 устанавливается автоматически при выборе этой рабочей нагрузки.</span><span class="sxs-lookup"><span data-stu-id="f7196-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="f7196-108">См. раздел [Установка пакета SDK для .NET с помощью Visual Studio](../install/windows.md#install-with-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f7196-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="f7196-109">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="f7196-109">Create the app</span></span>

<span data-ttu-id="f7196-110">Создайте проект консольного приложения .NET с именем HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="f7196-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="f7196-111">Запустите Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="f7196-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="f7196-112">На начальной странице выберите **Создать проект**.</span><span class="sxs-lookup"><span data-stu-id="f7196-112">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="Кнопка &quot;Создать проект&quot;, выбранная на начальной странице Visual Studio":::

1. <span data-ttu-id="f7196-114">На странице **Создание проекта** введите в поле поиска **консоль**.</span><span class="sxs-lookup"><span data-stu-id="f7196-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="f7196-115">Затем выберите **C#** или **Visual Basic** из списка языков, а затем — **Все платформы** из списка платформ.</span><span class="sxs-lookup"><span data-stu-id="f7196-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="f7196-116">Выберите шаблон **Консольное приложение** и нажмите **Далее**.</span><span class="sxs-lookup"><span data-stu-id="f7196-116">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="Окно &quot;Создание проекта&quot; с выбранными фильтрами":::

   > [!TIP]
   > <span data-ttu-id="f7196-118">Если вы не видите шаблоны .NET, вероятно, у вас не установлена требуемая рабочая нагрузка.</span><span class="sxs-lookup"><span data-stu-id="f7196-118">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="f7196-119">В сообщении **Не удается найти то, что ищете?** выберите ссылку **Установка других средств и компонентов**.</span><span class="sxs-lookup"><span data-stu-id="f7196-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="f7196-120">Откроется Visual Studio Installer.</span><span class="sxs-lookup"><span data-stu-id="f7196-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="f7196-121">Убедитесь, что у вас установлена рабочая нагрузка **Кроссплатформенная разработка .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="f7196-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="f7196-122">В диалоговом окне **Настройка нового проекта** в поле **Имя проекта** введите **HelloWorld**.</span><span class="sxs-lookup"><span data-stu-id="f7196-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="f7196-123">Нажмите кнопку **Далее**.</span><span class="sxs-lookup"><span data-stu-id="f7196-123">Then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="Окно настройки нового проекта с полями имени проекта, расположения и имени решения":::

1. <span data-ttu-id="f7196-125">В диалоговом окне **Дополнительные сведения** выберите **.NET 5.0 (текущая)** , а затем нажмите **Создать**.</span><span class="sxs-lookup"><span data-stu-id="f7196-125">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="Диалоговое окно &quot;Дополнительные сведения&quot;":::

<span data-ttu-id="f7196-127">Этот шаблон создает простое приложение Hello World.</span><span class="sxs-lookup"><span data-stu-id="f7196-127">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="f7196-128">Он вызывает метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> для отображения сообщения "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f7196-128">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="f7196-129">в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="f7196-129">in the console window.</span></span>

<span data-ttu-id="f7196-130">Код шаблона определяет класс `Program` с одним методом `Main`, который принимает в качестве аргумента массив <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="f7196-130">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

<span data-ttu-id="f7196-131">`Main` — точка входа в приложение. Это метод, который автоматически вызывается средой выполнения при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="f7196-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="f7196-132">Все аргументы, предоставленные в командной строке при запуске приложения, доступны через массив *args*.</span><span class="sxs-lookup"><span data-stu-id="f7196-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="f7196-133">Если нужный язык не отображается, измените выбор языка в верхней части страницы.</span><span class="sxs-lookup"><span data-stu-id="f7196-133">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="f7196-134">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="f7196-134">Run the app</span></span>

1. <span data-ttu-id="f7196-135">Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы запустить программу без отладки.</span><span class="sxs-lookup"><span data-stu-id="f7196-135">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="f7196-136">Откроется окно консоли с текстом "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="f7196-136">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="f7196-137">на экране.</span><span class="sxs-lookup"><span data-stu-id="f7196-137">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="Окно консоли с приложением Hello World и надписью &quot;Чтобы продолжить, нажмите любую клавишу&quot;":::

1. <span data-ttu-id="f7196-139">Для закрытия консольного окна нажмите любую клавишу.</span><span class="sxs-lookup"><span data-stu-id="f7196-139">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="f7196-140">Улучшение приложения</span><span class="sxs-lookup"><span data-stu-id="f7196-140">Enhance the app</span></span>

<span data-ttu-id="f7196-141">Давайте расширим приложение. Теперь у пользователя будет запрашиваться имя, которое затем будет отображаться с датой и временем.</span><span class="sxs-lookup"><span data-stu-id="f7196-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="f7196-142">В *Program.cs* или *Program.vb* замените содержимое метода `Main` (строка, вызывающая `Console.WriteLine`) следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="f7196-142">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="f7196-143">Этот код отображает запрос в окне консоли и ожидает, чтобы пользователь ввел строку текста и нажал клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f7196-143">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="f7196-144">Приложение сохраняет полученную строку в переменной с именем `name`.</span><span class="sxs-lookup"><span data-stu-id="f7196-144">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="f7196-145">Оно также получает значение свойства <xref:System.DateTime.Now?displayProperty=nameWithType>, которое содержит текущее локальное время, и присваивает его переменной с именем `currentDate`.</span><span class="sxs-lookup"><span data-stu-id="f7196-145">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `currentDate`.</span></span> <span data-ttu-id="f7196-146">Затем оно отображает эти значения в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="f7196-146">And it displays these values in the console window.</span></span> <span data-ttu-id="f7196-147">Наконец, приложение выводит запрос в окне консоли и вызывает метод <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> для ожидания ввода данных пользователем.</span><span class="sxs-lookup"><span data-stu-id="f7196-147">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="f7196-148"><xref:System.Environment.NewLine> — это независимый от платформы и языка способ для представления разрыва строки.</span><span class="sxs-lookup"><span data-stu-id="f7196-148"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="f7196-149">Его альтернативами являются `\n` в C# и `vbCrLf` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7196-149">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="f7196-150">Знак доллара (`$`) перед строкой позволяет вставить такие выражения, как имена переменных, в фигурные скобки в строке.</span><span class="sxs-lookup"><span data-stu-id="f7196-150">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="f7196-151">Значение выражения вставляется в строку вместо выражения.</span><span class="sxs-lookup"><span data-stu-id="f7196-151">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="f7196-152">Такой синтаксис называется [интерполированными строками](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="f7196-152">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="f7196-153">Нажмите клавиши <kbd>CTRL</kbd>+<kbd>F5</kbd>, чтобы запустить программу без отладки.</span><span class="sxs-lookup"><span data-stu-id="f7196-153">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="f7196-154">В ответ на приглашение в командной строке введите имя и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f7196-154">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="Окно консоли с измененными выходными данными программы":::

1. <span data-ttu-id="f7196-156">Для закрытия консольного окна нажмите любую клавишу.</span><span class="sxs-lookup"><span data-stu-id="f7196-156">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f7196-157">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="f7196-157">Additional resources</span></span>

- [<span data-ttu-id="f7196-158">Текущие выпуски и выпуски с долгосрочной поддержкой</span><span class="sxs-lookup"><span data-stu-id="f7196-158">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="f7196-159">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="f7196-159">Next steps</span></span>

<span data-ttu-id="f7196-160">В этом учебнике показано, как создать консольное приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="f7196-160">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="f7196-161">В следующем учебнике описывается отладка приложения.</span><span class="sxs-lookup"><span data-stu-id="f7196-161">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f7196-162">Отладка консольного приложения .NET с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7196-162">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
