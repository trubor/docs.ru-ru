---
title: Создание консольного приложения .NET в Visual Studio Code
description: Узнайте, как создать консольное приложение .NET с помощью Visual Studio Code и .NET CLI.
ms.date: 11/17/2020
ms.openlocfilehash: 51e5a897985af7576de03659efdd8520cb8e58e6
ms.sourcegitcommit: 1d3af230ec30d8d061be7a887f6ba38a530c4ece
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2021
ms.locfileid: "102511870"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="4e4ce-103">Учебник. Создание консольного приложения .NET в Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e4ce-103">Tutorial: Create a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="4e4ce-104">В этом учебнике показано, как создать и запустить консольное приложение .NET с помощью Visual Studio Code и .NET CLI.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-104">This tutorial shows how to create and run a .NET console application by using Visual Studio Code and the .NET CLI.</span></span> <span data-ttu-id="4e4ce-105">Задачи проекта, такие как создание, компиляция и запуск проекта, выполняются с помощью .NET CLI,</span><span class="sxs-lookup"><span data-stu-id="4e4ce-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET CLI.</span></span> <span data-ttu-id="4e4ce-106">поэтому вы можете следовать этому руководству, используя при желании другой редактор кода и выполняя команды в терминале.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4e4ce-107">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="4e4ce-107">Prerequisites</span></span>

1. <span data-ttu-id="4e4ce-108">Установленная платформа [Visual Studio Code](https://code.visualstudio.com/) с [расширением C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span><span class="sxs-lookup"><span data-stu-id="4e4ce-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="4e4ce-109">См. сведения об [установке расширений Visual Studio Code из Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span><span class="sxs-lookup"><span data-stu-id="4e4ce-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="4e4ce-110">[Пакет SDK для .NET 5.0 или более поздней версии](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="4e4ce-110">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="4e4ce-111">Создание приложения</span><span class="sxs-lookup"><span data-stu-id="4e4ce-111">Create the app</span></span>

<span data-ttu-id="4e4ce-112">Создайте проект консольного приложения .NET с именем HelloWorld.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-112">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="4e4ce-113">Запустите Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="4e4ce-114">В главном меню выберите **Файл** > **Открыть папку** (в macOS выберите **File** > **Open...**  (Файл > Открыть)).</span><span class="sxs-lookup"><span data-stu-id="4e4ce-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="4e4ce-115">В диалоговом окне **Открытие папки** создайте папку *HelloWorld* и щелкните **Выбрать папку** (в macOS щелкните **Open** (Открыть)).</span><span class="sxs-lookup"><span data-stu-id="4e4ce-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="4e4ce-116">Имя папки по умолчанию преобразуется в имя проекта и имя пространства имен.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="4e4ce-117">Вы добавите код позже в этом учебнике. Предполагается, что пространство имен проекта — `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="4e4ce-118">Откройте **терминал** в Visual Studio Code, выбрав в основном меню пункт **Вид** > **Терминал**.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="4e4ce-119">Откроется окно **Терминал** с командной строкой в папке *HelloWorld*.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="4e4ce-120">В **окне терминала** введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="4e4ce-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="4e4ce-121">Этот шаблон создает простое приложение Hello World.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="4e4ce-122">Он вызывает метод <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> для вывода ":::no-loc text="Hello World!":::" в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display ":::no-loc text="Hello World!":::" in the console window.</span></span>

<span data-ttu-id="4e4ce-123">Код шаблона определяет класс `Program` с одним методом `Main`, который принимает в качестве аргумента массив <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-123">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="4e4ce-124">`Main` — точка входа в приложение. Это метод, который автоматически вызывается средой выполнения при запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="4e4ce-125">Все аргументы, предоставленные в командной строке при запуске приложения, доступны через массив *args*.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4e4ce-126">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="4e4ce-126">Run the app</span></span>

<span data-ttu-id="4e4ce-127">Выполните следующие команды в **окне терминала**:</span><span class="sxs-lookup"><span data-stu-id="4e4ce-127">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="4e4ce-128">В программе отобразится сообщение "Hello World!",</span><span class="sxs-lookup"><span data-stu-id="4e4ce-128">The program displays "Hello World!"</span></span> <span data-ttu-id="4e4ce-129">после чего она завершится.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-129">and ends.</span></span>

![Команда dotnet run](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="4e4ce-131">Улучшение приложения</span><span class="sxs-lookup"><span data-stu-id="4e4ce-131">Enhance the app</span></span>

<span data-ttu-id="4e4ce-132">Давайте расширим приложение. Теперь у пользователя будет запрашиваться имя, которое затем будет отображаться с датой и временем.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-132">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="4e4ce-133">Откройте файл *Program.cs*, щелкнув его.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-133">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="4e4ce-134">Когда вы в первый раз открываете файл C# в Visual Studio Code, в редакторе загружается [OmniSharp](https://www.omnisharp.net/).</span><span class="sxs-lookup"><span data-stu-id="4e4ce-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![Откройте файл Program.cs](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="4e4ce-136">Когда в Visual Studio Code будет предложено добавить недостающие ресурсы для сборки и отладки приложения, выберите **Да**.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-136">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![Предупреждение о недостающих ресурсах](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="4e4ce-138">В *Program.cs* замените содержимое метода `Main` (строка, вызывающая `Console.WriteLine`) следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="4e4ce-138">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="4e4ce-139">Этот код отображает запрос в окне консоли и ожидает, чтобы пользователь ввел строку текста и нажал клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-139">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="4e4ce-140">Приложение сохраняет полученную строку в переменной с именем `name`.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="4e4ce-141">Оно также получает значение свойства <xref:System.DateTime.Now?displayProperty=nameWithType>, которое содержит текущее локальное время, и присваивает его переменной с именем `date`.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="4e4ce-142">Затем оно отображает эти значения в окне консоли.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-142">And it displays these values in the console window.</span></span> <span data-ttu-id="4e4ce-143">Наконец, приложение выводит запрос в окне консоли и вызывает метод <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> для ожидания ввода данных пользователем.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-143">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="4e4ce-144"><xref:System.Environment.NewLine> — это независимый от платформы и языка способ для представления разрыва строки.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-144"><xref:System.Environment.NewLine> is a platform-independent and language-independent way to represent a line break.</span></span> <span data-ttu-id="4e4ce-145">Его альтернативами являются `\n` в C# и `vbCrLf` в Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-145">Alternatives are `\n` in C# and `vbCrLf` in Visual Basic.</span></span>

   <span data-ttu-id="4e4ce-146">Знак доллара (`$`) перед строкой позволяет вставить такие выражения, как имена переменных, в фигурные скобки в строке.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-146">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="4e4ce-147">Значение выражения вставляется в строку вместо выражения.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-147">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="4e4ce-148">Такой синтаксис называется [интерполированными строками](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="4e4ce-148">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="4e4ce-149">Сохраните изменения.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-149">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="4e4ce-150">В Visual Studio Code необходимо явно сохранить изменения.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-150">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="4e4ce-151">В отличие от Visual Studio, изменения файлов не сохраняются автоматически при сборке и запуске приложения.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-151">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="4e4ce-152">Запустите программу еще раз:</span><span class="sxs-lookup"><span data-stu-id="4e4ce-152">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="4e4ce-153">В ответ на приглашение в командной строке введите имя и нажмите клавишу <kbd>ВВОД</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-153">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="Окно терминала с измененными выходными данными программы":::

1. <span data-ttu-id="4e4ce-155">Нажмите любую клавишу для выхода из программы.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-155">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="4e4ce-156">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="4e4ce-156">Additional resources</span></span>

- <span data-ttu-id="4e4ce-157">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview) (Настройка Visual Studio Code)</span><span class="sxs-lookup"><span data-stu-id="4e4ce-157">[Setting up Visual Studio Code](https://code.visualstudio.com/docs/setup/setup-overview)</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e4ce-158">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="4e4ce-158">Next steps</span></span>

<span data-ttu-id="4e4ce-159">В этом учебнике показано, как создать консольное приложение .NET.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-159">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="4e4ce-160">В следующем учебнике описывается отладка приложения.</span><span class="sxs-lookup"><span data-stu-id="4e4ce-160">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4e4ce-161">Отладка консольного приложения .NET с помощью Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4e4ce-161">Debug a .NET console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
