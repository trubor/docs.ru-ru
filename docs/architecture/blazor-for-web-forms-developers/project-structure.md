---
title: Структура проекта для Blazor приложений
description: Узнайте, как сравниваются структуры проекта веб-форм и Blazor проектов ASP.NET.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: d91430eb654ee16934408bf064803b34ca700640
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509810"
---
# <a name="project-structure-for-no-locblazor-apps"></a><span data-ttu-id="beb82-103">Структура проекта для Blazor приложений</span><span class="sxs-lookup"><span data-stu-id="beb82-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="beb82-104">Несмотря на существенные различия в структуре проекта, ASP.NET веб-формы и Blazor совместно используют многие схожие концепции.</span><span class="sxs-lookup"><span data-stu-id="beb82-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="beb82-105">Здесь мы рассмотрим структуру Blazor проекта и сравнив ее с проектом веб-форм ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="beb82-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="beb82-106">Чтобы создать свое первое Blazor приложение, следуйте инструкциям в [ Blazor статье Приступая к работе](/aspnet/core/blazor/get-started).</span><span class="sxs-lookup"><span data-stu-id="beb82-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="beb82-107">Вы можете выполнить инструкции, чтобы создать Blazor серверное приложение или приложение, Blazor WebAssembly размещенное в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="beb82-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="beb82-108">За исключением логики размещения для конкретной модели, большая часть кода в обоих проектах одинакова.</span><span class="sxs-lookup"><span data-stu-id="beb82-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="beb82-109">Файл проекта</span><span class="sxs-lookup"><span data-stu-id="beb82-109">Project file</span></span>

<span data-ttu-id="beb82-110">Blazor Серверные приложения — это проекты .NET.</span><span class="sxs-lookup"><span data-stu-id="beb82-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="beb82-111">Файл проекта для Blazor серверного приложения примерно так прост, как он может получить:</span><span class="sxs-lookup"><span data-stu-id="beb82-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="beb82-112">Файл проекта Blazor WebAssembly приложения выглядит немного подробнее (точный номер версии может отличаться):</span><span class="sxs-lookup"><span data-stu-id="beb82-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="beb82-113">BlazorWebAssemblyпроект ориентирован `Microsoft.NET.Sdk.BlazorWebAssembly` вместо `Microsoft.NET.Sdk.Web` пакета SDK, так как они выполняются в браузере в WebAssembly среде выполнения .NET на основе.</span><span class="sxs-lookup"><span data-stu-id="beb82-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="beb82-114">Вы не можете установить .NET в веб-браузер, как на сервере или на компьютере разработчика.</span><span class="sxs-lookup"><span data-stu-id="beb82-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="beb82-115">Следовательно, проект ссылается на Blazor платформу, используя отдельные ссылки на пакеты.</span><span class="sxs-lookup"><span data-stu-id="beb82-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="beb82-116">По сравнению, проект веб-форм ASP.NET по умолчанию включает в себя почти 300 строк XML в файле *. csproj* , большинство из которых явно задает в проекте различные файлы кода и содержимого.</span><span class="sxs-lookup"><span data-stu-id="beb82-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="beb82-117">С выпуском `.NET 5` `Blazor Server` и приложением, и `Blazor WebAssembly` приложение может легко совместно использовать одну единую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="beb82-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="beb82-118">Хотя они поддерживаются, отдельные ссылки на сборки менее распространены в проектах .NET.</span><span class="sxs-lookup"><span data-stu-id="beb82-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="beb82-119">Большинство зависимостей проектов обрабатываются как ссылки на пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="beb82-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="beb82-120">В проектах .NET необходимо ссылаться только на зависимости пакетов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="beb82-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="beb82-121">Транзитивные зависимости включаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="beb82-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="beb82-122">Вместо того чтобы использовать файл *packages.config* , который часто встречаются в проектах веб-форм ASP.NET для ссылки на пакеты, ссылки на пакет добавляются в файл проекта с помощью `<PackageReference>` элемента.</span><span class="sxs-lookup"><span data-stu-id="beb82-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="beb82-123">Точка входа</span><span class="sxs-lookup"><span data-stu-id="beb82-123">Entry point</span></span>

<span data-ttu-id="beb82-124">BlazorТочка входа серверного приложения определяется в файле *Program.CS* , как показано в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="beb82-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="beb82-125">При выполнении приложения он создает и запускает экземпляр веб-узла с использованием значений по умолчанию, относящихся к веб-приложениям.</span><span class="sxs-lookup"><span data-stu-id="beb82-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="beb82-126">Веб-узел управляет Blazor жизненным циклом серверного приложения и настраивает службы на уровне узла.</span><span class="sxs-lookup"><span data-stu-id="beb82-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="beb82-127">Примерами таких служб являются конфигурация, ведение журнала, внедрение зависимостей и HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="beb82-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="beb82-128">Этот код в основном является шаблоном, и часто остается без изменений.</span><span class="sxs-lookup"><span data-stu-id="beb82-128">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="beb82-129">BlazorWebAssemblyприложения также определяют точку входа в *Program.CS*.</span><span class="sxs-lookup"><span data-stu-id="beb82-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="beb82-130">Код выглядит немного иначе.</span><span class="sxs-lookup"><span data-stu-id="beb82-130">The code looks slightly different.</span></span> <span data-ttu-id="beb82-131">Код аналогичен тому, что настраивает узел приложения для предоставления приложению тех же служб уровня узла.</span><span class="sxs-lookup"><span data-stu-id="beb82-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="beb82-132">WebAssemblyУзел приложения, однако, не настраивает HTTP-сервер, так как он выполняется непосредственно в браузере.</span><span class="sxs-lookup"><span data-stu-id="beb82-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="beb82-133">Blazor приложения имеют `Startup` класс, а не файл *Global. asax* для определения логики запуска приложения.</span><span class="sxs-lookup"><span data-stu-id="beb82-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="beb82-134">`Startup`Класс используется для настройки приложения и всех служб, зависящих от приложения.</span><span class="sxs-lookup"><span data-stu-id="beb82-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="beb82-135">В Blazor серверном приложении `Startup` класс используется для настройки конечной точки для соединения в режиме реального времени, используемого Blazor между клиентскими браузерами и сервером.</span><span class="sxs-lookup"><span data-stu-id="beb82-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="beb82-136">В Blazor WebAssembly приложении `Startup` класс определяет корневые компоненты приложения и место, где они должны быть подготовлены к просмотру.</span><span class="sxs-lookup"><span data-stu-id="beb82-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="beb82-137">Мы подробнее рассмотрим `Startup` класс в разделе [Запуск приложения](./app-startup.md) .</span><span class="sxs-lookup"><span data-stu-id="beb82-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="beb82-138">Статические файлы</span><span class="sxs-lookup"><span data-stu-id="beb82-138">Static files</span></span>

<span data-ttu-id="beb82-139">В отличие от проектов веб-форм ASP.NET, не все файлы Blazor проекта могут запрашиваться как статические файлы.</span><span class="sxs-lookup"><span data-stu-id="beb82-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="beb82-140">Веб-адресацией могут быть только файлы в папке *wwwroot* .</span><span class="sxs-lookup"><span data-stu-id="beb82-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="beb82-141">Эта папка называется "корневым веб-приложением".</span><span class="sxs-lookup"><span data-stu-id="beb82-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="beb82-142">Все, что находится за пределами корневого веб-узла приложения, *не является* веб-адресацией.</span><span class="sxs-lookup"><span data-stu-id="beb82-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="beb82-143">Эта установка обеспечивает дополнительный уровень безопасности, который предотвращает случайное предоставление файлов проекта через Интернет.</span><span class="sxs-lookup"><span data-stu-id="beb82-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="beb82-144">Параметр Configuration</span><span class="sxs-lookup"><span data-stu-id="beb82-144">Configuration</span></span>

<span data-ttu-id="beb82-145">Конфигурация в приложениях ASP.NET Web Forms обычно обрабатывается с помощью одного или нескольких файлов *web.config* .</span><span class="sxs-lookup"><span data-stu-id="beb82-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="beb82-146">Blazor приложения обычно не имеют *web.config* файлов.</span><span class="sxs-lookup"><span data-stu-id="beb82-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="beb82-147">В противном случае файл будет использоваться только для настройки параметров IIS при размещении в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="beb82-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="beb82-148">Вместо этого Blazor серверные приложения используют абстракции конфигурации ASP.NET Core ( Blazor WebAssembly приложения в настоящее время не поддерживают одни и те же абстракции конфигурации, но это может быть функция, добавленная в будущем).</span><span class="sxs-lookup"><span data-stu-id="beb82-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="beb82-149">Например, Blazor серверное приложение по умолчанию хранит некоторые параметры в *appsettings.js*.</span><span class="sxs-lookup"><span data-stu-id="beb82-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="beb82-150">Дополнительные сведения о конфигурации в ASP.NET Core проектах см. в разделе [конфигурации](./config.md) .</span><span class="sxs-lookup"><span data-stu-id="beb82-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="beb82-151">Компоненты Razor</span><span class="sxs-lookup"><span data-stu-id="beb82-151">Razor components</span></span>

<span data-ttu-id="beb82-152">Большинство файлов в Blazor проектах являются файлами *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="beb82-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="beb82-153">Razor — это язык шаблонов, основанный на HTML и C#, который используется для динамического создания пользовательского веб-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="beb82-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="beb82-154">Файлы *. Razor* определяют компоненты, составляющие пользовательский интерфейс приложения.</span><span class="sxs-lookup"><span data-stu-id="beb82-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="beb82-155">В большинстве случаев компоненты идентичны как для Blazor сервера, так и для Blazor WebAssembly приложений.</span><span class="sxs-lookup"><span data-stu-id="beb82-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="beb82-156">Компоненты в Blazor являются аналогом пользовательских элементов управления в веб-формах ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="beb82-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="beb82-157">Каждый файл компонента Razor компилируется в класс .NET при построении проекта.</span><span class="sxs-lookup"><span data-stu-id="beb82-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="beb82-158">Созданный класс захватывает состояние компонента, логику отрисовки, методы жизненного цикла, обработчики событий и другую логику.</span><span class="sxs-lookup"><span data-stu-id="beb82-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="beb82-159">Мы рассмотрим создание компонентов [пользовательского интерфейса с возможностью повторного использования с помощью Blazor ](./components.md) раздела.</span><span class="sxs-lookup"><span data-stu-id="beb82-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="beb82-160">Файлы *_Imports. Razor* не являются файлами компонентов Razor.</span><span class="sxs-lookup"><span data-stu-id="beb82-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="beb82-161">Вместо этого они определяют набор директив Razor для импорта в другие файлы *Razor* в той же папке и ее вложенных папках.</span><span class="sxs-lookup"><span data-stu-id="beb82-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="beb82-162">Например, файл *_Imports. Razor* — это стандартный способ добавления `using` директив для часто используемых пространств имен:</span><span class="sxs-lookup"><span data-stu-id="beb82-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="beb82-163">Страницы</span><span class="sxs-lookup"><span data-stu-id="beb82-163">Pages</span></span>

<span data-ttu-id="beb82-164">Где находятся страницы в Blazor приложениях?</span><span class="sxs-lookup"><span data-stu-id="beb82-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="beb82-165">Blazor не определяет отдельное расширение файла для адресных страниц, например *ASPX* -файлы в ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="beb82-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="beb82-166">Вместо этого страницы определяются путем назначения маршрутов компонентам.</span><span class="sxs-lookup"><span data-stu-id="beb82-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="beb82-167">Маршрут обычно назначается с помощью `@page` директивы Razor.</span><span class="sxs-lookup"><span data-stu-id="beb82-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="beb82-168">Например, компонент, `Counter` созданный в файле *pages/Counter. Razor* , определяет следующий маршрут:</span><span class="sxs-lookup"><span data-stu-id="beb82-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="beb82-169">Маршрутизация в Blazor обрабатывается на стороне клиента, а не на сервере.</span><span class="sxs-lookup"><span data-stu-id="beb82-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="beb82-170">При переходе пользователя в браузере Blazor перехватывает навигацию, а затем отображает компонент с соответствующим маршрутом.</span><span class="sxs-lookup"><span data-stu-id="beb82-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="beb82-171">Маршруты к компонентам в настоящее время не выводятся расположением файлов компонента, как и страницы *ASPX* .</span><span class="sxs-lookup"><span data-stu-id="beb82-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="beb82-172">Эта функция может быть добавлена в будущем.</span><span class="sxs-lookup"><span data-stu-id="beb82-172">This feature may be added in the future.</span></span> <span data-ttu-id="beb82-173">Каждый маршрут должен быть явно указан в компоненте.</span><span class="sxs-lookup"><span data-stu-id="beb82-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="beb82-174">Хранение маршрутизируемых компонентов в папке *pages* не имеет особого смысла и является исключительно Соглашением.</span><span class="sxs-lookup"><span data-stu-id="beb82-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="beb82-175">Мы более подробно рассмотрим маршрутизацию в Blazor разделе [страницы, маршрутизация и макеты](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="beb82-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="beb82-176">Макет</span><span class="sxs-lookup"><span data-stu-id="beb82-176">Layout</span></span>

<span data-ttu-id="beb82-177">В приложениях ASP.NET Web Forms общий макет страницы обрабатывается с помощью главных страниц (*site. master*).</span><span class="sxs-lookup"><span data-stu-id="beb82-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="beb82-178">В Blazor приложениях макет страницы обрабатывается с помощью компонентов макета (*Shared/маинлайаут. Razor*).</span><span class="sxs-lookup"><span data-stu-id="beb82-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="beb82-179">Компоненты макета будут обсуждаться более подробно в разделе [страница, маршрутизация и макеты](./pages-routing-layouts.md) .</span><span class="sxs-lookup"><span data-stu-id="beb82-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-no-locblazor"></a><span data-ttu-id="beb82-180">Загрузке Blazor</span><span class="sxs-lookup"><span data-stu-id="beb82-180">Bootstrap Blazor</span></span>

<span data-ttu-id="beb82-181">Для начальной загрузки Blazor приложение должно:</span><span class="sxs-lookup"><span data-stu-id="beb82-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="beb82-182">Укажите, где на странице следует визуализировать корневой компонент (*app. Razor*).</span><span class="sxs-lookup"><span data-stu-id="beb82-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="beb82-183">Добавьте соответствующий Blazor скрипт платформы.</span><span class="sxs-lookup"><span data-stu-id="beb82-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="beb82-184">В Blazor серверном приложении страница узла корневого компонента определена в файле *_Host. cshtml* .</span><span class="sxs-lookup"><span data-stu-id="beb82-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="beb82-185">Этот файл определяет страницу Razor, а не компонент.</span><span class="sxs-lookup"><span data-stu-id="beb82-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="beb82-186">Razor Pages использовать синтаксис Razor для определения серверной страницы, которая во многом аналогична странице *. aspx* .</span><span class="sxs-lookup"><span data-stu-id="beb82-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="beb82-187">`Html.RenderComponentAsync<TComponent>(RenderMode)`Метод используется для определения места, где должен быть визуализирован компонент корневого уровня.</span><span class="sxs-lookup"><span data-stu-id="beb82-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="beb82-188">`RenderMode`Параметр указывает способ подготовки компонента к просмотру.</span><span class="sxs-lookup"><span data-stu-id="beb82-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="beb82-189">В следующей таблице приведены поддерживаемые `RenderMode` Параметры.</span><span class="sxs-lookup"><span data-stu-id="beb82-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="beb82-190">Параметр</span><span class="sxs-lookup"><span data-stu-id="beb82-190">Option</span></span>                        |<span data-ttu-id="beb82-191">Описание:</span><span class="sxs-lookup"><span data-stu-id="beb82-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="beb82-192">Интерактивный просмотр после установки соединения с браузером</span><span class="sxs-lookup"><span data-stu-id="beb82-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="beb82-193">Первая предварительно визуализированная и отображаемая в интерактивном режиме</span><span class="sxs-lookup"><span data-stu-id="beb82-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="beb82-194">Отображается как статическое содержимое</span><span class="sxs-lookup"><span data-stu-id="beb82-194">Rendered as static content</span></span>|

<span data-ttu-id="beb82-195">Ссылка на скрипт для *_framework/blazor.server.js* устанавливает подключение к серверу в режиме реального времени, а затем обрабатывает все взаимодействия с пользователем и обновления пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="beb82-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="beb82-196">В Blazor WebAssembly приложении страница узла представляет собой простой статический HTML-файл в каталоге *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="beb82-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="beb82-197">`<div>`Элемент с именем ID `app` используется для указания места, где должен быть визуализирован корневой компонент.</span><span class="sxs-lookup"><span data-stu-id="beb82-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

<span data-ttu-id="beb82-198">Корневой компонент для подготовки к просмотру настраивается в `Program.Main` методе приложения с гибкостью для регистрации различных служб посредством внедрения зависимостей. Добавить службы в приложение [ Blazor WebAssembly ](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly) можно на</span><span class="sxs-lookup"><span data-stu-id="beb82-198">The root component to render is configured in the app's `Program.Main` method with the flexibility to register different services through dependency injection.You can refer add services to an app in [Blazor WebAssembly](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly)</span></span>

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a><span data-ttu-id="beb82-199">Выходные данные при создании</span><span class="sxs-lookup"><span data-stu-id="beb82-199">Build output</span></span>

<span data-ttu-id="beb82-200">При Blazor сборке проекта все файлы компонента и кода Razor компилируются в одну сборку.</span><span class="sxs-lookup"><span data-stu-id="beb82-200">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="beb82-201">В отличие от проектов веб-форм ASP.NET Blazor не поддерживает компиляцию логики пользовательского интерфейса во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="beb82-201">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="beb82-202">Запуск приложения</span><span class="sxs-lookup"><span data-stu-id="beb82-202">Run the app</span></span>

<span data-ttu-id="beb82-203">Чтобы запустить Blazor серверное приложение, нажмите `F5` в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="beb82-203">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="beb82-204">Blazor приложения не поддерживают компиляцию во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="beb82-204">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="beb82-205">Чтобы просмотреть результаты изменений разметки кода и компонентов, перестройте и перезапустите приложение с подключенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="beb82-205">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="beb82-206">Если запустить без отладчика ( `Ctrl+F5` ), Visual Studio следит за изменениями файлов и перезапускает приложение при внесении изменений.</span><span class="sxs-lookup"><span data-stu-id="beb82-206">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="beb82-207">Вы вручную обновляете браузер по мере внесения изменений.</span><span class="sxs-lookup"><span data-stu-id="beb82-207">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="beb82-208">Чтобы запустить Blazor WebAssembly приложение, выберите один из следующих подходов:</span><span class="sxs-lookup"><span data-stu-id="beb82-208">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="beb82-209">Запустите клиентский проект непосредственно с помощью сервера разработки.</span><span class="sxs-lookup"><span data-stu-id="beb82-209">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="beb82-210">Запустите серверный проект при размещении приложения с ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="beb82-210">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="beb82-211">BlazorWebAssemblyприложения можно отлаживать как в браузере, так и в Visual Studio. Дополнительные сведения см. в [ASP.NET Core Blazor WebAssembly отладки](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="beb82-211">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="beb82-212">[Назад](hosting-models.md)
>[Вперед](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="beb82-212">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
