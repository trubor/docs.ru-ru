---
title: Структура проекта для приложений Blazor
description: Сведения о сравнении структур проектов ASP.NET Web Forms и Blazor.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: ba7113c88db728f30812821deaf7c06a80663d1f
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "98189093"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="c7ace-103">Структура проекта для приложений Blazor</span><span class="sxs-lookup"><span data-stu-id="c7ace-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="c7ace-104">Несмотря на существенные различия в структуре проекта, в ASP.NET Web Forms и Blazor применяются многие схожие концепции.</span><span class="sxs-lookup"><span data-stu-id="c7ace-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="c7ace-105">Здесь мы рассмотрим структуру проекта Blazor и сравним ее с проектом ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="c7ace-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="c7ace-106">Чтобы создать свое первое приложение Blazor, следуйте инструкциям в статье о [начале работы с Blazor](/aspnet/core/blazor/get-started).</span><span class="sxs-lookup"><span data-stu-id="c7ace-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="c7ace-107">Вы можете выполнить инструкции, чтобы создать приложение Blazor Server или приложение Blazor WebAssembly, размещенное в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7ace-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="c7ace-108">За исключением логики размещения для конкретной модели, большая часть кода в обоих проектах одинакова.</span><span class="sxs-lookup"><span data-stu-id="c7ace-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="c7ace-109">Файл проекта</span><span class="sxs-lookup"><span data-stu-id="c7ace-109">Project file</span></span>

<span data-ttu-id="c7ace-110">Приложения Blazor Server — это проекты .NET.</span><span class="sxs-lookup"><span data-stu-id="c7ace-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="c7ace-111">Файл проекта для приложения Blazor Server максимально прост:</span><span class="sxs-lookup"><span data-stu-id="c7ace-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="c7ace-112">Файл проекта для приложения Blazor WebAssembly выглядит немного более детальным (конкретные номера версии могут отличаться):</span><span class="sxs-lookup"><span data-stu-id="c7ace-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

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

<span data-ttu-id="c7ace-113">Проект Blazor WebAssembly ориентирован на `Microsoft.NET.Sdk.BlazorWebAssembly` вместо пакета SDK `Microsoft.NET.Sdk.Web`, так как они выполняются в браузере в среде выполнения .NET на основе WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="c7ace-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="c7ace-114">Вы не можете установить .NET в веб-браузер, как на сервере или на компьютере разработчика.</span><span class="sxs-lookup"><span data-stu-id="c7ace-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="c7ace-115">Следовательно, проект ссылается на платформу Blazor, используя отдельные ссылки на пакеты.</span><span class="sxs-lookup"><span data-stu-id="c7ace-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="c7ace-116">Для сравнения проект ASP.NET Web Forms по умолчанию включает в себя почти 300 строк XML-кода в файле *. CSPROJ*, большинство которых явно задает в проекте различные файлы кода и содержимого.</span><span class="sxs-lookup"><span data-stu-id="c7ace-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="c7ace-117">С выпуском `.NET 5` приложения `Blazor Server` и `Blazor WebAssembly` могут легко совместно использовать одну единую среду выполнения.</span><span class="sxs-lookup"><span data-stu-id="c7ace-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="c7ace-118">Отдельные ссылки на сборки, хотя они и поддерживаются, не так сильно распространены в проектах .NET.</span><span class="sxs-lookup"><span data-stu-id="c7ace-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="c7ace-119">Большинство зависимостей проектов обрабатываются как ссылки на пакеты NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7ace-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="c7ace-120">В проектах .NET требуется ссылаться только на зависимости пакетов верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="c7ace-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="c7ace-121">Транзитивные зависимости включаются автоматически.</span><span class="sxs-lookup"><span data-stu-id="c7ace-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="c7ace-122">Вместо того чтобы использовать для ссылок на пакеты файл *packages.config*, который обычно находится в проектах ASP.NET Web Forms, ссылки на пакеты добавляются в файл проекта с помощью элемента `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="c7ace-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="c7ace-123">Точка входа</span><span class="sxs-lookup"><span data-stu-id="c7ace-123">Entry point</span></span>

<span data-ttu-id="c7ace-124">Точка входа приложения Blazor Server определяется в файле *Program.cs*, как реализовано в консольном приложении.</span><span class="sxs-lookup"><span data-stu-id="c7ace-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="c7ace-125">При выполнении приложение создает и запускает экземпляр хост-сайта с использованием значений по умолчанию, характерных для веб-приложений.</span><span class="sxs-lookup"><span data-stu-id="c7ace-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="c7ace-126">Хост-сайт управляет жизненным циклом приложения Blazor Server и настраивает службы на уровне узла.</span><span class="sxs-lookup"><span data-stu-id="c7ace-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="c7ace-127">Примерами таких служб являются конфигурация, ведение журнала, внедрение зависимостей и HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="c7ace-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="c7ace-128">Этот код в основном является стандартным, и часто его оставляют без изменений.</span><span class="sxs-lookup"><span data-stu-id="c7ace-128">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="c7ace-129">Приложения Blazor WebAssembly также определяют точку входа в файле *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="c7ace-130">Сам код выглядит немного иначе.</span><span class="sxs-lookup"><span data-stu-id="c7ace-130">The code looks slightly different.</span></span> <span data-ttu-id="c7ace-131">Этот код аналогичен тому, который настраивает хост приложений для предоставления приложению тех же служб уровня узла.</span><span class="sxs-lookup"><span data-stu-id="c7ace-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="c7ace-132">Однако хост приложений WebAssembly не настраивает HTTP-сервер, так как он выполняется непосредственно в браузере.</span><span class="sxs-lookup"><span data-stu-id="c7ace-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="c7ace-133">Приложения Blazor имеют класс `Startup` вместо файла *Global.asax*, чтобы определить логику запуска для приложения.</span><span class="sxs-lookup"><span data-stu-id="c7ace-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="c7ace-134">Класс `Startup` используется для настройки приложения и всех связанных с ним служб.</span><span class="sxs-lookup"><span data-stu-id="c7ace-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="c7ace-135">В приложении Blazor Server класс `Startup` используется в целях настройки конечной точки для соединения в режиме реального времени, используемого Blazor между клиентскими браузерами и сервером.</span><span class="sxs-lookup"><span data-stu-id="c7ace-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="c7ace-136">В приложении Blazor WebAssembly класс `Startup` определяет корневые компоненты приложения и то, где они должны отрисовываться.</span><span class="sxs-lookup"><span data-stu-id="c7ace-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="c7ace-137">Мы подробнее рассмотрим класс `Startup` в разделе [Запуск приложения](./app-startup.md).</span><span class="sxs-lookup"><span data-stu-id="c7ace-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="c7ace-138">Статические файлы</span><span class="sxs-lookup"><span data-stu-id="c7ace-138">Static files</span></span>

<span data-ttu-id="c7ace-139">В отличие от проектов ASP.NET Web Forms, не все файлы проекта Blazor можно запрашивать как статические файлы.</span><span class="sxs-lookup"><span data-stu-id="c7ace-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="c7ace-140">Веб-адресации подлежат только файлы в папке *wwwroot*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="c7ace-141">Эта папка называется "веб-корнем" приложения.</span><span class="sxs-lookup"><span data-stu-id="c7ace-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="c7ace-142">Все, что находится за пределами веб-корня приложения, *не подлежит* веб-адресации.</span><span class="sxs-lookup"><span data-stu-id="c7ace-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="c7ace-143">Такая настройка обеспечивает дополнительный уровень безопасности, который предотвращает случайное раскрытие файлов проекта через Интернет.</span><span class="sxs-lookup"><span data-stu-id="c7ace-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="c7ace-144">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="c7ace-144">Configuration</span></span>

<span data-ttu-id="c7ace-145">Конфигурация в приложениях ASP.NET Web Forms обычно реализуется с помощью одного или нескольких файлов *web.config*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="c7ace-146">У приложений Blazor файлы *web.config* обычно отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="c7ace-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="c7ace-147">В противном случае этот файл используется только для настройки параметров, имеющих отношение к IIS, при размещении в службах IIS.</span><span class="sxs-lookup"><span data-stu-id="c7ace-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="c7ace-148">Вместо этого приложения Blazor Server используют абстракции конфигурации ASP.NET Core (сейчас приложения Blazor WebAssembly не поддерживают одни и те же абстракции конфигурации, но эта функция может быть добавлена в будущем).</span><span class="sxs-lookup"><span data-stu-id="c7ace-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="c7ace-149">Например, приложение Blazor Server по умолчанию хранит некоторые параметры в *appsettings.json*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="c7ace-150">Дополнительные сведения о конфигурации в проектах ASP.NET Core см. в разделе [Конфигурации](./config.md).</span><span class="sxs-lookup"><span data-stu-id="c7ace-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="c7ace-151">Компоненты Razor</span><span class="sxs-lookup"><span data-stu-id="c7ace-151">Razor components</span></span>

<span data-ttu-id="c7ace-152">Большинство файлов в проектах Blazor являются файлами *RAZOR*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="c7ace-153">Razor — это язык для создания шаблонов на основе HTML и C#, который используется для динамического создания пользовательского веб-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c7ace-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="c7ace-154">Файлы *RAZOR* определяют компоненты, составляющие пользовательский интерфейс приложения.</span><span class="sxs-lookup"><span data-stu-id="c7ace-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="c7ace-155">В большинстве случаев компоненты для приложений Blazor Server и Blazor WebAssembly идентичны.</span><span class="sxs-lookup"><span data-stu-id="c7ace-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="c7ace-156">Компоненты в Blazor аналогичны пользовательским элементам управления в ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="c7ace-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="c7ace-157">Каждый файл компонента Razor компилируется в класс .NET при сборке проекта.</span><span class="sxs-lookup"><span data-stu-id="c7ace-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="c7ace-158">Созданный класс захватывает состояние компонента, логику отрисовки, методы жизненного цикла, обработчики событий и другую логику.</span><span class="sxs-lookup"><span data-stu-id="c7ace-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="c7ace-159">Мы рассмотрим создание компонентов разделе [Создание компонентов пользовательского интерфейса, пригодных для повторного использования, с помощью Blazor](./components.md).</span><span class="sxs-lookup"><span data-stu-id="c7ace-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="c7ace-160">Файлы *_Imports.razor* не являются файлами компонентов Razor.</span><span class="sxs-lookup"><span data-stu-id="c7ace-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="c7ace-161">Вместо этого они определяют набор директив Razor для импорта в другие файлы *RAZOR* в той же папке и вложенных в нее папках.</span><span class="sxs-lookup"><span data-stu-id="c7ace-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="c7ace-162">Например, файл *_Imports.razor* представляет собой стандартный способ добавления директив `using` для часто используемых пространств имен:</span><span class="sxs-lookup"><span data-stu-id="c7ace-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="c7ace-163">Страницы</span><span class="sxs-lookup"><span data-stu-id="c7ace-163">Pages</span></span>

<span data-ttu-id="c7ace-164">Где находятся страницы в приложениях Blazor?</span><span class="sxs-lookup"><span data-stu-id="c7ace-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="c7ace-165">Blazor не определяет отдельное расширение файла для адресуемых страниц, например, как файлы *ASPX* в приложениях ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="c7ace-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="c7ace-166">Вместо этого страницы определяются путем назначения маршрутов компонентам.</span><span class="sxs-lookup"><span data-stu-id="c7ace-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="c7ace-167">Маршрут обычно назначается с помощью директивы Razor `@page`.</span><span class="sxs-lookup"><span data-stu-id="c7ace-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="c7ace-168">Например, компонент `Counter`, созданный в файле *Pages/Counter.razor*, определяет следующий маршрут:</span><span class="sxs-lookup"><span data-stu-id="c7ace-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="c7ace-169">Маршрутизация в Blazor обрабатывается на стороне клиента, а не на сервере.</span><span class="sxs-lookup"><span data-stu-id="c7ace-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="c7ace-170">При переходе пользователя в браузере Blazor перехватывает навигацию, а затем отрисовывает компонент с соответствующим маршрутом.</span><span class="sxs-lookup"><span data-stu-id="c7ace-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="c7ace-171">Маршруты компонентов сейчас не выводятся расположением файлов компонента, как это имеет место для страниц *ASPX*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="c7ace-172">Возможно, мы добавим эту функцию в будущем.</span><span class="sxs-lookup"><span data-stu-id="c7ace-172">This feature may be added in the future.</span></span> <span data-ttu-id="c7ace-173">Каждый маршрут должен быть указан для компонента явно.</span><span class="sxs-lookup"><span data-stu-id="c7ace-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="c7ace-174">Хранение маршрутизируемых компонентов в папке *Pages* не имеет особого значения и является просто соглашением.</span><span class="sxs-lookup"><span data-stu-id="c7ace-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="c7ace-175">Маршрутизацию в Blazor мы более подробно рассмотрим в разделе [Страницы, маршрутизация и макеты](./pages-routing-layouts.md).</span><span class="sxs-lookup"><span data-stu-id="c7ace-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="c7ace-176">Layout</span><span class="sxs-lookup"><span data-stu-id="c7ace-176">Layout</span></span>

<span data-ttu-id="c7ace-177">В приложениях ASP.NET Web Forms общий макет страницы обрабатывается с использованием эталонных страниц (*Site.Master*).</span><span class="sxs-lookup"><span data-stu-id="c7ace-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="c7ace-178">В приложениях Blazor макет страницы обрабатывается с использованием компонентов макета (*Shared/MainLayout.razor*).</span><span class="sxs-lookup"><span data-stu-id="c7ace-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="c7ace-179">Компоненты макета будут более подробно рассмотрены в разделе [Страницы, маршрутизация и макеты](./pages-routing-layouts.md).</span><span class="sxs-lookup"><span data-stu-id="c7ace-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="c7ace-180">Начальная загрузка Blazor</span><span class="sxs-lookup"><span data-stu-id="c7ace-180">Bootstrap Blazor</span></span>

<span data-ttu-id="c7ace-181">Для начальной загрузки Blazor приложение должно:</span><span class="sxs-lookup"><span data-stu-id="c7ace-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="c7ace-182">указывать, где на странице следует отрисовывать корневой компонент (*App.Razor*);</span><span class="sxs-lookup"><span data-stu-id="c7ace-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="c7ace-183">добавить соответствующий сценарий платформы Blazor.</span><span class="sxs-lookup"><span data-stu-id="c7ace-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="c7ace-184">В приложении Blazor Server страница узла корневого компонента определена в файле *_Host.cshtml*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="c7ace-185">Этот файл определяет страницу Razor, а не компонент.</span><span class="sxs-lookup"><span data-stu-id="c7ace-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="c7ace-186">Страницы Razor используют синтаксис Razor для определения адресуемой сервером страницы, которая во многом аналогична странице *ASPX*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="c7ace-187">Метод `Html.RenderComponentAsync<TComponent>(RenderMode)` используется для определения места, где требуется отрисовать компонент корневого уровня.</span><span class="sxs-lookup"><span data-stu-id="c7ace-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="c7ace-188">Параметр `RenderMode` указывает способ отрисовки компонента.</span><span class="sxs-lookup"><span data-stu-id="c7ace-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="c7ace-189">В следующей таблице указаны поддерживаемые параметры `RenderMode`.</span><span class="sxs-lookup"><span data-stu-id="c7ace-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="c7ace-190">Параметр</span><span class="sxs-lookup"><span data-stu-id="c7ace-190">Option</span></span>                        |<span data-ttu-id="c7ace-191">Описание</span><span class="sxs-lookup"><span data-stu-id="c7ace-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="c7ace-192">Интерактивная отрисовка после установки соединения с браузером</span><span class="sxs-lookup"><span data-stu-id="c7ace-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="c7ace-193">Сначала предварительная отрисовка, а затем интерактивная отрисовка.</span><span class="sxs-lookup"><span data-stu-id="c7ace-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="c7ace-194">Отрисовка в виде статического содержимого.</span><span class="sxs-lookup"><span data-stu-id="c7ace-194">Rendered as static content</span></span>|

<span data-ttu-id="c7ace-195">Ссылка сценария на *_framework/blazor.server.js* обеспечивает подключение к серверу в режиме реального времени и последующую обработку всего взаимодействия с пользователем и обновлений пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="c7ace-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="c7ace-196">В приложении Blazor WebAssembly страница узла представляет собой простой статический HTML-файл по пути *wwwroot/index.html*.</span><span class="sxs-lookup"><span data-stu-id="c7ace-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="c7ace-197">Элемент `<div>` с идентификатором `app` используется для указания того, где должен быть отрисован корневой компонент.</span><span class="sxs-lookup"><span data-stu-id="c7ace-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

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

<span data-ttu-id="c7ace-198">Подлежащий отрисовке корневой компонент указан в методе `Program.Main` приложения с гибкой возможностью регистрации служб посредством внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="c7ace-198">The root component to render is specified in the app's `Program.Main` method with the flexibility to register services through dependency injection.</span></span> <span data-ttu-id="c7ace-199">Дополнительные сведения см. в статье [Внедрение зависимостей Blazor ASP.NET Core](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span><span class="sxs-lookup"><span data-stu-id="c7ace-199">For more information, see [ASP.NET Core Blazor dependency injection](/aspnet/core/blazor/fundamentals/dependency-injection?pivots=webassembly).</span></span>

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

## <a name="build-output"></a><span data-ttu-id="c7ace-200">Выходные данные при создании</span><span class="sxs-lookup"><span data-stu-id="c7ace-200">Build output</span></span>

<span data-ttu-id="c7ace-201">При сборке проекта Blazor все файлы компонентов и кода Razor компилируются в одну сборку.</span><span class="sxs-lookup"><span data-stu-id="c7ace-201">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="c7ace-202">В отличие от проектов ASP.NET Web Forms, Blazor не поддерживает компиляцию логики пользовательского интерфейса во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c7ace-202">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c7ace-203">Запустите приложение</span><span class="sxs-lookup"><span data-stu-id="c7ace-203">Run the app</span></span>

<span data-ttu-id="c7ace-204">Чтобы запустить приложение Blazor Server, нажмите клавишу `F5` в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c7ace-204">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="c7ace-205">Приложения Blazor не поддерживают компиляцию во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c7ace-205">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="c7ace-206">Чтобы просмотреть результаты изменений разметки кода и компонентов, перестройте и перезапустите приложение с подключенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="c7ace-206">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="c7ace-207">Если выполнить запуск без подключенного отладчика (`Ctrl+F5`), Visual Studio отслеживает изменения файлов и перезапускает приложение при внесении изменений.</span><span class="sxs-lookup"><span data-stu-id="c7ace-207">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="c7ace-208">Вы вручную обновляете браузер по мере внесения изменений.</span><span class="sxs-lookup"><span data-stu-id="c7ace-208">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="c7ace-209">Чтобы запустить приложение Blazor WebAssembly, воспользуйтесь одним из перечисленных ниже подходов:</span><span class="sxs-lookup"><span data-stu-id="c7ace-209">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="c7ace-210">Запустите клиентский проект непосредственно с помощью сервера разработки.</span><span class="sxs-lookup"><span data-stu-id="c7ace-210">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="c7ace-211">Запустите серверный проект при размещении приложения в ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7ace-211">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="c7ace-212">Приложения Blazor WebAssembly можно отлаживать как в браузере, так и в Visual Studio. Дополнительные сведения см. в разделе [Отладка ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug).</span><span class="sxs-lookup"><span data-stu-id="c7ace-212">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c7ace-213">[Назад](hosting-models.md)
>[Вперед](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="c7ace-213">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
