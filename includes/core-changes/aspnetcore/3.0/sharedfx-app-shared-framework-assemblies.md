---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032869"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="91bf8-101">Общая платформа. Из Microsoft.AspNetCore.App удалены сборки</span><span class="sxs-lookup"><span data-stu-id="91bf8-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="91bf8-102">Начиная с ASP.NET Core версии 3.0 общая платформа ASP.NET Core (`Microsoft.AspNetCore.App`) содержит только сборки, которые полностью разработаны, поддерживаются и обслуживаются корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="91bf8-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="91bf8-103">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="91bf8-103">Change description</span></span>

<span data-ttu-id="91bf8-104">Это изменение следует рассматривать как переопределение границ для понятия "платформа ASP.NET Core".</span><span class="sxs-lookup"><span data-stu-id="91bf8-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="91bf8-105">Общую платформу [любой желающий может собрать из исходного кода, размещенного в репозитории GitHub](https://github.com/dotnet/source-build), и она по-прежнему предоставляет вашим приложениям все существующие преимущества общих платформ .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91bf8-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="91bf8-106">К таким преимуществам относятся меньший размер развертывания, централизованная установка исправлений и сокращенное время запуска.</span><span class="sxs-lookup"><span data-stu-id="91bf8-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="91bf8-107">В рамках этого обновления в `Microsoft.AspNetCore.App` добавлены несколько критических изменений.</span><span class="sxs-lookup"><span data-stu-id="91bf8-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="91bf8-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="91bf8-108">Version introduced</span></span>

<span data-ttu-id="91bf8-109">3.0</span><span class="sxs-lookup"><span data-stu-id="91bf8-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="91bf8-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="91bf8-110">Old behavior</span></span>

<span data-ttu-id="91bf8-111">Проекты ссылались на `Microsoft.AspNetCore.App` через элемент `<PackageReference>` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="91bf8-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="91bf8-112">Кроме того, в `Microsoft.AspNetCore.App` содержались следующие вложенные компоненты:</span><span class="sxs-lookup"><span data-stu-id="91bf8-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="91bf8-113">Json.NET (`Newtonsoft.Json`);</span><span class="sxs-lookup"><span data-stu-id="91bf8-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="91bf8-114">Entity Framework Core (сборки с префиксом `Microsoft.EntityFrameworkCore.`);</span><span class="sxs-lookup"><span data-stu-id="91bf8-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="91bf8-115">Roslyn (`Microsoft.CodeAnalysis`).</span><span class="sxs-lookup"><span data-stu-id="91bf8-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="91bf8-116">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="91bf8-116">New behavior</span></span>

<span data-ttu-id="91bf8-117">Ссылка на `Microsoft.AspNetCore.App` теперь не требует наличия элемента `<PackageReference>` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="91bf8-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="91bf8-118">Пакет SDK для .NET Core поддерживает новый элемент с именем `<FrameworkReference>`, который заменяет собой `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="91bf8-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="91bf8-119">Подробную информацию см. на странице [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="91bf8-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="91bf8-120">Entity Framework Core поставляется в формате пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="91bf8-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="91bf8-121">Это обновление приводит модель поставки в соответствие со схемой, принятой для всех остальных библиотек доступа к данным в .NET.</span><span class="sxs-lookup"><span data-stu-id="91bf8-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="91bf8-122">Теперь в Entity Framework Core доступен самый простой способ продолжать разработку инноваций, пользуясь поддержкой любых платформ .NET.</span><span class="sxs-lookup"><span data-stu-id="91bf8-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="91bf8-123">Несмотря на отделение от общей платформы Entity Framework Core остается библиотекой, разработанной, поддерживаемой и обслуживаемой корпорацией Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="91bf8-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="91bf8-124">На нее по-прежнему распространяется [политика поддержки .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="91bf8-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="91bf8-125">Json.NET и Entity Framework Core будут и дальше работать с ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="91bf8-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="91bf8-126">Но теперь они не будут входить в состав общей платформы.</span><span class="sxs-lookup"><span data-stu-id="91bf8-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="91bf8-127">Дополнительные сведения см. в статье [о перспективах для JSON в .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="91bf8-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="91bf8-128">Также обратите внимание на то, что из общей платформы удален [большой список двоичных файлов](https://github.com/dotnet/aspnetcore/issues/3755).</span><span class="sxs-lookup"><span data-stu-id="91bf8-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="91bf8-129">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="91bf8-129">Reason for change</span></span>

<span data-ttu-id="91bf8-130">Это изменение упрощает использование `Microsoft.AspNetCore.App` и сокращает дублирование функций между пакетами NuGet и общими платформами.</span><span class="sxs-lookup"><span data-stu-id="91bf8-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="91bf8-131">Дополнительные сведения о том, что подтолкнуло нас к этим изменениям, см. в [этой записи блога](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="91bf8-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="91bf8-132">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="91bf8-132">Recommended action</span></span>

<span data-ttu-id="91bf8-133">Сборки в `Microsoft.AspNetCore.App` не обязательно используются в проектах именно в виде пакетов NuGet.</span><span class="sxs-lookup"><span data-stu-id="91bf8-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="91bf8-134">Чтобы упростить нацеливание и использование общей платформы ASP.NET Core, многие пакеты NuGet, подготовленные с момента выхода ASP.NET Core 1.0, больше не выпускаются.</span><span class="sxs-lookup"><span data-stu-id="91bf8-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="91bf8-135">API-интерфейсы, которые предоставлялись в этих пакетах, по-прежнему можно использовать из приложений с помощью ссылки `<FrameworkReference>` на `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="91bf8-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="91bf8-136">Сюда относятся, например, довольно популярные API Kestrel, MVC и Razor.</span><span class="sxs-lookup"><span data-stu-id="91bf8-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="91bf8-137">Это изменение не затрагивает двоичные файлы, которые указываются через `Microsoft.AspNetCore.App` в ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="91bf8-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="91bf8-138">Несколько важных исключений:</span><span class="sxs-lookup"><span data-stu-id="91bf8-138">Notable exceptions include:</span></span>

- <span data-ttu-id="91bf8-139">Библиотеки `Microsoft.Extensions`, которые по-прежнему ориентированы на .NET Standard, будут доступны в виде пакетов NuGet (см. <https://github.com/dotnet/extensions>).</span><span class="sxs-lookup"><span data-stu-id="91bf8-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see <https://github.com/dotnet/extensions>).</span></span>
- <span data-ttu-id="91bf8-140">API-интерфейсы, которые выпускаются командой разработчиков ASP.NET Core и не входят в `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="91bf8-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="91bf8-141">Например, в формате пакетов NuGet предоставляются следующие компоненты:</span><span class="sxs-lookup"><span data-stu-id="91bf8-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="91bf8-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="91bf8-142">Entity Framework Core</span></span>
  - <span data-ttu-id="91bf8-143">API-интерфейсы, которые обеспечивают интеграцию с решениями сторонних разработчиков;</span><span class="sxs-lookup"><span data-stu-id="91bf8-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="91bf8-144">экспериментальные функции;</span><span class="sxs-lookup"><span data-stu-id="91bf8-144">Experimental features</span></span>
  - <span data-ttu-id="91bf8-145">API-интерфейсы с зависимостями, которые не позволяют [выполнить требования для включения в общую платформу](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md).</span><span class="sxs-lookup"><span data-stu-id="91bf8-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="91bf8-146">Расширения MVC, которые сохраняют поддержку Json.NET.</span><span class="sxs-lookup"><span data-stu-id="91bf8-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="91bf8-147">API-интерфейс будет предоставляться в виде пакета NuGet для поддержки работы с Json.NET и MVC.</span><span class="sxs-lookup"><span data-stu-id="91bf8-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="91bf8-148">Клиент SignalR .NET будет и далее поддерживать .NET Standard, а поставляться в виде пакета NuGet.</span><span class="sxs-lookup"><span data-stu-id="91bf8-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="91bf8-149">Он нужен для многих сред выполнения .NET, включая Xamarin и UWP.</span><span class="sxs-lookup"><span data-stu-id="91bf8-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="91bf8-150">Подробные сведения см. в объявлении [о прекращении выпуска пакетов для сборок общей платформы начиная с версии 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="91bf8-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="91bf8-151">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="91bf8-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="91bf8-152">Категория</span><span class="sxs-lookup"><span data-stu-id="91bf8-152">Category</span></span>

<span data-ttu-id="91bf8-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="91bf8-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="91bf8-154">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="91bf8-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
