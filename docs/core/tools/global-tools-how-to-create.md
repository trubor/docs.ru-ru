---
title: Учебник. Создание средства .NET
description: Сведения о создании средства .NET. Средство — это консольное приложение, которое устанавливается с помощью интерфейса командной строки .NET.
ms.topic: tutorial
ms.date: 12/14/2020
ms.openlocfilehash: dc5cf014336848ff1a3035647a386419653a083b
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633901"
---
# <a name="tutorial-create-a-net-tool-using-the-net-cli"></a><span data-ttu-id="c8b2d-104">Учебник. Создание средства .NET с помощью интерфейса командной строки .NET</span><span class="sxs-lookup"><span data-stu-id="c8b2d-104">Tutorial: Create a .NET tool using the .NET CLI</span></span>

<span data-ttu-id="c8b2d-105">**Эта статья относится к следующему.** ✔️ SDK для .NET Core 2.1 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="c8b2d-105">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="c8b2d-106">В этом учебнике объясняется, как создать и упаковать средство .NET.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-106">This tutorial teaches you how to create and package a .NET tool.</span></span> <span data-ttu-id="c8b2d-107">Интерфейс командной строки .NET позволяет создавать консольное приложение в качестве средства, которое смогут установить и запустить другие пользователи.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-107">The .NET CLI lets you create a console application as a tool, which others can install and run.</span></span> <span data-ttu-id="c8b2d-108">Средства .NET представляют собой пакеты NuGet, которые устанавливаются из командной строки .NET.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-108">.NET tools are NuGet packages that are installed from the .NET CLI.</span></span> <span data-ttu-id="c8b2d-109">Дополнительные сведения см. в статье [Обзор глобальных средств .NET](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="c8b2d-109">For more information about tools, see [.NET tools overview](global-tools.md).</span></span>

<span data-ttu-id="c8b2d-110">Создаваемое средство — это консольное приложение, которое принимает сообщение в качестве входных данных и отображает сообщение вместе со строками текста, которые создают образ робота.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-110">The tool that you'll create is a console application that takes a message as input and displays the message along with lines of text that create the image of a robot.</span></span>

<span data-ttu-id="c8b2d-111">Это первый учебник из серии из трех частей.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-111">This is the first in a series of three tutorials.</span></span> <span data-ttu-id="c8b2d-112">В этом руководстве описано, как создать и упаковать средство.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-112">In this tutorial, you create and package a tool.</span></span> <span data-ttu-id="c8b2d-113">В следующих двух учебниках вы будете [использовать средство в качестве глобального средства](global-tools-how-to-use.md) и [использовать средство в качестве локального средства](local-tools-how-to-use.md).</span><span class="sxs-lookup"><span data-stu-id="c8b2d-113">In the next two tutorials you [use the tool as a global tool](global-tools-how-to-use.md) and [use the tool as a local tool](local-tools-how-to-use.md).</span></span> <span data-ttu-id="c8b2d-114">Процедуры создания средства одинаковы как для глобального так и локального средства.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-114">The procedures for creating a tool are the same whether you use it as a global tool or as a local tool.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8b2d-115">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="c8b2d-115">Prerequisites</span></span>

- <span data-ttu-id="c8b2d-116">[Пакет SDK для .NET 5.0.100](https://dotnet.microsoft.com/download) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-116">[.NET SDK 5.0.100](https://dotnet.microsoft.com/download) or a later version.</span></span>

  <span data-ttu-id="c8b2d-117">В этом руководстве используется пакет SDK для .NET 5.0, однако глобальные средства доступны начиная с пакета SDK для .NET Core версии 2.1.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-117">This tutorial uses .NET SDK 5.0, but global tools are available starting in .NET Core SDK 2.1.</span></span> <span data-ttu-id="c8b2d-118">Глобальные средства доступны в пакете SDK для .NET Core, начиная с версии 3.0.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-118">Local tools are available starting in .NET Core SDK 3.0.</span></span>

- <span data-ttu-id="c8b2d-119">Текстовый редактор или редактор кода по вашему выбору.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-119">A text editor or code editor of your choice.</span></span>

## <a name="create-a-project"></a><span data-ttu-id="c8b2d-120">Создание проекта</span><span class="sxs-lookup"><span data-stu-id="c8b2d-120">Create a project</span></span>

1. <span data-ttu-id="c8b2d-121">Откройте командную строку и создайте папку с именем *репозиторий*.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-121">Open a command prompt and create a folder named *repository*.</span></span>

1. <span data-ttu-id="c8b2d-122">Перейдите в папку *repository* и введите следующую команду:</span><span class="sxs-lookup"><span data-stu-id="c8b2d-122">Navigate to the *repository* folder and enter the following command:</span></span>

   ```dotnetcli
   dotnet new console -n microsoft.botsay -f net5.0
   ```

   <span data-ttu-id="c8b2d-123">Команда создает папку с именем *microsoft.botsay* в папке *repository*.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-123">The command creates a new folder named *microsoft.botsay* under the *repository* folder.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c8b2d-124">В этом руководстве вы создадите средство, предназначенное для .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-124">For this tutorial you create a tool that targets .NET 5.0.</span></span> <span data-ttu-id="c8b2d-125">Чтобы выбрать другую платформу, измените параметр `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-125">To target a different framework, change the `-f|--framework` option.</span></span> <span data-ttu-id="c8b2d-126">Чтобы выбрать несколько платформ, измените элемент `TargetFramework` на элемент `TargetFrameworks` в файле проекта, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="c8b2d-126">To target multiple frameworks, change the `TargetFramework` element to a `TargetFrameworks` element in the project file, as shown in the following example:</span></span>
   >
   > ```xml
   > <Project Sdk="Microsoft.NET.Sdk">
   >   <PropertyGroup>
   >     <OutputType>Exe</OutputType>
   >     <TargetFrameworks>netcoreapp3.1;net5.0</TargetFrameworks>
   >   </PropertyGroup>
   > </Project>
   > ```

1. <span data-ttu-id="c8b2d-127">Перейдите в папку *microsoft.botsay*.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-127">Navigate to the *microsoft.botsay* folder.</span></span>

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a><span data-ttu-id="c8b2d-128">Добавление кода</span><span class="sxs-lookup"><span data-stu-id="c8b2d-128">Add the code</span></span>

1. <span data-ttu-id="c8b2d-129">Откройте файл `Program.cs` с помощью редактора кода.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-129">Open the `Program.cs` file with your code editor.</span></span>

1. <span data-ttu-id="c8b2d-130">Добавьте следующую директиву `using` в начало файла.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-130">Add the following `using` directive to the top of the file:</span></span>

   ```csharp
   using System.Reflection;
   ```

1. <span data-ttu-id="c8b2d-131">Замените этот метод `Main` приведенным ниже кодом, который будет обрабатывать аргументы командной строки для приложения.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-131">Replace the `Main` method with the following code to process the command-line arguments for the application.</span></span>

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   <span data-ttu-id="c8b2d-132">Если аргументы не переданы, отображается короткое справочное сообщение.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-132">If no arguments are passed, a short help message is displayed.</span></span> <span data-ttu-id="c8b2d-133">В противном случае все аргументы объединяются в одну строку и выводятся путем вызова метода `ShowBot`, созданного на следующем шаге.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-133">Otherwise, all of the arguments are concatenated into a single string and printed by calling the `ShowBot` method that you create in the next step.</span></span>

1. <span data-ttu-id="c8b2d-134">Добавьте новый метод с именем `ShowBot`, который принимает один строковый параметр.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-134">Add a new method named `ShowBot` that takes a string parameter.</span></span> <span data-ttu-id="c8b2d-135">Метод выводит сообщение и образ робота, используя строки текста.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-135">The method prints out the message and an image of a robot using lines of text.</span></span>

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. <span data-ttu-id="c8b2d-136">Сохраните изменения.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-136">Save your changes.</span></span>

## <a name="test-the-application"></a><span data-ttu-id="c8b2d-137">Тестирование приложения</span><span class="sxs-lookup"><span data-stu-id="c8b2d-137">Test the application</span></span>

<span data-ttu-id="c8b2d-138">Запустите проект и просмотрите выходные данные.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-138">Run the project and see the output.</span></span> <span data-ttu-id="c8b2d-139">Поработайте с разными вариантами командной строки и сравните результаты.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-139">Try these variations at the command line to see different results:</span></span>

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

<span data-ttu-id="c8b2d-140">Все аргументы после разделителя `--` передаются выполняемому приложению.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-140">All arguments after the `--` delimiter are passed to your application.</span></span>

## <a name="package-the-tool"></a><span data-ttu-id="c8b2d-141">Упаковка средства</span><span class="sxs-lookup"><span data-stu-id="c8b2d-141">Package the tool</span></span>

<span data-ttu-id="c8b2d-142">Прежде чем упаковать и распространять приложение в качестве средства, измените файл проекта.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-142">Before you can pack and distribute the application as a tool, you need to modify the project file.</span></span>

1. <span data-ttu-id="c8b2d-143">Откройте файл *microsoft.botsay.csproj* и добавьте три новых узла XML в конец узла `<PropertyGroup>`:</span><span class="sxs-lookup"><span data-stu-id="c8b2d-143">Open the *microsoft.botsay.csproj* file and add three new XML nodes to the end of the `<PropertyGroup>` node:</span></span>

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   <span data-ttu-id="c8b2d-144">`<ToolCommandName>` — это необязательный элемент, указывающий команду, которая будет вызывать средство после его установки.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-144">`<ToolCommandName>` is an optional element that specifies the command that will invoke the tool after it's installed.</span></span> <span data-ttu-id="c8b2d-145">Если этот элемент не указан, имя команды для средства — это имя файла проекта без расширения *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-145">If this element isn't provided, the command name for the tool is the project file name without the *.csproj* extension.</span></span>

   <span data-ttu-id="c8b2d-146">`<PackageOutputPath>` — это необязательный элемент, который определяет, где будет создан пакет NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-146">`<PackageOutputPath>` is an optional element that determines where the NuGet package will be produced.</span></span> <span data-ttu-id="c8b2d-147">Пакет NuGet будет использоваться в интерфейсе командной строки .NET для установки средства.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-147">The NuGet package is what the .NET CLI uses to install your tool.</span></span>

   <span data-ttu-id="c8b2d-148">Файл проекта выглядит так, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-148">The project file now looks like the following example:</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>net5.0</TargetFramework>

       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>

     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="c8b2d-149">Создайте пакет NuGet с помощью команды [dotnet pack](dotnet-pack.md):</span><span class="sxs-lookup"><span data-stu-id="c8b2d-149">Create a NuGet package by running the [dotnet pack](dotnet-pack.md) command:</span></span>

   ```dotnetcli
   dotnet pack
   ```

   <span data-ttu-id="c8b2d-150">Файл *microsoft.botsay.1.0.0.nupkg* создается в папке, которую указывает значение `<PackageOutputPath>` из файла *microsoft.botsay.csproj*. В нашем примере это папка *./nupkg*.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-150">The *microsoft.botsay.1.0.0.nupkg* file is created in the folder identified by the `<PackageOutputPath>` value from the *microsoft.botsay.csproj* file, which in this example is the *./nupkg* folder.</span></span>

   <span data-ttu-id="c8b2d-151">Если вы решите сделать это средство общедоступным, его можно отправить в `https://www.nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-151">When you want to release a tool publicly, you can upload it to `https://www.nuget.org`.</span></span> <span data-ttu-id="c8b2d-152">Когда это средство станет доступно в NuGet, разработчикам можно будет выполнить его установку, используя команду [dotnet tool install](dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="c8b2d-152">Once the tool is available on NuGet, developers can install the tool by using the [dotnet tool install](dotnet-tool-install.md) command.</span></span> <span data-ttu-id="c8b2d-153">В этом учебнике пакет устанавливается непосредственно из локальной папки *nupkg*, поэтому его не нужно передавать в NuGet.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-153">For this tutorial you install the package directly from the local *nupkg* folder, so there's no need to upload the package to NuGet.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="c8b2d-154">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="c8b2d-154">Troubleshoot</span></span>

<span data-ttu-id="c8b2d-155">Если при выполнении учебника появляется сообщение об ошибке, см. статью [Устранение неполадок при использовании средства .NET](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="c8b2d-155">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8b2d-156">Следующие шаги</span><span class="sxs-lookup"><span data-stu-id="c8b2d-156">Next steps</span></span>

<span data-ttu-id="c8b2d-157">В этом учебнике вы создали консольное приложение и упаковали его в качестве средства.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-157">In this tutorial, you created a console application and packaged it as a tool.</span></span> <span data-ttu-id="c8b2d-158">Чтобы узнать, как использовать это средство в качестве глобального, перейдите к следующему учебнику.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-158">To learn how to use the tool as a global tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="c8b2d-159">[Tutorial: Install and use a .NET Core global tool using the .NET Core CLI](global-tools-how-to-use.md) (Краткое руководство. Установка и использование глобального средства .NET Core с помощью CLI .NET Core)</span><span class="sxs-lookup"><span data-stu-id="c8b2d-159">[Install and use a global tool](global-tools-how-to-use.md)</span></span>

<span data-ttu-id="c8b2d-160">При желании вы можете пропустить учебник по глобальным средствам и перейти непосредственно к учебнику для локальных средств.</span><span class="sxs-lookup"><span data-stu-id="c8b2d-160">If you prefer, you can skip the global tools tutorial and go directly to the local tools tutorial.</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="c8b2d-161">[Tutorial: Install and use a .NET Core local tool using the .NET Core CLI](local-tools-how-to-use.md) (Краткое руководство. Установка и использование локального средства .NET Core с помощью CLI .NET Core)</span><span class="sxs-lookup"><span data-stu-id="c8b2d-161">[Install and use a local tool](local-tools-how-to-use.md)</span></span>
