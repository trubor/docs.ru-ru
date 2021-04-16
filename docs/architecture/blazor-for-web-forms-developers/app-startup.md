---
title: Запуск приложений
description: Узнайте, как определить логику запуска для приложения.
author: csharpfritz
ms.author: jefritz
ms.date: 11/20/2020
ms.openlocfilehash: d812079f84f67409334d07c4c10c5577446503be
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509706"
---
# <a name="app-startup"></a><span data-ttu-id="7bb9d-103">Запуск приложений</span><span class="sxs-lookup"><span data-stu-id="7bb9d-103">App startup</span></span>

<span data-ttu-id="7bb9d-104">Приложения, написанные для ASP.NET, обычно имеют файл `global.asax.cs`, определяющий событие `Application_Start`, которое управляет тем, какие службы настроены и доступны как для преобразования для просмотра HTML, так и для обработки .NET.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="7bb9d-105">В этой главе рассматриваются небольшие различия между ASP.NET Core и Blazor Server.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="7bb9d-106">Application_Start и Web Forms</span><span class="sxs-lookup"><span data-stu-id="7bb9d-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="7bb9d-107">Метод Web Forms по умолчанию `Application_Start` разросся в течение нескольких лет для решения многих задач настройки.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="7bb9d-108">Новый проект Web Forms с шаблоном по умолчанию в Visual Studio 2019 теперь содержит следующую логику конфигурации:</span><span class="sxs-lookup"><span data-stu-id="7bb9d-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="7bb9d-109">`RouteConfig` — маршрутизация URL-адресов приложений.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="7bb9d-110">`BundleConfig` — объединение и минификация CSS и JavaScript.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="7bb9d-111">Каждый из этих отдельных файлов находится в папке `App_Start` и запускается только один раз в начале приложения.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-111">Each of these individual files resides in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="7bb9d-112">`RouteConfig` в шаблоне проекта по умолчанию добавляет `FriendlyUrlSettings` для Web Forms, чтобы разрешить URL-адресам приложений опустить расширение файла `.ASPX`.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="7bb9d-113">Шаблон по умолчанию также содержит директиву, которая предоставляет постоянные коды состояния перенаправления HTTP (HTTP 301) для страниц `.ASPX` по понятному URL-адресу с именем файла, в котором пропущено расширение.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="7bb9d-114">В ASP.NET Core и Blazor эти методы либо упрощены и объединяются в класс `Startup`, либо устраняются в пользу распространенных веб-технологий.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="7bb9d-115">Структура класса Startup Blazor Server</span><span class="sxs-lookup"><span data-stu-id="7bb9d-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="7bb9d-116">Приложения Blazor Server размещаются поверх ASP.NET Core 3.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later version.</span></span>  <span data-ttu-id="7bb9d-117">Веб-приложения ASP.NET Core настраиваются с помощью пары методов класса `Startup.cs` в корневой папке приложения.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="7bb9d-118">Содержимое класса Startup по умолчанию указано ниже.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="7bb9d-119">Как и остальная часть ASP.NET Core, класс Startup создается с принципами внедрения зависимостей.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="7bb9d-120">`IConfiguration` предоставляется конструктору и скрывается в открытом свойстве для последующего доступа во время настройки.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="7bb9d-121">Метод `ConfigureServices`, представленный в ASP.NET Core, позволяет настроить различные службы платформы ASP.NET Core для встроенного контейнера внедрения зависимостей платформы.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="7bb9d-122">Различные методы `services.Add*` добавляют службы, которые включают такие функции, как проверка подлинности, Razor Pages, маршрутизация контроллера MVC, SignalR и взаимодействие с Blazor Server, среди многих других.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="7bb9d-123">Этот метод не требовался в веб-формах, так как синтаксический анализ и обработка файлов ASPX, ASCX, ASHX и ASMX были определены ссылками на ASP.NET в файле конфигурации web.config.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files were defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="7bb9d-124">Дополнительные сведения о внедрении зависимостей в ASP.NET Core доступны в [интерактивной документации](/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="7bb9d-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="7bb9d-125">Метод `Configure` представляет концепцию конвейера HTTP для ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="7bb9d-126">В этом методе мы объявляем сверху вниз [ПО промежуточного слоя](middleware.md), которое будет обрабатывать все запросы, отправленные в наше приложение.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="7bb9d-127">Большинство этих функций в конфигурации по умолчанию были разбиты по файлам конфигурации Web Forms и теперь находятся в одном месте для простоты ссылок.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="7bb9d-128">Конфигурация настраиваемой страницы ошибок больше не помещается в файл `web.config`, теперь она настроена так, чтобы всегда отображаться, если среда приложения не помечена `Development`.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="7bb9d-129">Кроме того, приложения ASP.NET Core настроены для предоставления защищенных страниц с помощью TLS по умолчанию, используя вызов метода `UseHttpsRedirection`.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="7bb9d-130">Далее в `UseStaticFiles` указан непредвиденный метод конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="7bb9d-131">В ASP.NET Core поддержка запросов для статических файлов (таких как JavaScript, CSS и файлы изображений) должна быть явно включена. По умолчанию общедоступными могут быть только файлы в папке *wwwroot* приложения.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="7bb9d-132">Следующая строка является первой, которая реплицирует один из параметров конфигурации из Web Forms: `UseRouting`.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="7bb9d-133">Этот метод добавляет маршрутизатор ASP.NET Core к конвейеру, который можно настроить здесь или в отдельных файлах, к которым может быть выполнена маршрутизация.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="7bb9d-134">Дополнительные сведения о конфигурации маршрутизации см. в [разделе "Маршрутизация"](pages-routing-layouts.md).</span><span class="sxs-lookup"><span data-stu-id="7bb9d-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="7bb9d-135">Последняя инструкция в этом методе определяет конечные точки, которые прослушивает ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="7bb9d-136">Эти маршруты представляют собой доступные в Интернете расположения, к которым вы можете получить доступ на веб-сервере для получения некоторого содержимого, обрабатываемого .NET, и возвращаемого вам.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-136">These routes are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="7bb9d-137">Первая запись, `MapBlazorHub`, настраивает концентратор SignalR для предоставления постоянного подключения в режиме реального времени к серверу, где обрабатывается состояние и преобразование для просмотра компонентов Blazor.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="7bb9d-138">Вызов метода `MapFallbackToPage` указывает на веб-расположение страницы, которая запускает приложение Blazor, а также настраивает приложение для обработки запросов на глубокую компоновку со стороны клиента.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="7bb9d-139">Эту функцию можно увидеть в действии, если открыть браузер и перейти непосредственно к обработанному Blazor маршруту в приложении, например `/counter` в шаблоне проекта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="7bb9d-140">Запрос обрабатывается с помощью резервной страницы *_Host. cshtml*, которая затем запускает маршрутизатор Blazor и визуализирует страницу счетчика.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="7bb9d-141">Обновление процесса BundleConfig</span><span class="sxs-lookup"><span data-stu-id="7bb9d-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="7bb9d-142">Технологии объединения таких ресурсов, как таблицы стилей CSS и файлы JavaScript, значительно развились благодаря другим технологиям, обеспечивающим быстрое развитие средств и методов управления этими ресурсами.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="7bb9d-143">Для этого мы рекомендуем использовать средство командной строки узла, такое как Grunt/Gulp/WebPack, для упаковки статических ресурсов.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="7bb9d-144">Средства командной строки Grunt, Gulp и WebPack и связанные с ними конфигурации могут быть добавлены в приложение, а ASP.NET Core будет тихо игнорировать эти файлы в процессе сборки приложения.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="7bb9d-145">Можно добавить вызов для выполнения их задач, добавив `Target` внутри файла проекта, с синтаксисом, аналогичный приведенному ниже, который будет запускать сценарий gulp и целевой объект `min` внутри этого скрипта.</span><span class="sxs-lookup"><span data-stu-id="7bb9d-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="7bb9d-146">Дополнительные сведения о обеих стратегиях управления файлами CSS и JavaScript можно найти в документации по [Объединению и минификации статических ресурсов в ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span><span class="sxs-lookup"><span data-stu-id="7bb9d-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7bb9d-147">[Назад](project-structure.md)
>[Вперед](components.md)</span><span class="sxs-lookup"><span data-stu-id="7bb9d-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
