---
title: Обновление приложений ASP.NET MVC до .NET 5
description: Используйте помощник по обновлению .NET, чтобы обновить существующее приложение ASP.NET MVC до .NET 5. Помощник по обновлению .NET — это средство CLI, которое помогает перенести приложение с .NET Framework на .NET 5.
author: ardalis
ms.date: 02/25/2021
ms.openlocfilehash: 0c9af9e12b78df7c4a2aaed18155f7ee9f02870d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2021
ms.locfileid: "102108361"
---
# <a name="upgrade-an-aspnet-mvc-app-to-net-5-with-the-net-upgrade-assistant"></a><span data-ttu-id="e70ca-104">Обновление приложения ASP.NET MVC до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="e70ca-104">Upgrade an ASP.NET MVC App to .NET 5 with the .NET Upgrade Assistant</span></span>

<span data-ttu-id="e70ca-105">[Помощник по обновлению .NET](upgrade-assistant-overview.md) — это средство командной строки, которое может помочь при обновлении приложений ASP.NET MVC до .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e70ca-105">The [.NET Upgrade Assistant](upgrade-assistant-overview.md) is a command-line tool that can assist with upgrading .NET Framework ASP.NET MVC apps to .NET 5.</span></span> <span data-ttu-id="e70ca-106">В этой статье приводится следующее:</span><span class="sxs-lookup"><span data-stu-id="e70ca-106">This article provides:</span></span>

* <span data-ttu-id="e70ca-107">Демонстрация запуска средства для приложения ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="e70ca-107">A demonstration of how to run the tool against a .NET Framework ASP.NET MVC app</span></span>
* <span data-ttu-id="e70ca-108">Советы по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="e70ca-108">Troubleshooting tips</span></span>

## <a name="upgrade-net-framework-aspnet-mvc-apps"></a><span data-ttu-id="e70ca-109">Обновление приложений .NET Framework ASP.NET MVC</span><span class="sxs-lookup"><span data-stu-id="e70ca-109">Upgrade .NET Framework ASP.NET MVC apps</span></span>

<span data-ttu-id="e70ca-110">В этом разделе демонстрируется запуск помощника по обновлению .NET для вновь созданного приложения ASP.NET MVC, предназначенного для платформы .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="e70ca-110">This section demonstrates running the .NET Upgrade Assistant against a newly created ASP.NET MVC app targeting .NET Framework 4.6.1.</span></span> <span data-ttu-id="e70ca-111">Дополнительные сведения об установке этого средства см. в разделе [Обзор помощника по обновлению .NET](upgrade-assistant-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e70ca-111">For more information on how to install the tool, see [Overview of the .NET Upgrade Assistant](upgrade-assistant-overview.md).</span></span>

### <a name="initial-demo-setup"></a><span data-ttu-id="e70ca-112">Начальная настройка для демонстрации</span><span class="sxs-lookup"><span data-stu-id="e70ca-112">Initial demo setup</span></span>

<span data-ttu-id="e70ca-113">Если вы используете помощник по обновлению .NET для собственного приложения .NET Framework, этот шаг можно пропустить.</span><span class="sxs-lookup"><span data-stu-id="e70ca-113">If you're running the .NET Upgrade Assistant against your own .NET Framework app, you can skip this step.</span></span> <span data-ttu-id="e70ca-114">Если вы просто хотите посмотреть, как это работает, на данном шаге показано, как настроить пример проекта ASP.NET MVC и веб-API (.NET Framework).</span><span class="sxs-lookup"><span data-stu-id="e70ca-114">If you just want to try it out to see how it works, this step shows you how to set up a sample ASP.NET MVC and Web API (.NET Framework) project to use.</span></span>

<span data-ttu-id="e70ca-115">С помощью Visual Studio создайте новый проект веб-приложения ASP.NET с использованием .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e70ca-115">Using Visual Studio, create a new ASP.NET Web Application project using .NET Framework.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/new-project.png" alt-text="Создание проекта веб-приложения ASP.NET в Visual Studio":::

<span data-ttu-id="e70ca-117">Назовите проект **AspNetMvcTest**.</span><span class="sxs-lookup"><span data-stu-id="e70ca-117">Name the project **AspNetMvcTest**.</span></span> <span data-ttu-id="e70ca-118">Настройте проект для использования **.NET Framework 4.6.1**.</span><span class="sxs-lookup"><span data-stu-id="e70ca-118">Configure the project to use **.NET Framework 4.6.1**.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/configure-project.png" alt-text="Настройка проекта ASP.NET в Visual Studio":::

<span data-ttu-id="e70ca-120">В следующем диалоговом окне выберите приложение **MVC**, а затем нажмите кнопку **Создать**.</span><span class="sxs-lookup"><span data-stu-id="e70ca-120">In the next dialog, choose **MVC** application, then select **Create**.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/create-mvc-webapi.png" alt-text="Создание проекта ASP.NET MVC в Visual Studio":::

<span data-ttu-id="e70ca-122">Ознакомьтесь с созданным проектом и его файлами, в особенности с файлами проекта.</span><span class="sxs-lookup"><span data-stu-id="e70ca-122">Review the created project and its files, especially its project file(s).</span></span>

### <a name="run-upgrade-assistant"></a><span data-ttu-id="e70ca-123">Запуск upgrade-assistant</span><span class="sxs-lookup"><span data-stu-id="e70ca-123">Run upgrade-assistant</span></span>

<span data-ttu-id="e70ca-124">Откройте терминал и перейдите в папку, в которой находится целевой проект или решение.</span><span class="sxs-lookup"><span data-stu-id="e70ca-124">Open a terminal and navigate to the folder where the target project or solution is located.</span></span> <span data-ttu-id="e70ca-125">Выполните команду `upgrade-assistant`, передав имя целевого проекта (можно выполнить команду из любого места, если путь к файлу проекта является допустимым).</span><span class="sxs-lookup"><span data-stu-id="e70ca-125">Run the `upgrade-assistant` command, passing in the name of the project you're targeting (you can run the command from anywhere, as long as the path to the project file is valid).</span></span>

```console
upgrade-assistant .\AspNetMvcTest.csproj
```

<span data-ttu-id="e70ca-126">Средство запустится и отобразит список действий, которые оно будет выполнять.</span><span class="sxs-lookup"><span data-stu-id="e70ca-126">The tool runs and shows you a list of the steps it will do.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/initial-run.png" alt-text="Начальный экран помощника по обновлению .NET":::

<span data-ttu-id="e70ca-128">По мере завершения каждого шага средство предоставляет набор команд, позволяющих пользователю применить или пропустить следующий шаг, просмотреть дополнительные сведения, настроить ведение журнала или выйти из процесса.</span><span class="sxs-lookup"><span data-stu-id="e70ca-128">As each step is completed, the tool provides a set of commands allowing the user to apply or skip the next step, see more details, configure logging, or exit the process.</span></span> <span data-ttu-id="e70ca-129">Если помощник обнаруживает, что шаг не выполняет никаких действий, он автоматически пропускает его и переходит к следующему, пока не достигнет шага, который будет выполнять действия.</span><span class="sxs-lookup"><span data-stu-id="e70ca-129">If the tool detects that a step will perform no actions, it automatically skips that step and continues to the next step until it reaches one that has actions to perform.</span></span> <span data-ttu-id="e70ca-130">Нажатие клавиши <kbd>ВВОД</kbd> приведет к выполнению следующего шага, если не были выбраны другие действия.</span><span class="sxs-lookup"><span data-stu-id="e70ca-130">Pressing <kbd>Enter</kbd> will perform the next step if no other selection is made.</span></span>

<span data-ttu-id="e70ca-131">В этом примере каждый раз выбирается шаг "применить".</span><span class="sxs-lookup"><span data-stu-id="e70ca-131">In this example, the apply step is chosen each time.</span></span> <span data-ttu-id="e70ca-132">Первым шагом является резервное копирование проекта.</span><span class="sxs-lookup"><span data-stu-id="e70ca-132">The first step is to back up the project.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/backup-project.png" alt-text="Помощник по обновлению .NET: резервное копирование проекта":::

<span data-ttu-id="e70ca-134">Помощник просит указать путь для резервной копии или использует значение по умолчанию, которое размещает резервную копию проекта в той же папке с расширением `.backup`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-134">The tool prompts for a custom path for the backup, or to use the default, which will place the project backup in the same folder with a `.backup` extension.</span></span> <span data-ttu-id="e70ca-135">На следующем шаге происходит преобразование файла проекта в стиль пакета SDK.</span><span class="sxs-lookup"><span data-stu-id="e70ca-135">The next step the tool does is to convert the project file to SDK style.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/convert-project.png" alt-text="Помощник по обновлению .NET: преобразование проекта в стиль пакета SDK":::

<span data-ttu-id="e70ca-137">После изменения формата проекта следующим шагом является обновление TFM проекта.</span><span class="sxs-lookup"><span data-stu-id="e70ca-137">Once the project format has been updated, the next step is to update the TFM of the project.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-tfm.png" alt-text="Помощник по обновлению .NET: преобразование проекта в стиль пакета SDK":::

<span data-ttu-id="e70ca-139">Затем средство обновляет пакеты NuGet проекта.</span><span class="sxs-lookup"><span data-stu-id="e70ca-139">Next, the tool updates the project's NuGet packages.</span></span> <span data-ttu-id="e70ca-140">В обновлении нуждаются несколько пакетов, поэтому добавляется новый пакет анализатора.</span><span class="sxs-lookup"><span data-stu-id="e70ca-140">Several packages need updates, and a new analyzer package is added.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-nuget-packages.png" alt-text="Помощник по обновлению .NET: обновление пакетов NuGet":::

<span data-ttu-id="e70ca-142">После обновления пакетов следующим шагом будет добавление файлов шаблонов (если они есть).</span><span class="sxs-lookup"><span data-stu-id="e70ca-142">Once the packages are updated, the next step is to add template files, if any.</span></span> <span data-ttu-id="e70ca-143">Помощник определил, что необходимо добавить четыре ожидаемых элемента шаблона, и затем добавляет их.</span><span class="sxs-lookup"><span data-stu-id="e70ca-143">The tool notes there are four expected template items that must be added, and then adds them.</span></span> <span data-ttu-id="e70ca-144">Эти элементы включают следующие файлы:</span><span class="sxs-lookup"><span data-stu-id="e70ca-144">These include the following files:</span></span>

- `Program.cs`
- `Startup.cs`
- `appsettings.json`
- `appsettings.Development.json`

<span data-ttu-id="e70ca-145">Эти файлы используются ASP.NET Core для [запуска приложения](/aspnet/core/fundamentals/startup) и [настройки](/aspnet/core/fundamentals/configuration).</span><span class="sxs-lookup"><span data-stu-id="e70ca-145">These files are used by ASP.NET Core for [app startup](/aspnet/core/fundamentals/startup) and [configuration](/aspnet/core/fundamentals/configuration).</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/add-template-files.png" alt-text="Помощник по обновлению .NET: добавление файлов шаблонов":::

<span data-ttu-id="e70ca-147">Затем средство переносит файлы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e70ca-147">Next, the tool migrates config files.</span></span> <span data-ttu-id="e70ca-148">Помощник определяет параметры приложения и отключает неподдерживаемые разделы конфигурации, а затем переносит значения конфигурации `appSettings`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-148">The tool identifies app settings and disables unsupported configuration sections, then migrates the `appSettings` configuration values.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config.png" alt-text="Помощник по обновлению .NET: перенос конфигурации":::

<span data-ttu-id="e70ca-150">В завершение переноса файлов конфигурации выполняется миграция `system.web.webPages.razor/pages/namespaces`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-150">The tool completes the migration of config files by migrating `system.web.webPages.razor/pages/namespaces`.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/migrate-config2.png" alt-text="Помощник по обновлению .NET: перенос конфигурации":::

<span data-ttu-id="e70ca-152">Помощник применяет известные исправления для замены ссылок C# на новые аналоги.</span><span class="sxs-lookup"><span data-stu-id="e70ca-152">The tool applies known fixes to migrate C# references to their new counterparts.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/update-csharp.png" alt-text="Помощник по обновлению .NET: обновление исходного кода C#":::

<span data-ttu-id="e70ca-154">Так как это последний проект, следующий шаг, "переход к следующему проекту", выводит запрос на завершение процесса переноса всего решения.</span><span class="sxs-lookup"><span data-stu-id="e70ca-154">Since this is the last project, the next step, "Move to next project", prompts to complete the process of migrating the entire solution.</span></span>

:::image type="content" source="media/upgrade-assistant-aspnetmvc/complete-solution.png" alt-text="Помощник по обновлению .NET: завершение обработки решения":::

<span data-ttu-id="e70ca-156">После завершения этого процесса откройте файл проекта и проверьте его.</span><span class="sxs-lookup"><span data-stu-id="e70ca-156">Once this process has completed, open the project file and review it.</span></span> <span data-ttu-id="e70ca-157">Ищите статические файлы, подобные следующим:</span><span class="sxs-lookup"><span data-stu-id="e70ca-157">Look for static files like these:</span></span>

```xml
  <ItemGroup>
    <Content Include="fonts\glyphicons-halflings-regular.woff2" />
    <Content Include="fonts\glyphicons-halflings-regular.woff" />
    <Content Include="fonts\glyphicons-halflings-regular.ttf" />
    <Content Include="fonts\glyphicons-halflings-regular.eot" />
    <Content Include="Content\bootstrap.min.css.map" />
    <Content Include="Content\bootstrap.css.map" />
    <Content Include="Content\bootstrap-theme.min.css.map" />
    <Content Include="Content\bootstrap-theme.css.map" />
    <Content Include="Scripts\jquery-3.4.1.slim.min.map" />
    <Content Include="Scripts\jquery-3.4.1.min.map" />
  </ItemGroup>
```

<span data-ttu-id="e70ca-158">Статические файлы, которые должны обслуживаться веб-сервером, должны быть перемещены в соответствующую папку в папке корневого уровня с именем `wwwroot`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-158">Static files that should be served by the web server should be moved to an appropriate folder within a root level folder named `wwwroot`.</span></span> <span data-ttu-id="e70ca-159">Дополнительные сведения см. в разделе [Статические файлы в ASP.NET Core](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0).</span><span class="sxs-lookup"><span data-stu-id="e70ca-159">See [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files?view=aspnetcore-5.0) for details.</span></span> <span data-ttu-id="e70ca-160">После перемещения файлов можно удалить в файле проекта элементы `<Content>`, соответствующие этим файлам.</span><span class="sxs-lookup"><span data-stu-id="e70ca-160">Once the files have been moved, the `<Content>` elements in the project file corresponding to these files can be deleted.</span></span> <span data-ttu-id="e70ca-161">Фактически все элементы `<Content>` и содержащиеся в них группы можно удалить.</span><span class="sxs-lookup"><span data-stu-id="e70ca-161">In fact, all `<Content>` elements and their containing groups can be removed.</span></span> <span data-ttu-id="e70ca-162">Кроме того, необходимо удалить все ссылки `<PackageReference>` на клиентские библиотеки, такие как `bootstrap` или `jQuery`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-162">Also, any `<PackageReference>` to a client-side library like `bootstrap` or `jQuery` should be removed.</span></span>

<span data-ttu-id="e70ca-163">По умолчанию проект будет преобразован в вид библиотеки классов.</span><span class="sxs-lookup"><span data-stu-id="e70ca-163">By default, the project will be converted as a class library.</span></span> <span data-ttu-id="e70ca-164">Измените атрибут первой строки `Sdk` на `Microsoft.NET.Sdk.Web` и присвойте свойству `<TargetFramework>` значение `net5.0`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-164">Change the first line's `Sdk` attribute to `Microsoft.NET.Sdk.Web` and set the `<TargetFramework>` to `net5.0`.</span></span> <span data-ttu-id="e70ca-165">Скомпилируйте проект.</span><span class="sxs-lookup"><span data-stu-id="e70ca-165">Compile the project.</span></span> <span data-ttu-id="e70ca-166">На этом этапе количество ошибок не должно быть большим.</span><span class="sxs-lookup"><span data-stu-id="e70ca-166">At this point, the number of errors should be fairly small.</span></span> <span data-ttu-id="e70ca-167">При переносе нового проекта ASP.NET 4.6.1 MVC, оставшиеся ошибки относятся к файлам в папке `App_Start`:</span><span class="sxs-lookup"><span data-stu-id="e70ca-167">When porting a new ASP.NET 4.6.1 MVC project, the remaining errors refer to files in the `App_Start` folder:</span></span>

- <span data-ttu-id="e70ca-168">BundleConfig.cs</span><span class="sxs-lookup"><span data-stu-id="e70ca-168">BundleConfig.cs</span></span>
- <span data-ttu-id="e70ca-169">FilterConfig.cs</span><span class="sxs-lookup"><span data-stu-id="e70ca-169">FilterConfig.cs</span></span>
- <span data-ttu-id="e70ca-170">RouteConfig.cs.</span><span class="sxs-lookup"><span data-stu-id="e70ca-170">RouteConfig.cs</span></span>

<span data-ttu-id="e70ca-171">Эти файлы и всю папку `App_Start` можно удалить.</span><span class="sxs-lookup"><span data-stu-id="e70ca-171">These files - and the entire `App_Start` folder - can be deleted.</span></span> <span data-ttu-id="e70ca-172">Аналогично можно удалить файлы `Global.asax` и `Global.asax.cs`.</span><span class="sxs-lookup"><span data-stu-id="e70ca-172">Likewise, the `Global.asax` and `Global.asax.cs` files can be removed.</span></span>

<span data-ttu-id="e70ca-173">На этом этапе остались только ошибки, связанные с объединением.</span><span class="sxs-lookup"><span data-stu-id="e70ca-173">At this point the only errors that remain are related to bundling.</span></span> <span data-ttu-id="e70ca-174">Существует [несколько способов настройки объединения и минификации в ASP.NET Core](/aspnet/core/migration/mvc?view=aspnetcore-5.0#configure-bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="e70ca-174">There are [several ways to configure bundling and minification in ASP.NET Core](/aspnet/core/migration/mvc?view=aspnetcore-5.0#configure-bundling-and-minification).</span></span> <span data-ttu-id="e70ca-175">Выберите наиболее подходящий для вашего проекта.</span><span class="sxs-lookup"><span data-stu-id="e70ca-175">Choose whatever makes the most sense for your project.</span></span>

## <a name="troubleshooting-tips"></a><span data-ttu-id="e70ca-176">Советы по устранению неполадок</span><span class="sxs-lookup"><span data-stu-id="e70ca-176">Troubleshooting tips</span></span>

<span data-ttu-id="e70ca-177">Существует несколько известных проблем, которые могут возникнуть при использовании помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="e70ca-177">There are several known problems that can occur when using the .NET Upgrade Assistant.</span></span> <span data-ttu-id="e70ca-178">В некоторых случаях эти проблемы связаны со [средством try-convert](https://github.com/dotnet/try-convert), которое помощник по обновлению .NET использует для внутренних целей.</span><span class="sxs-lookup"><span data-stu-id="e70ca-178">In some cases, these are problems with the [try-convert tool](https://github.com/dotnet/try-convert) that the .NET Upgrade Assistant uses internally.</span></span> <span data-ttu-id="e70ca-179">Это средство часто обновляется для учета большего количества сценариев, поэтому убедитесь, что вы используете последнюю версию.</span><span class="sxs-lookup"><span data-stu-id="e70ca-179">This tool is being frequently updated to address more scenarios, so make sure you're using a recent version.</span></span>

- <span data-ttu-id="e70ca-180">Средство **try-convert** должно быть установлено и обновлено по крайней мере до версии _0.7.212201_.</span><span class="sxs-lookup"><span data-stu-id="e70ca-180">The **try-convert** tool must be installed and updated to at least version _0.7.212201_.</span></span>
- <span data-ttu-id="e70ca-181">Более ранние версии средства **try-convert** не поддерживали пользовательские целевые объекты и файлы PROPS.</span><span class="sxs-lookup"><span data-stu-id="e70ca-181">Earlier versions of the **try-convert** tool didn't support custom target or props files.</span></span> <span data-ttu-id="e70ca-182">Если не удается выполнить обновление до последней версии, может потребоваться вручную решить эти проблемы.</span><span class="sxs-lookup"><span data-stu-id="e70ca-182">If you can't upgrade to the latest version, you may need to manually address these issues.</span></span> <span data-ttu-id="e70ca-183">Если целевой файл проекта содержит ссылки на пользовательские целевые объекты или файлы PROPS, эти ссылки необходимо вручную удалить из файла до запуска помощника по обновлению .NET.</span><span class="sxs-lookup"><span data-stu-id="e70ca-183">If the target project file includes references to custom targets or props files, these references may need to be manually deleted from the file before the .NET Upgrade Assistant is run against it.</span></span>

```xml
<Import Project="packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props" Condition="Exists('packages\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.2.0.1\build\net46\Microsoft.CodeDom.Providers.DotNetCompilerPlatform.props')" />
```

<span data-ttu-id="e70ca-184">[В репозитории GitHub этого средства](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) содержатся дополнительные советы по устранению неполадок и известные проблемы.</span><span class="sxs-lookup"><span data-stu-id="e70ca-184">[The tool's GitHub repository](https://github.com/dotnet/upgrade-assistant#troubleshooting-common-issues) has more troubleshooting tips and known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="e70ca-185">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e70ca-185">See also</span></span>

- [<span data-ttu-id="e70ca-186">Обновление приложения WPF до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="e70ca-186">Upgrade a WPF App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-wpf-framework.md)
- [<span data-ttu-id="e70ca-187">Обновление приложения Windows Forms до .NET 5 с помощью помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="e70ca-187">Upgrade a Windows Forms App to .NET 5 with the .NET Upgrade Assistant</span></span>](upgrade-assistant-winforms-framework.md)
- [<span data-ttu-id="e70ca-188">Обзор помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="e70ca-188">Overview of the .NET Upgrade Assistant</span></span>](upgrade-assistant-overview.md)
- [<span data-ttu-id="e70ca-189">Репозиторий GitHub помощника по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="e70ca-189">.NET Upgrade Assistant GitHub Repository</span></span>](https://github.com/dotnet/upgrade-assistant)
