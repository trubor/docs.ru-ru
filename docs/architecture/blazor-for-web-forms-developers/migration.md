---
title: Миграция с ASP.NET Web Forms в Blazor
description: Узнайте, как подходить к переносу существующего приложения веб-форм ASP.NET в Blazor.
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: 893b6f851681ec540629fe160749b2622b6d5440
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96509836"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Миграция с ASP.NET Web Forms в Blazor

Миграция базы кода из ASP.NET Web Forms в Blazor является трудоемкой задачей, требующей планирования. В этой главе описывается данный процесс. Для упрощения перехода следует убедиться, что приложение соответствует *N-уровневой* архитектуре, где модель приложения (в нашем примере это Web Forms) отделена от бизнес-логики. Это логическое разделение слоев делает ясным, что именно необходимо перенести на .NET Core и Blazor .

В этом примере используется приложение eShop, доступное на сайте [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor). eShop — это служба каталога, которая предоставляет возможности CRUD посредством ввода форм и проверки.

Зачем следует выполнять миграцию рабочего приложения в Blazor? Во многих случаях в этом нет необходимости. Поддержка ASP.NET Web Forms продлится еще много лет. Однако многие функции, предоставляемые Blazor, поддерживаются только в перенесенном приложении. В том числе:

- улучшения производительности на такой платформе, как `Span<T>`;
- возможность работать как WebAssembly;
- кроссплатформенная поддержка для Linux и macOS;
- локальное развертывание приложения или развертывание общей платформы без влияния на другие приложения.

Если эти или другие новые функции достаточно привлекательны, стоит обдумать миграцию приложения. Миграция может принять разные формы. Это может быть все приложение или только определенные конечные точки, для которых требуются изменения. Решение о миграции в конечном итоге зависит от бизнес-задач, которые следует решить разработчику.

## <a name="server-side-versus-client-side-hosting"></a>Размещение на стороне сервера или клиента

Как описано в главе о [моделях размещения](hosting-models.md), приложение Blazor можно разместить двумя разными способами: на стороне сервера и на стороне клиента. Серверная модель использует подключения SignalR ASP.NET Core для управления обновлениями DOM при выполнении любого фактического кода на сервере. Клиентская модель выполняется как WebAssembly в браузере и не требует соединения с сервером. Существует ряд различий, которые могут повлиять на то, что лучше всего подходит для конкретного приложения:

- Выполнение от имени WebAssembly в настоящее время не поддерживает все функции (например, потоки).
- Активный обмен данными между клиентом и сервером может вызвать проблемы с задержкой в серверном режиме.
- Для доступа к базам данных и внутренним или защищенным службам требуется отдельная служба с размещением на стороне клиента.

На момент написания этой статьи, серверная модель более похожа на Web Forms. Большая часть этой главы посвящена модели размещения на стороне сервера, так как она готова к работе.

## <a name="create-a-new-project"></a>Создание нового проекта

Этот этап начальной миграции заключается в создании нового проекта. Этот тип проекта основан на проектах в стиле пакета SDK .NET и упрощает большую часть стандартного кода, который использовался в предыдущих форматах проектов. Дополнительные сведения см. в разделе [Структура проекта](project-structure.md).

После создания проекта установите библиотеки, которые использовались в предыдущем проекте. В более старых проектах Web Forms вы могли использовать файл *packages.config* для перечисления необходимых пакетов NuGet. В новом проекте типа SDK *packages.config* был заменен элементами `<PackageReference>` в файле проекта. Преимуществом этого подхода является то, что все зависимости устанавливаются транзитно. Вы перечислите только те зависимости верхнего уровня, которые вас интересуют.

Многие из зависимостей, которые вы используете, доступны для .NET, включая Entity Framework 6 и log4net. Если нет доступной версии .NET или .NET Standard, часто можно использовать версию платформы .NET Framework. Тут все субъективно. Все используемые API, недоступные в .NET, вызывают ошибку среды выполнения. Visual Studio уведомляет вас о таких пакетах. На узле **Ссылки** проекта в **Обозревателе решений** появляется желтый значок.

В проекте eShop на основе Blazor можно просмотреть установленные пакеты. Ранее файл *packages.config* перечислял все пакеты, используемые в проекте, что приводило к длине файла в почти 50 строк. Фрагмент *packages.config* является:

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

Элемент `<packages>` включает все необходимые зависимости. Трудно выявить, какие из этих пакетов включены из-за того, что необходимы. Некоторые элементы `<package>` перечислены просто для удовлетворения потребностей необходимых зависимостей.

Проект Blazor перечисляет зависимости, которые требуются в элементе `<ItemGroup>` файла проекта:

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.4.4" />
    <PackageReference Include="log4net" Version="2.0.12" />
    <PackageReference Include="Microsoft.Extensions.Logging.Log4Net.AspNetCore" Version="2.2.12" />
</ItemGroup>
```

Одним из пакетов NuGet, которые упрощают жизнь разработчиков Web Forms, является [Пакет обеспечения совместимости Windows](../../core/porting/windows-compat-pack.md). Несмотря на то, что .NET работает на разных платформах, некоторые функции доступны только в Windows. Функции для Windows становятся доступными путем установки пакета обеспечения совместимости. Примеры таких функций включают в себя реестр, WMI и службы каталогов. Этот пакет добавляет около 20 000 API и активирует множество служб, с которыми вы, возможно, уже знакомы. Для проекта eShop не требуется пакет обеспечения совместимости; но если в проектах используются функции Windows, этот пакет упрощает миграцию.

## <a name="enable-startup-process"></a>Включение процесса запуска

Процесс запуска Blazor был изменен по сравнению с Web Forms и соответствует аналогичной настройке для других служб ASP.NET Core. При размещении на стороне сервера компоненты Blazor запускаются как часть обычного приложения ASP.NET Core. При размещении в браузере с WebAssembly компоненты Blazor используют аналогичную модель размещения. Различие состоит в том, что компоненты запускаются как отдельная служба из любого серверного процесса. В любом случае запуск будет похожим.

Файл *Global.asax.cs* является страницей запуска по умолчанию для проектов Web Forms. В проекте eShop этот файл настраивает контейнер инверсии управления (IoC) и обрабатывает различные события жизненного цикла приложения или запроса. Некоторые из этих событий обрабатываются с использованием ПО промежуточного слоя (например, `Application_BeginRequest`). Другие события нуждаются в переопределении конкретных служб посредством внедрения зависимостей (DI).

Например, файл *Global.asax.cs* для eShop содержит следующий код:

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

Предыдущий файл станет классом `Startup` на стороне сервера Blazor:

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

Одно существенное изменение по сравнению с Web Forms, которое можно заметить, — большое значение внедрения зависимостей. DI является руководящим принципом проекта ASP.NET Core. Он поддерживает настройку почти всех аспектов платформы ASP.NET Core. Существует даже встроенный поставщик услуг, который можно использовать во многих сценариях. Если требуется дополнительная настройка, она может поддерживаться многими проектами сообщества. Например, вы можете перенести свои вложения в библиотеку внедрений зависимостей от сторонних разработчиков.

В исходном приложении eSho существует определенная конфигурация управления сеансами. Так как на стороне сервер Blazor использует ASP.NET Core SignalR для связи, состояние сеанса не поддерживается, так как соединения могут происходить независимо от контекста HTTP. Для приложения, использующего состояние сеанса, требуется пересоздать архитектуру перед запуском в качестве приложения Blazor.

Дополнительные сведения о запуске приложения см. в разделе [Запуск приложения](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Перенос HTTP-модулей и обработчиков в ПО промежуточного слоя

HTTP-модули и обработчики — это общие шаблоны для управления конвейером HTTP-запросов в Web Forms. Классы, которые реализуют `IHttpModule` или `IHttpHandler`, могут быть зарегистрированы и обрабатывать входящие запросы. Web Forms настраивает модули и обработчики в файле *web.config*. Web Forms также во многом строятся вокруг обработки событий жизненного цикла приложения. Вместо этого ASP.NET Core использует ПО промежуточного слоя. ПО промежуточного слоя регистрируется в методе `Configure` класса `Startup`. Порядок выполнения ПО промежуточного слоя определяется порядком регистрации.

В разделе [Включение процесса запуска](#enable-startup-process) событие жизненного цикла было вызвано Web Forms в качестве метода `Application_BeginRequest`. Это событие недоступно в ASP.NET Core. Одним из способов добиться такого поведения является реализация ПО промежуточного слоя, как показано в файле *Startup.cs*. Это ПО промежуточного слоя выполняет ту же логику, а затем передает управление следующему обработчику в конвейере ПО промежуточного слоя.

Дополнительные сведения о миграции модулей и обработчиков см. в разделе [Миграция обработчиков и модулей HTTP в ПО промежуточного слоя ASP.NET Core](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Миграция статических файлов

Для обслуживания статических файлов (например, HTML, CSS, изображений и JavaScript) файлы должны предоставляться ПО промежуточного слоя. Вызов метода `UseStaticFiles` позволяет обслуживать статические файлы из корневого пути в Интернете. Корневой каталог веб-сайта по умолчанию — *wwwroot*, но его можно настроить. Как включено в `Configure` метод класса `Startup` eShop:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Проект eShop обеспечивает базовый доступ к статическим файлам. Существует множество настроек, доступных для доступа к статическим файлам. Сведения о включении файлов по умолчанию или обозревателя файлов см. в разделе [Статические файлы в ASP.NET Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Перенос настройки объединения и минификации среды выполнения

Объединение и минификация — это методы оптимизации производительности, позволяющие сократить количество и размер запросов сервера для получения определенных типов файлов. JavaScript и CSS часто проходят некоторую форму объединения или минификации перед отправкой клиенту. В ASP.NET Web Forms эти оптимизации обрабатываются во время выполнения. Соглашения по оптимизации определяют файл *App_Start/BundleConfig.cs*. В ASP.NET Core применяется более декларативный подход. Файл содержит список файлов, которые будут минифицированы, а также конкретные параметры минификации.

Дополнительные сведения о объединениях и минификации см. в разделе [Объединяйте и минифицируйте статические ресурсы в ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Перенос страниц ASPX

Страница в приложении Web Forms — это файл с расширением *.aspx*. Страница Web Forms часто может быть сопоставлена с компонентом в Blazor. Компонент Blazor создан в файле с расширением *.razor*. Для проекта eShop пять страниц преобразуются в страницу Razor.

Например, подробное представление состоит из трех файлов в проекте Web Forms: *Details.aspx*, *Details.aspx.cs* и *Details.aspx.designer.cs*. При преобразовании в Blazor код программной части и разметка объединяются в *Details.razor*. Компиляция Razor (эквивалентная содержимому файлов *.designer.cs*) хранится в каталоге *obj* и по умолчанию не отображается в **Обозревателе решений**. Страница Web Forms состоит из следующей разметки:

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

Код программной части предыдущей разметки включает следующий код:

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

При преобразовании в Blazor страница Web Forms преобразуется в следующий код:

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

Обратите внимание, что код и разметка находятся в одном файле. Все необходимые службы становятся доступными с помощью атрибута `@inject`. Согласно директиве `@page`, эта страница доступна по маршруту `Catalog/Details/{id}`. Значение заполнителя `{id}` маршрута ограничено целым числом. Как описано в разделе о [маршрутизации](pages-routing-layouts.md), в отличие от Web Forms, компонент Razor явным образом указывает свой маршрут и все включенные параметры. Многие элементы управления Web Forms могут не иметь точных аналогов в Blazor. Часто существует эквивалентный фрагмент кода HTML, который будет использоваться в той же цели. Например, элемент управления `<asp:Label />` можно заменить на HTML-элемент `<label>`.

### <a name="model-validation-in-blazor"></a>Проверка модели в Blazor

Если код Web Forms включает проверку, вы можете переносить многие из них с минимальными изменениями. Преимуществом работы в Blazor является то, что та же логика проверки может быть запущена без использования пользовательского кода JavaScript. Заметки к данным обеспечивают простую проверку модели.

Например, страница *Create.aspx* содержит форму ввода данных с проверкой. Пример фрагмента кода будет выглядеть следующим образом:

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

В Blazor эквивалентная разметка указана в файле *Create.razor*:

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

Контекст `EditForm` включает поддержку проверки и может быть оболочкой вокруг входных данных. Заметки к данным являются обычным способом добавления проверки. Такая поддержка проверки может быть добавлена через компонент `DataAnnotationsValidator`. Дополнительные сведения об этом механизме см. в разделе [Формы и проверка Blazor ASP.NET Core](/aspnet/core/blazor/forms-validation).

## <a name="migrate-configuration"></a>Миграция конфигурации

В проекте Web Forms данные конфигурации чаще всего хранятся в файле *web.config*. Доступ к данным конфигурации осуществляется с помощью `ConfigurationManager`. Службам часто требовалось анализировать объекты. С выходом платформы .NET Framework 4.7.2 компонуемость была добавлена в конфигурацию с помощью `ConfigurationBuilders`. Эти построители позволяли разработчикам добавлять различные источники для конфигурации, которая затем компоновалась во время выполнения, чтобы получить необходимые значения.

ASP.NET Core представил гибкую систему конфигурации, позволяющую определять источник или источники конфигурации, используемые приложением и развертыванием. Инфраструктура `ConfigurationBuilder`, которую можно использовать в приложении ASP.NET Web Forms, была смоделирована на основе концепций, используемых в системе конфигурации ASP.NET Core.

В следующем фрагменте кода показано, как проект eShop Web Forms использует *web.config* для хранения значений конфигурации:

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

Секреты, такие как строки подключения к базе данных, часто хранятся в *web.config*. Такие секреты неизбежно оказываются в незащищенных расположениях, таких как система управления версиями. При использовании Blazor в ASP.NET Core предыдущая конфигурация на основе XML заменяется следующим JSON:

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON является форматом конфигурации по умолчанию. Однако ASP.NET Core поддерживает многие другие форматы, в том числе XML. Существует также несколько форматов, поддерживаемых сообществом.

Конструктор в классе `Startup` проекта Blazor принимает экземпляр `IConfiguration` с помощью метода DI, известного как внедрение конструктора:

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

По умолчанию переменные среды, JSON-файлы (*appsettings.json* и *appsettings.{Environment}.json*) и параметры командной строки регистрируются в объекте конфигурации как допустимые источники конфигурации. Доступ к источникам конфигурации можно получить с помощью `Configuration[key]`. Более сложная методика — привязать данные конфигурации к объектам с помощью шаблона параметров. Дополнительные сведения о конфигурации и шаблоне параметров см. в разделах [Конфигурация в ASP.NET Core](/aspnet/core/fundamentals/configuration/) и [Шаблон параметров в ASP.NET Core](/aspnet/core/fundamentals/configuration/options), соответственно.

## <a name="migrate-data-access"></a>Перенос доступа к данным

Доступ к данным является важным аспектом любого приложения. Проект eShop хранит сведения о каталоге в базе данных и извлекает их с помощью Entity Framework (EF) 6. Поскольку EF 6 поддерживается в .NET 5.0, проект может продолжать его использовать.

Для eShop были необходимы следующие изменения, связанные с EF:

- В .NET Framework объект `DbContext` принимает строку с *name=ConnectionString* и использует строку подключения из `ConfigurationManager.AppSettings[ConnectionString]` для подключения. В .NET Core это не поддерживается. Строку подключения необходимо предоставить.
- Доступ к базе данных осуществлялся синхронно. Хотя это и работает, масштабируемость может снизиться. Эта логика должна быть перемещена в асинхронную модель.

Несмотря на то, что такой собственной поддержки привязки набора данных больше не будет, Blazor обеспечивает гибкость и большие возможности за счет поддержки C# на странице Razor. Например, можно выполнять вычисления и отображать результат. Дополнительные сведения о шаблонах данных в Blazor см. в главе [Доступ к данным](data.md).

## <a name="architectural-changes"></a>Изменения архитектуры

Наконец, существуют некоторые важные архитектурные различия, которые следует учитывать при переходе на Blazor. Многие из этих изменений применимы ко всему, основанному на .NET Core или ASP.NET Core.

Поскольку Blazor основана на .NET Core, есть рекомендации по обеспечению поддержки в .NET Core. Некоторые из основных изменений включают удаление следующих компонентов:

- Несколько доменов AppDomain
- Удаленное взаимодействие
- CAS (Code Access Security — безопасность доступа кода)
- Прозрачность безопасности

Дополнительные сведения о методах, позволяющих определить необходимые изменения для поддержки работы в .NET Core, см. в разделе [Перенос кода из .NET Framework в .NET Core](../../core/porting/index.md).

ASP.NET Core является пересмотренной версией ASP.NET и содержит некоторые изменения, которые изначально не кажутся очевидными. Основные изменения таковы:

- Нет контекста синхронизации, что означает отсутствие `HttpContext.Current`, `Thread.CurrentPrincipal` или иных статических методов доступа.
- Нет теневого копирования.
- Нет очереди запросов.

Многие операции в ASP.NET Core являются асинхронными, что позволяет упростить отгрузку задач, связанных с вводом-выводом. Важно никогда не блокировать с помощью `Task.Wait()` или `Task.GetResult()`, что может быстро истощить ресурсы пула потоков.

## <a name="migration-conclusion"></a>Заключение по миграции

На этом этапе вы видели много примеров того, что требуется для перемещения проекта Web Forms в Blazor. Полный пример см. в проекте [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor).

>[!div class="step-by-step"]
>[Назад](security-authentication-authorization.md)
