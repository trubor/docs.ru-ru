---
title: Обновление приложений WPF до .NET 5
description: Используйте помощник по обновлению .NET, чтобы обновить существующее приложение WPF до .NET 5. Помощник по обновлению .NET — это средство CLI, которое помогает перенести приложение с .NET Framework на .NET 5.
author: ardalis
ms.date: 03/08/2021
ms.openlocfilehash: b0c9baa25be6da4e7849f28c875a1d8f5f5a5d07
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604844"
---
# <a name="upgrade-a-wpf-app-to-net-5-with-the-net-upgrade-assistant"></a><span data-ttu-id="9e002-104">Обновление приложения WPF до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="9e002-104">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>

<span data-ttu-id="9e002-105">[Помощник по обновлению .NET](upgrade-assistant-overview.md) — это средство командной строки, которое может помочь при обновлении приложений WPF до .NET 5.</span><span class="sxs-lookup"><span data-stu-id="9e002-105">The [.NET Upgrade Assistant](upgrade-assistant-overview.md) is a command-line tool that can assist with upgrading .NET Framework WPF apps to .NET 5.</span></span> <span data-ttu-id="9e002-106">В этой статье приводится следующее:</span><span class="sxs-lookup"><span data-stu-id="9e002-106">This article provides:</span></span>

- <span data-ttu-id="9e002-107">Демонстрация запуска средства для приложения WPF</span><span class="sxs-lookup"><span data-stu-id="9e002-107">A demonstration of how to run the tool against a .NET Framework WPF app</span></span>
- <span data-ttu-id="9e002-108">Советы по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="9e002-108">Troubleshooting tips</span></span>

## <a name="upgrade-net-framework-wpf-apps"></a><span data-ttu-id="9e002-109">Обновление приложений .NET Framework WPF</span><span class="sxs-lookup"><span data-stu-id="9e002-109">Upgrade .NET Framework WPF apps</span></span>

<span data-ttu-id="9e002-110">В этом разделе демонстрируется запуск помощника по обновлению .NET для вновь созданного приложения WPF, предназначенного для платформы .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="9e002-110">This section demonstrates running the .NET Upgrade Assistant against a newly created WPF app targeting .NET Framework 4.6.1.</span></span> <span data-ttu-id="9e002-111">Дополнительные сведения об установке этого средства см. в разделе [Обзор помощника по обновлению .NET](upgrade-assistant-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9e002-111">For more information on how to install the tool, see [Overview of the .NET Upgrade Assistant](upgrade-assistant-overview.md).</span></span>

### <a name="initial-demo-setup"></a><span data-ttu-id="9e002-112">Начальная настройка для демонстрации</span><span class="sxs-lookup"><span data-stu-id="9e002-112">Initial demo setup</span></span>

<span data-ttu-id="9e002-113">Если вы используете помощник по обновлению .NET для собственного приложения .NET Framework, этот шаг можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="9e002-113">If you're running the .NET Upgrade Assistant against your own .NET Framework app, you can skip this step.</span></span> <span data-ttu-id="9e002-114">Если вы просто хотите посмотреть, как это работает, на этом шаге вы узнаете, как настроить пример проекта .NET WPF.</span><span class="sxs-lookup"><span data-stu-id="9e002-114">If you just want to try it out to see how it works, this step shows you how to set up a sample .NET WPF project to use.</span></span>

<span data-ttu-id="9e002-115">С помощью Visual Studio создайте новое приложение WPF с использованием платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e002-115">Using Visual Studio, create a new WPF App using .NET Framework.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/new-project.png" alt-text="Создание нового проекта WPF в Visual Studio":::

<span data-ttu-id="9e002-117">Присвойте проекту имя **WpfTest**.</span><span class="sxs-lookup"><span data-stu-id="9e002-117">Name the project **WpfTest**.</span></span> <span data-ttu-id="9e002-118">Настройте проект для использования **.NET Framework 4.6.1**.</span><span class="sxs-lookup"><span data-stu-id="9e002-118">Configure the project to use **.NET Framework 4.6.1**.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/configure-project.png" alt-text="Настройка проекта Windows Forms в Visual Studio":::

<span data-ttu-id="9e002-120">Ознакомьтесь с созданным проектом и его файлами, в особенности с файлами проекта.</span><span class="sxs-lookup"><span data-stu-id="9e002-120">Review the created project and its files, especially its project file(s).</span></span>

### <a name="run-upgrade-assistant"></a><span data-ttu-id="9e002-121">Запуск upgrade-assistant</span><span class="sxs-lookup"><span data-stu-id="9e002-121">Run upgrade-assistant</span></span>

<span data-ttu-id="9e002-122">Откройте терминал и перейдите в папку, в которой находится целевой проект или решение.</span><span class="sxs-lookup"><span data-stu-id="9e002-122">Open a terminal and navigate to the folder where the target project or solution is located.</span></span> <span data-ttu-id="9e002-123">Выполните команду `upgrade-assistant`, передав имя целевого проекта (можно выполнить команду из любого места, если путь к файлу проекта является допустимым).</span><span class="sxs-lookup"><span data-stu-id="9e002-123">Run the `upgrade-assistant` command, passing in the name of the project you're targeting (you can run the command from anywhere, as long as the path to the project file is valid).</span></span>

```console
upgrade-assistant .\WpfTest.csproj
```

<span data-ttu-id="9e002-124">Средство запустится и отобразит список действий, которые оно будет выполнять.</span><span class="sxs-lookup"><span data-stu-id="9e002-124">The tool runs and shows you a list of the steps it will do.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/initial-run.png" alt-text="Начальный экран помощника по обновлению .NET":::

<span data-ttu-id="9e002-126">По мере завершения каждого шага средство предоставляет набор команд, позволяющих пользователю применить или пропустить следующий шаг, просмотреть дополнительные сведения, настроить ведение журнала или выйти из процесса.</span><span class="sxs-lookup"><span data-stu-id="9e002-126">As each step is completed, the tool provides a set of commands allowing the user to apply or skip the next step, see more details, configure logging, or exit the process.</span></span> <span data-ttu-id="9e002-127">Если помощник обнаруживает, что шаг не выполняет никаких действий, он автоматически пропускает его и переходит к следующему, пока не достигнет шага, который будет выполнять действия.</span><span class="sxs-lookup"><span data-stu-id="9e002-127">If the tool detects that a step will perform no actions, it will automatically skip that step and continue to the next step until it reaches one that will have actions to perform.</span></span> <span data-ttu-id="9e002-128">Нажатие клавиши ВВОД приведет к выполнению следующего шага, если не были выбраны другие действия.</span><span class="sxs-lookup"><span data-stu-id="9e002-128">Pressing enter will perform the next step if no other selection is made.</span></span>

<span data-ttu-id="9e002-129">В этом примере каждый раз выбирается шаг "применить".</span><span class="sxs-lookup"><span data-stu-id="9e002-129">In this example, the apply step is chosen each time.</span></span> <span data-ttu-id="9e002-130">Первым шагом является резервное копирование проекта.</span><span class="sxs-lookup"><span data-stu-id="9e002-130">The first step is to back up the project.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/backup-project.png" alt-text="Помощник по обновлению .NET: резервное копирование проекта":::

<span data-ttu-id="9e002-132">Помощник просит указать путь для резервной копии или использует значение по умолчанию, которое размещает резервную копию проекта в той же папке с расширением `.backup`.</span><span class="sxs-lookup"><span data-stu-id="9e002-132">The tool prompts for a custom path for the backup, or to use the default, which will place the project backup in the same folder with a `.backup` extension.</span></span> <span data-ttu-id="9e002-133">На следующем шаге происходит преобразование файла проекта в стиль пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="9e002-133">The next step the tool performs is to convert the project file to SDK style.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/convert-project.png" alt-text="Помощник по обновлению .NET: преобразование проекта в стиль пакета SDK":::

<span data-ttu-id="9e002-135">После изменения формата проекта следующим шагом является обновление TFM проекта.</span><span class="sxs-lookup"><span data-stu-id="9e002-135">Once the project format has been updated, the next step is to update the TFM of the project.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-tfm.png" alt-text="Помощник по обновлению .NET: обновление TFM":::

<span data-ttu-id="9e002-137">Затем средство обновляет пакеты NuGet проекта.</span><span class="sxs-lookup"><span data-stu-id="9e002-137">Next, the tool updates the project's NuGet packages.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/update-nuget-packages.png" alt-text="Помощник по обновлению .NET: обновление пакетов NuGet":::

<span data-ttu-id="9e002-139">После обновления пакетов следующим шагом будет добавление файлов шаблонов (если они есть).</span><span class="sxs-lookup"><span data-stu-id="9e002-139">Once the packages are updated, the next step is to add template files, if any.</span></span> <span data-ttu-id="9e002-140">В этом примере отсутствуют файлы шаблонов, которые нужно добавить.</span><span class="sxs-lookup"><span data-stu-id="9e002-140">In this case, there are no template files that need to be added.</span></span> <span data-ttu-id="9e002-141">Этот шаг продолжит выполнение, перенесет файлы конфигурации приложения и обновит исходный код C#, чтобы применить исправления, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="9e002-141">This step continues and migrates app config files and updates C# source to apply fixes, as shown below.</span></span> <span data-ttu-id="9e002-142">Для этого проекта не требуется вносить изменения в файл конфигурации или исходный код, поэтому этот шаг пройдет автоматически.</span><span class="sxs-lookup"><span data-stu-id="9e002-142">This project didn't need any config file or source code changes, so these steps proceeded automatically.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/add-template-files.png" alt-text="Помощник по обновлению .NET: добавление файлов шаблонов и миграция конфигурации":::

<span data-ttu-id="9e002-144">Так как это последний проект, следующий шаг, "переход к следующему проекту", выводит запрос на завершение процесса переноса всего решения.</span><span class="sxs-lookup"><span data-stu-id="9e002-144">Since this is the last project, the next step, "Move to next project", prompts to complete the process of migrating the entire solution.</span></span>

:::image type="content" source="media/upgrade-assistant-wpf-framework/complete-solution.png" alt-text="Помощник по обновлению .NET: завершение обработки решения":::

<span data-ttu-id="9e002-146">После завершения этого процесса перенесенный проект WPF будет выглядеть примерно так:</span><span class="sxs-lookup"><span data-stu-id="9e002-146">Once this process has completed, the migrated WPF project will look something like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net5.0-windows</TargetFramework>
    <OutputType>WinExe</OutputType>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    <UseWPF>true</UseWPF>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
    <PackageReference Include="Microsoft.DotNet.UpgradeAssistant.Extensions.Default.Analyzers" Version="0.2.211942">
      <PrivateAssets>all</PrivateAssets>
    </PackageReference>
    <PackageReference Include="Microsoft.Windows.Compatibility" Version="5.0.2" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="9e002-147">Обратите внимание, что помощник по обновлению .NET также добавляет в проект анализаторы, помогающие продолжить процесс обновления.</span><span class="sxs-lookup"><span data-stu-id="9e002-147">Notice that the .NET Upgrade Assistant also adds analyzers to the project that assist with continuing the upgrade process.</span></span>

## <a name="troubleshooting-tips"></a><span data-ttu-id="9e002-148">Советы по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="9e002-148">Troubleshooting tips</span></span>

<span data-ttu-id="9e002-149">Существует несколько известных проблем, которые могут возникнуть при использовании помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="9e002-149">There are several known problems that can occur when using the .NET Upgrade Assistant.</span></span> <span data-ttu-id="9e002-150">В некоторых случаях эти проблемы связаны со [средством try-convert](https://github.com/dotnet/try-convert), которое помощник по обновлению .NET использует для внутренних целей.</span><span class="sxs-lookup"><span data-stu-id="9e002-150">In some cases, these are problems with the [try-convert tool](https://github.com/dotnet/try-convert) that the .NET Upgrade Assistant uses internally.</span></span> <span data-ttu-id="9e002-151">Это средство часто обновляется для учета большего количества сценариев, поэтому убедитесь, что вы используете последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="9e002-151">This tool is being frequently updated to address more scenarios, so make sure you're using a recent version.</span></span>

- <span data-ttu-id="9e002-152">Средство try-convert должно быть установлено и обновлено по крайней мере до версии _0.7.21201_.</span><span class="sxs-lookup"><span data-stu-id="9e002-152">The try-convert tool must be installed and updated to at least version _0.7.21201_.</span></span>
- <span data-ttu-id="9e002-153">Более ранние версии средства try-convert не поддерживали пользовательские целевые объекты и файлы PROPS.</span><span class="sxs-lookup"><span data-stu-id="9e002-153">Earlier versions of the try-convert tool didn't support custom target or props files.</span></span> <span data-ttu-id="9e002-154">Если не удается выполнить обновление до последней версии, может потребоваться вручную решить эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="9e002-154">If you can't upgrade to the latest version, you may need to manually address these issues.</span></span> <span data-ttu-id="9e002-155">Если целевой файл проекта содержит ссылки на пользовательские целевые объекты или файлы PROPS, эти ссылки необходимо вручную удалить из файла до запуска помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="9e002-155">If the target project file includes references to custom targets or props files, these references may need to be manually deleted from the file before the .NET Upgrade Assistant is run against it.</span></span>

<span data-ttu-id="9e002-156">[В репозитории GitHub этого средства](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) содержатся дополнительные советы по устранению неполадок и известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="9e002-156">[The tool's GitHub repository](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) has more troubleshooting tips and known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e002-157">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="9e002-157">See also</span></span>

- [<span data-ttu-id="9e002-158">Обновление приложения Windows Forms до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="9e002-158">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="9e002-159">Обновление приложения ASP.NET MVC до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="9e002-159">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-aspnetmvc.md)
- [<span data-ttu-id="9e002-160">Обзор помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="9e002-160">Overview of the .NET Upgrade Assistant</span></span>](upgrade-assistant-overview.md)
- [<span data-ttu-id="9e002-161">Репозиторий GitHub помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="9e002-161">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
