---
title: Создание повторно используемых компонентов пользовательского интерфейса с помощью Blazor
description: Узнайте, как создавать повторно используемые компоненты пользовательского интерфейса с помощью Blazor и сравните их с элементами управления ASP.NET Web Forms.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: fd560c84c095dffc3718a7709af904d9ba722a18
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97512773"
---
# <a name="build-reusable-ui-components-with-blazor"></a>Создание повторно используемых компонентов пользовательского интерфейса с помощью Blazor

Одним из преимуществ ASP.NET Web Forms является инкапсуляция многоразовых фрагментов кода пользовательского интерфейса в повторно используемые элементы управления пользовательского интерфейса. Настраиваемые пользовательские элементы управления могут быть определены в разметке с помощью *ASCX*-файлов. Кроме того, можно создавать сложные серверные элементы управления в коде с полной поддержкой конструктора.

Blazor также поддерживает инкапсуляцию пользовательского интерфейса через *компоненты*. Особенности компонента:

- Это автономный фрагмент пользовательского интерфейса.
- Поддерживает собственную логику состояния и отрисовки.
- Может определять обработчики событий пользовательского интерфейса, выполнять привязку к входным данным и управлять собственным жизненным циклом.
- Обычно определяется в *RAZOR*-файле с помощью синтаксиса Razor.

## <a name="an-introduction-to-razor"></a>Введение в Razor

Razor — это облегченный язык создания шаблонов разметки на основе HTML и C#. С помощью Razor можно легко переходить между разметкой и кодом C#, чтобы определить логику отрисовки компонента. При компиляции *RAZOR*-файла логика отрисовки записывается структурированным образом в классе .NET. Имя скомпилированного класса берется из имени *RAZOR*-файла. Пространство имен берется из пространства имен по умолчанию для проекта и пути к папке, либо можно явно указать пространство имен с помощью директивы `@namespace` (подробнее о директивах Razor ниже).

Логика отрисовки компонента создается с помощью обычной разметки HTML с динамической логикой, добавленной с помощью C#. Символ `@` используется для перехода на C#. Razor обычно понимает, когда вы переключаетесь на HTML. Например, следующий компонент отрисовывает тег `<p>` с текущим временем:

```razor
<p>@DateTime.Now</p>
```

Чтобы явно указать начало и конец выражения C#, используйте круглые скобки:

```razor
<p>@(DateTime.Now)</p>
```

Razor также упрощает использование потока управления C# в логике отрисовки. Например, можно выполнить условную отрисовку HTML-кода следующим образом:

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

Также можно создать список элементов с помощью обычного цикла C# `foreach` следующим образом:

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

Директивы Razor, такие как директивы в ASP.NET Web Forms, управляют многими аспектами компиляции компонента Razor. Вот несколько примеров:

- Пространство имен
- Базовый класс
- Реализованные интерфейсы
- Универсальные параметры
- Импортированные пространства имен
- Маршруты

Директивы Razor начинаются с символа `@` и обычно используются в начале новой строки в начале файла. Например, директива `@namespace` определяет пространство имен компонента:

```razor
@namespace MyComponentNamespace
```

В следующей таблице перечислены различные директивы Razor, используемые в Blazor, и их эквиваленты ASP.NET Web Forms, если они существуют.

|Директива    |Описание|Пример|Эквивалент в Web Forms|
|-------------|-----------|-------|--------------------|
|`@attribute` |Добавляет атрибут уровня класса в компонент|`@attribute [Authorize]`|Нет|
|`@code`      |Добавляет члены класса в компонент|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|Реализует заданный интерфейс|`@implements IDisposable`|Использование кода программной части|
|`@inherits`  |Наследует от указанного базового класса|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |Внедряет службу в компонент|`@inject IJSRuntime JS`|Нет|
|`@layout`    |Задает компонент макета для компонента|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |Задает пространство имен для компонента|`@namespace MyNamespace`|Нет|
|`@page`      |Указывает маршрут для компонента|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |Указывает параметр универсального типа для компонента|`@typeparam TItem`|Использование кода программной части|
|`@using`     |Указывает пространство имен для переноса в область|`@using MyComponentNamespace`|Добавляет пространство имен в *web.config*|

Компоненты Razor также активно используют *атрибуты директивы* в элементах для управления различными аспектами компиляции компонентов (обработка событий, привязка данных, ссылки на компоненты и элементы и т. д.). Все атрибуты директивы следуют общему универсальному синтаксису, в котором значения в круглых скобках являются необязательными:

```razor
@directive(-suffix(:name))(="value")
```

В следующей таблице перечислены различные атрибуты директив Razor, используемые в Blazor.

|attribute    |Описание|Пример|
|-------------|-----------|-------|
|`@attributes`|Преобразует для просмотра словарь атрибутов|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |Создает двустороннюю привязку данных    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |Добавляет обработчик событий для указанного события|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |Задает ключ, используемый алгоритмом сравнения для сохранения элементов в коллекции|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |Получает ссылку на компонент или HTML-элемент|`<MyDialog @ref="myDialog" />`|

Различные атрибуты директивы, используемые Blazor (`@onclick`, `@bind`, `@ref` и т. д.), описаны в разделах ниже и последующих главах.

Многие из синтаксисов, используемые в *ASPX* и *ASCX*-файлах имеют параллельные синтаксисы в Razor. Ниже приведено простое сравнение синтаксиса для ASP.NET Web Forms и Razor.

|Компонент                      |веб-формы           |Синтаксис               |Razor         |Синтаксис |
|-----------------------------|--------------------|---------------------|--------------|-------|
|Директивы                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|Блоки кода                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|Выражения<br>(В кодировке HTML)|`<%: %>`            |`<%:DateTime.Now %>` |Неявно: `@`<br>Явно: `@()`|`@DateTime.Now`<br>`@(DateTime.Now)`|
|Комментарии                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|привязка данных,                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

Чтобы добавить члены в класс компонента Razor, используйте директиву `@code`. Этот метод аналогичен использованию блока `<script runat="server">...</script>` в пользовательском элементе управления или на странице ASP.NET Web Forms.

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

Поскольку Razor основан на C#, он должен быть скомпилирован из проекта C# ( *.csproj*). *RAZOR*-файлы нельзя компилировать из проекта Visual Basic ( *.vbproj*). Однако вы можете ссылаться на проекты Visual Basic из проекта Blazor. Верно и обратное.

Полный справочник по синтаксису Razor см. в статье [Справочник по синтаксису Razor для ASP.NET Core](/aspnet/core/mvc/views/razor).

## <a name="use-components"></a>Использование компонентов

Помимо обычного HTML, компоненты также могут использовать другие компоненты как часть логики отрисовки. Синтаксис использования компонента в Razor подобен использованию пользовательского элемента управления в приложении ASP.NET Web Forms. Компоненты указываются с помощью тега элемента, соответствующего имени типа компонента. Например, вы можете добавить компонент `Counter`:

```razor
<Counter />
```

В отличие от ASP.NET Web Forms, компоненты в Blazor:

- Не используют префикс элемента (например, `asp:`).
- Не требуют регистрации на странице или в *web.config*.

Компоненты Razor можно сравнить с типами .NET, так как, по сути, именно это они собой и представляют. Если имеется ссылка на сборку, содержащую компонент, то компонент доступен для использования. Чтобы перенести пространство имен компонента в область, примените директиву `@using`:

```razor
@using MyComponentLib

<Counter />
```

Как видно в проектах по умолчанию Blazor, директивы `@using` можно размещать в файле *_Imports.razor*, чтобы импортировать их во все *RAZOR*-файлы в одном и том же каталоге и в дочерних каталогах.

Если пространство имен для компонента не находится в области, можно указать компонент, используя его полное имя типа, как в C#:

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a>Параметры компонентов

В ASP.NET Web Forms можно передавать параметры и данные в элементы управления с помощью общедоступных свойств. Эти свойства можно задать в разметке с помощью атрибутов или непосредственно в коде. Компоненты Blazor работают аналогичным образом, хотя свойства компонентов также должны быть помечены атрибутом `[Parameter]`, чтобы считаться параметрами компонента.

Следующий компонент `Counter` определяет параметр компонента с именем `IncrementAmount`, который можно использовать для указания величины приращения `Counter` при каждом нажатии кнопки.

```razor
<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    void IncrementCount()
    {
        currentCount+=IncrementAmount;
    }
}
```

Чтобы указать параметр компонента в Blazor, используйте атрибут, как в ASP.NET Web Forms:

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a>Обработчики событий

ASP.NET Web Forms и Blazor предоставляют модель программирования на основе событий для обработки событий пользовательского интерфейса. Примеры таких событий включают нажатие кнопок и ввод текста. В ASP.NET Web Forms используются серверные элементы управления HTML для работы с событиями пользовательского интерфейса, предоставляемыми моделью DOM. Или вы можете обрабатывать события, предоставляемые элементами управления веб-сервера. События поступают на сервер посредством запросов обратной передачи. Рассмотрим следующие примеры кнопок Web Forms:

*Counter.ascx*

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

В Blazor можно зарегистрировать обработчики для событий пользовательского интерфейса DOM напрямую с помощью атрибутов директивы в форме `@on{event}`. Заполнитель `{event}` представляет имя события. Например, можно ожидать нажатие кнопок следующим образом:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

Обработчики событий могут принимать необязательный аргумент, относящийся к конкретному событию, для предоставления дополнительных сведений о событии. Например, события мыши могут принимать аргумент `MouseEventArgs`, но это не обязательно.

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

Вместо ссылки на группу методов для обработчика событий можно использовать лямбда-выражение. Лямбда-выражение позволяет закрывать другие значения в области.

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

Обработчики событий могут выполняться синхронно или асинхронно. Например, следующий обработчик событий `OnClick` выполняется асинхронно:

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

После обработки события компонент преобразуется для просмотра с учетом изменений состояния компонента. При использовании асинхронных обработчиков событий компонент преобразуется для просмотра сразу после выполнения обработчика. Компонент отрисовывается *снова* после выполнения асинхронной задачи `Task`. Этот асинхронный режим выполнения позволяет визуализировать соответствующий пользовательский интерфейс во время выполнения асинхронной задачи `Task`.

```razor
<button @onclick="ShowMessage">Get message</button>

@if (showMessage)
{
    @if (message == null)
    {
        <p><em>Loading...</em></p>
    }
    else
    {
        <p>The message is: @message</p>
    }
}

@code
{
    bool showMessage = false;
    string message;

    public async Task ShowMessage()
    {
        showMessage = true;
        message = await MessageService.GetMessageAsync();
    }
}
```

Компоненты также могут определять собственные события, определяя параметр компонента типа `EventCallback<TValue>`. Обратные вызовы событий поддерживают все разновидности обработчиков событий пользовательского интерфейса DOM: необязательные аргументы, синхронные или асинхронные операции, группы методов или лямбда-выражения.

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a>привязка данных,

Blazor предоставляет простой механизм привязки данных из компонента пользовательского интерфейса к состоянию компонента. Этот подход отличается от функций в ASP.NET Web Forms для привязки данных из источников данных к элементам управления пользовательского интерфейса. Мы обсудим обработку данных из различных источников данных в разделе [Работа с данными](data.md).

Чтобы создать двустороннюю привязку данных из компонента пользовательского интерфейса к состоянию компонента, используйте атрибут директивы `@bind`. В следующем примере значение флажка привязано к полю `isChecked`.

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

При подготовке компонента к просмотру значение флажка устанавливается равным значению поля `isChecked`. Когда пользователь переключает флажок, событие `onchange` срабатывает и для поля `isChecked` задается новое значение. Синтаксис `@bind` в этом случае эквивалентен следующей разметке:

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

Чтобы изменить событие, используемое для привязки, используйте атрибут `@bind:event`.

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

Компоненты также могут поддерживать привязку данных к параметрам. Для привязки данных определите параметр обратного вызова события с тем же именем, что и у привязываемого параметра. К имени добавляется суффикс "Changed".

*PasswordBox.razor*

```razor
Password: <input
    value="@Password"
    @oninput="OnPasswordChanged"
    type="@(showPassword ? "text" : "password")" />

<label><input type="checkbox" @bind="showPassword" />Show password</label>

@code {
    private bool showPassword;

    [Parameter]
    public string Password { get; set; }

    [Parameter]
    public EventCallback<string> PasswordChanged { get; set; }

    private Task OnPasswordChanged(ChangeEventArgs e)
    {
        Password = e.Value.ToString();
        return PasswordChanged.InvokeAsync(Password);
    }
}
```

Чтобы связать привязку данных с базовым элементом пользовательского интерфейса, установите значение и обработайте событие непосредственно в элементе пользовательского интерфейса, а не с помощью атрибута `@bind`.

Для привязки к параметру компонента используйте атрибут `@bind-{Parameter}`, чтобы указать параметр, с которым необходимо выполнить привязку.

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a>Изменения состояния

Если состояние компонента изменилось за пределами обычного пользовательского интерфейса или обратного вызова события, компонент должен вручную сообщить о необходимости повторной отрисовки. Чтобы сообщить о том, что состояние компонента изменилось, вызовите метод `StateHasChanged` для компонента.

В приведенном ниже примере компонент отображает сообщение из службы `AppState`, которая может быть обновлена другими частями приложения. Компонент регистрирует свой метод `StateHasChanged` с событием `AppState.OnChange`, чтобы компонент преобразовывался для просмотра при каждом обновлении сообщения.

```csharp
public class AppState
{
    public string Message { get; }

    // Lets components receive change notifications
    public event Action OnChange;

    public void UpdateMessage(string message)
    {
        Message = message;
        NotifyStateChanged();
    }

    private void NotifyStateChanged() => OnChange?.Invoke();
}
```

```razor
@inject AppState AppState

<p>App message: @AppState.Message</p>

@code {
    protected override void OnInitialized()
    {
        AppState.OnChange += StateHasChanged
    }
}
```

## <a name="component-lifecycle"></a>Жизненный цикл компонента

Платформа ASP.NET Web Forms имеет четко определенные методы жизненного цикла для модулей, страниц и элементов управления. Например, следующий элемент управления реализует обработчики событий для событий жизненного цикла `Init`, `Load` и `UnLoad`:

*Counter.ascx.cs*

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

Компоненты Blazor также имеют четко определенный жизненный цикл. Жизненный цикл компонента можно использовать для инициализации состояния компонента и реализации дополнительного поведения компонентов.

Все методы жизненного цикла компонента Blazor имеют как синхронные, так и асинхронные версии. Преобразование компонента для просмотра является синхронным. Асинхронную логику нельзя выполнять в процессе преобразования компонента для просмотра. Вся асинхронная логика должна выполняться как часть метода жизненного цикла `async`.

### <a name="oninitialized"></a>OnInitialized

Методы `OnInitialized` и `OnInitializedAsync` используются для инициализации компонента. Обычно компонент инициализируется после первой отрисовки. После инициализации компонента он может быть отрисован несколько раз, прежде чем будет удален в конечном итоге. Метод `OnInitialized` аналогичен событию `Page_Load` на страницах и в элементах управления ASP.NET Web Forms.

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a>OnParametersSet

Методы `OnParametersSet` и `OnParametersSetAsync` вызываются, когда компонент получил параметры от своего родительского элемента, и значение присваивается свойствам. Эти методы выполняются после инициализации компонента и *при каждой отрисовке компонента*.

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a>OnAfterRender

Методы `OnAfterRender` и `OnAfterRenderAsync` вызываются после завершения отрисовки компонента. Ссылки на элементы и компоненты заполняются на этом этапе (подробнее об этих концепциях см. ниже). На этом этапе включается интерактивное взаимодействие с браузером. Может происходить взаимодействие с моделью DOM и выполнение JavaScript.

```csharp
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender)
    {
        ...
    }
}
protected override async Task OnAfterRenderAsync(bool firstRender)
{
    if (firstRender)
    {
        await ...
    }
}
```

`OnAfterRender` и `OnAfterRenderAsync` *не вызываются при предварительной отрисовке на сервере*.

Параметр `firstRender` имеет значение `true` при первой отрисовке компонента. В остальных случаях он имеет значение `false`.

### <a name="idisposable"></a>IDisposable

Компоненты Blazor могут реализовать `IDisposable` для удаления ресурсов при удалении компонента из пользовательского интерфейса. Компонент Razor может реализовать `IDispose` с помощью директивы `@implements`:

```razor
@using System
@implements IDisposable

...

@code {
    public void Dispose()
    {
        ...
    }
}
```

## <a name="capture-component-references"></a>Сбор ссылок на компонент

В ASP.NET Web Forms можно управлять экземпляром элемента управления непосредственно в коде, ссылаясь на его идентификатор. В Blazor также можно получить ссылку на компонент и использовать ее, хотя это происходит реже.

Чтобы записать ссылку на компонент в Blazor, используйте атрибут директивы `@ref`. Значение атрибута должно совпадать с именем настраиваемого поля, имеющего тот же тип, что и компонент, на который указывает ссылка.

```razor
<MyLoginDialog @ref="loginDialog" ... />

@code {
    MyLoginDialog loginDialog;

    void OnSomething()
    {
        loginDialog.Show();
    }
}
```

При отрисовке родительского компонента поле заполняется экземпляром дочернего компонента. Затем можно вызывать методы в экземпляре компонента или иным образом использовать его.

Не рекомендуется напрямую обрабатывать состояние компонента с помощью ссылок на компоненты. Это помешает автоматической отрисовке компонента в нужное время.

## <a name="capture-element-references"></a>Запись ссылок на элементы

Компоненты Blazor могут записывать ссылки на элемент. В отличие от серверных элементов управления HTML в ASP.NET Web Forms, с моделью DOM нельзя работать напрямую с помощью ссылки на элемент в Blazor. Blazor обрабатывает большинство взаимодействий DOM с помощью алгоритма сравнения DOM. Записанные ссылки на элементы в Blazor являются непрозрачными. Однако они используются для передачи определенной ссылки на элемент в вызове взаимодействия JavaScript. Дополнительные сведения о взаимодействии JavaScript см. в разделе [Взаимодействие ASP.NET Core Blazor JavaScript](/aspnet/core/blazor/javascript-interop).

## <a name="templated-components"></a>Шаблонные компоненты

В ASP.NET Web Forms можно создавать *элементы управления — шаблоны*. Элементы управления — шаблоны позволяют разработчику указать часть HTML-кода, используемую для отрисовки контейнерного элемента управления. Механизм создания серверных элементов управления — шаблонов является сложным, но он позволяет создавать эффективные сценарии для отрисовки данных настраиваемым пользователем способом. Примеры элементов управления — шаблонов включают `Repeater` и `DataList`.

Для компонентов Blazor также можно создавать шаблоны путем определения параметров компонентов типа `RenderFragment` или `RenderFragment<T>`. `RenderFragment` представляет фрагмент разметки Razor, который затем может быть визуализирован компонентом. `RenderFragment<T>` — это фрагмент разметки Razor, принимающий параметр, который может быть указан при отрисовке фрагмента.

### <a name="child-content"></a>Дочернее содержимое

Компоненты Blazor могут записывать свое дочернее содержимое в виде `RenderFragment` и преобразовывать это содержимое для просмотра в процессе отрисовки компонента. Чтобы записать дочернее содержимое, определите параметр компонента типа `RenderFragment` и присвойте ему имя `ChildContent`.

*ChildContentComponent.razor*

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

После этого родительский компонент может предоставить дочернее содержимое, используя обычный синтаксис Razor.

```razor
<ChildContentComponent>
    <ChildContent>
        <p>The time is @DateTime.Now</p>
    </ChildContent>
</ChildContentComponent>
```

### <a name="template-parameters"></a>Параметры шаблона

Шаблонный компонент Blazor может также определять несколько параметров компонента типа `RenderFragment` или `RenderFragment<T>`. Параметр для `RenderFragment<T>` можно указать при вызове. Чтобы указать параметр универсального типа для компонента, используйте директиву Razor `@typeparam`.

*SimpleListView.razor*

```razor
@typeparam TItem

@Heading

<ul>
@foreach (var item in Items)
{
    <li>@ItemTemplate(item)</li>
}
</ul>

@code {
    [Parameter]
    public RenderFragment Heading { get; set; }

    [Parameter]
    public RenderFragment<TItem> ItemTemplate { get; set; }

    [Parameter]
    public IEnumerable<TItem> Items { get; set; }
}
```

При использовании шаблонного компонента параметры шаблона можно задать с помощью дочерних элементов, имена которых совпадают с именами параметров. Аргументы компонента типа `RenderFragment<T>`, переданные как элементы, имеют неявный параметр `context`. Вы можете изменить имя неявного параметра с помощью атрибута `Context` в дочернем элементе. Параметр универсального типа можно указать с помощью атрибута, совпадающего с именем параметра типа. Параметр типа будет выведен, если это возможно:

```razor
<SimpleListView Items="messages" TItem="string">
    <Heading>
        <h1>My list</h1>
    </Heading>
    <ItemTemplate Context="message">
        <p>The message is: @message</p>
    </ItemTemplate>
</SimpleListView>
```

Выходные данные этого компонента имеют следующий вид:

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a>Файл с кодом программной части

Компонент Blazor обычно создается в одном *RAZOR*-файле. Однако можно разделить код и разметку с помощью файла кода программной части. Чтобы использовать файл компонента, добавьте файл C#, соответствующий имени файла компонента, но с расширением *.cs* (*Counter.razor.cs*). Используйте файл C#, чтобы определить базовый класс для компонента. Вы можете присвоить любое имя базовому классу, хотя обычно имя класса совпадает с классом компонента, но имеет расширение `Base` (`CounterBase`). Класс на основе компонента также должен быть производным от `ComponentBase`. Затем в файле компонента Razor добавьте директиву `@inherits`, чтобы указать базовый класс для компонента (`@inherits CounterBase`).

*Counter.razor*

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

*Counter.razor.cs*

```csharp
public class CounterBase : ComponentBase
{
    protected int currentCount = 0;

    protected void IncrementCount()
    {
        currentCount++;
    }
}
```

Видимость членов компонента в базовом классе должна быть `protected` или `public`, чтобы у класса компонента был доступ.

## <a name="additional-resources"></a>Дополнительные ресурсы

Мы рассмотрели не все аспекты компонентов Blazor. Дополнительные сведения о [создании и использовании компонентов Razor ASP.NET Core](/aspnet/core/blazor/components) см в документации по Blazor.

>[!div class="step-by-step"]
>[Назад](app-startup.md)
>[Вперед](pages-routing-layouts.md)
