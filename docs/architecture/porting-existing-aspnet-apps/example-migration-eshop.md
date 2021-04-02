---
title: Пример миграции Ешоп в ASP.NET Core
description: Пошаговое руководство по переносу существующего приложения ASP.NET MVC в ASP.NET Core с помощью примера приложения Интернет-магазина в качестве ссылки.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 119ba64134813fa17848cf9f5fe02cb1a14f8a5d
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122980"
---
# <a name="example-migration-of-eshop-to-aspnet-core"></a><span data-ttu-id="9aa14-103">Пример миграции Ешоп в ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9aa14-103">Example migration of eShop to ASP.NET Core</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="9aa14-104">В этой главе вы узнаете, как перенести платформа .NET Framework приложение в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-104">In this chapter, you'll see how to migrate a .NET Framework app to .NET Core.</span></span> <span data-ttu-id="9aa14-105">В этой главе рассматривается пример приложения для Интернет-магазина, написанного для ASP.NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="9aa14-105">The chapter examines a sample online store app written for ASP.NET 5.0.</span></span> <span data-ttu-id="9aa14-106">Приложение будет использовать множество концепций и средств, описанных ранее в этой книге.</span><span class="sxs-lookup"><span data-stu-id="9aa14-106">The app will use many of the concepts and tools described earlier in this book.</span></span> <span data-ttu-id="9aa14-107">Вы найдете приложение начальной точки в [репозитории *eShopModernizing* GitHub](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="9aa14-107">You'll find the starting point app in the [*eShopModernizing* GitHub repository](https://github.com/dotnet-architecture/eShopModernizing).</span></span> <span data-ttu-id="9aa14-108">Существует несколько различных приложений-отправной точки.</span><span class="sxs-lookup"><span data-stu-id="9aa14-108">There are several different starting point apps.</span></span> <span data-ttu-id="9aa14-109">Эта глава посвящена *ешоплегацимвксолутион*.</span><span class="sxs-lookup"><span data-stu-id="9aa14-109">This chapter focuses on the *eShopLegacyMVCSolution*.</span></span>

<span data-ttu-id="9aa14-110">Исходная версия проекта показана на рис. 4-1.</span><span class="sxs-lookup"><span data-stu-id="9aa14-110">The initial version of the project is shown in Figure 4-1.</span></span> <span data-ttu-id="9aa14-111">Это довольно стандартное приложение ASP.NET MVC 5.</span><span class="sxs-lookup"><span data-stu-id="9aa14-111">It's a fairly standard ASP.NET MVC 5 app.</span></span>

![Рис. 4-1](media/Figure4-1.png)

<span data-ttu-id="9aa14-113">**Рис. 4-1.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-113">**Figure 4-1.**</span></span> <span data-ttu-id="9aa14-114">Структура образца проекта MVC *eShopModernizing* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-114">The *eShopModernizing* MVC sample project structure.</span></span>

<span data-ttu-id="9aa14-115">В этой главе показано, как выполнить многие действия по обновлению вручную.</span><span class="sxs-lookup"><span data-stu-id="9aa14-115">This chapter demonstrates how to perform many of the upgrade steps by hand.</span></span> <span data-ttu-id="9aa14-116">Кроме того, [средство "помощник по обновлению .NET](https://aka.ms/dotnet-upgrade-assistant) " можно использовать для выполнения многих начальных действий, таких как преобразование файла проекта, изменение целевой платформы и обновление пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="9aa14-116">Alternatively, you can use the [.NET Upgrade Assistant tool](https://aka.ms/dotnet-upgrade-assistant) to perform many of the initial steps, like converting the project file, changing the target framework, and updating NuGet packages.</span></span>

## <a name="run-apiport-to-identify-problematic-apis"></a><span data-ttu-id="9aa14-117">Запуск *ApiPort* для обнаружения проблемных API</span><span class="sxs-lookup"><span data-stu-id="9aa14-117">Run *ApiPort* to identify problematic APIs</span></span>

<span data-ttu-id="9aa14-118">Первым шагом в подготовке к миграции является запуск средства *ApiPort* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-118">The first step in preparing to migrate is to run the *ApiPort* tool.</span></span> <span data-ttu-id="9aa14-119">Это средство определяет, сколько платформа .NET Framework интерфейсов API вызывается приложением и сколько из них имеет .NET Standard или эквиваленты .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-119">The tool identifies how many .NET Framework APIs the app calls and how many of these have .NET Standard or .NET Core equivalents.</span></span> <span data-ttu-id="9aa14-120">Сосредоточьтесь в основном на логике вашего приложения, а не на зависимостях сторонних производителей и обратите внимание на `System.Web` зависимости, которые потребуется перенести.</span><span class="sxs-lookup"><span data-stu-id="9aa14-120">Focus primarily on your own app's logic, not third-party dependencies, and pay attention to `System.Web` dependencies that will need to be ported.</span></span> <span data-ttu-id="9aa14-121">Средство ApiPort было представлено в последней главе, посвященной [пониманию и обновлению зависимостей](understand-update-dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="9aa14-121">The ApiPort tool was introduced in the last chapter on [understanding and updating dependencies](understand-update-dependencies.md).</span></span>

<span data-ttu-id="9aa14-122">После [установки и настройки средства *ApiPort*](../../standard/analyzers/portability-analyzer.md)запустите анализ в Visual Studio, как показано на рис. 4-2.</span><span class="sxs-lookup"><span data-stu-id="9aa14-122">After [installing and configuring the *ApiPort* tool](../../standard/analyzers/portability-analyzer.md), run the analysis from within Visual Studio, as shown in Figure 4-2.</span></span>

![Рис. 4-2](media/Figure4-2.png)

<span data-ttu-id="9aa14-124">**Рис. 4-2.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-124">**Figure 4-2.**</span></span> <span data-ttu-id="9aa14-125">Анализ переносимости сборок в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9aa14-125">Analyze assembly portability in Visual Studio.</span></span>

<span data-ttu-id="9aa14-126">Выберите сборку веб-проекта из папки *bin* проекта, как показано на рис. 4-3.</span><span class="sxs-lookup"><span data-stu-id="9aa14-126">Choose the web project's assembly from the project's *bin* folder, as shown in Figure 4-3.</span></span>

![Рис. 4-3](media/Figure4-3.png)

<span data-ttu-id="9aa14-128">**Рис. 4-3.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-128">**Figure 4-3.**</span></span> <span data-ttu-id="9aa14-129">Выберите веб-сборку проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-129">Choose the project's web assembly.</span></span>

<span data-ttu-id="9aa14-130">Если решение содержит несколько проектов, можно выбрать их все.</span><span class="sxs-lookup"><span data-stu-id="9aa14-130">If your solution includes several projects, you can choose all of them.</span></span> <span data-ttu-id="9aa14-131">Пример *ешоп* включает только один проект MVC.</span><span class="sxs-lookup"><span data-stu-id="9aa14-131">The *eShop* sample includes just a single MVC project.</span></span>

<span data-ttu-id="9aa14-132">После создания отчета откройте файл и проверьте результаты.</span><span class="sxs-lookup"><span data-stu-id="9aa14-132">Once the report is generated, open the file and review the results.</span></span> <span data-ttu-id="9aa14-133">В сводке представлено общее представление о том, какой процент платформа .NET Framework вызовов вашего приложения имеет совместимые версии.</span><span class="sxs-lookup"><span data-stu-id="9aa14-133">The summary provides a high-level view of what percentage of .NET Framework calls your app is making have compatible versions.</span></span> <span data-ttu-id="9aa14-134">На рис. 4-4 показана сводка по проекту MVC *ешоп* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-134">Figure 4-4 shows the summary for the *eShop* MVC project.</span></span>

![Рис. 4-4](media/Figure4-4.png)

<span data-ttu-id="9aa14-136">**Рис. 4-4.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-136">**Figure 4-4.**</span></span> <span data-ttu-id="9aa14-137">Сводка ApiPort.</span><span class="sxs-lookup"><span data-stu-id="9aa14-137">ApiPort summary.</span></span>

<span data-ttu-id="9aa14-138">Для этого приложения около 80 процентов вызовов платформа .NET Framework совместимы.</span><span class="sxs-lookup"><span data-stu-id="9aa14-138">For this app, about 80 percent of the .NET Framework calls are compatible.</span></span> <span data-ttu-id="9aa14-139">в процессе переноса необходимо устранить 20 процентов вызовов.</span><span class="sxs-lookup"><span data-stu-id="9aa14-139">20 percent of the calls need to be addressed during the porting process.</span></span> <span data-ttu-id="9aa14-140">Просмотр сведений показывает, что все несовместимые вызовы являются частью `System.Web` , что является ожидаемым несовместимостью.</span><span class="sxs-lookup"><span data-stu-id="9aa14-140">Viewing the details reveals that all of the incompatible calls are part of `System.Web`, which is an expected incompatibility.</span></span> <span data-ttu-id="9aa14-141">Зависимости от `System.Web` вызовов будут устранены, когда контроллеры и связанные классы приложения будут перенесены на более позднем этапе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-141">The dependencies on `System.Web` calls will be addressed when the app's controllers and related classes are migrated in a later step.</span></span> <span data-ttu-id="9aa14-142">На рис. 4-5 перечислены некоторые из определенных типов, обнаруженных средством.</span><span class="sxs-lookup"><span data-stu-id="9aa14-142">Figure 4-5 lists some of the specific types found by the tool:</span></span>

![Рис. 4-5](media/Figure4-5.png)

<span data-ttu-id="9aa14-144">**Рис. 4-5.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-144">**Figure 4-5.**</span></span> <span data-ttu-id="9aa14-145">*ApiPort* несовместимые сведения о типе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-145">*ApiPort* incompatible type details.</span></span>

<span data-ttu-id="9aa14-146">Большинство несовместимых типов относятся к `Controller` и различным связанным атрибутам, которые имеют эквиваленты в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-146">Most of the incompatible types refer to `Controller` and various related attributes that have equivalents in ASP.NET Core.</span></span>

## <a name="update-project-files-and-nuget-reference-syntax"></a><span data-ttu-id="9aa14-147">Обновление файлов проекта и синтаксиса ссылок NuGet</span><span class="sxs-lookup"><span data-stu-id="9aa14-147">Update project files and NuGet reference syntax</span></span>

<span data-ttu-id="9aa14-148">Затем выполните миграцию из старой структуры файлов *. csproj* в более новую, более простую структуру, появившуюся в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-148">Next, migrate from the older *.csproj* file structure to the newer, simpler structure introduced with .NET Core.</span></span> <span data-ttu-id="9aa14-149">При этом вы также выполняете миграцию с помощью файла *packages.config* для ссылок NuGet на использование `<PackageReference>` элементов в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-149">In doing so, you'll also migrate from using a *packages.config* file for NuGet references to using `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="9aa14-150">Файлы проектов в старом стиле также могут использовать `<PackageReference>` элементы, поэтому обычно имеет смысл сначала перенести все ссылки на пакеты NuGet в этот формат, прежде чем выполнять обновление до нового формата файла проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-150">Old-style project files may also use `<PackageReference>` elements, so it usually makes sense to migrate all NuGet package references to this format first, before upgrading to the new project file format.</span></span>

<span data-ttu-id="9aa14-151">Файл *ешоплегацимвк. csproj* исходного проекта имеет длину 418 строк.</span><span class="sxs-lookup"><span data-stu-id="9aa14-151">The original project's *eShopLegacyMVC.csproj* file is 418 lines long.</span></span> <span data-ttu-id="9aa14-152">Пример файла проекта показан на рис. 4-6.</span><span class="sxs-lookup"><span data-stu-id="9aa14-152">A sample of the project file is shown in Figure 4-6.</span></span> <span data-ttu-id="9aa14-153">Чтобы получить представление об общем размере и сложности, в правой части изображения содержится миниатюра всего файла.</span><span class="sxs-lookup"><span data-stu-id="9aa14-153">To offer a sense of its overall size and complexity, the right side of the image contains a miniature view of the entire file.</span></span>

![Рис. 4-6](media/Figure4-6.png)

<span data-ttu-id="9aa14-155">**Рис. 4-6.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-155">**Figure 4-6.**</span></span> <span data-ttu-id="9aa14-156">Структура файла *ешоплегацимвк. csproj* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-156">The *eShopLegacyMVC.csproj* file structure.</span></span>

<span data-ttu-id="9aa14-157">Распространенным способом создания нового файла проекта для существующего проекта ASP.NET является создание нового приложения ASP.NET Core с помощью `dotnet new` или **файла**  >  **нового**  >  **проекта** в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9aa14-157">A common way to create a new project file for an existing ASP.NET project is to create a new ASP.NET Core app using `dotnet new` or **File** > **New** > **Project** in Visual Studio.</span></span> <span data-ttu-id="9aa14-158">Затем файлы можно скопировать из старого проекта в новый, чтобы завершить миграцию.</span><span class="sxs-lookup"><span data-stu-id="9aa14-158">Then files can be copied from the old project to the new one to complete the migration.</span></span>

<span data-ttu-id="9aa14-159">Помимо файла проекта C#, зависимости NuGet хранятся в отдельном *packages.configном* файле 45, как показано на рис. 4-7.</span><span class="sxs-lookup"><span data-stu-id="9aa14-159">In addition to the C# project file, NuGet dependencies are stored in a separate 45-line *packages.config* file, as shown in Figure 4-7.</span></span>

![Рис. 4-7](media/Figure4-7.png)

<span data-ttu-id="9aa14-161">**Рис. 4-7**.</span><span class="sxs-lookup"><span data-stu-id="9aa14-161">**Figure 4-7.**</span></span> <span data-ttu-id="9aa14-162">Файл *packages.config* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-162">The *packages.config* file.</span></span>

<span data-ttu-id="9aa14-163">*packages.config* можно перенести в проекты библиотеки классов с помощью Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9aa14-163">You can migrate *packages.config* in class library projects using Visual Studio.</span></span> <span data-ttu-id="9aa14-164">Однако эта функциональность не работает с проектами ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9aa14-164">This functionality doesn't work with ASP.NET projects, however.</span></span> <span data-ttu-id="9aa14-165">Дополнительные [сведения о миграции *packages.config* в `<PackageReference>` Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span><span class="sxs-lookup"><span data-stu-id="9aa14-165">[Learn more about migrating *packages.config* to `<PackageReference>` in Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).</span></span> <span data-ttu-id="9aa14-166">При наличии большого количества проектов для миграции [это средство сообщества может помочь](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).</span><span class="sxs-lookup"><span data-stu-id="9aa14-166">If you have a large number of projects to migrate, [this community tool may help](https://github.com/MarkKharitonov/NuGetPCToPRMigrator).</span></span> <span data-ttu-id="9aa14-167">Если вы используете средство для переноса файла проекта в новый формат, это следует сделать после завершения переноса всех ссылок NuGet для использования `<PackageReverence>` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-167">If you're using a tool to migrate the project file to the new format, you should do that after you've finished migrating all NuGet references to use `<PackageReverence>`.</span></span>

## <a name="create-new-aspnet-core-project"></a><span data-ttu-id="9aa14-168">Создание нового ASP.NET Core проекта</span><span class="sxs-lookup"><span data-stu-id="9aa14-168">Create new ASP.NET Core project</span></span>

<span data-ttu-id="9aa14-169">Добавьте новый проект ASP.NET Core в решение существующего приложения, чтобы упростить перемещение файлов, так как большая часть работы может быть выполнена в **Обозреватель решений** Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9aa14-169">Add a new ASP.NET Core project to the existing app's solution to make moving files easier, as most of the work can be done from within Visual Studio's **Solution Explorer**.</span></span> <span data-ttu-id="9aa14-170">В Visual Studio щелкните правой кнопкой мыши решение приложения и выберите команду **Добавить новый проект**.</span><span class="sxs-lookup"><span data-stu-id="9aa14-170">In Visual Studio, right-click on your app's solution and choose **Add New Project**.</span></span> <span data-ttu-id="9aa14-171">Выберите **ASP.NET Core веб-приложение** и присвойте имя новому проекту, как показано на рис. 4-8.</span><span class="sxs-lookup"><span data-stu-id="9aa14-171">Choose **ASP.NET Core web application**, and give the new project a name as shown in Figure 4-8.</span></span>

![Рис. 4-8](media/Figure4-8.png)

<span data-ttu-id="9aa14-173">**Рис. 4-8.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-173">**Figure 4-8.**</span></span> <span data-ttu-id="9aa14-174">Добавление нового веб-приложения ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-174">Add new ASP.NET Core web application.</span></span>

<span data-ttu-id="9aa14-175">В следующем диалоговом окне будет предложено выбрать шаблон для использования.</span><span class="sxs-lookup"><span data-stu-id="9aa14-175">The next dialog will ask you to choose which template to use.</span></span> <span data-ttu-id="9aa14-176">Выберите шаблон **Пустой**.</span><span class="sxs-lookup"><span data-stu-id="9aa14-176">Select the **Empty** template.</span></span> <span data-ttu-id="9aa14-177">Не забудьте также изменить раскрывающийся список **.NET Core** на **платформа .NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="9aa14-177">Be sure to also change the dropdown from **.NET Core** to **.NET Framework**.</span></span> <span data-ttu-id="9aa14-178">Выберите **ASP.NET Core 2,2**, как показано на рис. 4-9.</span><span class="sxs-lookup"><span data-stu-id="9aa14-178">Select **ASP.NET Core 2.2**, as shown in Figure 4-9.</span></span>

![Рис. 4-9](media/Figure4-9.png)

<span data-ttu-id="9aa14-180">**Рис. 4-9**</span><span class="sxs-lookup"><span data-stu-id="9aa14-180">**Figure 4-9.**</span></span> <span data-ttu-id="9aa14-181">Выберите пустой шаблон проекта, предназначенный для платформа .NET Framework с ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="9aa14-181">Choose an Empty project template targeting .NET Framework with ASP.NET Core 2.2.</span></span>

### <a name="migrating-nuget-packages"></a><span data-ttu-id="9aa14-182">Перенос пакетов NuGet</span><span class="sxs-lookup"><span data-stu-id="9aa14-182">Migrating NuGet Packages</span></span>

<span data-ttu-id="9aa14-183">Так как встроенное средство миграции для миграции *packages.config* `<PackageReference>` не работает в проектах ASP.NET, вы можете использовать вместо этого средство сообщества или выполнить миграцию вручную.</span><span class="sxs-lookup"><span data-stu-id="9aa14-183">Since the built-in migration tool for migrating *packages.config* to `<PackageReference>` doesn't work on ASP.NET projects, you can use a community tool instead, or migrate by hand.</span></span> <span data-ttu-id="9aa14-184">[Используемое мной средство сообщества](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) использует XSL-файл для преобразования одного формата в другой.</span><span class="sxs-lookup"><span data-stu-id="9aa14-184">A [community tool I've used](https://gist.github.com/tomkuijsten/2d75074d9a3c19c04ee8ea19a6289ddf) uses an XSL file to transform from one format to the other.</span></span> <span data-ttu-id="9aa14-185">Чтобы использовать его, сначала скопируйте файл *packages.config* во вновь созданную папку проекта ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-185">To use it, first copy the *packages.config* file to the newly created ASP.NET Core project folder.</span></span> <span data-ttu-id="9aa14-186">Создайте резервную копию файлов, так как этот сценарий удаляет файл *packages.config* из всех папок, в которых выполняется сценарий.</span><span class="sxs-lookup"><span data-stu-id="9aa14-186">Make a backup of your files, as this script removes the *packages.config* file from all folders under where you run the script.</span></span> <span data-ttu-id="9aa14-187">Затем выполните эти команды из папки проекта (или для всего решения, если хотите):</span><span class="sxs-lookup"><span data-stu-id="9aa14-187">Then run these commands from the project folder (or for the entire solution if you prefer):</span></span>

```powershell
iwr https://git.io/vdKaV -OutFile Convert-ToPackageReference.ps1
iwr https://git.io/vdKar -OutFile  Convert-ToPackageReference.xsl
./Convert-ToPackageReference.ps1 | Out-Null
```

<span data-ttu-id="9aa14-188">Первые две команды загружают файлы, чтобы они существовали локально.</span><span class="sxs-lookup"><span data-stu-id="9aa14-188">The first two commands download files so that they exist locally.</span></span> <span data-ttu-id="9aa14-189">В последней строке выполняется сценарий.</span><span class="sxs-lookup"><span data-stu-id="9aa14-189">The last line runs the script.</span></span> <span data-ttu-id="9aa14-190">После запуска попытайтесь выполнить сборку нового проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-190">After running it, try to build the new project.</span></span> <span data-ttu-id="9aa14-191">Скорее всего, будут возникнет ошибки.</span><span class="sxs-lookup"><span data-stu-id="9aa14-191">You'll most likely get some errors.</span></span> <span data-ttu-id="9aa14-192">Чтобы устранить их, необходимо устранить некоторые ссылки (например, большинство `Microsoft.AspNet` `System` пакетов и), а также удалить некоторые `xmlns` атрибуты.</span><span class="sxs-lookup"><span data-stu-id="9aa14-192">To resolve them, you'll want to eliminate some references (like most of the `Microsoft.AspNet` and `System` packages), and you may need to remove some `xmlns` attributes.</span></span>

<span data-ttu-id="9aa14-193">В большинстве ASP.NET приложений MVC многие клиентские зависимости, такие как начальная загрузка и jQuery, были развернуты с помощью пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="9aa14-193">In most ASP.NET MVC apps, many client-side dependencies like Bootstrap and jQuery were deployed using NuGet packages.</span></span> <span data-ttu-id="9aa14-194">В ASP.NET Core пакеты NuGet используются только для функций на стороне сервера.</span><span class="sxs-lookup"><span data-stu-id="9aa14-194">In ASP.NET Core, NuGet packages are only used for server-side functionality.</span></span> <span data-ttu-id="9aa14-195">Клиентские файлы должны управляться другими способами.</span><span class="sxs-lookup"><span data-stu-id="9aa14-195">Client files should be managed through other means.</span></span> <span data-ttu-id="9aa14-196">Просмотрите список `<PackageReference>` добавленных и удаляемых элементов, а также запишите все, что необходимо для клиентских библиотек, в том числе:</span><span class="sxs-lookup"><span data-stu-id="9aa14-196">Review the list of `<PackageReference>` elements added and remove and make note of any that are for client libraries, including:</span></span>

- <span data-ttu-id="9aa14-197">Бутстрэп</span><span class="sxs-lookup"><span data-stu-id="9aa14-197">Bootstrap</span></span>
- <span data-ttu-id="9aa14-198">jQuery</span><span class="sxs-lookup"><span data-stu-id="9aa14-198">jQuery</span></span>
- <span data-ttu-id="9aa14-199">jQuery. Validation</span><span class="sxs-lookup"><span data-stu-id="9aa14-199">jQuery.Validation</span></span>
- <span data-ttu-id="9aa14-200">Modernizr</span><span class="sxs-lookup"><span data-stu-id="9aa14-200">Modernizr</span></span>
- <span data-ttu-id="9aa14-201">popper.js</span><span class="sxs-lookup"><span data-stu-id="9aa14-201">popper.js</span></span>
- <span data-ttu-id="9aa14-202">Устранение</span><span class="sxs-lookup"><span data-stu-id="9aa14-202">Respond</span></span>

<span data-ttu-id="9aa14-203">Статические клиентские файлы, установленные NuGet для этих пакетов, будут скопированы в папку *wwwroot* нового проекта и размещены там.</span><span class="sxs-lookup"><span data-stu-id="9aa14-203">The static client files installed by NuGet for these packages will be copied over to the new project's *wwwroot* folder and hosted from there.</span></span> <span data-ttu-id="9aa14-204">Стоит подумать, что эти файлы по-прежнему нужны для приложения, а также имеет ли смысл продолжать их размещение или использовать сеть доставки содержимого (CDN).</span><span class="sxs-lookup"><span data-stu-id="9aa14-204">It's worth considering whether these files are still needed by the app, and whether it makes sense to continue hosting them or to use a content delivery network (CDN) instead.</span></span> <span data-ttu-id="9aa14-205">Этими версиями библиотеки можно управлять во время сборки с помощью таких средств, как [Либман](/aspnet/core/client-side/libman/) или [NPM](https://www.npmjs.com/).</span><span class="sxs-lookup"><span data-stu-id="9aa14-205">These library versions can be managed at build time using tools like [LibMan](/aspnet/core/client-side/libman/) or [npm](https://www.npmjs.com/).</span></span> <span data-ttu-id="9aa14-206">На рис. 4-10 показан полный файл *ешоппортед. csproj* после переноса ссылок на пакеты с помощью показанного средства преобразования и удаления ненужных пакетов.</span><span class="sxs-lookup"><span data-stu-id="9aa14-206">Figure 4-10 shows the full *eShopPorted.csproj* file after migrating package references using the conversion tool shown and removing unnecessary packages.</span></span>

![Рис. 4-10](media/Figure4-10.png)

<span data-ttu-id="9aa14-208">**Рис. 4-10.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-208">**Figure 4-10.**</span></span> <span data-ttu-id="9aa14-209">Ссылки на пакеты в файле *ешоппортед. csproj* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-209">Package references in the *eShopPorted.csproj* file.</span></span>

<span data-ttu-id="9aa14-210">Ссылки на пакет можно дополнительно сжать, сделав `<Version>1.0.0.0</Version>` элемент `Version=1.0.0.0` атрибутом `<PackageReference>` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-210">The package references can be further compacted by making the `<Version>1.0.0.0</Version>` element a `Version=1.0.0.0` attribute on `<PackageReference>`.</span></span>

### <a name="migrate-static-files"></a><span data-ttu-id="9aa14-211">Миграция статических файлов</span><span class="sxs-lookup"><span data-stu-id="9aa14-211">Migrate static files</span></span>

<span data-ttu-id="9aa14-212">Все статические файлы, используемые приложением, включая сценарии и платформы сторонних производителей, но также пользовательские образы и таблицы стилей, должны быть скопированы из старого проекта в новый.</span><span class="sxs-lookup"><span data-stu-id="9aa14-212">Any static files the app uses, including third-party scripts and frameworks but also custom images and stylesheets, must be copied from the old project to the new one.</span></span> <span data-ttu-id="9aa14-213">В приложениях ASP.NET MVC доступ к файлам обычно осуществлялся в соответствии с их расположением в папке проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-213">In ASP.NET MVC apps, files were typically accessed based on their location within the project folder.</span></span> <span data-ttu-id="9aa14-214">В ASP.NET Coreных приложениях доступ к этим статическим файлам будет осуществляться в зависимости от их расположения в папке *wwwroot* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-214">In ASP.NET Core apps, these static files will be accessed based on their location within the *wwwroot* folder.</span></span> <span data-ttu-id="9aa14-215">Для проекта *ешоп* в следующих папках есть статические файлы:</span><span class="sxs-lookup"><span data-stu-id="9aa14-215">For the *eShop* project, there are static files in the following folders:</span></span>

* <span data-ttu-id="9aa14-216">*Содержимое*</span><span class="sxs-lookup"><span data-stu-id="9aa14-216">*Content*</span></span>
* <span data-ttu-id="9aa14-217">*шрифты*</span><span class="sxs-lookup"><span data-stu-id="9aa14-217">*fonts*</span></span>
* <span data-ttu-id="9aa14-218">*Изображения*</span><span class="sxs-lookup"><span data-stu-id="9aa14-218">*Images*</span></span>
* <span data-ttu-id="9aa14-219">*Pics*</span><span class="sxs-lookup"><span data-stu-id="9aa14-219">*Pics*</span></span>
* <span data-ttu-id="9aa14-220">*Создание и запуск скриптов PowerShell из консоли Configuration Manager*</span><span class="sxs-lookup"><span data-stu-id="9aa14-220">*Scripts*</span></span>

<span data-ttu-id="9aa14-221">**Пустой** шаблон проекта, используемый на предыдущем шаге, не включает эту папку по умолчанию или по промежуточного слоя, необходимое для работы.</span><span class="sxs-lookup"><span data-stu-id="9aa14-221">The **Empty** project template used in the previous step doesn't include this folder by default, or the middleware needed for it to work.</span></span> <span data-ttu-id="9aa14-222">Их необходимо добавить.</span><span class="sxs-lookup"><span data-stu-id="9aa14-222">You'll need to add them.</span></span>

<span data-ttu-id="9aa14-223">Добавьте папку *wwwroot* в корень проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-223">Add a *wwwroot* folder to the root of the project.</span></span>

<span data-ttu-id="9aa14-224">Добавьте версию 2.2.0 `Microsoft.AspNetCore.StaticFiles` пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="9aa14-224">Add version 2.2.0 of the `Microsoft.AspNetCore.StaticFiles` NuGet package.</span></span>

<span data-ttu-id="9aa14-225">В *Startup. CS* добавьте вызов `app.UseStaticFiles()` в `Configure` методе:</span><span class="sxs-lookup"><span data-stu-id="9aa14-225">In *Startup.cs*, add a call to `app.UseStaticFiles()` in the `Configure` method:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseStaticFiles();

    // ...
}
```

<span data-ttu-id="9aa14-226">Скопируйте папку *Content* из приложения ASP.NET MVC в папку *wwwroot* нового проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-226">Copy the *Content* folder from the ASP.NET MVC app to the new project's *wwwroot* folder.</span></span>

<span data-ttu-id="9aa14-227">Запустите приложение и перейдите к папке */контент/Басе.КСС* , чтобы убедиться, что статический файл правильно обрабатывается по ожидаемому пути.</span><span class="sxs-lookup"><span data-stu-id="9aa14-227">Run the app and navigate to its */Content/base.css* folder to verify that the static file is served correctly from its expected path.</span></span> <span data-ttu-id="9aa14-228">Продолжайте копирование остальных папок, содержащих статические файлы, в новый проект.</span><span class="sxs-lookup"><span data-stu-id="9aa14-228">Continue copying the rest of the folders containing static files to the new project.</span></span> <span data-ttu-id="9aa14-229">Также необходимо скопировать файл *фавикон. ico* из корневого каталога проекта в папку *wwwroot* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-229">You'll also want to copy the *favicon.ico* file from the project's root to the *wwwroot* folder.</span></span> <span data-ttu-id="9aa14-230">На рис. 4-11 показаны результаты копирования этих файлов и их папок.</span><span class="sxs-lookup"><span data-stu-id="9aa14-230">Figure 4-11 shows the results after these files and their folders have all been copied.</span></span>

![Рис. 4-11](media/Figure4-11.png)

<span data-ttu-id="9aa14-232">**Рис. 4-11.**</span><span class="sxs-lookup"><span data-stu-id="9aa14-232">**Figure 4-11.**</span></span> <span data-ttu-id="9aa14-233">Статические папки скопированы в папку *wwwroot* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-233">Static folders copied over to *wwwroot* folder.</span></span>

### <a name="migrate-c-files"></a><span data-ttu-id="9aa14-234">Перенос файлов C#</span><span class="sxs-lookup"><span data-stu-id="9aa14-234">Migrate C# files</span></span>

<span data-ttu-id="9aa14-235">Затем скопируйте файлы C#, используемые приложением, включая стандартные папки MVC и их содержимое, например *контроллеры*, *модели*, *ViewModel* и *службы*.</span><span class="sxs-lookup"><span data-stu-id="9aa14-235">Next, copy over the C# files used by the app, including standard MVC folders and their contents like *Controllers*, *Models*, *ViewModel*, and *Services*.</span></span> <span data-ttu-id="9aa14-236">Скорее всего, в этих файлах потребуется внести некоторые изменения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-236">There will most likely be some changes needed in these files.</span></span> <span data-ttu-id="9aa14-237">Лучше копировать одну папку (или вложенную папку) за раз и компилировать, чтобы узнать, какие ошибки необходимо решить по мере того, как вы уходите.</span><span class="sxs-lookup"><span data-stu-id="9aa14-237">It's best to copy one folder (or subfolder) at a time and compile to see what errors need to be addressed as you go.</span></span>

<span data-ttu-id="9aa14-238">Для примера *ешоп* первой папкой, которую я выбрал для переноса, является папка *Models* , включающая сущности C# и классы Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9aa14-238">For the *eShop* sample, the first folder I choose to migrate is the *Models* folder, which includes C# entities and Entity Framework classes.</span></span> <span data-ttu-id="9aa14-239">Классы этой папки используются большинством других компонентов, поэтому они не будут работать до тех пор, пока эти классы не будут скопированы.</span><span class="sxs-lookup"><span data-stu-id="9aa14-239">This folder's classes are used by most of the others, so they won't work until these classes have been copied.</span></span> <span data-ttu-id="9aa14-240">После копирования папки и сборки компилятор выявил ошибки, связанные с отсутствием пространства имен `System.Web.Hosting` , связанным доступом к `HostingEnvironment` и ссылкой на `ConfigurationManager.AppSettings` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-240">After copying the folder and building, the compiler revealed errors related to missing namespace `System.Web.Hosting`, related access to `HostingEnvironment`, and a reference to `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="9aa14-241">Решением этих проблем будет передача необходимых данных пути. для этого разрывы строк записываются в комментарий и к `TODO:` каждому из них добавляется комментарий для его трассировки.</span><span class="sxs-lookup"><span data-stu-id="9aa14-241">The solution to these issues will be to pass in the necessary path data; for now the breaking lines are commented out and a `TODO:` comment is added to each one to track it.</span></span> <span data-ttu-id="9aa14-242">После изменения пяти строк в **список задач** отображается пять элементов и сборка проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-242">After changing five lines, the **Task List** shows five items and the project builds.</span></span>

<span data-ttu-id="9aa14-243">Далее будет скопирована папка *ViewModel* с одним из классов.</span><span class="sxs-lookup"><span data-stu-id="9aa14-243">Next, the *ViewModel* folder, with its one class, is copied over.</span></span> <span data-ttu-id="9aa14-244">Это просто, и сборка выполняется немедленно.</span><span class="sxs-lookup"><span data-stu-id="9aa14-244">It's an easy one, and builds immediately.</span></span>

<span data-ttu-id="9aa14-245">Папка *Services* будет скопирована.</span><span class="sxs-lookup"><span data-stu-id="9aa14-245">The *Services* folder is copied over.</span></span> <span data-ttu-id="9aa14-246">Классы этой папки зависят от Entity Framework классов из папки *Models* , поэтому ее необходимо скопировать после этой папки.</span><span class="sxs-lookup"><span data-stu-id="9aa14-246">This folder's classes depend on Entity Framework classes from the *Models* folder, which is why it needed to be copied after that folder.</span></span> <span data-ttu-id="9aa14-247">К счастью, это слишком сложное построение без ошибок.</span><span class="sxs-lookup"><span data-stu-id="9aa14-247">Fortunately, it too builds without errors.</span></span>

<span data-ttu-id="9aa14-248">Это оставляет папку *Controllers* и ее два `Controller` класса.</span><span class="sxs-lookup"><span data-stu-id="9aa14-248">That leaves the *Controllers* folder and its two `Controller` classes.</span></span> <span data-ttu-id="9aa14-249">После копирования папки в новый проект и сборки возникает семь ошибок сборки.</span><span class="sxs-lookup"><span data-stu-id="9aa14-249">After copying the folder to the new project and building, there are seven build errors.</span></span> <span data-ttu-id="9aa14-250">Четыре из них связаны с `ViewBag` доступом и сообщают об ошибке:</span><span class="sxs-lookup"><span data-stu-id="9aa14-250">Four of them are related to `ViewBag` access and report an error of:</span></span>

> `Missing compiler required member 'Microsoft.CSharp.RuntimeBinder.CSharpArgumentInfo.Create'`

<span data-ttu-id="9aa14-251">Чтобы устранить эту ошибку, добавьте ссылку на пакет NuGet в C#:</span><span class="sxs-lookup"><span data-stu-id="9aa14-251">To resolve this error add a NuGet package reference to C#:</span></span>

```xml
<PackageReference Include="Microsoft.CSharp" Version="4.7.0" />
```

<span data-ttu-id="9aa14-252">Оставшиеся три ошибки указывают типы, определенные в сборке, на которую нет ссылок.</span><span class="sxs-lookup"><span data-stu-id="9aa14-252">The remaining three errors specify types that are defined in an assembly that isn't referenced.</span></span> <span data-ttu-id="9aa14-253">В частности, это следующие типы:</span><span class="sxs-lookup"><span data-stu-id="9aa14-253">Specifically these types:</span></span>

- `HttpServerUtilityBase`
- `RouteValueDictionary`
- `HttpRequestBase`

<span data-ttu-id="9aa14-254">Давайте рассмотрим каждую ошибку один за другой.</span><span class="sxs-lookup"><span data-stu-id="9aa14-254">Let's look at each error one by one.</span></span> <span data-ttu-id="9aa14-255">Первая ошибка возникает при попытке сослаться на `Server` свойство объекта `Controller` , который больше не существует.</span><span class="sxs-lookup"><span data-stu-id="9aa14-255">The first error occurs while trying to reference the `Server` property of `Controller`, which no longer exists.</span></span> <span data-ttu-id="9aa14-256">Цель операции — получить путь к файлу изображения в приложении:</span><span class="sxs-lookup"><span data-stu-id="9aa14-256">The goal of the operation is to get the path to an image file in the app:</span></span>

```csharp
if (item != null)
{
    var webRoot = Server.MapPath("~/Pics"); // compiler error on this line
    var path = Path.Combine(webRoot, item.PictureFileName);

    string imageFileExtension = Path.GetExtension(item.PictureFileName);
    string mimetype = GetImageMimeTypeFromImageFileExtension(imageFileExtension);

    var buffer = System.IO.File.ReadAllBytes(path);

    return File(buffer, mimetype);
}
```

<span data-ttu-id="9aa14-257">Существует два возможных решения этой проблемы.</span><span class="sxs-lookup"><span data-stu-id="9aa14-257">There are two possible solutions to this problem.</span></span> <span data-ttu-id="9aa14-258">Первый заключается в том, чтобы функциональные возможности оставались в таком виде.</span><span class="sxs-lookup"><span data-stu-id="9aa14-258">The first is to keep the functionality as it is.</span></span> <span data-ttu-id="9aa14-259">В этом случае вместо использования `Server.MapPath` следует использовать фиксированный путь, ссылающийся на файлы изображений в папке *wwwroot* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-259">In this case, rather than using `Server.MapPath`, a fixed path referencing the image files' location in *wwwroot* should be used.</span></span> <span data-ttu-id="9aa14-260">Кроме того, поскольку единственным предназначением этого метода действия является возврат статического файла изображения, ссылки на это действие в файлах представления можно обновить, чтобы ссылаться на статические файлы напрямую, что повышает производительность во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-260">Alternately, since the only purpose of this action method is to return a static image file, the references to this action in view files can be updated to reference the static files directly, which improves runtime performance.</span></span> <span data-ttu-id="9aa14-261">Так как ни одна обработка не выполняется в рамках этого действия, нет никакой причины не просто обслуживать файлы напрямую.</span><span class="sxs-lookup"><span data-stu-id="9aa14-261">Since no processing is being done as part of this action, there's no reason not to just serve the files directly.</span></span> <span data-ttu-id="9aa14-262">Если не тенабле обновить все ссылки на это действие, то действие может быть перезаписано для создания перенаправления к расположению статического файла.</span><span class="sxs-lookup"><span data-stu-id="9aa14-262">If it's not tenable to update all references to this action, the action could be rewritten to produce a redirect to the static file's location.</span></span>

<span data-ttu-id="9aa14-263">Следующие две ошибки возникают в одном и том же частном методе в той же строке кода:</span><span class="sxs-lookup"><span data-stu-id="9aa14-263">The next two errors both occur in the same private method in the same line of code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="9aa14-264">`this.Url`И, и `this.Request` вызывают ошибки компилятора.</span><span class="sxs-lookup"><span data-stu-id="9aa14-264">Both `this.Url` and `this.Request` cause compiler errors.</span></span> <span data-ttu-id="9aa14-265">Исходя из того, как используется этот код, его целью является создание ссылки на `PicController` действие, которое визуализирует файлы изображений.</span><span class="sxs-lookup"><span data-stu-id="9aa14-265">Looking at how this code is used, its purpose is to build a link to the `PicController` action that renders image files.</span></span> <span data-ttu-id="9aa14-266">То же самое, что было обнаружено, может быть заменено прямыми ссылками на статические файлы, расположенные в папке *wwwroot*.</span><span class="sxs-lookup"><span data-stu-id="9aa14-266">The same one we just discovered could probably be replaced with direct links to the static files located in *wwwroot*.</span></span> <span data-ttu-id="9aa14-267">Сейчас стоит закомментировать этот код и добавить `TODO:` комментарий для ссылки на него другим способом.</span><span class="sxs-lookup"><span data-stu-id="9aa14-267">For now, it's worth commenting out this code and adding a `TODO:` comment to reference the pics another way.</span></span>

<span data-ttu-id="9aa14-268">Стоит отметить, что базовый `Controller` класс, используемый `CatalogController` классом, в котором отображается этот код, по-прежнему ссылается на `System.Web.Mvc.Controller` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-268">It's worth noting that the base `Controller` class, used by the `CatalogController` class in which this code appears, is still referring to `System.Web.Mvc.Controller`.</span></span> <span data-ttu-id="9aa14-269">После обновления для использования ASP.NET Core будут устранены ошибки, которые необходимо устранить.</span><span class="sxs-lookup"><span data-stu-id="9aa14-269">There will undoubtedly be more errors to fix once we update this to use ASP.NET Core.</span></span> <span data-ttu-id="9aa14-270">Сначала удалите `using System.Web.Mvc;` строку из списка `using` операторов в `CatalogController` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-270">First, remove the `using System.Web.Mvc;` line from the list of `using` statements in `CatalogController`.</span></span> <span data-ttu-id="9aa14-271">Затем добавьте пакет NuGet `Microsoft.AspNetCore.Mvc` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-271">Next, add the NuGet package `Microsoft.AspNetCore.Mvc`.</span></span> <span data-ttu-id="9aa14-272">Наконец, добавьте `using Microsoft.AspNetCore.Mvc;` оператор и повторите сборку приложения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-272">Finally, add a `using Microsoft.AspNetCore.Mvc;` statement, and build the app again.</span></span>

<span data-ttu-id="9aa14-273">На этот раз возникает 16 ошибок:</span><span class="sxs-lookup"><span data-stu-id="9aa14-273">This time, there are 16 errors:</span></span>

- <span data-ttu-id="9aa14-274">`Include` не является допустимым аргументом именованного атрибута (2)</span><span class="sxs-lookup"><span data-stu-id="9aa14-274">`Include` is not a valid named attribute argument (2)</span></span>
- <span data-ttu-id="9aa14-275">`HttpStatusCodeResult` не найдено (3)</span><span class="sxs-lookup"><span data-stu-id="9aa14-275">`HttpStatusCodeResult` not found (3)</span></span>
- <span data-ttu-id="9aa14-276">`HttpNotFound` не существует (3)</span><span class="sxs-lookup"><span data-stu-id="9aa14-276">`HttpNotFound` does not exist (3)</span></span>
- <span data-ttu-id="9aa14-277">`SelectList` не найдено (8)</span><span class="sxs-lookup"><span data-stu-id="9aa14-277">`SelectList` not found (8)</span></span>

<span data-ttu-id="9aa14-278">Еще раз давайте рассмотрим эти ошибки один за другим.</span><span class="sxs-lookup"><span data-stu-id="9aa14-278">Once more, let's review these errors one by one.</span></span> <span data-ttu-id="9aa14-279">Сначала `SelectList` можно исправить, добавив `using Microsoft.AspNetCore.Mvc.Rendering;` , что не позволит устранить половину ошибок.</span><span class="sxs-lookup"><span data-stu-id="9aa14-279">First, `SelectList` can be fixed by adding `using Microsoft.AspNetCore.Mvc.Rendering;`, which eliminates half of the errors.</span></span>

<span data-ttu-id="9aa14-280">Все ссылки на `return HttpNotFound();` должны быть заменены на `return NotFound();` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-280">All references to `return HttpNotFound();` should be replaced with `return NotFound();`.</span></span>

<span data-ttu-id="9aa14-281">Все ссылки на `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` должны быть заменены на `return BadRequest();` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-281">All references to `return new HttpStatusCodeResult(HttpStatusCode.BadRequest);` should be replaced with `return BadRequest();`.</span></span>

<span data-ttu-id="9aa14-282">Это просто оставляет за собой использование `Include` `[Bind]` атрибута в нескольких методах действия, которые выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="9aa14-282">That just leaves the use of `Include` with a `[Bind]` attribute on a couple of action methods that look like this:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind(Include = "Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="9aa14-283">Приведенный выше код ограничивают привязку модели к свойствам, перечисленным в `Include` строке.</span><span class="sxs-lookup"><span data-stu-id="9aa14-283">The preceding code restricts model binding to the properties listed in the `Include` string.</span></span> <span data-ttu-id="9aa14-284">В ASP.NET Core MVC `[Bind]` атрибут по-прежнему существует, но больше не требует `Include =` аргумента.</span><span class="sxs-lookup"><span data-stu-id="9aa14-284">In ASP.NET Core MVC, the `[Bind]` attribute still exists, but no longer needs the `Include =` argument.</span></span> <span data-ttu-id="9aa14-285">Передайте список свойств непосредственно в `[Bind]` атрибут:</span><span class="sxs-lookup"><span data-stu-id="9aa14-285">Pass the list of properties directly to the `[Bind]` attribute:</span></span>

```csharp
[HttpPost]
[ValidateAntiForgeryToken]
public ActionResult Create([Bind("Id,Name,Description,Price,PictureFileName,CatalogTypeId,CatalogBrandId,AvailableStock,RestockThreshold,MaxStockThreshold,OnReorder")] CatalogItem catalogItem)
{
```

<span data-ttu-id="9aa14-286">После этих изменений проект компилируется еще раз.</span><span class="sxs-lookup"><span data-stu-id="9aa14-286">With these changes, the project compiles once more.</span></span> <span data-ttu-id="9aa14-287">Обычно рекомендуется использовать отдельные типы моделей для входных данных контроллера, вместо того чтобы использовать привязку модели непосредственно к модели предметной области или типам модели данных.</span><span class="sxs-lookup"><span data-stu-id="9aa14-287">It's generally a better practice to use separate model types for controller inputs, rather than using model binding directly to your domain model or data model types.</span></span>

## <a name="migrate-views"></a><span data-ttu-id="9aa14-288">Миграция представлений</span><span class="sxs-lookup"><span data-stu-id="9aa14-288">Migrate views</span></span>

<span data-ttu-id="9aa14-289">Два крупнейших ASP.NET Core функций MVC, связанных с представлениями, [Razor Pages](/aspnet/core/razor-pages/) и [вспомогательные функции тегов](/aspnet/core/mvc/views/tag-helpers/built-in/).</span><span class="sxs-lookup"><span data-stu-id="9aa14-289">The two biggest ASP.NET Core MVC features related to views are [Razor Pages](/aspnet/core/razor-pages/) and [Tag Helpers](/aspnet/core/mvc/views/tag-helpers/built-in/).</span></span> <span data-ttu-id="9aa14-290">Для первоначальной миграции мы не будем использовать ни одну из этих функций.</span><span class="sxs-lookup"><span data-stu-id="9aa14-290">For the initial migration, we won't use either feature.</span></span> <span data-ttu-id="9aa14-291">Однако следует помнить о возможностях, если продолжить поддержку приложения после его переноса.</span><span class="sxs-lookup"><span data-stu-id="9aa14-291">You should, however, keep the features in mind if you continue supporting the app once it's been migrated.</span></span> <span data-ttu-id="9aa14-292">Следующим шагом является копирование папки *views* из исходного проекта в новую.</span><span class="sxs-lookup"><span data-stu-id="9aa14-292">The next step is to copy the *Views* folder from the original project into the new one.</span></span> <span data-ttu-id="9aa14-293">После сборки возникает девять ошибок:</span><span class="sxs-lookup"><span data-stu-id="9aa14-293">After building, there are nine errors:</span></span>

- <span data-ttu-id="9aa14-294">HttpContext не существует (2)</span><span class="sxs-lookup"><span data-stu-id="9aa14-294">HttpContext does not exist (2)</span></span>
- <span data-ttu-id="9aa14-295">Скрипты не существуют (5)</span><span class="sxs-lookup"><span data-stu-id="9aa14-295">Scripts does not exist (5)</span></span>
- <span data-ttu-id="9aa14-296">Стили не существуют (1)</span><span class="sxs-lookup"><span data-stu-id="9aa14-296">Styles does not exist (1)</span></span>
- <span data-ttu-id="9aa14-297">Не удалось найти Хтмлстринг (1)</span><span class="sxs-lookup"><span data-stu-id="9aa14-297">HtmlString could not be found(1)</span></span>

<span data-ttu-id="9aa14-298">Исследование этих ошибок позволяет обнаружить, что большинство из них находятся в основном *_layout. cshtml*, с несколькими, относящимися к отрисовке скриптов и тегами стилей, а также при последнем перезапуске сервера, на котором размещено приложение.</span><span class="sxs-lookup"><span data-stu-id="9aa14-298">Investigating these errors finds that most of them are in the main *_Layout.cshtml*, with several related to rendering script and style tags, or displaying when the server hosting the app was last restarted.</span></span> <span data-ttu-id="9aa14-299">В следующем листинге кода показаны проблемные области в файле *_layout. cshtml* :</span><span class="sxs-lookup"><span data-stu-id="9aa14-299">The following code listing shows problem areas in the *_Layout.cshtml* file:</span></span>

```razor
// other lines omitted; only errors shown
@Styles.Render("~/Content/css")
@Scripts.Render("~/bundles/modernizr")

@{ var sessionInfo = new HtmlString($"{HttpContext.Current.Session["MachineName"]}, {HttpContext.Current.Session["SessionStartTime"]}");}

@Scripts.Render("~/bundles/jquery")
@Scripts.Render("~/bundles/bootstrap")
```

<span data-ttu-id="9aa14-300">Ссылка на Modernizr может быть удалена.</span><span class="sxs-lookup"><span data-stu-id="9aa14-300">The reference to Modernizr can be removed.</span></span> <span data-ttu-id="9aa14-301">Ссылки на загрузку и jQuery можно заменить ссылками CDN на соответствующую версию.</span><span class="sxs-lookup"><span data-stu-id="9aa14-301">The references to Bootstrap and jQuery can be replaced with CDN links to the appropriate version.</span></span>

<span data-ttu-id="9aa14-302">Заменить `@Styles.Render` строку на:</span><span class="sxs-lookup"><span data-stu-id="9aa14-302">Replace `@Styles.Render` line with:</span></span>

```html
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
```

<span data-ttu-id="9aa14-303">Замените последние две `Scripts.Render` строки на:</span><span class="sxs-lookup"><span data-stu-id="9aa14-303">Replace the last two `Scripts.Render` lines with:</span></span>

```html
<script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
```

<span data-ttu-id="9aa14-304">Наконец, после начальной загрузки `<link>` добавьте дополнительные `<link>` элементы для локальных стилей, используемых вашим приложением.</span><span class="sxs-lookup"><span data-stu-id="9aa14-304">Finally, after the Bootstrap `<link>`, add additional `<link>` elements for local styles your app uses.</span></span> <span data-ttu-id="9aa14-305">Для *ешоп* результат показан здесь:</span><span class="sxs-lookup"><span data-stu-id="9aa14-305">For *eShop*, the result is shown here:</span></span>

```html
<link rel="stylesheet" href="~/Content/custom.css" />
<link rel="stylesheet" href="~/Content/base.css" />
<link rel="stylesheet" href="~/Content/Site.css" />
```

<span data-ttu-id="9aa14-306">Чтобы определить порядок, в котором `<link>` должны отображаться элементы, просмотрите код HTML, отображаемый в исходном приложении.</span><span class="sxs-lookup"><span data-stu-id="9aa14-306">To determine the order in which the `<link>` elements should appear, look at your original app's rendered HTML.</span></span> <span data-ttu-id="9aa14-307">Кроме того, ознакомьтесь с *бундлеконфиг. CS*, который в образце *ешоп* содержит следующий код, указывающий соответствующую последовательность:</span><span class="sxs-lookup"><span data-stu-id="9aa14-307">Alternatively, review *BundleConfig.cs*, which for the *eShop* sample includes this code indicating the appropriate sequence:</span></span>

```csharp
bundles.Add(new StyleBundle("~/Content/css").Include(
          "~/Content/bootstrap.css",
          "~/Content/custom.css",
          "~/Content/base.css",
          "~/Content/site.css"));
```

<span data-ttu-id="9aa14-308">Повторное создание показывает еще одну ошибку при загрузке проверки jQuery в представлениях *создания* и *редактирования* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-308">Building again reveals one more error loading jQuery Validation on the *Create* and *Edit* views.</span></span> <span data-ttu-id="9aa14-309">Замените его следующим сценарием:</span><span class="sxs-lookup"><span data-stu-id="9aa14-309">Replace it with this script:</span></span>

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-validate/1.17.0/jquery.validate.min.js" integrity="sha512-O/nUTF5mdFkhEoQHFn9N5wmgYyW323JO6v8kr6ltSRKriZyTr/8417taVWeabVS4iONGk2V444QD0P2cwhuTkg==" crossorigin="anonymous"></script>
```

<span data-ttu-id="9aa14-310">Последнее, что нужно исправить в представлениях, — это ссылка на, `Session` чтобы показать, как долго выполняется приложение и на какой компьютер.</span><span class="sxs-lookup"><span data-stu-id="9aa14-310">The last thing to fix in the views is the reference to `Session` to display how long the app has been running, and on which machine.</span></span> <span data-ttu-id="9aa14-311">Эти данные можно отобразить непосредственно в *_layout. cshtml* сайта с помощью `System.Environment.MachineName` и `System.Diagnostics.Process.GetCurrentProcess().StartTime` :</span><span class="sxs-lookup"><span data-stu-id="9aa14-311">We can display this data directly in the site's *_Layout.cshtml* by using `System.Environment.MachineName` and `System.Diagnostics.Process.GetCurrentProcess().StartTime`:</span></span>

```razor
<section class="col-sm-6">
    <img class="esh-app-footer-text hidden-xs" src="~/images/main_footer_text.png" width="335" height="26" alt="footer text image" />
    <br />
<small>@Environment.MachineName - @System.Diagnostics.Process.GetCurrentProcess().StartTime.ToString() UTC</small>
</section>
```

<span data-ttu-id="9aa14-312">На этом этапе приложение будет успешно построено.</span><span class="sxs-lookup"><span data-stu-id="9aa14-312">At this point, the app once more builds successfully.</span></span> <span data-ttu-id="9aa14-313">Однако при попытке запустить его просто выдается *Hello World!*</span><span class="sxs-lookup"><span data-stu-id="9aa14-313">However, trying to run it just yields *Hello World!*</span></span> <span data-ttu-id="9aa14-314">Поскольку **пустой** шаблон ASP.NET Core настроен для вывода в ответ на любой запрос.</span><span class="sxs-lookup"><span data-stu-id="9aa14-314">because the **Empty** ASP.NET Core template is only configured to display that in response to any request.</span></span> <span data-ttu-id="9aa14-315">В следующем разделе я завершаю миграцию, настраивая приложение для использования ASP.NET Core MVC, включая внедрение и настройку зависимостей.</span><span class="sxs-lookup"><span data-stu-id="9aa14-315">In the next section, I complete the migration by configuring the app to use ASP.NET Core MVC, including dependency injection and configuration.</span></span> <span data-ttu-id="9aa14-316">После этого приложение должно запуститься.</span><span class="sxs-lookup"><span data-stu-id="9aa14-316">Once that's in place, the app should run.</span></span> <span data-ttu-id="9aa14-317">Затем будет пора исправить `TODO:` созданные ранее задачи.</span><span class="sxs-lookup"><span data-stu-id="9aa14-317">Then it will be time to fix the `TODO:` tasks that were created earlier.</span></span>

## <a name="migrate-app-startup-components"></a><span data-ttu-id="9aa14-318">Перенос компонентов запуска приложений</span><span class="sxs-lookup"><span data-stu-id="9aa14-318">Migrate app startup components</span></span>

<span data-ttu-id="9aa14-319">Последний шаг миграции заключается в том, чтобы выполнить задачи запуска приложения из *Global. asax* и классов, которые он вызывает, и перенести их в ASP.NET Core эквиваленты.</span><span class="sxs-lookup"><span data-stu-id="9aa14-319">The last migration step is to take the app startup tasks from *Global.asax*, and the classes it calls, and migrate these to their ASP.NET Core equivalents.</span></span> <span data-ttu-id="9aa14-320">Эти задачи включают в себя настройку модели MVC, настройку внедрения зависимостей и работу с новой системой конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9aa14-320">These tasks include configuration of MVC itself, setting up dependency injection, and working with the new configuration system.</span></span> <span data-ttu-id="9aa14-321">В ASP.NET Core эти задачи обрабатываются в файле *Startup. CS* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-321">In ASP.NET Core, these tasks are handled in the *Startup.cs* file.</span></span>

### <a name="configure-mvc"></a><span data-ttu-id="9aa14-322">Настройка MVC</span><span class="sxs-lookup"><span data-stu-id="9aa14-322">Configure MVC</span></span>

<span data-ttu-id="9aa14-323">Исходное приложение ASP.NET MVC содержит следующий код в `Application_Start` *Global. asax*, который запускается при запуске приложения:</span><span class="sxs-lookup"><span data-stu-id="9aa14-323">The original ASP.NET MVC app has the following code in its `Application_Start` in *Global.asax*, which runs when the app starts up:</span></span>

```csharp
protected void Application_Start()
{
    container = RegisterContainer();
    AreaRegistration.RegisterAllAreas();
    FilterConfig.RegisterGlobalFilters(GlobalFilters.Filters);
    RouteConfig.RegisterRoutes(RouteTable.Routes);
    BundleConfig.RegisterBundles(BundleTable.Bundles);
    ConfigDataBase();
}
```

<span data-ttu-id="9aa14-324">Просматривая эти строки по одному, `RegisterContainer` метод настраивает внедрение зависимостей, которое будет перенесено ниже.</span><span class="sxs-lookup"><span data-stu-id="9aa14-324">Looking at these lines one by one, the `RegisterContainer` method sets up dependency injection, which will be ported below.</span></span> <span data-ttu-id="9aa14-325">Следующие три строки настраивают различные части MVC: области, фильтры и маршруты.</span><span class="sxs-lookup"><span data-stu-id="9aa14-325">The next three lines configure different parts of MVC: areas, filters, and routes.</span></span> <span data-ttu-id="9aa14-326">Пакеты заменяются статическими файлами в перенесенном приложении.</span><span class="sxs-lookup"><span data-stu-id="9aa14-326">Bundles are replaced by static files in the ported app.</span></span> <span data-ttu-id="9aa14-327">В последней строке настраивается доступ к данным приложения, которое будет показано в следующем разделе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-327">The last line sets up data access for the app, which will be shown in a later section.</span></span>

<span data-ttu-id="9aa14-328">Поскольку это приложение на самом деле не использует области, нет ничего делать, чтобы перенести вызов регистрации в области.</span><span class="sxs-lookup"><span data-stu-id="9aa14-328">Since this app isn't actually using areas, there's nothing that needs to be done to migrate the area registration call.</span></span> <span data-ttu-id="9aa14-329">Если приложению необходимо выполнить миграцию областей, [Документация укажет, как настроить области в ASP.NET Core](/aspnet/core/mvc/controllers/areas).</span><span class="sxs-lookup"><span data-stu-id="9aa14-329">If your app does need to migrate areas, the [docs specify how to configure areas in ASP.NET Core](/aspnet/core/mvc/controllers/areas).</span></span>

<span data-ttu-id="9aa14-330">Вызов для регистрации глобальных фильтров вызывает вспомогательное приложение для `FilterConfig` класса в папке *App_Start* приложения:</span><span class="sxs-lookup"><span data-stu-id="9aa14-330">The call to register global filters invokes a helper on the `FilterConfig` class in the app's *App_Start* folder:</span></span>

```csharp
public static void RegisterGlobalFilters(GlobalFilterCollection filters)
{
    filters.Add(new HandleErrorAttribute());
}
```

<span data-ttu-id="9aa14-331">Единственным атрибутом, добавленным в приложение, является фильтр MVC ASP.NET `HandleErrorAttribute` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-331">The only attribute added to the app is the ASP.NET MVC filter, `HandleErrorAttribute`.</span></span> <span data-ttu-id="9aa14-332">Этот фильтр гарантирует, что при возникновении исключения в составе запроса отображаются действие и представление по умолчанию, а не сведения об исключении.</span><span class="sxs-lookup"><span data-stu-id="9aa14-332">This filter ensures that when an exception occurs as part of a request, a default action and view are displayed, rather than the exception details.</span></span> <span data-ttu-id="9aa14-333">В ASP.NET Core эти же функции выполняются по `UseExceptionHandler` промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="9aa14-333">In ASP.NET Core, this same functionality is performed by the `UseExceptionHandler` middleware.</span></span> <span data-ttu-id="9aa14-334">Подробные сообщения об ошибках по умолчанию не включены.</span><span class="sxs-lookup"><span data-stu-id="9aa14-334">The detailed error messages aren't enabled by default.</span></span> <span data-ttu-id="9aa14-335">Они должны быть настроены с использованием по `UseDeveloperExceptionPage` промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="9aa14-335">They must be configured using the `UseDeveloperExceptionPage` middleware.</span></span> <span data-ttu-id="9aa14-336">Чтобы настроить такое поведение в соответствии с исходным приложением, необходимо добавить следующий код в начало `Configure` метода в *Startup. CS*:</span><span class="sxs-lookup"><span data-stu-id="9aa14-336">To configure this behavior to match the original app, the following code must be added to the start of the `Configure` method in *Startup.cs*:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
    }
    // ...
}
```

<span data-ttu-id="9aa14-337">Это берет на себя единственный фильтр, используемый приложением Ешоп, и в данном случае он выполнялся с помощью встроенного по промежуточного слоя.</span><span class="sxs-lookup"><span data-stu-id="9aa14-337">This takes care of the only filter used by the eShop app, and in this case it was done by using built-in middleware.</span></span> <span data-ttu-id="9aa14-338">Если у вас есть глобальные фильтры, которые должны быть настроены в приложении, это делается при добавлении MVC в `ConfigureServices` метод, который показан далее в этой главе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-338">If you have global filters that must be configured in your app, this is done when MVC is added in the `ConfigureServices` method, which is shown later in this chapter.</span></span>

<span data-ttu-id="9aa14-339">Последняя часть логики, относящейся к MVC, которую необходимо перенести, — это маршруты приложения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9aa14-339">The last piece of MVC-related logic that needs to be migrated are the app's default routes.</span></span> <span data-ttu-id="9aa14-340">Вызов `RouteConfig.RegisterRoutes(RouteTable.Routes)` метода передает таблицу маршрутов MVC в `RegisterRoutes` вспомогательный метод, где при запуске приложения выполняется следующий код:</span><span class="sxs-lookup"><span data-stu-id="9aa14-340">The call to `RouteConfig.RegisterRoutes(RouteTable.Routes)` passes the MVC route table to the `RegisterRoutes` helper method, where the following code is executed when the app starts up:</span></span>

```csharp
public static void RegisterRoutes(RouteCollection routes)
{
    routes.MapMvcAttributeRoutes();
    routes.IgnoreRoute("{resource}.axd/{*pathInfo}");

    routes.MapRoute(
        name: "Default",
        url: "{controller}/{action}/{id}",
        defaults: new { controller = "Catalog", action = "Index", id = UrlParameter.Optional }
    );
}
```

<span data-ttu-id="9aa14-341">Переводя этот код в построчную, первая строка настраивает поддержку для маршрутов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="9aa14-341">Taking this code line-by-line, the first line sets up support for attribute routes.</span></span> <span data-ttu-id="9aa14-342">Эта возможность встроена в ASP.NET Core, поэтому ее не нужно настраивать отдельно.</span><span class="sxs-lookup"><span data-stu-id="9aa14-342">This is built into ASP.NET Core, so it's unnecessary to configure it separately.</span></span> <span data-ttu-id="9aa14-343">Аналогично, файлы *{Resource}. axd* не используются с ASP.NET Core, поэтому нет необходимости пропускать такие маршруты.</span><span class="sxs-lookup"><span data-stu-id="9aa14-343">Likewise, *{resource}.axd* files aren't used with ASP.NET Core, so there's no need to ignore such routes.</span></span> <span data-ttu-id="9aa14-344">`MapRoute`Метод настраивает значение по умолчанию для MVC, в котором используется стандартный `{controller}/{action}/{id}` шаблон маршрута.</span><span class="sxs-lookup"><span data-stu-id="9aa14-344">The `MapRoute` method configures the default for MVC, which uses the typical `{controller}/{action}/{id}` route template.</span></span> <span data-ttu-id="9aa14-345">Он также задает значения по умолчанию для этого шаблона, так что используется `CatalogController` контроллером по умолчанию, а `Index` метод является действием по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="9aa14-345">It also specifies the defaults for this template, such that the `CatalogController` is the default controller used and the `Index` method is the default action.</span></span> <span data-ttu-id="9aa14-346">Большие приложения часто содержат дополнительные вызовы для `MapRoute` настройки дополнительных маршрутов.</span><span class="sxs-lookup"><span data-stu-id="9aa14-346">Larger apps will frequently include more calls to `MapRoute` to set up additional routes.</span></span>

<span data-ttu-id="9aa14-347">ASP.NET Core MVC поддерживает [обычную маршрутизацию и маршрутизацию атрибутов](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="9aa14-347">ASP.NET Core MVC supports [conventional routing and attribute routing](/aspnet/core/mvc/controllers/routing?preserve-view=true&view=aspnetcore-2.2).</span></span> <span data-ttu-id="9aa14-348">Обычная маршрутизация аналогична настройке таблицы маршрутов в `RegisterRoutes` приведенном выше методе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-348">Conventional routing is analogous to how the route table is configured in the `RegisterRoutes` method listed previously.</span></span> <span data-ttu-id="9aa14-349">Чтобы настроить стандартную маршрутизацию с использованием маршрута по умолчанию, аналогичного используемому в приложении *ешоп* , добавьте следующий код в конец `Configure` метода в *Startup. CS*:</span><span class="sxs-lookup"><span data-stu-id="9aa14-349">To set up conventional routing with a default route like the one used in the *eShop* app, add the following code to the bottom of the `Configure` method in *Startup.cs*:</span></span>

```csharp
app.UseMvc(routes =>
{
   routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
});
```

> [!NOTE]
> <span data-ttu-id="9aa14-350">При использовании ASP.NET Core 3,0 и более поздних версий это значение изменяется на использование конечных точек.</span><span class="sxs-lookup"><span data-stu-id="9aa14-350">With ASP.NET Core 3.0 and later, this is changed to use endpoints.</span></span> <span data-ttu-id="9aa14-351">Чтобы начальный порт ASP.NET Core 2,2, это правильный синтаксис для сопоставления стандартных маршрутов.</span><span class="sxs-lookup"><span data-stu-id="9aa14-351">For the initial port to ASP.NET Core 2.2, this is the proper syntax for mapping conventional routes.</span></span>

<span data-ttu-id="9aa14-352">После внесения этих изменений `Configure` метод почти выполняется.</span><span class="sxs-lookup"><span data-stu-id="9aa14-352">With these changes in place, the `Configure` method is almost done.</span></span> <span data-ttu-id="9aa14-353">Метод исходного шаблона `app.Run` , который выводит *Hello World!*</span><span class="sxs-lookup"><span data-stu-id="9aa14-353">The original template's `app.Run` method that prints *Hello World!*</span></span> <span data-ttu-id="9aa14-354">следует удалить.</span><span class="sxs-lookup"><span data-stu-id="9aa14-354">should be deleted.</span></span> <span data-ttu-id="9aa14-355">На этом этапе метод показан ниже:</span><span class="sxs-lookup"><span data-stu-id="9aa14-355">At this point, the method is as shown here:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }
    else
    {
        app.UseExceptionHandler("/Home/Error");
    }

    app.UseStaticFiles();

    app.UseMvc(routes =>
    {
        routes.MapRoute("default", "{controller=Catalog}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="9aa14-356">Теперь пора настроить службы MVC, а затем оставшуюся часть поддержки внедрения зависимостей (DI) в приложении.</span><span class="sxs-lookup"><span data-stu-id="9aa14-356">Now it's time to configure MVC services, followed by the rest of the app's support for dependency injection (DI).</span></span> <span data-ttu-id="9aa14-357">До сих пор метод проекта *ешоппортед* `ConfigureServices` остается пустым.</span><span class="sxs-lookup"><span data-stu-id="9aa14-357">So far, the *eShopPorted* project's `ConfigureServices` method has remained empty.</span></span> <span data-ttu-id="9aa14-358">Теперь пора приступить к заполнению.</span><span class="sxs-lookup"><span data-stu-id="9aa14-358">Now it's time to start populating it.</span></span>

<span data-ttu-id="9aa14-359">Сначала необходимо добавить ASP.NET Core MVC для правильной работы.</span><span class="sxs-lookup"><span data-stu-id="9aa14-359">First, to get ASP.NET Core MVC to work properly, it needs to be added:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
}
```

<span data-ttu-id="9aa14-360">Приведенный выше код является минимальной конфигурацией, необходимой для получения работоспособных компонентов MVC.</span><span class="sxs-lookup"><span data-stu-id="9aa14-360">The preceding code is the minimal configuration required to get MVC features working.</span></span> <span data-ttu-id="9aa14-361">Существует множество дополнительных функций, которые можно настроить на основе этого вызова (некоторые из которых подробно описаны далее в этой главе), но теперь для этого достаточно будет создать приложение.</span><span class="sxs-lookup"><span data-stu-id="9aa14-361">There are many additional features that can be configured from this call (some of which are detailed later in this chapter), but for now this will suffice to build the app.</span></span> <span data-ttu-id="9aa14-362">Теперь он правильно направляет запрос по умолчанию, но, поскольку мы еще не настроили DI, во время активации возникает ошибка `CatalogController` , поскольку реализация типа `ICatalogService` еще не предоставлена.</span><span class="sxs-lookup"><span data-stu-id="9aa14-362">Running it now routes the default request properly, but since we've not yet configured DI, an error occurs while activating `CatalogController`, because no implementation of type `ICatalogService` has been provided yet.</span></span> <span data-ttu-id="9aa14-363">Сейчас мы вернемся к настройке MVC.</span><span class="sxs-lookup"><span data-stu-id="9aa14-363">We'll return to configure MVC further in a moment.</span></span> <span data-ttu-id="9aa14-364">Сейчас выполним миграцию внедрения зависимостей приложения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-364">For now, let's migrate the app's dependency injection.</span></span>

#### <a name="migrate-dependency-injection-configuration"></a><span data-ttu-id="9aa14-365">Миграция конфигурации внедрения зависимостей</span><span class="sxs-lookup"><span data-stu-id="9aa14-365">Migrate dependency injection configuration</span></span>

<span data-ttu-id="9aa14-366">Файл *Global. asax* исходного приложения определяет следующий метод, который вызывается при запуске приложения:</span><span class="sxs-lookup"><span data-stu-id="9aa14-366">The original app's *Global.asax* file defines the following method, called when the app starts up:</span></span>

```csharp
protected IContainer RegisterContainer()
{
  var builder = new ContainerBuilder();

  builder.RegisterControllers(typeof(MvcApplication).Assembly);

  var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
  builder.RegisterModule(new ApplicationModule(mockData));

  var container = builder.Build();
  DependencyResolver.SetResolver(new AutofacDependencyResolver(container));

  return container;
}
```

<span data-ttu-id="9aa14-367">Этот код настраивает контейнер [Autofac](https://autofac.org/) , считывает параметр конфигурации, чтобы определить, следует ли использовать реальные или фиктивные данные, и передает этот параметр в модуль Autofac (находится в каталоге */модулес* приложения).</span><span class="sxs-lookup"><span data-stu-id="9aa14-367">This code configures an [Autofac](https://autofac.org/) container, reads a config setting to determine whether real or mock data should be used, and passes this setting into an Autofac module (found in the app's */Modules* directory).</span></span> <span data-ttu-id="9aa14-368">К счастью, Autofac поддерживает .NET Core, поэтому модуль можно перенести напрямую.</span><span class="sxs-lookup"><span data-stu-id="9aa14-368">Fortunately, Autofac supports .NET Core, so the module can be migrated directly.</span></span> <span data-ttu-id="9aa14-369">Скопируйте папку в новый проект и обновите пространство имен класса, и оно должно быть скомпилировано.</span><span class="sxs-lookup"><span data-stu-id="9aa14-369">Copy the folder into the new project and updates the class's namespace and it should compile.</span></span>

<span data-ttu-id="9aa14-370">ASP.NET Core имеет встроенную поддержку внедрения зависимостей, но при необходимости можно с легкостью подключить сторонний контейнер, например Autofac.</span><span class="sxs-lookup"><span data-stu-id="9aa14-370">ASP.NET Core has built-in support for dependency injection, but you can wire up a third-party container such as Autofac easily if necessary.</span></span> <span data-ttu-id="9aa14-371">В этом случае, поскольку приложение уже настроено для использования Autofac, самым простым решением является поддержание его использования.</span><span class="sxs-lookup"><span data-stu-id="9aa14-371">In this case, since the app is already configured to use Autofac, the simplest solution is to maintain its usage.</span></span> <span data-ttu-id="9aa14-372">Для этого `ConfigureServices` необходимо изменить сигнатуру метода, чтобы она возвращала `IServiceProvider` , а экземпляр контейнера Autofac должен быть настроен и возвращен из метода.</span><span class="sxs-lookup"><span data-stu-id="9aa14-372">To do so, the `ConfigureServices` method signature must be modified to return an `IServiceProvider`, and the Autofac container instance must be configured and returned from the method.</span></span>

<span data-ttu-id="9aa14-373">**Примечание.** В .NET Core 3,0 и более поздних версиях процесс интеграции стороннего контейнера внедрения изменился.</span><span class="sxs-lookup"><span data-stu-id="9aa14-373">**Note:** In .NET Core 3.0 and later, the process for integrating a third-party DI container has changed.</span></span>

<span data-ttu-id="9aa14-374">Часть настройки Autofac требует вызова `builder.Populate(services)` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-374">Part of configuring Autofac requires a call to `builder.Populate(services)`.</span></span> <span data-ttu-id="9aa14-375">Это расширение находится в `Autofac.Extensions.DependencyInjection` пакете NuGet, которое необходимо установить перед компиляцией кода.</span><span class="sxs-lookup"><span data-stu-id="9aa14-375">This extension is found in the `Autofac.Extensions.DependencyInjection` NuGet package, which must be installed before the code will compile.</span></span>

<span data-ttu-id="9aa14-376">После изменения `ConfigureServices` для настройки контейнера Autofac используется новый метод, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="9aa14-376">After modifying `ConfigureServices` to configure an Autofac container, the new method is as shown here:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    bool useMockData = true; // TODO: read from config
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

<span data-ttu-id="9aa14-377">Пока параметр для `useMockData` имеет значение `true` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-377">For now, the setting for `useMockData` is set to `true`.</span></span> <span data-ttu-id="9aa14-378">Этот параметр будет считан из конфигурации через некоторое время.</span><span class="sxs-lookup"><span data-stu-id="9aa14-378">This setting will be read from configuration in a moment.</span></span> <span data-ttu-id="9aa14-379">На этом этапе приложение компилируется и должно успешно загружаться при запуске, как показано на рис. 4-12.</span><span class="sxs-lookup"><span data-stu-id="9aa14-379">At this point, the app compiles and should load successfully when run, as shown in Figure 4-12.</span></span>

![Рис. 4-12](media/Figure4-12.png)

<span data-ttu-id="9aa14-381">**Рис. 4-12**.</span><span class="sxs-lookup"><span data-stu-id="9aa14-381">**Figure 4-12.**</span></span> <span data-ttu-id="9aa14-382">Перенесенное приложение *ешоп* , работающее локально с фиктивными данными.</span><span class="sxs-lookup"><span data-stu-id="9aa14-382">Ported *eShop* app running locally with mock data.</span></span>

#### <a name="migrate-app-settings"></a><span data-ttu-id="9aa14-383">Перенос параметров приложения</span><span class="sxs-lookup"><span data-stu-id="9aa14-383">Migrate app settings</span></span>

<span data-ttu-id="9aa14-384">В ASP.NET Core используется новая [система конфигурации](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2), которая по умолчанию использует *appsettings.jsв* файле.</span><span class="sxs-lookup"><span data-stu-id="9aa14-384">ASP.NET Core uses a new [configuration system](/aspnet/core/fundamentals/configuration/?preserve-view=true&view=aspnetcore-2.2), which by default leverages an *appsettings.json* file.</span></span> <span data-ttu-id="9aa14-385">При использовании `CreateDefaultBuilder` в *Program. CS* конфигурация по умолчанию уже настроена в приложении.</span><span class="sxs-lookup"><span data-stu-id="9aa14-385">By using `CreateDefaultBuilder` in *Program.cs*, the default configuration is already set up in the app.</span></span> <span data-ttu-id="9aa14-386">Для доступа к конфигурации классы просто должны запросить его в своем конструкторе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-386">To access configuration, classes just need to request it in their constructor.</span></span> <span data-ttu-id="9aa14-387">`Startup`Класс не является исключением.</span><span class="sxs-lookup"><span data-stu-id="9aa14-387">The `Startup` class is no exception.</span></span> <span data-ttu-id="9aa14-388">Чтобы начать доступ к конфигурации в `Startup` и остальной части приложения, запросите экземпляр `IConfiguration` из своего конструктора:</span><span class="sxs-lookup"><span data-stu-id="9aa14-388">To start accessing configuration in `Startup` and the rest of the app, request an instance of `IConfiguration` from its constructor:</span></span>

```csharp
public Startup(IConfiguration configuration)
{
    Configuration = configuration;
}

public IConfiguration Configuration { get; }
```

<span data-ttu-id="9aa14-389">Исходное приложение, на которое ссылаются параметры с помощью `ConfigurationManager.AppSettings` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-389">The original app referenced its settings using `ConfigurationManager.AppSettings`.</span></span> <span data-ttu-id="9aa14-390">Быстрый поиск всех ссылок этого термина дает набор параметров, необходимых для нового приложения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-390">A quick search for all references of this term yields the set of settings the new app needs.</span></span> <span data-ttu-id="9aa14-391">Существует только два:</span><span class="sxs-lookup"><span data-stu-id="9aa14-391">There are only two:</span></span>

- `UseMockData`
- `UseCustomizationData`

<span data-ttu-id="9aa14-392">Если приложение имеет более сложную конфигурацию, особенно если он использует пользовательские разделы конфигурации, то, вероятно, потребуется создать и привязать объекты к разным частям конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-392">If your app has more complex configuration, especially if it's using custom configuration sections, you'll probably want to create and bind objects to different parts of your app's configuration.</span></span> <span data-ttu-id="9aa14-393">Затем доступ к этим типам можно получить с помощью [шаблона параметров](../../core/extensions/options.md).</span><span class="sxs-lookup"><span data-stu-id="9aa14-393">These types can then be accessed using the [options pattern](../../core/extensions/options.md).</span></span> <span data-ttu-id="9aa14-394">Однако, как отмечалось в упоминаемом документе, этот шаблон не должен использоваться в `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-394">However, as noted in the referenced doc, this pattern shouldn't be used in `ConfigureServices`.</span></span> <span data-ttu-id="9aa14-395">Вместо этого перенесенное приложение будет ссылаться на `UseMockData` значение конфигурации напрямую.</span><span class="sxs-lookup"><span data-stu-id="9aa14-395">Instead the ported app will reference the `UseMockData` configuration value directly.</span></span>

<span data-ttu-id="9aa14-396">Сначала измените файл перенесенного приложения `appsettings.json` и добавьте два параметра в корневой каталог:</span><span class="sxs-lookup"><span data-stu-id="9aa14-396">First, modify the ported app's `appsettings.json` file and add the two settings in the root:</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "true",
  "UseCustomizationData" :  "true"
}
```

<span data-ttu-id="9aa14-397">Теперь измените, `ConfigureServices` чтобы получить доступ к `UseMockData` параметру из `Configuration` Свойства (где ранее мы установили значение `true` ):</span><span class="sxs-lookup"><span data-stu-id="9aa14-397">Now, modify `ConfigureServices` to access the `UseMockData` setting from the `Configuration` property (where previously we set the value to `true`):</span></span>

```csharp
  bool useMockData = Configuration.GetValue<bool>("UseMockData");
```

<span data-ttu-id="9aa14-398">На этом этапе параметр извлекается из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9aa14-398">At this point, the setting is pulled from configuration.</span></span> <span data-ttu-id="9aa14-399">Другой параметр, `UseCustomizationData` , используется `CatalogDBInitializer` классом.</span><span class="sxs-lookup"><span data-stu-id="9aa14-399">The other setting, `UseCustomizationData`, is used by the `CatalogDBInitializer` class.</span></span> <span data-ttu-id="9aa14-400">При первом переносе этого класса вы заносите в комментарий доступ к `ConfigurationManager.AppSettings["UseCustomizationData"]` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-400">When you first ported this class, you commented out the access to `ConfigurationManager.AppSettings["UseCustomizationData"]`.</span></span> <span data-ttu-id="9aa14-401">Пришло время изменить его, чтобы использовать ASP.NET Coreную конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="9aa14-401">Now it's time to modify it to use ASP.NET Core configuration.</span></span> <span data-ttu-id="9aa14-402">Измените конструктор следующим образом `CatalogDBInitializer` :</span><span class="sxs-lookup"><span data-stu-id="9aa14-402">Modify the constructor of `CatalogDBInitializer` as follows:</span></span>

```csharp
  // add using Microsoft.Extensions.Configuration
  public CatalogDBInitializer(CatalogItemHiLoGenerator indexGenerator,
      IConfiguration configuration)
  {
      this.indexGenerator = indexGenerator;
      useCustomizationData = configuration.GetValue<bool>("UseCustomizationData");
  }
```

<span data-ttu-id="9aa14-403">Любой доступ к конфигурации в веб-приложении следует изменить таким образом, чтобы использовать новый `IConfiguration` тип.</span><span class="sxs-lookup"><span data-stu-id="9aa14-403">All access to configuration within the web app should be modified in this manner to use the new `IConfiguration` type.</span></span> <span data-ttu-id="9aa14-404">Зависимости, которым требуется доступ к платформа .NET Framework конфигурации, могут включать такие параметры в файл *app.config* , добавленный в веб-проект.</span><span class="sxs-lookup"><span data-stu-id="9aa14-404">Dependencies that require access to .NET Framework configuration can include such settings in an *app.config* file added to the web project.</span></span> <span data-ttu-id="9aa14-405">Зависимые проекты могут работать с `ConfigurationManager` параметрами доступа и не должны требовать изменений, если они уже используют этот подход.</span><span class="sxs-lookup"><span data-stu-id="9aa14-405">The dependent projects can work with `ConfigurationManager` to access settings, and shouldn't require any changes if they already use this approach.</span></span> <span data-ttu-id="9aa14-406">Однако, поскольку ASP.NET Core приложения выполняются как собственные исполняемые файлы, они не ссылаются на *web.config* , а не *app.config*. При переносе параметров из файла *web.config* устаревших приложений в новый файл *app.config* в приложении ASP.NET Core, компоненты, использующиеся `ConfigurationManager` для доступа к их параметрам, будут продолжать работать правильно.</span><span class="sxs-lookup"><span data-stu-id="9aa14-406">However, since ASP.NET Core apps run as their own executable, they don't reference *web.config* but rather *app.config*. By migrating settings from the legacy app's *web.config* file to a new *app.config* file in the ASP.NET Core app, components that use `ConfigurationManager` to access their settings will continue to function properly.</span></span>

<span data-ttu-id="9aa14-407">Миграция приложения почти завершена.</span><span class="sxs-lookup"><span data-stu-id="9aa14-407">The app's migration is nearly complete.</span></span> <span data-ttu-id="9aa14-408">Единственная оставшаяся задача — конфигурация доступа к данным.</span><span class="sxs-lookup"><span data-stu-id="9aa14-408">The only remaining task is data access configuration.</span></span>
  
## <a name="data-access-considerations"></a><span data-ttu-id="9aa14-409">Рекомендации по доступу к данным</span><span class="sxs-lookup"><span data-stu-id="9aa14-409">Data access considerations</span></span>

<span data-ttu-id="9aa14-410">ASP.NET Core приложения, работающие на платформа .NET Framework, могут продолжать использовать Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="9aa14-410">ASP.NET Core apps running on .NET Framework can continue to leverage Entity Framework (EF).</span></span> <span data-ttu-id="9aa14-411">При выполнении добавочной миграции получение приложения, работающего с EF 6, перед попыткой переноса доступа к данным для использования EF Core может быть целесообразным.</span><span class="sxs-lookup"><span data-stu-id="9aa14-411">If performing an incremental migration, getting the app working with EF 6 before trying to port its data access to use EF Core may be worthwhile.</span></span> <span data-ttu-id="9aa14-412">Таким образом, все проблемы, связанные с миграцией приложения, можно определить и устранить до начала другого блока усилий по миграции.</span><span class="sxs-lookup"><span data-stu-id="9aa14-412">In this way, any problems with the app's migration can be identified and addressed before another block of migration effort is begun.</span></span>

<span data-ttu-id="9aa14-413">Как только это происходит, Настройка EF 6 в примере миграции Ешоп не требует специальной работы, так как эта работа была выполнена в Autofac `ApplicationModule` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-413">As it happens, configuring EF 6 in the eShop sample migration doesn't require any special work, since this work was performed in the Autofac `ApplicationModule`.</span></span> <span data-ttu-id="9aa14-414">Единственная проблема заключается в том, что в настоящее время `CatalogDBContext` класс пытается считать строку подключения из *web.config*. Чтобы устранить эту эту необходимость, необходимо добавить сведения о подключении в *appsettings.js*.</span><span class="sxs-lookup"><span data-stu-id="9aa14-414">The only problem is that currently the `CatalogDBContext` class tries to read its connection string from *web.config*. To address this, the connection details need to be added to *appsettings.json*.</span></span> <span data-ttu-id="9aa14-415">После этого строка подключения должна быть передана в `CatalogDBContext` момент ее создания.</span><span class="sxs-lookup"><span data-stu-id="9aa14-415">Then the connection string must be passed into `CatalogDBContext` when it's created.</span></span>

<span data-ttu-id="9aa14-416">Обновите *appsettings.jsв* , чтобы включить строку подключения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-416">Update the *appsettings.json* to include the connection string.</span></span> <span data-ttu-id="9aa14-417">Полный файл указан здесь:</span><span class="sxs-lookup"><span data-stu-id="9aa14-417">The full file is listed here:</span></span>

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=eShopPorted;Trusted_Connection=True;MultipleActiveResultSets=true"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Warning"
    }
  },
  "AllowedHosts": "*",
  "UseMockData": "false",
  "UseCustomizationData": "true"
}
```

<span data-ttu-id="9aa14-418">Строка подключения должна быть передана в конструктор при `DbContext` создании.</span><span class="sxs-lookup"><span data-stu-id="9aa14-418">The connection string must be passed into the constructor when the `DbContext` is created.</span></span> <span data-ttu-id="9aa14-419">Так как экземпляры создаются с помощью Autofac, необходимо внести изменения в `ApplicationModule` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-419">Since the instances are created by Autofac, the change needs to be made in `ApplicationModule`.</span></span> <span data-ttu-id="9aa14-420">Измените модуль, чтобы в нем перестать в `connectionString` конструктор и назначить его полю.</span><span class="sxs-lookup"><span data-stu-id="9aa14-420">Modify the module to take in a `connectionString` in its constructor and assign it to a field.</span></span> <span data-ttu-id="9aa14-421">Затем измените регистрацию для `CatalogDBContext` , чтобы добавить строку подключения в качестве параметра:</span><span class="sxs-lookup"><span data-stu-id="9aa14-421">Then modify the registration for `CatalogDBContext` to add connection string as a parameter:</span></span>

```csharp
builder.RegisterType<CatalogDBContext>()
  .WithParameter("connectionString", _connectionString)
  .InstancePerLifetimeScope();
```

<span data-ttu-id="9aa14-422">Параметр также необходимо добавить в новую перегрузку конструктора `CatalogDBContext` :</span><span class="sxs-lookup"><span data-stu-id="9aa14-422">The parameter must also be added to a new constructor overload in `CatalogDBContext` itself:</span></span>

```csharp
public CatalogDBContext(string connectionString) : base(connectionString)
{
}
```

<span data-ttu-id="9aa14-423">Наконец, `ConfigureServices` необходимо прочитать строку подключения из `Config` и передать ее в экземпляр, `ApplicationModule` когда он его создает.</span><span class="sxs-lookup"><span data-stu-id="9aa14-423">Finally, `ConfigureServices` must read the connection string from `Config` and pass it into the `ApplicationModule` when it instantiates it:</span></span>

```csharp
bool useMockData = Configuration.GetValue<bool>("UseMockData");
string connectionString = Configuration.GetConnectionString("DefaultConnection");
builder.RegisterModule(new ApplicationModule(useMockData, connectionString));
```

<span data-ttu-id="9aa14-424">После выполнения этого кода приложение выполняется, как и раньше, подключаясь к базе данных SQL Server, когда `UseMockData` имеет значение `false` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-424">With this code in place, the app runs as it did before, connecting to a SQL Server database when `UseMockData` is `false`.</span></span>

<span data-ttu-id="9aa14-425">На этом этапе приложение может быть развернуто и запущено в рабочей среде, преобразованное в ASP.NET Core, но по-прежнему выполняется на платформа .NET Framework и EF 6.</span><span class="sxs-lookup"><span data-stu-id="9aa14-425">The app can be deployed and run in production at this point, converted to ASP.NET Core but still running on .NET Framework and EF 6.</span></span> <span data-ttu-id="9aa14-426">При необходимости можно выполнить миграцию приложения на .NET Core и Entity Framework Core, что обеспечит дополнительные преимущества, описанные в предыдущих главах.</span><span class="sxs-lookup"><span data-stu-id="9aa14-426">If desired, the app can be migrated to run on .NET Core and Entity Framework Core, which will bring additional advantages described in earlier chapters.</span></span> <span data-ttu-id="9aa14-427">В этой документации, относящейся к Entity Framework, [сравниваются EF Core и EF 6](/ef/efcore-and-ef6/) и включает сетку, показывающую, какая библиотека поддерживает каждую десятку отдельных функций.</span><span class="sxs-lookup"><span data-stu-id="9aa14-427">Specific to Entity Framework, [this documentation compares EF Core and EF 6](/ef/efcore-and-ef6/) and includes a grid showing which library supports each of dozens of individual features.</span></span>

### <a name="migrate-to-entity-framework-core"></a><span data-ttu-id="9aa14-428">Переход на Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="9aa14-428">Migrate to Entity Framework Core</span></span>

<span data-ttu-id="9aa14-429">При принятии решения о переходе на EF Core действия могут быть довольно простыми, особенно если в исходном приложении использовался подход к модели на основе кода.</span><span class="sxs-lookup"><span data-stu-id="9aa14-429">Assuming a decision is made to migrate to EF Core, the steps can be fairly straightforward, especially if the original app used a code-based model approach.</span></span> <span data-ttu-id="9aa14-430">При [подготовке к порту от EF 6 до EF Core](/ef/efcore-and-ef6/porting/)проверьте доступность функций в целевой версии EF Core, которую вы будете использовать.</span><span class="sxs-lookup"><span data-stu-id="9aa14-430">When [preparing to port from EF 6 to EF Core](/ef/efcore-and-ef6/porting/), review the availability of features in the destination version of EF Core you'll be using.</span></span> <span data-ttu-id="9aa14-431">Изучите документацию по [переносу и модели на основе EDMX, а](/ef/efcore-and-ef6/porting/port-edmx) также [переносу из модели на основе кода](/ef/efcore-and-ef6/porting/port-code).</span><span class="sxs-lookup"><span data-stu-id="9aa14-431">Review the documentation on [porting from and EDMX-based model](/ef/efcore-and-ef6/porting/port-edmx) versus [porting from a code-based model](/ef/efcore-and-ef6/porting/port-code).</span></span>

<span data-ttu-id="9aa14-432">Чтобы выполнить обновление до EF Core 2,2, необходимо добавить соответствующие пакеты NuGet и обновить пространства имен.</span><span class="sxs-lookup"><span data-stu-id="9aa14-432">To upgrade to EF Core 2.2, the basic steps involved are to add the appropriate NuGet package(s) and update namespaces.</span></span> <span data-ttu-id="9aa14-433">Затем настройте способ передачи строки подключения в `DbContext` тип и способ их связывания для внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="9aa14-433">Then adjust how the connection string is passed to the `DbContext` type and how they're wired up for dependency injection.</span></span>

<span data-ttu-id="9aa14-434">EF Core добавляется в качестве ссылки на пакет в проект:</span><span class="sxs-lookup"><span data-stu-id="9aa14-434">EF Core is added as a package reference to the project:</span></span>

```xml
<PackageReference Include="Microsoft.EntityFrameworkCore" Version="2.2.6" />
```

<span data-ttu-id="9aa14-435">Ссылка на EF 6 удалена:</span><span class="sxs-lookup"><span data-stu-id="9aa14-435">The reference to EF 6 is removed:</span></span>

```xml
<PackageReference Include="EntityFramework" Version="6.2.0" />
```

<span data-ttu-id="9aa14-436">Компилятор сообщит об ошибках в `CatalogDBContext` и `CatalogDBInitializer` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-436">The compiler will report errors in `CatalogDBContext` and `CatalogDBInitializer`.</span></span> <span data-ttu-id="9aa14-437">`CatalogDbContext` необходимо удалить старые пространства имен и заменить их на `Microsoft.EntityFrameworkCore` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-437">`CatalogDbContext` needs to have the old namespaces removed and replaced with `Microsoft.EntityFrameworkCore`.</span></span> <span data-ttu-id="9aa14-438">Его конструкторы можно удалить.</span><span class="sxs-lookup"><span data-stu-id="9aa14-438">Its constructors can be removed.</span></span> <span data-ttu-id="9aa14-439">`DbModelBuilder` следует заменить на `ModelBuilder` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-439">`DbModelBuilder` should be replaced with `ModelBuilder`.</span></span> <span data-ttu-id="9aa14-440">Вспомогательные методы для настройки типов перемещаются в отдельные классы, реализующие `IEntityTypeConfiguration<T>` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-440">The helper methods for configuring types are moved to separate classes implementing `IEntityTypeConfiguration<T>`.</span></span> <span data-ttu-id="9aa14-441">Затем `CatalogDBContext` `OnModelCreating` метод класса просто превращается в:</span><span class="sxs-lookup"><span data-stu-id="9aa14-441">Then the `CatalogDBContext` class's `OnModelCreating` method simply becomes:</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder builder)
{
    builder.ApplyConfigurationsFromAssembly(Assembly.GetExecutingAssembly());

    base.OnModelCreating(builder);
}
```

<span data-ttu-id="9aa14-442">К другим задействованным изменениям относятся:</span><span class="sxs-lookup"><span data-stu-id="9aa14-442">Other changes involved include:</span></span>

- <span data-ttu-id="9aa14-443">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` заменяется на `ValueGeneratedNever()`</span><span class="sxs-lookup"><span data-stu-id="9aa14-443">`HasDatabaseGeneratedOption(DatabaseGeneratedOption.None)` replaced with `ValueGeneratedNever()`</span></span>
- <span data-ttu-id="9aa14-444">`HasRequired<T>` заменяется на `HasOne<T>`</span><span class="sxs-lookup"><span data-stu-id="9aa14-444">`HasRequired<T>` replaced with `HasOne<T>`</span></span>
- <span data-ttu-id="9aa14-445">Установленный `Microsoft.EntityFrameworkCore.Relational` пакет</span><span class="sxs-lookup"><span data-stu-id="9aa14-445">Installed `Microsoft.EntityFrameworkCore.Relational` package</span></span>
- <span data-ttu-id="9aa14-446">Добавление конструктора для получения `CatalogDBContext` `DbContextOptions` и передачи его в базовый конструктор</span><span class="sxs-lookup"><span data-stu-id="9aa14-446">Add a constructor to `CatalogDBContext` taking `DbContextOptions` and passing it to the base constructor</span></span>

<span data-ttu-id="9aa14-447">Ниже приведен пример класса конфигурации для `CatalogType` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-447">An example configuration class for `CatalogType` is shown here:</span></span>

```csharp
using Microsoft.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore.Metadata.Builders;

namespace eShopPorted.Models.Config
{
    public class CatalogTypeConfig : IEntityTypeConfiguration<CatalogType>
    {
        public void Configure(EntityTypeBuilder<CatalogType> builder)
        {
            builder.ToTable(nameof(CatalogType));

            builder.HasKey(ci => ci.Id);

            builder.Property(ci => ci.Id)
               .IsRequired();

            builder.Property(cb => cb.Type)
                .IsRequired()
                .HasMaxLength(100);
        }
    }
}
```

<span data-ttu-id="9aa14-448">`CatalogDBInitializer`И его базовый класс, `CreateDatabaseIfNotExists<T>` не совместимы с EF Core.</span><span class="sxs-lookup"><span data-stu-id="9aa14-448">The `CatalogDBInitializer` and its base class, `CreateDatabaseIfNotExists<T>`, are incompatible with EF Core.</span></span> <span data-ttu-id="9aa14-449">Этот класс предназначен для создания и заполнения базы данных.</span><span class="sxs-lookup"><span data-stu-id="9aa14-449">The purpose of this class is to create and seed the database.</span></span> <span data-ttu-id="9aa14-450">При использовании EF Core будет [создана и удалена связанная база `DbContext` данных для](/ef/core/managing-schemas/ensure-created) с использованием следующих методов:</span><span class="sxs-lookup"><span data-stu-id="9aa14-450">Using EF Core will [create and drop the associated database for a `DbContext`](/ef/core/managing-schemas/ensure-created) using these methods:</span></span>

```csharp
dbContext.Database.EnsureDeleted();
dbContext.Database.EnsureCreated();
```

<span data-ttu-id="9aa14-451">Заполнение данных в EF Core можно выполнить с помощью ручных скриптов или в составе конфигурации типа.</span><span class="sxs-lookup"><span data-stu-id="9aa14-451">Seeding data in EF Core can be done with manual scripts, or as part of the type configuration.</span></span> <span data-ttu-id="9aa14-452">Вместе с другими свойствами сущности начальные данные можно настроить в `IEntityTypeConfiguration` классах с помощью `builder.HasData()` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-452">Along with other entity properties, seed data can be configured in `IEntityTypeConfiguration` classes by using `builder.HasData()`.</span></span> <span data-ttu-id="9aa14-453">Исходное приложение загрузило начальные данные из CSV-файлов в каталоге *установки* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-453">The original app loaded seed data from CSV files in the *Setup* directory.</span></span> <span data-ttu-id="9aa14-454">Учитывая, что существует всего несколько элементов, эти записи данных могут быть добавлены как часть конфигурации сущности.</span><span class="sxs-lookup"><span data-stu-id="9aa14-454">Given that there are only a handful of items, these data records can instead be added as part of the entity configuration.</span></span> <span data-ttu-id="9aa14-455">Этот подход хорошо подходит для уточняющих данных в таблицах, которые изменяются редко.</span><span class="sxs-lookup"><span data-stu-id="9aa14-455">This approach works well for lookup data in tables that change infrequently.</span></span> <span data-ttu-id="9aa14-456">Добавление следующего метода в `CatalogTypeConfig` `Configure` метод гарантирует, что связанные строки будут представлены при создании базы данных:</span><span class="sxs-lookup"><span data-stu-id="9aa14-456">Adding the following to `CatalogTypeConfig`'s `Configure` method ensures the associated rows are present when the database is created:</span></span>

```csharp
builder.HasData(
    new CatalogType { Id = 1, Type = "Mug" },
    new CatalogType { Id = 2, Type = "T-Shirt" },
    new CatalogType { Id = 3, Type = "Sheet" },
    new CatalogType { Id = 4, Type = "USB Memory Stick" }
);
```

<span data-ttu-id="9aa14-457">Исходное приложение включает `PreconfiguredData` класс, который включает данные для `CatalogBrand` и `CatalogType` , поэтому использование этого метода `HasData` сокращается до:</span><span class="sxs-lookup"><span data-stu-id="9aa14-457">The initial app includes a `PreconfiguredData` class, which includes data for `CatalogBrand` and `CatalogType`, so using this method the `HasData` call reduces to:</span></span>

```csharp
builder.HasData(
    PreconfiguredData.GetPreconfiguredCatalogBrands()
);
```

<span data-ttu-id="9aa14-458">`CatalogItem`Данные также могут быть извлечены из `PreconfiguredData` , и при условии, что связанные с ними образы хранятся в системе управления версиями, это последняя таблица, необходимая для работы приложения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-458">The `CatalogItem` data can also be pulled from `PreconfiguredData`, and assuming the associated images are kept in source control, that is the last table needed for the app to function.</span></span> <span data-ttu-id="9aa14-459">`CatalogDBInitializer`Класс можно удалить вместе со всеми ссылками на него.</span><span class="sxs-lookup"><span data-stu-id="9aa14-459">The `CatalogDBInitializer` class can be removed, along with any references to it.</span></span> <span data-ttu-id="9aa14-460">`CatalogItemHiLoGenerator`Класс и файлы SQL в `Infrastructure` каталоге также удаляются вместе со всеми ссылками на них (в `CatalogService` `ApplicationModule` ).</span><span class="sxs-lookup"><span data-stu-id="9aa14-460">The `CatalogItemHiLoGenerator` class and the SQL files in the `Infrastructure` directory are also removed, along with any references to them (in `CatalogService`, `ApplicationModule`).</span></span>

<span data-ttu-id="9aa14-461">После удаления специальных классов ключевых генераторов для `CatalogItem` этот код удаляется из `CatalogItemConfig` :</span><span class="sxs-lookup"><span data-stu-id="9aa14-461">With the elimination of the special key generator classes for `CatalogItem`, this code now is removed from `CatalogItemConfig`:</span></span>

```csharp
builder.Property(ci => ci.Id)
    .ValueGeneratedNever()
    .IsRequired();
```

<span data-ttu-id="9aa14-462">После внесения этих изменений приложение ASP.NET Core строится, но еще не работает с EF Core, которое по-прежнему должно быть настроено для внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="9aa14-462">With these modifications, the ASP.NET Core app builds, but it doesn't yet work with EF Core, which must still be configured for dependency injection.</span></span> <span data-ttu-id="9aa14-463">С EF Core самый простой способ ее настройки `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="9aa14-463">With EF Core, the simplest way to configure it is in `ConfigureServices`:</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    bool useMockData = Configuration.GetValue<bool>("UseMockData");
    if (!useMockData)
    {
        string connectionString = Configuration.GetConnectionString("DefaultConnection");

        services.AddDbContext<CatalogDBContext>(options =>
            options.UseSqlServer(connectionString)
        );
    }

    // Create Autofac container builder
    var builder = new ContainerBuilder();
    builder.Populate(services);
    builder.RegisterModule(new ApplicationModule(useMockData));

    ILifetimeScope container = builder.Build();

    return new AutofacServiceProvider(container);
}
```

<span data-ttu-id="9aa14-464">Окончательная версия Autofac `ApplicationModule` настраивает только один тип в зависимости от того, настроено ли приложение для использования фиктивных данных:</span><span class="sxs-lookup"><span data-stu-id="9aa14-464">The final version of Autofac's `ApplicationModule` only configures one type, depending on whether the app is configured to use mock data:</span></span>

```csharp
public class ApplicationModule : Module
{
    private bool _useMockData;

    public ApplicationModule(bool useMockData)
    {
        _useMockData = useMockData;
    }

    protected override void Load(ContainerBuilder builder)
    {
        if (_useMockData)
        {
            builder.RegisterType<CatalogServiceMock>()
                .As<ICatalogService>()
                .SingleInstance();
        }
        else
        {
            builder.RegisterType<CatalogService>()
                .As<ICatalogService>()
                .InstancePerLifetimeScope();
        }
    }
}
```

<span data-ttu-id="9aa14-465">Переданное приложение выполняется, но не отображает данные, если настроено использование нефиктивных данных.</span><span class="sxs-lookup"><span data-stu-id="9aa14-465">The ported app runs, but doesn't display any data if configured to use non-mock data.</span></span> <span data-ttu-id="9aa14-466">Начальные данные, добавленные с помощью `HasData` , вставляются только при применении миграции.</span><span class="sxs-lookup"><span data-stu-id="9aa14-466">The seed data added through `HasData` is only inserted when migrations are applied.</span></span> <span data-ttu-id="9aa14-467">Исходное приложение не использовало миграцию, и, если оно имелось, они не будут перенесены как есть.</span><span class="sxs-lookup"><span data-stu-id="9aa14-467">The source app didn't use migrations, and if it had, they wouldn't migrate as-is.</span></span> <span data-ttu-id="9aa14-468">Лучший подход — начать с нового сценария миграции.</span><span class="sxs-lookup"><span data-stu-id="9aa14-468">The best approach is to start with a new migration script.</span></span> <span data-ttu-id="9aa14-469">Для этого добавьте ссылку на пакет для `Microsoft.EntityFrameworkCore.Design` и откройте окно терминала в корневом каталоге проекта.</span><span class="sxs-lookup"><span data-stu-id="9aa14-469">To do this, add a package reference for `Microsoft.EntityFrameworkCore.Design` and open a terminal window in the project root.</span></span> <span data-ttu-id="9aa14-470">Далее выполните:</span><span class="sxs-lookup"><span data-stu-id="9aa14-470">Then run:</span></span>

```dotnetcli
dotnet ef migrations add Initial
```

<span data-ttu-id="9aa14-471">Удалите существующую базу данных *ешоппортед* , если она существует, а затем выполните команду:</span><span class="sxs-lookup"><span data-stu-id="9aa14-471">Drop the existing *eShopPorted* database if it exists, then run:</span></span>

```dotnetcli
dotnet ef database update
```

<span data-ttu-id="9aa14-472">При этом создается и заполняется база данных.</span><span class="sxs-lookup"><span data-stu-id="9aa14-472">This creates and seeds the database.</span></span> <span data-ttu-id="9aa14-473">Теперь он готов к запуску, и в нем осталось несколько небольших обновлений.</span><span class="sxs-lookup"><span data-stu-id="9aa14-473">It's now ready to run, with a few small updates left to address.</span></span>

## <a name="fix-all-todo-tasks"></a><span data-ttu-id="9aa14-474">Исправить все задачи TODO</span><span class="sxs-lookup"><span data-stu-id="9aa14-474">Fix all TODO tasks</span></span>

<span data-ttu-id="9aa14-475">Запуск перенесенного приложения на этом этапе показывает, что на странице не отображаются изображения.</span><span class="sxs-lookup"><span data-stu-id="9aa14-475">Running the ported app at this point reveals that no pictures are shown on the page.</span></span> <span data-ttu-id="9aa14-476">Это обусловлено тем, что `PictureUri` свойство объекта не `CatalogItem` задано.</span><span class="sxs-lookup"><span data-stu-id="9aa14-476">This is because the `PictureUri` property of `CatalogItem` is never set.</span></span> <span data-ttu-id="9aa14-477">Просмотрев список элементов, `TODO` созданных с помощью **список задач** Visual Studio, это единственный элемент, который остается в `CatalogController` , с заметкой "ссылка на Pic из wwwroot".</span><span class="sxs-lookup"><span data-stu-id="9aa14-477">Looking at the list of `TODO` items we created using Visual Studio's **Task List**, the only one that remains is in `CatalogController`, with a note to "Reference pic from wwwroot."</span></span> <span data-ttu-id="9aa14-478">Рассматриваемый код:</span><span class="sxs-lookup"><span data-stu-id="9aa14-478">The code in question is:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    //TODO: Reference pic from wwwroot
    //item.PictureUri = this.Url.RouteUrl(PicController.GetPicRouteName, new { catalogItemId = item.Id }, this.Request.Url.Scheme);
}
```

<span data-ttu-id="9aa14-479">Самым простым исправлением является ссылка на общедоступные файлы образов в общедоступном каталоге *wwwroot/pics* .</span><span class="sxs-lookup"><span data-stu-id="9aa14-479">The simplest fix is to reference the public image files in the site's public *wwwroot/Pics* directory.</span></span> <span data-ttu-id="9aa14-480">Эту задачу можно выполнить, заменив метод следующим кодом:</span><span class="sxs-lookup"><span data-stu-id="9aa14-480">This task can be accomplished by replacing the method with the following code:</span></span>

```csharp
private void AddUriPlaceHolder(CatalogItem item)
{
    item.PictureUri = $"/Pics/{item.Id}.png";
}
```

<span data-ttu-id="9aa14-481">После этого изменения при запуске приложения образы работают как прежде.</span><span class="sxs-lookup"><span data-stu-id="9aa14-481">With this change, running the app reveals the images work as before.</span></span>

## <a name="additional-mvc-customizations"></a><span data-ttu-id="9aa14-482">Дополнительные настройки MVC</span><span class="sxs-lookup"><span data-stu-id="9aa14-482">Additional MVC customizations</span></span>

<span data-ttu-id="9aa14-483">Приложение *ешоплегацимвк* довольно простое, поэтому настройка в контексте поведения MVC по умолчанию не требует много усилий.</span><span class="sxs-lookup"><span data-stu-id="9aa14-483">The *eShopLegacyMVC* app is fairly simple, so there isn't much to configure in terms of default MVC behavior.</span></span> <span data-ttu-id="9aa14-484">Однако, если необходимо настроить дополнительные компоненты MVC, такие как CORS, фильтры и ограничения маршрутов, обычно эти сведения предоставляются в `Startup.ConfigureServices` , где `UseMvc` вызывается.</span><span class="sxs-lookup"><span data-stu-id="9aa14-484">However, if you do need to configure additional MVC components, such as CORS, filters, and route constraints, you generally provide this information in `Startup.ConfigureServices`, where `UseMvc` is called.</span></span> <span data-ttu-id="9aa14-485">Например, в следующем листинге кода настраивается [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) и настраивается глобальный фильтр действий:</span><span class="sxs-lookup"><span data-stu-id="9aa14-485">For example, the following code listing configures [CORS](/aspnet/core/security/cors?preserve-view=true&view=aspnetcore-2.2) and sets up a global action filter:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy(MyAllowSpecificOrigins,
            builder =>
                builder.WithOrigins("http://example.com", "http://www.contoso.com")
                    .AllowAnyHeader()
                    .AllowAnyMethod());
    });

    services.AddMvc(options =>
    {
      options.Filters.Add(new SampleGlobalActionFilter());
    }).SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
}
```

> [!Note]
> <span data-ttu-id="9aa14-486">Чтобы завершить настройку CORS, необходимо также вызвать `app.UseCors()` в `Configure` .</span><span class="sxs-lookup"><span data-stu-id="9aa14-486">To finish configuring CORS, you must also call `app.UseCors()` in `Configure`.</span></span>

<span data-ttu-id="9aa14-487">В подробных ASP.NET Core документах рассматриваются другие сложные сценарии, например добавление [пользовательских связывателей модели](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2), модулей форматирования и многое другое. Как правило, их можно применять к отдельному контроллеру или действию или глобально с помощью тех же параметров, что и в приведенном выше листинге кода.</span><span class="sxs-lookup"><span data-stu-id="9aa14-487">Other advanced scenarios, like adding [custom model binders](/aspnet/core/mvc/advanced/custom-model-binding?preserve-view=true&view=aspnetcore-2.2), formatters, and more are covered in the detailed ASP.NET Core docs. Generally these can be applied on an individual controller or action basis, or globally using the same options approach shown in the previous code listing.</span></span>

## <a name="other-dependencies"></a><span data-ttu-id="9aa14-488">Другие зависимости</span><span class="sxs-lookup"><span data-stu-id="9aa14-488">Other dependencies</span></span>

<span data-ttu-id="9aa14-489">Зависимости, использующие платформа .NET Framework функции, которые имеют зависимость от устаревшей модели конфигурации, например тип клиента WCF и код трассировки, должны быть изменены при переносе.</span><span class="sxs-lookup"><span data-stu-id="9aa14-489">Dependencies that use .NET Framework features that had a dependency on the legacy configuration model, such as the WCF client type and tracing code, must be modified when ported.</span></span> <span data-ttu-id="9aa14-490">Вместо того, чтобы эти типы извлекать данные о конфигурации напрямую, их следует настроить в коде.</span><span class="sxs-lookup"><span data-stu-id="9aa14-490">Rather than having these types pull in their configuration information directly, they should be configured in code.</span></span> <span data-ttu-id="9aa14-491">Например, подключение к службе WCF, которая была настроена в *web.config* приложения ASP.NET для использования, `basicHttpBinding` может быть настроено программно с помощью следующего кода:</span><span class="sxs-lookup"><span data-stu-id="9aa14-491">For example, a connection to a WCF service that was configured in an ASP.NET app's *web.config* to use `basicHttpBinding` could instead be configured programmatically with the following code:</span></span>

```csharp
var binding = new BasicHttpBinding();
binding.MaxReceivedMessageSize = 2_000_000;

var endpointAddress = new EndpointAddress("http://localhost:9200/ExampleService");

var myClient = new MyServiceClient(binding, endpointAddress);
```

<span data-ttu-id="9aa14-492">Вместо использования файлов конфигурации для его параметров клиенты WCF и другие типы платформа .NET Framework должны иметь свои параметры, указанные в коде.</span><span class="sxs-lookup"><span data-stu-id="9aa14-492">Rather than relying on config files for its settings, WCF clients and other .NET Framework types should have their settings specified in code.</span></span> <span data-ttu-id="9aa14-493">Эти типы, настроенные таким образом, могут продолжать работать в приложениях ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="9aa14-493">Configured in this manner, these types can continue to work in ASP.NET Core 2.2 apps.</span></span>

## <a name="references"></a><span data-ttu-id="9aa14-494">Ссылки</span><span class="sxs-lookup"><span data-stu-id="9aa14-494">References</span></span>

- [<span data-ttu-id="9aa14-495">репозиторий eShopModernizing GitHub</span><span class="sxs-lookup"><span data-stu-id="9aa14-495">eShopModernizing GitHub repository</span></span>](https://github.com/dotnet-architecture/eShopModernizing)
- [<span data-ttu-id="9aa14-496">Помощник по обновлению .NET</span><span class="sxs-lookup"><span data-stu-id="9aa14-496">.NET Upgrade Assistant tool</span></span>](https://aka.ms/dotnet-upgrade-assistant)
- [<span data-ttu-id="9aa14-497">API и ViewModels не должны ссылаться на модели предметной области</span><span class="sxs-lookup"><span data-stu-id="9aa14-497">Your API and ViewModels Should Not Reference Domain Models</span></span>](https://ardalis.com/your-api-and-view-models-should-not-reference-domain-models/)
- [<span data-ttu-id="9aa14-498">Промежуточное по страницы исключений разработчика</span><span class="sxs-lookup"><span data-stu-id="9aa14-498">Developer Exception Page Middleware</span></span>](/aspnet/core/fundamentals/error-handling#developer-exception-page)
- [<span data-ttu-id="9aa14-499">Углубленное углубление в EF Core Хасдата</span><span class="sxs-lookup"><span data-stu-id="9aa14-499">Deep Dive into EF Core HasData</span></span>](/archive/msdn-magazine/2018/august/data-points-deep-dive-into-ef-core-hasdata-seeding)

>[!div class="step-by-step"]
><span data-ttu-id="9aa14-500">[Назад](more-migration-scenarios.md)
>[Вперед](deployment-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="9aa14-500">[Previous](more-migration-scenarios.md)
[Next](deployment-scenarios.md)</span></span>
