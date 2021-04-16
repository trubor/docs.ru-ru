---
title: Страницы, маршрутизация и макеты
description: Узнайте, как создавать страницы в Blazor, работать с маршрутизацией на стороне клиента и управлять разметкой страниц.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/19/2019
ms.openlocfilehash: 714ba0be7c2014895a75250a47e6ce448863eb6c
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "88267793"
---
# <a name="pages-routing-and-layouts"></a><span data-ttu-id="6c010-103">Страницы, маршрутизация и макеты</span><span class="sxs-lookup"><span data-stu-id="6c010-103">Pages, routing, and layouts</span></span>

<span data-ttu-id="6c010-104">Приложения ASP.NET Web Forms состоят из страниц, определенных в *ASPX*-файлах.</span><span class="sxs-lookup"><span data-stu-id="6c010-104">ASP.NET Web Forms apps are composed of pages defined in *.aspx* files.</span></span> <span data-ttu-id="6c010-105">Адрес каждой страницы зависит от физического пути к файлу в проекте.</span><span class="sxs-lookup"><span data-stu-id="6c010-105">Each page's address is based on its physical file path in the project.</span></span> <span data-ttu-id="6c010-106">Когда браузер выполняет запрос к странице, содержимое страницы динамически отображается на сервере.</span><span class="sxs-lookup"><span data-stu-id="6c010-106">When a browser makes a request to the page, the contents of the page are dynamically rendered on the server.</span></span> <span data-ttu-id="6c010-107">Рендеринг учитывает как HTML-разметку страницы, так и ее серверные элементы управления.</span><span class="sxs-lookup"><span data-stu-id="6c010-107">The rendering accounts for both the page's HTML markup and its server controls.</span></span>

<span data-ttu-id="6c010-108">В Blazor каждая страница в приложении является компонентом, обычно определяемым в *RAZOR*-файле, с одним или несколькими указанными маршрутами.</span><span class="sxs-lookup"><span data-stu-id="6c010-108">In Blazor, each page in the app is a component, typically defined in a *.razor* file, with one or more specified routes.</span></span> <span data-ttu-id="6c010-109">Маршрутизация, в основном, происходит на стороне клиента без участия конкретного запроса сервера.</span><span class="sxs-lookup"><span data-stu-id="6c010-109">Routing mostly happens client-side without involving a specific server request.</span></span> <span data-ttu-id="6c010-110">Сначала браузер выполняет запрос к корневому адресу приложения.</span><span class="sxs-lookup"><span data-stu-id="6c010-110">The browser first makes a request to the root address of the app.</span></span> <span data-ttu-id="6c010-111">Затем корневой компонент `Router` в приложении Blazor обрабатывает перехват запросов навигации и направляет их в нужный компонент.</span><span class="sxs-lookup"><span data-stu-id="6c010-111">A root `Router` component in the Blazor app then handles intercepting navigation requests and them to the correct component.</span></span>

<span data-ttu-id="6c010-112">Blazor также поддерживает *создание глубинных ссылок*.</span><span class="sxs-lookup"><span data-stu-id="6c010-112">Blazor also supports *deep linking*.</span></span> <span data-ttu-id="6c010-113">Создание глубинных ссылок происходит, когда браузер выполняет запрос к конкретному маршруту, отличному от корневого каталога приложения.</span><span class="sxs-lookup"><span data-stu-id="6c010-113">Deep linking occurs when the browser makes a request to a specific route other than the root of the app.</span></span> <span data-ttu-id="6c010-114">Запросы для глубинных ссылок, отправленные на сервер, направляются в приложение Blazor, которое затем направляет клиентский запрос к нужному компоненту.</span><span class="sxs-lookup"><span data-stu-id="6c010-114">Requests for deep links sent to the server are routed to the Blazor app, which then routes the request client-side to the correct component.</span></span>

<span data-ttu-id="6c010-115">Простая страница в ASP.NET Web Forms может содержать следующую разметку:</span><span class="sxs-lookup"><span data-stu-id="6c010-115">A simple page in ASP.NET Web Forms might contain the following markup:</span></span>

<span data-ttu-id="6c010-116">*Name.aspx*</span><span class="sxs-lookup"><span data-stu-id="6c010-116">*Name.aspx*</span></span>

```aspx-csharp
<%@ Page Title="Name" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Name.aspx.cs" Inherits="WebApplication1.Name" %>

<asp:Content ID="BodyContent" ContentPlaceHolderID="MainContent" runat="server">
    <div>
        What is your name?<br />
        <asp:TextBox ID="TextBox1" runat="server"></asp:TextBox>
        <asp:Button ID="Button1" runat="server" Text="Submit" OnClick="Button1_Click" />
    </div>
    <div>
        <asp:Literal ID="Literal1" runat="server" />
    </div>
</asp:Content>
```

<span data-ttu-id="6c010-117">*Name.aspx.cs*</span><span class="sxs-lookup"><span data-stu-id="6c010-117">*Name.aspx.cs*</span></span>

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

<span data-ttu-id="6c010-118">Эквивалентная страница в приложении Blazor будет выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6c010-118">The equivalent page in a Blazor app would look like this:</span></span>

<span data-ttu-id="6c010-119">*Name.razor*</span><span class="sxs-lookup"><span data-stu-id="6c010-119">*Name.razor*</span></span>

```razor
@page "/Name"
@layout MainLayout

<div>
    What is your name?<br />
    <input @bind="text" />
    <button @onclick="OnClick">Submit</button>
</div>
<div>
    @if (name != null)
    {
        @:Hello @name
    }
</div>

@code {
    string text;
    string name;

    void OnClick() {
        name = text;
    }
}
```

## <a name="create-pages"></a><span data-ttu-id="6c010-120">Создание страниц</span><span class="sxs-lookup"><span data-stu-id="6c010-120">Create pages</span></span>

<span data-ttu-id="6c010-121">Чтобы создать страницу в Blazor, создайте компонент и добавьте директиву Razor `@page`, чтобы указать маршрут для компонента.</span><span class="sxs-lookup"><span data-stu-id="6c010-121">To create a page in Blazor, create a component and add the `@page` Razor directive to specify the route for the component.</span></span> <span data-ttu-id="6c010-122">Директива `@page` принимает один параметр, который является шаблоном маршрута, добавляемым к этому компоненту.</span><span class="sxs-lookup"><span data-stu-id="6c010-122">The `@page` directive takes a single parameter, which is the route template to add to that component.</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="6c010-123">Параметр шаблона маршрута является обязательным.</span><span class="sxs-lookup"><span data-stu-id="6c010-123">The route template parameter is required.</span></span> <span data-ttu-id="6c010-124">В отличие от ASP.NET Web Forms, маршрут к компоненту Blazor *не* определяется местоположением файла (хотя эта возможность может быть добавлена в будущем).</span><span class="sxs-lookup"><span data-stu-id="6c010-124">Unlike ASP.NET Web Forms, the route to a Blazor component *isn't* inferred from its file location (although that may be a feature added in the future).</span></span>

<span data-ttu-id="6c010-125">Синтаксис шаблона маршрута — это тот же базовый синтаксис, который используется для маршрутизации в ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="6c010-125">The route template syntax is the same basic syntax used for routing in ASP.NET Web Forms.</span></span> <span data-ttu-id="6c010-126">Параметры маршрута указываются в шаблоне с помощью фигурных скобок.</span><span class="sxs-lookup"><span data-stu-id="6c010-126">Route parameters are specified in the template using braces.</span></span> <span data-ttu-id="6c010-127">Blazor привязывает значения маршрута к параметрам компонента с тем же именем (без учета регистра).</span><span class="sxs-lookup"><span data-stu-id="6c010-127">Blazor will bind route values to component parameters with the same name (case-insensitive).</span></span>

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

<span data-ttu-id="6c010-128">Вы также можете указать ограничения для значения параметра маршрута.</span><span class="sxs-lookup"><span data-stu-id="6c010-128">You can also specify constraints on the value of the route parameter.</span></span> <span data-ttu-id="6c010-129">Например, чтобы идентификатор продукта был `int`:</span><span class="sxs-lookup"><span data-stu-id="6c010-129">For example, to constrain the product ID to be an `int`:</span></span>

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

<span data-ttu-id="6c010-130">Полный список ограничений маршрута, поддерживаемых Blazor, см. в разделе [Ограничения маршрута](/aspnet/core/blazor/routing#route-constraints).</span><span class="sxs-lookup"><span data-stu-id="6c010-130">For a full list of the route constraints supported by Blazor, see [Route constraints](/aspnet/core/blazor/routing#route-constraints).</span></span>

## <a name="router-component"></a><span data-ttu-id="6c010-131">Компонент маршрутизатора</span><span class="sxs-lookup"><span data-stu-id="6c010-131">Router component</span></span>

<span data-ttu-id="6c010-132">Маршрутизация в Blazor обрабатывается компонентом `Router`.</span><span class="sxs-lookup"><span data-stu-id="6c010-132">Routing in Blazor is handled by the `Router` component.</span></span> <span data-ttu-id="6c010-133">Компонент `Router` обычно используется в корневом компоненте приложения (*App.razor*).</span><span class="sxs-lookup"><span data-stu-id="6c010-133">The `Router` component is typically used in the app's root component (*App.razor*).</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <LayoutView Layout="@typeof(MainLayout)">
            <p>Sorry, there's nothing at this address.</p>
        </LayoutView>
    </NotFound>
</Router>
```

<span data-ttu-id="6c010-134">Компонент `Router` обнаруживает маршрутизируемые компоненты в указанном `AppAssembly` и в дополнительно указанном `AdditionalAssemblies`.</span><span class="sxs-lookup"><span data-stu-id="6c010-134">The `Router` component discovers the routable components in the specified `AppAssembly` and in the optionally specified `AdditionalAssemblies`.</span></span> <span data-ttu-id="6c010-135">При переходе в браузере объект `Router` перехватывает навигацию и отображает содержимое своего параметра `Found` с извлеченным `RouteData`, если маршрут соответствует адресу, в противном случае `Router` отрисовывает свой параметр `NotFound`.</span><span class="sxs-lookup"><span data-stu-id="6c010-135">When the browser navigates, the `Router` intercepts the navigation and renders the contents of its `Found` parameter with the extracted `RouteData` if a route matches the address, otherwise the `Router` renders its `NotFound` parameter.</span></span>

<span data-ttu-id="6c010-136">Компонент `RouteView` обрабатывает рендеринг сопоставленного компонента, указанного в `RouteData`, с собственным макетом, если он имеется.</span><span class="sxs-lookup"><span data-stu-id="6c010-136">The `RouteView` component handles rendering the matched component specified by the `RouteData` with its layout if it has one.</span></span> <span data-ttu-id="6c010-137">Если сопоставленный компонент не имеет макета, используется дополнительно указанный параметр `DefaultLayout`.</span><span class="sxs-lookup"><span data-stu-id="6c010-137">If the matched component doesn't have a layout, then the optionally specified `DefaultLayout` is used.</span></span>

<span data-ttu-id="6c010-138">Компонент `LayoutView` визуализирует свое дочернее содержимое в указанном макете.</span><span class="sxs-lookup"><span data-stu-id="6c010-138">The `LayoutView` component renders its child content within the specified layout.</span></span> <span data-ttu-id="6c010-139">Далее в этой главе мы рассмотрим макеты более подробно.</span><span class="sxs-lookup"><span data-stu-id="6c010-139">We'll look at layouts more in detail later in this chapter.</span></span>

## <a name="navigation"></a><span data-ttu-id="6c010-140">Навигация</span><span class="sxs-lookup"><span data-stu-id="6c010-140">Navigation</span></span>

<span data-ttu-id="6c010-141">В ASP.NET Web Forms вы запускаете навигацию на другую страницу, возвращая ответ перенаправления в браузер.</span><span class="sxs-lookup"><span data-stu-id="6c010-141">In ASP.NET Web Forms, you trigger navigation to a different page by returning a redirect response to the browser.</span></span> <span data-ttu-id="6c010-142">Пример:</span><span class="sxs-lookup"><span data-stu-id="6c010-142">For example:</span></span>

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

<span data-ttu-id="6c010-143">Возврат ответа перенаправления обычно не поддерживается в Blazor.</span><span class="sxs-lookup"><span data-stu-id="6c010-143">Returning a redirect response isn't typically possible in Blazor.</span></span> <span data-ttu-id="6c010-144">Blazor не использует модель "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="6c010-144">Blazor doesn't use a request-reply model.</span></span> <span data-ttu-id="6c010-145">Однако вы можете активировать навигацию в браузере напрямую, как и в случае с JavaScript.</span><span class="sxs-lookup"><span data-stu-id="6c010-145">You can, however, trigger browser navigations directly, as you can with JavaScript.</span></span>

<span data-ttu-id="6c010-146">Blazor предоставляет службу `NavigationManager`, которую можно использовать в следующих целях:</span><span class="sxs-lookup"><span data-stu-id="6c010-146">Blazor provides a `NavigationManager` service that can be used to:</span></span>

- <span data-ttu-id="6c010-147">Получение текущего адреса браузера.</span><span class="sxs-lookup"><span data-stu-id="6c010-147">Get the current browser address</span></span>
- <span data-ttu-id="6c010-148">Получение базового адреса.</span><span class="sxs-lookup"><span data-stu-id="6c010-148">Get the base address</span></span>
- <span data-ttu-id="6c010-149">Активация навигаций.</span><span class="sxs-lookup"><span data-stu-id="6c010-149">Trigger navigations</span></span>
- <span data-ttu-id="6c010-150">Получение уведомлений при изменении адреса.</span><span class="sxs-lookup"><span data-stu-id="6c010-150">Get notified when the address changes</span></span>

<span data-ttu-id="6c010-151">Для перехода к другому адресу используйте метод `NavigateTo`:</span><span class="sxs-lookup"><span data-stu-id="6c010-151">To navigate to a different address, use the `NavigateTo` method:</span></span>

```razor
@page "/"
@inject NavigationManager NavigationManager

<button @onclick="Navigate">Navigate</button>

@code {
    void Navigate() {
        NavigationManager.NavigateTo("counter");
    }
}
```

<span data-ttu-id="6c010-152">Описание всех элементов `NavigationManager` см. в разделе [Вспомогательные методы состояния URI и навигации](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span><span class="sxs-lookup"><span data-stu-id="6c010-152">For a description of all `NavigationManager` members, see [URI and navigation state helpers](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).</span></span>

## <a name="base-urls"></a><span data-ttu-id="6c010-153">Базовые URL-адреса</span><span class="sxs-lookup"><span data-stu-id="6c010-153">Base URLs</span></span>

<span data-ttu-id="6c010-154">Если приложение Blazor развертывается по базовому пути, необходимо указать базовый URL-адрес в метаданных страницы с помощью тега `<base>`, чтобы маршрутизация работала корректно.</span><span class="sxs-lookup"><span data-stu-id="6c010-154">If your Blazor app is deployed under a base path, then you need to specify the base URL in the page metadata using the `<base>` tag for routing to work property.</span></span> <span data-ttu-id="6c010-155">Если страница узла для приложения отображается на сервере с помощью Razor, можно использовать синтаксис `~/` для указания базового адреса приложения.</span><span class="sxs-lookup"><span data-stu-id="6c010-155">If the host page for the app is server-rendered using Razor, then you can use the `~/` syntax to specify the app's base address.</span></span> <span data-ttu-id="6c010-156">Если страница узла является статическим HTML, необходимо явно указать базовый URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="6c010-156">If the host page is static HTML, then you need to specify the base URL explicitly.</span></span>

```html
<base href="~/" />
```

## <a name="page-layout"></a><span data-ttu-id="6c010-157">Макет страницы</span><span class="sxs-lookup"><span data-stu-id="6c010-157">Page layout</span></span>

<span data-ttu-id="6c010-158">Разметка страницы в ASP.NET Web Forms обрабатывается эталонными страницами.</span><span class="sxs-lookup"><span data-stu-id="6c010-158">Page layout in ASP.NET Web Forms is handled by Master Pages.</span></span> <span data-ttu-id="6c010-159">Эталонные страницы определяют шаблон с одним или несколькими заполнителями содержимого, которое затем может быть предоставлено отдельными страницами.</span><span class="sxs-lookup"><span data-stu-id="6c010-159">Master Pages define a template with one or more content placeholders that can then be supplied by individual pages.</span></span> <span data-ttu-id="6c010-160">Эталонные страницы определяются в *MASTER*-файлах и начинаются с директивы `<%@ Master %>`.</span><span class="sxs-lookup"><span data-stu-id="6c010-160">Master Pages are defined in *.master* files and start with the `<%@ Master %>` directive.</span></span> <span data-ttu-id="6c010-161">Содержимое *MASTER*-файлов задается как страница *ASPX*, но с добавлением элементов управления `<asp:ContentPlaceHolder>` для пометки места, куда страницы могут предоставлять содержимое.</span><span class="sxs-lookup"><span data-stu-id="6c010-161">The content of the *.master* files is coded as you would an *.aspx* page, but with the addition of `<asp:ContentPlaceHolder>` controls to mark where pages can supply content.</span></span>

<span data-ttu-id="6c010-162">*Site.master*</span><span class="sxs-lookup"><span data-stu-id="6c010-162">*Site.master*</span></span>

```aspx-csharp
<%@ Master Language="C#" AutoEventWireup="true" CodeBehind="Site.master.cs" Inherits="WebApplication1.SiteMaster" %>

<!DOCTYPE html>
<html lang="en">
<head runat="server">
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title><%: Page.Title %> - My ASP.NET Application</title>
    <link href="~/favicon.ico" rel="shortcut icon" type="image/x-icon" />
</head>
<body>
    <form runat="server">
        <div class="container body-content">
            <asp:ContentPlaceHolder ID="MainContent" runat="server">
            </asp:ContentPlaceHolder>
            <hr />
            <footer>
                <p>&copy; <%: DateTime.Now.Year %> - My ASP.NET Application</p>
            </footer>
        </div>
    </form>
</body>
</html>
```

<span data-ttu-id="6c010-163">В Blazor разметка страницы обрабатывается с помощью компонентов макета.</span><span class="sxs-lookup"><span data-stu-id="6c010-163">In Blazor, you handle page layout using layout components.</span></span> <span data-ttu-id="6c010-164">Компоненты макета наследуют от `LayoutComponentBase`, определяющего одно свойство `Body` типа `RenderFragment`, которое можно использовать для визуализации содержимого страницы.</span><span class="sxs-lookup"><span data-stu-id="6c010-164">Layout components inherit from `LayoutComponentBase`, which defines a single `Body` property of type `RenderFragment`, which can be used to render the contents of the page.</span></span>

<span data-ttu-id="6c010-165">*MainLayout.razor*</span><span class="sxs-lookup"><span data-stu-id="6c010-165">*MainLayout.razor*</span></span>

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

<span data-ttu-id="6c010-166">При рендеринге страницы с макетом эта страница отрисовывается в пределах содержимого указанного макета в расположении, в котором макет отрисовывает свое свойство `Body`.</span><span class="sxs-lookup"><span data-stu-id="6c010-166">When the page with a layout is rendered, the page is rendered within the contents of the specified layout at the location where the layout renders its `Body` property.</span></span>

<span data-ttu-id="6c010-167">Чтобы применить разметку к странице, используйте директиву `@layout`:</span><span class="sxs-lookup"><span data-stu-id="6c010-167">To apply a layout to a page, use the `@layout` directive:</span></span>

```razor
@layout MainLayout
```

<span data-ttu-id="6c010-168">Вы можете указать макет для всех компонентов в папке и вложенных папках, используя файл *_Imports.razor*.</span><span class="sxs-lookup"><span data-stu-id="6c010-168">You can specify the layout for all components in a folder and subfolders using an *_Imports.razor* file.</span></span> <span data-ttu-id="6c010-169">Вы также можете указать макет по умолчанию для всех страниц с помощью [компонента маршрутизатора](#router-component).</span><span class="sxs-lookup"><span data-stu-id="6c010-169">You can also specify a default layout for all your pages using the [Router component](#router-component).</span></span>

<span data-ttu-id="6c010-170">Эталонные страницы могут определять несколько заполнителей содержимого, но макеты в Blazor имеют только одно свойство `Body`.</span><span class="sxs-lookup"><span data-stu-id="6c010-170">Master Pages can define multiple content placeholders, but layouts in Blazor only have a single `Body` property.</span></span> <span data-ttu-id="6c010-171">Это ограничение в отношении компонентов макета Blazor будет пересмотрено в следующем выпуске.</span><span class="sxs-lookup"><span data-stu-id="6c010-171">This limitation of Blazor layout components will hopefully be addressed in a future release.</span></span>

<span data-ttu-id="6c010-172">Эталонные страницы в ASP.NET Web Forms могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="6c010-172">Master Pages in ASP.NET Web Forms can be nested.</span></span> <span data-ttu-id="6c010-173">То есть эталонная страница может также использовать эталонную страницу.</span><span class="sxs-lookup"><span data-stu-id="6c010-173">That is, a Master Page may also use a Master Page.</span></span> <span data-ttu-id="6c010-174">Компоненты макета в Blazor также могут быть вложенными.</span><span class="sxs-lookup"><span data-stu-id="6c010-174">Layout components in Blazor may be nested too.</span></span> <span data-ttu-id="6c010-175">Компонент макета можно применить к компоненту макета.</span><span class="sxs-lookup"><span data-stu-id="6c010-175">You can apply a layout component to a layout component.</span></span> <span data-ttu-id="6c010-176">Содержимое внутреннего макета будет отрисовываться во внешнем макете.</span><span class="sxs-lookup"><span data-stu-id="6c010-176">The contents of the inner layout will be rendered within the outer layout.</span></span>

<span data-ttu-id="6c010-177">*ChildLayout.razor*</span><span class="sxs-lookup"><span data-stu-id="6c010-177">*ChildLayout.razor*</span></span>

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

<span data-ttu-id="6c010-178">*Index.razor*</span><span class="sxs-lookup"><span data-stu-id="6c010-178">*Index.razor*</span></span>

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

<span data-ttu-id="6c010-179">Отрисованные выходные данные для страницы будут выглядеть следующим образом:</span><span class="sxs-lookup"><span data-stu-id="6c010-179">The rendered output for the page would then be:</span></span>

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

<span data-ttu-id="6c010-180">Макеты в Blazor обычно не определяют корневые элементы HTML для страницы (`<html>`, `<body>`, `<head>` и т. д.).</span><span class="sxs-lookup"><span data-stu-id="6c010-180">Layouts in Blazor don't typically define the root HTML elements for a page (`<html>`, `<body>`, `<head>`, and so on).</span></span> <span data-ttu-id="6c010-181">Корневые элементы HTML определяются на странице узла приложения Blazor, которая используется для отрисовки начального содержимого HTML для приложения (см. раздел [Начальная загрузка Blazor](project-structure.md#bootstrap-blazor)).</span><span class="sxs-lookup"><span data-stu-id="6c010-181">The root HTML elements are instead defined in a Blazor app's host page, which is used to render the initial HTML content for the app (see [Bootstrap Blazor](project-structure.md#bootstrap-blazor)).</span></span> <span data-ttu-id="6c010-182">Страница узла может отрисовывать несколько корневых компонентов для приложения с окружающей разметкой.</span><span class="sxs-lookup"><span data-stu-id="6c010-182">The host page can render multiple root components for the app with surrounding markup.</span></span>

<span data-ttu-id="6c010-183">Компоненты в Blazor, включая страницы, не могут отрисовывать теги `<script>`.</span><span class="sxs-lookup"><span data-stu-id="6c010-183">Components in Blazor, including pages, can't render `<script>` tags.</span></span> <span data-ttu-id="6c010-184">Это ограничение отрисовки существует, так как теги `<script>` загружаются один раз, а затем не могут быть изменены.</span><span class="sxs-lookup"><span data-stu-id="6c010-184">This rendering restriction exists because `<script>` tags get loaded once and then can't be changed.</span></span> <span data-ttu-id="6c010-185">Если вы попытаетесь динамически отрисовать теги с помощью синтаксиса Razor, может возникнуть непредвиденное поведение.</span><span class="sxs-lookup"><span data-stu-id="6c010-185">Unexpected behavior may occur if you try to render the tags dynamically using Razor syntax.</span></span> <span data-ttu-id="6c010-186">Вместо этого все теги `<script>` должны быть добавлены на страницу узла приложения.</span><span class="sxs-lookup"><span data-stu-id="6c010-186">Instead, all `<script>` tags should be added to the app's host page.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6c010-187">[Назад](components.md)
>[Вперед](state-management.md)</span><span class="sxs-lookup"><span data-stu-id="6c010-187">[Previous](components.md)
[Next](state-management.md)</span></span>
