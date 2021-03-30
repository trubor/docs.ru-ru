---
title: Развертывание приложений .NET Core с помощью Visual Studio
description: Научитесь развертыванию приложений .NET Core с помощью Visual Studio
ms.date: 09/03/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4fe2663f7fd428035aaca61e4e47bd2bf2a4f391
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872916"
---
# <a name="deploy-net-core-apps-with-visual-studio"></a><span data-ttu-id="b6c3b-103">Развертывание приложений .NET Core с помощью Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6c3b-103">Deploy .NET Core apps with Visual Studio</span></span>

<span data-ttu-id="b6c3b-104">Приложение .NET Core можно развернуть как *развертывание, зависящее от платформы*, которое содержит двоичные файлы приложений, но зависит от наличия .NET Core в целевой системе, или как *автономное развертывание*, которое содержит и приложение, и двоичные файлы .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-104">You can deploy a .NET Core application either as a *framework-dependent deployment*, which includes your application binaries but depends on the presence of .NET Core on the target system, or as a *self-contained deployment*, which includes both your application and .NET Core binaries.</span></span> <span data-ttu-id="b6c3b-105">Общие сведения о развертывании приложений .NET Core см. в разделе [Развертывание приложений .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-105">For an overview of .NET Core application deployment, see [.NET Core Application Deployment](index.md).</span></span>

<span data-ttu-id="b6c3b-106">В разделах ниже содержатся сведения об использовании Microsoft Visual Studio для создания следующих типов развертывания:</span><span class="sxs-lookup"><span data-stu-id="b6c3b-106">The following sections show how to use Microsoft Visual Studio to create the following kinds of deployments:</span></span>

- <span data-ttu-id="b6c3b-107">развертывание, зависящее от платформы;</span><span class="sxs-lookup"><span data-stu-id="b6c3b-107">Framework-dependent deployment</span></span>
- <span data-ttu-id="b6c3b-108">развертывание, зависящее от платформы, с зависимостями сторонних разработчиков;</span><span class="sxs-lookup"><span data-stu-id="b6c3b-108">Framework-dependent deployment with third-party dependencies</span></span>
- <span data-ttu-id="b6c3b-109">автономное развертывание;</span><span class="sxs-lookup"><span data-stu-id="b6c3b-109">Self-contained deployment</span></span>
- <span data-ttu-id="b6c3b-110">Автономное развертывание с зависимостями сторонних разработчиков</span><span class="sxs-lookup"><span data-stu-id="b6c3b-110">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="b6c3b-111">Сведения об использовании Visual Studio для разработки приложений .NET Core см. в статье [Зависимости и требования для .NET Core](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-111">For information on using Visual Studio to develop .NET Core applications, see [.NET Core dependencies and requirements](../install/windows.md).</span></span>

## <a name="framework-dependent-deployment"></a><span data-ttu-id="b6c3b-112">развертывание, зависящее от платформы;</span><span class="sxs-lookup"><span data-stu-id="b6c3b-112">Framework-dependent deployment</span></span>

<span data-ttu-id="b6c3b-113">Если развертывание, зависящее от платформы, не содержит зависимостей сторонних разработчиков, то необходимо просто выполнить сборку, протестировать и опубликовать приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-113">Deploying a framework-dependent deployment with no third-party dependencies simply involves building, testing, and publishing the app.</span></span> <span data-ttu-id="b6c3b-114">Проиллюстрируем этот процесс на примере простого приложения, написанного на языке C#.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-114">A simple example written in C# illustrates the process.</span></span>

1. <span data-ttu-id="b6c3b-115">Создание проекта.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-115">Create the project.</span></span>

   <span data-ttu-id="b6c3b-116">Выберите **Файл** > **Создать** > **Проект**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-116">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="b6c3b-117">В диалоговом окне **Создать проект** разверните категории проекта своего языка (C# или Visual Basic) на панели типов проектов **Установлено**, выберите **.NET Core**, а затем выберите шаблон **Консольное приложение (.NET Core)** на центральной панели.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-117">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="b6c3b-118">В поле **Имя** введите имя проекта, например "FDD".</span><span class="sxs-lookup"><span data-stu-id="b6c3b-118">Enter a project name, such as "FDD", in the **Name** text box.</span></span> <span data-ttu-id="b6c3b-119">Нажмите кнопку **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-119">Select the **OK** button.</span></span>

1. <span data-ttu-id="b6c3b-120">Добавление исходного кода приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-120">Add the application's source code.</span></span>

   <span data-ttu-id="b6c3b-121">Откройте файл *Program.cs* или *Program.vb* в редакторе и замените автоматически созданный код приведенным ниже кодом.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-121">Open the *Program.cs* or *Program.vb* file in the editor and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="b6c3b-122">Он выводит запрос на ввод текста и отображает отдельные слова, введенные пользователем.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-122">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="b6c3b-123">Для разделения слов во введенном тексте в нем используется регулярное выражение `\w+`.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-123">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. <span data-ttu-id="b6c3b-124">Создание отладочной сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-124">Create a Debug build of your app.</span></span>

   <span data-ttu-id="b6c3b-125">Выберите **Сборка** > **Собрать решение**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-125">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="b6c3b-126">Также можно скомпилировать и выполнить отладочную сборку приложения, выбрав **Отладка** > **Начать отладку**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-126">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span>

1. <span data-ttu-id="b6c3b-127">Разверните приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-127">Deploy your app.</span></span>

   <span data-ttu-id="b6c3b-128">Отладив и протестировав программу, создайте файлы, которые будут развертываться с приложением.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-128">After you've debugged and tested the program, create the files to be deployed with your app.</span></span> <span data-ttu-id="b6c3b-129">Для публикации из Visual Studio выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-129">To publish from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="b6c3b-130">На панели инструментов измените конфигурацию решения с **Отладка** на **Выпуск**, чтобы собрать версию выпуска (а не отладочную версию) приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-130">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="b6c3b-131">Щелкните правой кнопкой мыши проект (не решение) в **обозревателе решений** и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-131">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="b6c3b-132">На вкладке **Публикация** выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-132">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="b6c3b-133">Visual Studio записывает файлы, которые составляют приложение, в локальную файловую систему.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-133">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="b6c3b-134">Теперь на вкладке **Публикация** отображается один профиль — **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-134">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="b6c3b-135">Параметры конфигурации профиля отображаются на вкладке в разделе **Сводка**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-135">The profile's configuration settings are shown in the **Summary** section of the tab.</span></span>

   <span data-ttu-id="b6c3b-136">Итоговые файлы помещаются в каталог с именем `Publish` в Windows и `publish` в системах Unix, который находится в подкаталоге каталога проекта *.\bin\release\netcoreapp2.1*.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-136">The resulting files are placed in a directory named `Publish` on Windows and `publish` on Unix systems that is in a subdirectory of your project's *.\bin\release\netcoreapp2.1* subdirectory.</span></span>

<span data-ttu-id="b6c3b-137">Помимо файлов приложения, процесс публикации создает файл базы данных программы (PDB), который содержит отладочную информацию о приложении.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-137">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b6c3b-138">Файл используется в основном для отладки исключений.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-138">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b6c3b-139">Его можно не упаковывать вместе с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-139">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b6c3b-140">Однако его следует сохранить на случай, если потребуется выполнить отладку сборки выпуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-140">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b6c3b-141">Любым способом разверните полный набор файлов приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-141">Deploy the complete set of application files in any way you like.</span></span> <span data-ttu-id="b6c3b-142">Например, их можно упаковать в ZIP-файл, использовать простую команду `copy` или развернуть их с помощью любого установочного пакета на ваш выбор.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-142">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span> <span data-ttu-id="b6c3b-143">После установки пользователи могут выполнять приложение с помощью команды `dotnet`, указав имя файла приложения, например `dotnet fdd.dll`.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-143">Once installed, users can then execute your application by using the `dotnet` command and providing the application filename, such as `dotnet fdd.dll`.</span></span>

<span data-ttu-id="b6c3b-144">Помимо двоичных файлов приложения, установщик должен либо включать в себя установщик общей платформы, либо проверять наличие платформы в процессе установки приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-144">In addition to the application binaries, your installer should also either bundle the shared framework installer or check for it as a prerequisite as part of the application installation.</span></span>  <span data-ttu-id="b6c3b-145">Установка общей платформы требует наличия прав администратор или root, так как она производится на уровне всего компьютера.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-145">Installation of the shared framework requires Administrator/root access since it is machine-wide.</span></span>

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a><span data-ttu-id="b6c3b-146">Развертывание, зависящее от платформы, с зависимостями сторонних разработчиков</span><span class="sxs-lookup"><span data-stu-id="b6c3b-146">Framework-dependent deployment with third-party dependencies</span></span>

<span data-ttu-id="b6c3b-147">Для зависящего от платформы развертывания с одной или более зависимостями сторонних разработчиков требуется, чтобы зависимости были доступны в проекте.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-147">Deploying a framework-dependent deployment with one or more third-party dependencies requires that any dependencies be available to your project.</span></span> <span data-ttu-id="b6c3b-148">Перед сборкой приложения следует выполнить два дополнительных действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-148">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="b6c3b-149">С помощью **диспетчера пакетов NuGet** добавьте ссылку на пакет NuGet в проект, а если пакет еще недоступен в системе, установите его.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-149">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="b6c3b-150">Чтобы открыть диспетчер пакетов, последовательно выберите **Сервис** > **Диспетчер пакетов NuGet** > **Управление пакетами NuGet для решения**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-150">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="b6c3b-151">Убедитесь, что в вашей системе установлены зависимости от сторонних разработчиков (например, `Newtonsoft.Json`), если это не так, установите их.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-151">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="b6c3b-152">На вкладке **Установленные** перечислены пакеты NuGet, установленные в системе.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-152">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="b6c3b-153">Если `Newtonsoft.Json` отсутствует в списке, откройте вкладку **Обзор** и введите "Newtonsoft.Json" в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-153">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="b6c3b-154">Выберите `Newtonsoft.Json` и в области справа выберите проект, прежде чем нажать кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-154">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="b6c3b-155">Если `Newtonsoft.Json` уже установлен в системе, добавьте его в проект, выбрав проект в правой области на вкладке **Управление пакетами для решения**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-155">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="b6c3b-156">Переносимость зависящего от платформы развертывания с зависимостями сторонних разработчиков напрямую зависит от переносимости этих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-156">A framework-dependent deployment with third-party dependencies is only as portable as its third-party dependencies.</span></span> <span data-ttu-id="b6c3b-157">Например, если библиотека стороннего разработчика поддерживает только Mac OS, приложение нельзя перенести в системы Windows.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-157">For example, if a third-party library only supports macOS, the app isn't portable to Windows systems.</span></span> <span data-ttu-id="b6c3b-158">Это происходит, если зависимость стороннего разработчика сама зависит от машинного кода.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-158">This happens if the third-party dependency itself depends on native code.</span></span> <span data-ttu-id="b6c3b-159">Хорошим примером является [сервер Kestrel](/aspnet/core/fundamentals/servers/kestrel), требующий собственной зависимости от [libuv](https://github.com/libuv/libuv).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-159">A good example of this is [Kestrel server](/aspnet/core/fundamentals/servers/kestrel), which requires a native dependency on [libuv](https://github.com/libuv/libuv).</span></span> <span data-ttu-id="b6c3b-160">Когда зависящее от платформы развертывание создается для приложения с таким типом зависимости стороннего разработчика, опубликованные выходные данные содержат папку для каждого [идентификатора среды выполнения (RID)](../rid-catalog.md), поддерживаемого зависимостью (и имеющегося в ее пакете NuGet).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-160">When an FDD is created for an application with this kind of third-party dependency, the published output contains a folder for each [Runtime Identifier (RID)](../rid-catalog.md) that the native dependency supports (and that exists in its NuGet package).</span></span>

## <a name="self-contained-deployment-without-third-party-dependencies"></a><a name="simpleSelf"></a> <span data-ttu-id="b6c3b-161">Автономное развертывание без зависимостей сторонних разработчиков</span><span class="sxs-lookup"><span data-stu-id="b6c3b-161">Self-contained deployment without third-party dependencies</span></span>

<span data-ttu-id="b6c3b-162">Выполнение автономного развертывания без зависимостей сторонних разработчиков предполагает создание проекта, изменение файла *csproj*, сборку, тестирование и публикацию приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-162">Deploying a self-contained deployment with no third-party dependencies involves creating the project, modifying the *csproj* file, building, testing, and publishing the app.</span></span> <span data-ttu-id="b6c3b-163">Проиллюстрируем этот процесс на примере простого приложения, написанного на языке C#.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-163">A simple example written in C# illustrates the process.</span></span> <span data-ttu-id="b6c3b-164">Вы начнете с создания, программирования и тестирования проекта, как и при развертывании, зависимом от платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-164">You begin by creating, coding, and testing your project just as you would a framework-dependent deployment:</span></span>

1. <span data-ttu-id="b6c3b-165">Создание проекта.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-165">Create the project.</span></span>

   <span data-ttu-id="b6c3b-166">Выберите **Файл** > **Создать** > **Проект**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-166">Select **File** > **New** > **Project**.</span></span> <span data-ttu-id="b6c3b-167">В диалоговом окне **Создать проект** разверните категории проекта своего языка (C# или Visual Basic) на панели типов проектов **Установлено**, выберите **.NET Core**, а затем выберите шаблон **Консольное приложение (.NET Core)** на центральной панели.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-167">In the **New Project** dialog, expand your language's (C# or Visual Basic) project categories in the **Installed** project types pane, choose **.NET Core**, and then select the **Console App (.NET Core)** template in the center pane.</span></span> <span data-ttu-id="b6c3b-168">В поле **Имя** введите имя проекта, например "SCD", а затем нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-168">Enter a project name, such as "SCD", in the **Name** text box, and select the **OK** button.</span></span>

1. <span data-ttu-id="b6c3b-169">Добавление исходного кода приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-169">Add the application's source code.</span></span>

   <span data-ttu-id="b6c3b-170">Откройте файл *Program.cs* или *Program.vb* в редакторе и замените автоматически созданный код приведенным ниже кодом.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-170">Open the *Program.cs* or *Program.vb* file in your editor, and replace the autogenerated code with the following code.</span></span> <span data-ttu-id="b6c3b-171">Он выводит запрос на ввод текста и отображает отдельные слова, введенные пользователем.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-171">It prompts the user to enter text and displays the individual words entered by the user.</span></span> <span data-ttu-id="b6c3b-172">Для разделения слов во введенном тексте в нем используется регулярное выражение `\w+`.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-172">It uses the regular expression `\w+` to separate the words in the input text.</span></span>

   [!code-csharp[deployment#1](./snippets/deploy-with-vs/csharp/deployment-example.cs)]
   [!code-vb[deployment#1](./snippets/deploy-with-vs/vb/deployment-example.vb)]

1. <span data-ttu-id="b6c3b-173">Определите, хотите ли вы использовать инвариантный режим глобализации.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-173">Determine whether you want to use globalization invariant mode.</span></span>

   <span data-ttu-id="b6c3b-174">Особенно в том случае, если приложение предназначено для Linux, вы можете уменьшить размер развертывания, используя преимущества [инвариантного режима глобализации](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-174">Particularly if your app targets Linux, you can reduce the total size of your deployment by taking advantage of [globalization invariant mode](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).</span></span> <span data-ttu-id="b6c3b-175">Инвариантный режим глобализации подходит для приложений, которые не имеют глобальных параметров и могут использовать соглашения о форматировании, соглашения о регистре, сравнение строк и порядок сортировки для [инвариантного языка и региональных параметров](xref:System.Globalization.CultureInfo.InvariantCulture).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-175">Globalization invariant mode is useful for applications that are not globally aware and that can use the formatting conventions, casing conventions, and string comparison and sort order of the [invariant culture](xref:System.Globalization.CultureInfo.InvariantCulture).</span></span>

   <span data-ttu-id="b6c3b-176">Чтобы включить инвариантный режим, щелкните правой кнопкой мыши проект (не решение) в **обозревателе решений** и выберите **Изменить SCD.csproj** или **Изменить SCD.vbproj**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-176">To enable invariant mode, right-click on your project (not the solution) in **Solution Explorer**, and select **Edit SCD.csproj** or **Edit SCD.vbproj**.</span></span> <span data-ttu-id="b6c3b-177">Затем добавьте следующие выделенные строки в файл:</span><span class="sxs-lookup"><span data-stu-id="b6c3b-177">Then add the following highlighted lines to the file:</span></span>

   [!code-xml[globalization-invariant-mode](./snippets/deploy-with-vs/xml/invariant.csproj?highlight=7-9)]

1. <span data-ttu-id="b6c3b-178">Создание отладочной сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-178">Create a Debug build of your application.</span></span>

   <span data-ttu-id="b6c3b-179">Выберите **Сборка** > **Собрать решение**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-179">Select **Build** > **Build Solution**.</span></span> <span data-ttu-id="b6c3b-180">Также можно скомпилировать и выполнить отладочную сборку приложения, выбрав **Отладка** > **Начать отладку**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-180">You can also compile and run the Debug build of your application by selecting **Debug** > **Start Debugging**.</span></span> <span data-ttu-id="b6c3b-181">Этот шаг отладки позволяет выявить проблемы в приложении, когда оно выполняется на вашей платформе.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-181">This debugging step lets you identify problems with your application when it's running on your host platform.</span></span> <span data-ttu-id="b6c3b-182">Его все равно придется тестировать на каждой целевой платформе.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-182">You still will have to test it on each of your target platforms.</span></span>

   <span data-ttu-id="b6c3b-183">Если вы включили инвариантный режим глобализации, обязательно проверьте, подходит ли отсутствие данных, зависящих от языка и региональных параметров, для вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-183">If you've enabled globalization invariant mode, be particularly sure to test whether the absence of culture-sensitive data is suitable for your application.</span></span>

<span data-ttu-id="b6c3b-184">Когда вы закончите отладку, вы можете опубликовать автономное развертывание.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-184">Once you've finished debugging, you can publish your self-contained deployment:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="b6c3b-185">Visual Studio 15.6 и более ранние версии</span><span class="sxs-lookup"><span data-stu-id="b6c3b-185">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

<span data-ttu-id="b6c3b-186">Создание после отладки и тестирования программы файлов, которые будут развертываться с приложением, для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-186">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

<span data-ttu-id="b6c3b-187">Для публикации приложения из Visual Studio выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-187">To publish your app from Visual Studio, do the following:</span></span>

1. <span data-ttu-id="b6c3b-188">Определение платформ, для которых будет предназначено приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-188">Define the platforms that your app will target.</span></span>

   1. <span data-ttu-id="b6c3b-189">Щелкните правой кнопкой мыши проект (не решение) в **обозревателе решений** и выберите **Изменить SCD.csproj**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-189">Right-click on your project (not the solution) in **Solution Explorer** and select **Edit SCD.csproj**.</span></span>

   1. <span data-ttu-id="b6c3b-190">В разделе `<PropertyGroup>` файла *csproj* создайте тег `<RuntimeIdentifiers>`, определяющий платформы, для которых предназначено приложение, и укажите идентификатор среды выполнения (RID) каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-190">Create a `<RuntimeIdentifiers>` tag in the `<PropertyGroup>` section of your *csproj* file that defines the platforms your app targets, and specify the runtime identifier (RID) of each platform that you target.</span></span> <span data-ttu-id="b6c3b-191">Для разделения идентификаторов RID необходимо добавлять точку с запятой.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-191">You also need to add a semicolon to separate the RIDs.</span></span> <span data-ttu-id="b6c3b-192">Список идентификаторов сред выполнения см. в [каталоге идентификаторов сред выполнения](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b6c3b-192">See [Runtime identifier catalog](../rid-catalog.md) for a list of runtime identifiers.</span></span>

   <span data-ttu-id="b6c3b-193">Например, приведенный ниже пример указывает, что приложение выполняется в 64-разрядной операционной системе Windows 10 и в 64-разрядной операционной системе OS X 10.11.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-193">For example, the following example indicates that the app runs on 64-bit Windows 10 operating systems and the 64-bit OS X Version 10.11 operating system.</span></span>

   ```xml
   <PropertyGroup>
      <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
   </PropertyGroup>
   ```

   <span data-ttu-id="b6c3b-194">Элемент `<RuntimeIdentifiers>` можно переносить в другие группы `<PropertyGroup>` в пределах файла *csproj*.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-194">The `<RuntimeIdentifiers>` element can go into any `<PropertyGroup>` that you have in your *csproj* file.</span></span> <span data-ttu-id="b6c3b-195">Полный пример файла *csproj* будет приведен далее в этом разделе.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-195">A complete sample *csproj* file appears later in this section.</span></span>

1. <span data-ttu-id="b6c3b-196">Опубликуйте приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-196">Publish your app.</span></span>

   <span data-ttu-id="b6c3b-197">Создание после отладки и тестирования программы файлов, которые будут развертываться с приложением, для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-197">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span>

   <span data-ttu-id="b6c3b-198">Для публикации приложения из Visual Studio выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-198">To publish your app from Visual Studio, do the following:</span></span>

      1. <span data-ttu-id="b6c3b-199">На панели инструментов измените конфигурацию решения с **Отладка** на **Выпуск**, чтобы собрать версию выпуска (а не отладочную версию) приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-199">Change the solution configuration from **Debug** to **Release** on the toolbar to build a Release (rather than a Debug) version of your app.</span></span>

      1. <span data-ttu-id="b6c3b-200">Щелкните правой кнопкой мыши проект (не решение) в **обозревателе решений** и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-200">Right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

      1. <span data-ttu-id="b6c3b-201">На вкладке **Публикация** выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-201">In the **Publish** tab, select **Publish**.</span></span> <span data-ttu-id="b6c3b-202">Visual Studio записывает файлы, которые составляют приложение, в локальную файловую систему.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-202">Visual Studio writes the files that comprise your application to the local file system.</span></span>

      1. <span data-ttu-id="b6c3b-203">Теперь на вкладке **Публикация** отображается один профиль — **FolderProfile**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-203">The **Publish** tab now shows a single profile, **FolderProfile**.</span></span> <span data-ttu-id="b6c3b-204">Параметры конфигурации профиля отображаются на вкладке в разделе **Сводка**. Параметр **Целевая среда выполнения** определяет, какая среда выполнения была опубликована, а параметр **Целевое расположение** определяет, куда были записаны файлы автономного развертывания.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-204">The profile's configuration settings are shown in the **Summary** section of the tab. **Target Runtime** identifies which runtime has been published, and **Target Location** identifies where the files for the self-contained deployment were written.</span></span>

      1. <span data-ttu-id="b6c3b-205">По умолчанию Visual Studio записывает все опубликованные файлы в один каталог.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-205">Visual Studio by default writes all published files to a single directory.</span></span> <span data-ttu-id="b6c3b-206">Для удобства рекомендуется создать отдельные профили для каждой целевой среды выполнения и размещать опубликованные файлы в каталоге для определенной платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-206">For convenience, it's best to create separate profiles for each target runtime and to place published files in a platform-specific directory.</span></span> <span data-ttu-id="b6c3b-207">Это предполагает создание отдельного профиля публикации для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-207">This involves creating a separate publishing profile for each target platform.</span></span> <span data-ttu-id="b6c3b-208">Теперь выполните повторную сборку приложения для каждой платформы следующим образом.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-208">So now rebuild the application for each platform by doing the following:</span></span>

         1. <span data-ttu-id="b6c3b-209">Выберите **Создать новый профиль** в диалоговом окне **Публикация**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-209">Select **Create new profile** in the **Publish** dialog.</span></span>

         1. <span data-ttu-id="b6c3b-210">В диалоговом окне **Выберите целевой объект публикации** измените расположение в поле **Выберите папку** на *bin\Release\PublishOutput\win10-x64*.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-210">In the **Pick a publish target** dialog, change the **Choose a folder** location to *bin\Release\PublishOutput\win10-x64*.</span></span> <span data-ttu-id="b6c3b-211">Нажмите кнопку **ОК**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-211">Select **OK**.</span></span>

         1. <span data-ttu-id="b6c3b-212">В списке профилей выберите новый профиль (**FolderProfile1**) и убедитесь, что параметр **Целевая среда выполнения** имеет значение `win10-x64`.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-212">Select the new profile (**FolderProfile1**) in the list of profiles, and make sure that the **Target Runtime** is `win10-x64`.</span></span> <span data-ttu-id="b6c3b-213">В противном случае выберите **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-213">If it isn't, select **Settings**.</span></span> <span data-ttu-id="b6c3b-214">В диалоговом окне **Параметры профиля** измените значение параметра **Целевая среда выполнения** на `win10-x64`, а затем нажмите кнопку **Сохранить**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-214">In the **Profile Settings** dialog, change the **Target Runtime** to `win10-x64` and select **Save**.</span></span> <span data-ttu-id="b6c3b-215">В противном случае нажмите кнопку **Отмена**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-215">Otherwise, select **Cancel**.</span></span>

         1. <span data-ttu-id="b6c3b-216">Выберите **Опубликовать**, чтобы опубликовать приложение для 64-разрядных платформ Windows 10.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-216">Select **Publish** to publish your app for 64-bit Windows 10 platforms.</span></span>

         1. <span data-ttu-id="b6c3b-217">Выполните приведенные выше шаги еще раз, чтобы создать профиль для платформы `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-217">Follow the previous steps again to create a profile for the `osx.10.11-x64` platform.</span></span> <span data-ttu-id="b6c3b-218">Параметр **Целевое расположение** имеет значение *bin\Release\PublishOutput\osx.10.11-x64*, а параметр **Целевая среда выполнения** — `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-218">The **Target Location** is *bin\Release\PublishOutput\osx.10.11-x64*, and the **Target Runtime** is `osx.10.11-x64`.</span></span> <span data-ttu-id="b6c3b-219">Visual Studio присваивает этому профилю имя **FolderProfile2**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-219">The name that Visual Studio assigns to this profile is **FolderProfile2**.</span></span>

      <span data-ttu-id="b6c3b-220">Каждое целевое расположение содержит полный набор файлов (как файлов приложения, так и всех файлов .NET Core), необходимых для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-220">Each target location contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="b6c3b-221">Помимо файлов приложения, процесс публикации создает файл базы данных программы (PDB), который содержит отладочную информацию о приложении.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-221">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b6c3b-222">Файл используется в основном для отладки исключений.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-222">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b6c3b-223">Его можно не упаковывать вместе с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-223">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b6c3b-224">Однако его следует сохранить на случай, если потребуется выполнить отладку сборки выпуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-224">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b6c3b-225">Разверните опубликованные файлы любым способом.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-225">Deploy the published files in any way you like.</span></span> <span data-ttu-id="b6c3b-226">Например, их можно упаковать в ZIP-файл, использовать простую команду `copy` или развернуть их с помощью любого установочного пакета на ваш выбор.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-226">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="b6c3b-227">Ниже приведено полное содержимое файла *csproj* для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-227">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="b6c3b-228">Visual Studio 15.7 и более поздние версии</span><span class="sxs-lookup"><span data-stu-id="b6c3b-228">Visual Studio 15.7 and later</span></span>](#tab/vs157)

<span data-ttu-id="b6c3b-229">Создание после отладки и тестирования программы файлов, которые будут развертываться с приложением, для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-229">After you've debugged and tested the program, create the files to be deployed with your app for each platform that it targets.</span></span> <span data-ttu-id="b6c3b-230">Это предполагает создание отдельного профиля для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-230">This involves creating a separate profile for each target platform.</span></span>

<span data-ttu-id="b6c3b-231">Для каждой платформы, для которой предназначено приложение, выполните следующие действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-231">For each platform that your application targets, do the following:</span></span>

1. <span data-ttu-id="b6c3b-232">Создайте профиль для целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-232">Create a profile for your target platform.</span></span>

   <span data-ttu-id="b6c3b-233">Если это первый созданный профиль, щелкните правой кнопкой мыши проект (не решение) в **обозревателе решений** и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-233">If this is the first profile you've created, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   <span data-ttu-id="b6c3b-234">Если вы уже создали профиль, щелкните правой кнопкой мыши проект, чтобы открыть диалоговое окно **Опубликовать**, если оно еще не открыто.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-234">If you've already created a profile, right-click on the project to open the **Publish** dialog if it isn't already open.</span></span> <span data-ttu-id="b6c3b-235">Затем выберите **Создать профиль**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-235">Then select **New Profile**.</span></span>

   <span data-ttu-id="b6c3b-236">Откроется диалоговое окно **Выбрать целевой объект для публикации**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-236">The **Pick a Publish Target** dialog box opens.</span></span>

1. <span data-ttu-id="b6c3b-237">Выберите расположение, где Visual Studio опубликует приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-237">Select the location where Visual Studio publishes your application.</span></span>

   <span data-ttu-id="b6c3b-238">Если вы публикуете приложение только на одной платформе, можно принять значение по умолчанию в текстовом поле **Выбрать папку**. Вы опубликуете зависимое от платформы развертывание приложения в каталоге *\<project-directory>\bin\Release\netcoreapp2.1\publish*.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-238">If you're only publishing to a single platform, you can accept the default value in the **Choose a folder** text box; this publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish* directory.</span></span>

   <span data-ttu-id="b6c3b-239">Если публикация выполняется для нескольких платформ, добавьте строку, которая указывает целевую платформу.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-239">If you're publishing to more than one platform, append a string that identifies the target platform.</span></span> <span data-ttu-id="b6c3b-240">Например, если добавить строку "linux" в путь к файлу, Visual Studio опубликует развертывание приложения, зависимое от платформы, в каталоге *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux*.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-240">For example, if you append the string "linux" to the file path, Visual Studio publishes the framework-dependent deployment of your application to the *\<project-directory>\bin\Release\netcoreapp2.1\publish\linux* directory.</span></span>

1. <span data-ttu-id="b6c3b-241">Создайте профиль, щелкнув значок раскрывающегося списка рядом с полем **Опубликовать** и нажав **Создать профиль**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-241">Create the profile by selecting the drop-down list icon next to the **Publish** button and selecting **Create Profile**.</span></span> <span data-ttu-id="b6c3b-242">Затем нажмите на кнопку **Создать профиль**, чтобы создать профиль.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-242">Then select the **Create Profile** button to create the profile.</span></span>

1. <span data-ttu-id="b6c3b-243">Укажите, что вы публикуете автономное развертывание, и определите платформу, для которой будет предназначено приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-243">Indicate that you are publishing a self-contained deployment and define a platform that your app will target.</span></span>

   1. <span data-ttu-id="b6c3b-244">В диалоговом окне **Опубликовать** нажмите на ссылку **Настройка**, чтобы открыть диалоговое окно **Параметры профиля**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-244">In the **Publish** dialog, select the **Configure** link to open the **Profile Settings** dialog.</span></span>

   1. <span data-ttu-id="b6c3b-245">Выберите **Автономное** в списке **Режим развертывания**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-245">Select **Self-contained** in the **Deployment Mode** list box.</span></span>

   1. <span data-ttu-id="b6c3b-246">В списке **Целевая среда выполнения** выберите одну из платформ, для которой предназначено приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-246">In the **Target Runtime** list box, select one of the platforms that your application targets.</span></span>

   1. <span data-ttu-id="b6c3b-247">Нажмите **Сохранить**, чтобы принять изменения и закрыть диалоговое окно.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-247">Select **Save** to accept your changes and close the dialog.</span></span>

1. <span data-ttu-id="b6c3b-248">Укажите имя профиля.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-248">Name your profile.</span></span>

   1. <span data-ttu-id="b6c3b-249">Выберите **Действия** > **Переименовать профиль**, чтобы указать имя профиля.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-249">Select **Actions** > **Rename Profile** to name your profile.</span></span>

   2. <span data-ttu-id="b6c3b-250">Выберите для профиля имя, которое указывает на целевую платформу, а затем нажмите \**Сохранить*.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-250">Assign your profile a name that identifies the target platform, then select \**Save*.</span></span>

<span data-ttu-id="b6c3b-251">Повторите эти шаги, чтобы определить любые дополнительные целевые платформы, для которых предназначено приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-251">Repeat these steps to define any additional target platforms that your application targets.</span></span>

<span data-ttu-id="b6c3b-252">Вы настроили профили и готовы опубликовать приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-252">You've configured your profiles and are now ready to publish your app.</span></span> <span data-ttu-id="b6c3b-253">Выполните указанные ниже действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-253">To do this:</span></span>

   1. <span data-ttu-id="b6c3b-254">Если диалоговое окно **Опубликовать** еще не открыто, щелкните правой кнопкой мыши проект (не решение) в **обозревателе решений** и выберите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-254">If the **Publish** window isn't currently open, right-click on the project (not the solution) in **Solution Explorer** and select **Publish**.</span></span>

   2. <span data-ttu-id="b6c3b-255">Выберите профиль, который вы хотите опубликовать, а затем нажмите **Опубликовать**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-255">Select the profile that you'd like to publish, then select **Publish**.</span></span> <span data-ttu-id="b6c3b-256">Повторите это действие для каждого профиля.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-256">Do this for each profile to be published.</span></span>

   <span data-ttu-id="b6c3b-257">Каждое целевое расположение (в нашем примере это bin\release\netcoreapp2.1\publish\\*profile-name*) содержит полный набор файлов (как файлов приложения, так и всех файлов .NET Core), необходимых для запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-257">Each target location (in the case of our example, bin\release\netcoreapp2.1\publish\\*profile-name* contains the complete set of files (both your app files and all .NET Core files) needed to launch your app.</span></span>

<span data-ttu-id="b6c3b-258">Помимо файлов приложения, процесс публикации создает файл базы данных программы (PDB), который содержит отладочную информацию о приложении.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-258">Along with your application's files, the publishing process emits a program database (.pdb) file that contains debugging information about your app.</span></span> <span data-ttu-id="b6c3b-259">Файл используется в основном для отладки исключений.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-259">The file is useful primarily for debugging exceptions.</span></span> <span data-ttu-id="b6c3b-260">Его можно не упаковывать вместе с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-260">You can choose not to package it with your application's files.</span></span> <span data-ttu-id="b6c3b-261">Однако его следует сохранить на случай, если потребуется выполнить отладку сборки выпуска приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-261">You should, however, save it in the event that you want to debug the Release build of your app.</span></span>

<span data-ttu-id="b6c3b-262">Разверните опубликованные файлы любым способом.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-262">Deploy the published files in any way you like.</span></span> <span data-ttu-id="b6c3b-263">Например, их можно упаковать в ZIP-файл, использовать простую команду `copy` или развернуть их с помощью любого установочного пакета на ваш выбор.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-263">For example, you can package them in a Zip file, use a simple `copy` command, or deploy them with any installation package of your choice.</span></span>

<span data-ttu-id="b6c3b-264">Ниже приведено полное содержимое файла *csproj* для этого проекта.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-264">The following is the complete *csproj* file for this project.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="b6c3b-265">Кроме того, Visual Studio создает отдельный профиль публикации (\*.pubxml) для каждой целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-265">In addition, Visual Studio creates a separate publishing profile (\*.pubxml) for each platform that you target.</span></span> <span data-ttu-id="b6c3b-266">Например, файл для профиля linux (linux.pubxml) выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="b6c3b-266">For example, the file for our linux profile (linux.pubxml) appears as follows:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--
https://go.microsoft.com/fwlink/?LinkID=208121.
-->
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <PublishProtocol>FileSystem</PublishProtocol>
    <Configuration>Release</Configuration>
    <Platform>Any CPU</Platform>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <PublishDir>bin\Release\netcoreapp2.1\publish\linux</PublishDir>
    <RuntimeIdentifier>win-x86</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <_IsPortable>false</_IsPortable>
  </PropertyGroup>
</Project>
```

---

## <a name="self-contained-deployment-with-third-party-dependencies"></a><span data-ttu-id="b6c3b-267">Автономное развертывание с зависимостями сторонних разработчиков</span><span class="sxs-lookup"><span data-stu-id="b6c3b-267">Self-contained deployment with third-party dependencies</span></span>

<span data-ttu-id="b6c3b-268">Выполнение автономного развертывания с одной или несколькими зависимостями сторонних разработчиков предполагает добавление этих зависимостей.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-268">Deploying a self-contained deployment with one or more third-party dependencies involves adding the dependencies.</span></span> <span data-ttu-id="b6c3b-269">Перед сборкой приложения следует выполнить два дополнительных действия.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-269">The following additional steps are required before you can build your app:</span></span>

1. <span data-ttu-id="b6c3b-270">С помощью **диспетчера пакетов NuGet** добавьте ссылку на пакет NuGet в проект, а если пакет еще недоступен в системе, установите его.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-270">Use the **NuGet Package Manager** to add a reference to a NuGet package to your project; and if the package is not already available on your system, install it.</span></span> <span data-ttu-id="b6c3b-271">Чтобы открыть диспетчер пакетов, последовательно выберите **Сервис** > **Диспетчер пакетов NuGet** > **Управление пакетами NuGet для решения**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-271">To open the package manager, select **Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**.</span></span>

1. <span data-ttu-id="b6c3b-272">Убедитесь, что в вашей системе установлены зависимости от сторонних разработчиков (например, `Newtonsoft.Json`), если это не так, установите их.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-272">Confirm that your third-party dependencies (for example, `Newtonsoft.Json`) are installed on your system and, if they aren't, install them.</span></span> <span data-ttu-id="b6c3b-273">На вкладке **Установленные** перечислены пакеты NuGet, установленные в системе.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-273">The **Installed** tab lists NuGet packages installed on your system.</span></span> <span data-ttu-id="b6c3b-274">Если `Newtonsoft.Json` отсутствует в списке, откройте вкладку **Обзор** и введите "Newtonsoft.Json" в поле поиска.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-274">If `Newtonsoft.Json` is not listed there, select the **Browse** tab and enter "Newtonsoft.Json" in the search box.</span></span> <span data-ttu-id="b6c3b-275">Выберите `Newtonsoft.Json` и в области справа выберите проект, прежде чем нажать кнопку **Установить**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-275">Select `Newtonsoft.Json` and, in the right pane, select your project before selecting **Install**.</span></span>

1. <span data-ttu-id="b6c3b-276">Если `Newtonsoft.Json` уже установлен в системе, добавьте его в проект, выбрав проект в правой области на вкладке **Управление пакетами для решения**.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-276">If `Newtonsoft.Json` is already installed on your system, add it to your project by selecting your project in the right pane of the **Manage Packages for Solution** tab.</span></span>

<span data-ttu-id="b6c3b-277">Ниже приведено полное содержимое файла *csproj* для этого проекта:</span><span class="sxs-lookup"><span data-stu-id="b6c3b-277">The following is the complete *csproj* file for this project:</span></span>

# <a name="visual-studio-156-and-earlier"></a>[<span data-ttu-id="b6c3b-278">Visual Studio 15.6 и более ранние версии</span><span class="sxs-lookup"><span data-stu-id="b6c3b-278">Visual Studio 15.6 and earlier</span></span>](#tab/vs156)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

# <a name="visual-studio-157-and-later"></a>[<span data-ttu-id="b6c3b-279">Visual Studio 15.7 и более поздние версии</span><span class="sxs-lookup"><span data-stu-id="b6c3b-279">Visual Studio 15.7 and later</span></span>](#tab/vs157)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

---

<span data-ttu-id="b6c3b-280">При развертывании приложения все зависимости сторонних разработчиков, используемые в нем, также содержатся в файлах приложения.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-280">When you deploy your application, any third-party dependencies used in your app are also contained with your application files.</span></span> <span data-ttu-id="b6c3b-281">Библиотеки сторонних разработчиков не требуются в системе, в которой выполняется приложение.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-281">Third-party libraries aren't required on the system on which the app is running.</span></span>

<span data-ttu-id="b6c3b-282">Автономное развертывание с библиотекой стороннего разработчика возможно только на платформах, которые поддерживаются этой библиотекой.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-282">You can only deploy a self-contained deployment with a third-party library to platforms supported by that library.</span></span> <span data-ttu-id="b6c3b-283">Это похоже на наличие сторонних зависимостей с собственными зависимостями в развертывании, зависящем от платформы, где собственные зависимости существуют в целевой платформе, только если они были установлены в ней ранее.</span><span class="sxs-lookup"><span data-stu-id="b6c3b-283">This is similar to having third-party dependencies with native dependencies in your framework-dependent deployment, where the native dependencies won't exist on the target platform unless they were previously installed there.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6c3b-284">См. также</span><span class="sxs-lookup"><span data-stu-id="b6c3b-284">See also</span></span>

- [<span data-ttu-id="b6c3b-285">Развертывание приложений .NET Core</span><span class="sxs-lookup"><span data-stu-id="b6c3b-285">.NET Core Application Deployment</span></span>](index.md)
- [<span data-ttu-id="b6c3b-286">Каталог идентификаторов сред выполнения (RID) в .NET Core</span><span class="sxs-lookup"><span data-stu-id="b6c3b-286">.NET Core Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
