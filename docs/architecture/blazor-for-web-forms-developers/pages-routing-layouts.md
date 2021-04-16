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
# <a name="pages-routing-and-layouts"></a>Страницы, маршрутизация и макеты

Приложения ASP.NET Web Forms состоят из страниц, определенных в *ASPX*-файлах. Адрес каждой страницы зависит от физического пути к файлу в проекте. Когда браузер выполняет запрос к странице, содержимое страницы динамически отображается на сервере. Рендеринг учитывает как HTML-разметку страницы, так и ее серверные элементы управления.

В Blazor каждая страница в приложении является компонентом, обычно определяемым в *RAZOR*-файле, с одним или несколькими указанными маршрутами. Маршрутизация, в основном, происходит на стороне клиента без участия конкретного запроса сервера. Сначала браузер выполняет запрос к корневому адресу приложения. Затем корневой компонент `Router` в приложении Blazor обрабатывает перехват запросов навигации и направляет их в нужный компонент.

Blazor также поддерживает *создание глубинных ссылок*. Создание глубинных ссылок происходит, когда браузер выполняет запрос к конкретному маршруту, отличному от корневого каталога приложения. Запросы для глубинных ссылок, отправленные на сервер, направляются в приложение Blazor, которое затем направляет клиентский запрос к нужному компоненту.

Простая страница в ASP.NET Web Forms может содержать следующую разметку:

*Name.aspx*

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

*Name.aspx.cs*

```csharp
public partial class Name : System.Web.UI.Page
{
    protected void Button1_Click1(object sender, EventArgs e)
    {
        Literal1.Text = "Hello " + TextBox1.Text;
    }
}
```

Эквивалентная страница в приложении Blazor будет выглядеть следующим образом:

*Name.razor*

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

## <a name="create-pages"></a>Создание страниц

Чтобы создать страницу в Blazor, создайте компонент и добавьте директиву Razor `@page`, чтобы указать маршрут для компонента. Директива `@page` принимает один параметр, который является шаблоном маршрута, добавляемым к этому компоненту.

```razor
@page "/counter"
```

Параметр шаблона маршрута является обязательным. В отличие от ASP.NET Web Forms, маршрут к компоненту Blazor *не* определяется местоположением файла (хотя эта возможность может быть добавлена в будущем).

Синтаксис шаблона маршрута — это тот же базовый синтаксис, который используется для маршрутизации в ASP.NET Web Forms. Параметры маршрута указываются в шаблоне с помощью фигурных скобок. Blazor привязывает значения маршрута к параметрам компонента с тем же именем (без учета регистра).

```razor
@page "/product/{id}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public string Id { get; set; }
}
```

Вы также можете указать ограничения для значения параметра маршрута. Например, чтобы идентификатор продукта был `int`:

```razor
@page "/product/{id:int}"

<h1>Product @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

Полный список ограничений маршрута, поддерживаемых Blazor, см. в разделе [Ограничения маршрута](/aspnet/core/blazor/routing#route-constraints).

## <a name="router-component"></a>Компонент маршрутизатора

Маршрутизация в Blazor обрабатывается компонентом `Router`. Компонент `Router` обычно используется в корневом компоненте приложения (*App.razor*).

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

Компонент `Router` обнаруживает маршрутизируемые компоненты в указанном `AppAssembly` и в дополнительно указанном `AdditionalAssemblies`. При переходе в браузере объект `Router` перехватывает навигацию и отображает содержимое своего параметра `Found` с извлеченным `RouteData`, если маршрут соответствует адресу, в противном случае `Router` отрисовывает свой параметр `NotFound`.

Компонент `RouteView` обрабатывает рендеринг сопоставленного компонента, указанного в `RouteData`, с собственным макетом, если он имеется. Если сопоставленный компонент не имеет макета, используется дополнительно указанный параметр `DefaultLayout`.

Компонент `LayoutView` визуализирует свое дочернее содержимое в указанном макете. Далее в этой главе мы рассмотрим макеты более подробно.

## <a name="navigation"></a>Навигация

В ASP.NET Web Forms вы запускаете навигацию на другую страницу, возвращая ответ перенаправления в браузер. Пример:

```csharp
protected void NavigateButton_Click(object sender, EventArgs e)
{
    Response.Redirect("Counter");
}
```

Возврат ответа перенаправления обычно не поддерживается в Blazor. Blazor не использует модель "запрос-ответ". Однако вы можете активировать навигацию в браузере напрямую, как и в случае с JavaScript.

Blazor предоставляет службу `NavigationManager`, которую можно использовать в следующих целях:

- Получение текущего адреса браузера.
- Получение базового адреса.
- Активация навигаций.
- Получение уведомлений при изменении адреса.

Для перехода к другому адресу используйте метод `NavigateTo`:

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

Описание всех элементов `NavigationManager` см. в разделе [Вспомогательные методы состояния URI и навигации](/aspnet/core/blazor/routing#uri-and-navigation-state-helpers).

## <a name="base-urls"></a>Базовые URL-адреса

Если приложение Blazor развертывается по базовому пути, необходимо указать базовый URL-адрес в метаданных страницы с помощью тега `<base>`, чтобы маршрутизация работала корректно. Если страница узла для приложения отображается на сервере с помощью Razor, можно использовать синтаксис `~/` для указания базового адреса приложения. Если страница узла является статическим HTML, необходимо явно указать базовый URL-адрес.

```html
<base href="~/" />
```

## <a name="page-layout"></a>Макет страницы

Разметка страницы в ASP.NET Web Forms обрабатывается эталонными страницами. Эталонные страницы определяют шаблон с одним или несколькими заполнителями содержимого, которое затем может быть предоставлено отдельными страницами. Эталонные страницы определяются в *MASTER*-файлах и начинаются с директивы `<%@ Master %>`. Содержимое *MASTER*-файлов задается как страница *ASPX*, но с добавлением элементов управления `<asp:ContentPlaceHolder>` для пометки места, куда страницы могут предоставлять содержимое.

*Site.master*

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

В Blazor разметка страницы обрабатывается с помощью компонентов макета. Компоненты макета наследуют от `LayoutComponentBase`, определяющего одно свойство `Body` типа `RenderFragment`, которое можно использовать для визуализации содержимого страницы.

*MainLayout.razor*

```razor
@inherits LayoutComponentBase
<h1>Main layout</h1>
<div>
    @Body
</div>
```

При рендеринге страницы с макетом эта страница отрисовывается в пределах содержимого указанного макета в расположении, в котором макет отрисовывает свое свойство `Body`.

Чтобы применить разметку к странице, используйте директиву `@layout`:

```razor
@layout MainLayout
```

Вы можете указать макет для всех компонентов в папке и вложенных папках, используя файл *_Imports.razor*. Вы также можете указать макет по умолчанию для всех страниц с помощью [компонента маршрутизатора](#router-component).

Эталонные страницы могут определять несколько заполнителей содержимого, но макеты в Blazor имеют только одно свойство `Body`. Это ограничение в отношении компонентов макета Blazor будет пересмотрено в следующем выпуске.

Эталонные страницы в ASP.NET Web Forms могут быть вложенными. То есть эталонная страница может также использовать эталонную страницу. Компоненты макета в Blazor также могут быть вложенными. Компонент макета можно применить к компоненту макета. Содержимое внутреннего макета будет отрисовываться во внешнем макете.

*ChildLayout.razor*

```razor
@layout MainLayout
<h2>Child layout</h2>
<div>
    @Body
</div>
```

*Index.razor*

```razor
@page "/"
@layout ChildLayout
<p>I'm in a nested layout!</p>
```

Отрисованные выходные данные для страницы будут выглядеть следующим образом:

```html
<h1>Main layout</h1>
<div>
    <h2>Child layout</h2>
    <div>
        <p>I'm in a nested layout!</p>
    </div>
</div>
```

Макеты в Blazor обычно не определяют корневые элементы HTML для страницы (`<html>`, `<body>`, `<head>` и т. д.). Корневые элементы HTML определяются на странице узла приложения Blazor, которая используется для отрисовки начального содержимого HTML для приложения (см. раздел [Начальная загрузка Blazor](project-structure.md#bootstrap-blazor)). Страница узла может отрисовывать несколько корневых компонентов для приложения с окружающей разметкой.

Компоненты в Blazor, включая страницы, не могут отрисовывать теги `<script>`. Это ограничение отрисовки существует, так как теги `<script>` загружаются один раз, а затем не могут быть изменены. Если вы попытаетесь динамически отрисовать теги с помощью синтаксиса Razor, может возникнуть непредвиденное поведение. Вместо этого все теги `<script>` должны быть добавлены на страницу узла приложения.

>[!div class="step-by-step"]
>[Назад](components.md)
>[Вперед](state-management.md)
