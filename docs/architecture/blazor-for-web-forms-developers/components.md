---
title: Создание повторно используемых компонентов пользовательского интерфейса с помощью Blazor
description: Узнайте, как создавать повторно используемые компоненты пользовательского интерфейса с помощью Blazor и сравнивать их с элементами управления веб-форм ASP.NET.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/18/2019
ms.openlocfilehash: fd560c84c095dffc3718a7709af904d9ba722a18
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512773"
---
# <a name="build-reusable-ui-components-with-no-locblazor"></a><span data-ttu-id="0ec0c-103">Создание повторно используемых компонентов пользовательского интерфейса с помощью Blazor</span><span class="sxs-lookup"><span data-stu-id="0ec0c-103">Build reusable UI components with Blazor</span></span>

<span data-ttu-id="0ec0c-104">Одним из замечательных вещей ASP.NET Web Forms является то, как она позволяет инкапсулировать многократно используемые фрагменты кода пользовательского интерфейса в многократно используемые элементы управления ПОЛЬЗОВАТЕЛЬСКОГО интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-104">One of the beautiful things about ASP.NET Web Forms is how it enables encapsulation of reusable pieces of user interface (UI) code into reusable UI controls.</span></span> <span data-ttu-id="0ec0c-105">Настраиваемые пользовательские элементы управления могут быть определены в разметке с помощью файлов *. ascx* .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-105">Custom user controls can be defined in markup using *.ascx* files.</span></span> <span data-ttu-id="0ec0c-106">Кроме того, можно создавать сложные серверные элементы управления в коде с полной поддержкой конструктора.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-106">You can also build elaborate server controls in code with full designer support.</span></span>

<span data-ttu-id="0ec0c-107">Blazor также поддерживает инкапсуляцию пользовательского интерфейса через *компоненты*.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-107">Blazor also supports UI encapsulation through *components*.</span></span> <span data-ttu-id="0ec0c-108">Компонент:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-108">A component:</span></span>

- <span data-ttu-id="0ec0c-109">— Это автономный фрагмент пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-109">Is a self-contained chunk of UI.</span></span>
- <span data-ttu-id="0ec0c-110">Поддерживает собственную логику состояния и отрисовки.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-110">Maintains its own state and rendering logic.</span></span>
- <span data-ttu-id="0ec0c-111">Может определять обработчики событий пользовательского интерфейса, выполнять привязку к входным данным и управлять собственным жизненным циклом.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-111">Can define UI event handlers, bind to input data, and manage its own lifecycle.</span></span>
- <span data-ttu-id="0ec0c-112">Обычно определяется в файле с *расширением Razor* с помощью синтаксис Razor.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-112">Is typically defined in a *.razor* file using Razor syntax.</span></span>

## <a name="an-introduction-to-razor"></a><span data-ttu-id="0ec0c-113">Введение в Razor</span><span class="sxs-lookup"><span data-stu-id="0ec0c-113">An introduction to Razor</span></span>

<span data-ttu-id="0ec0c-114">Razor — это облегченный язык создания шаблонов разметки на основе HTML и C#.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-114">Razor is a light-weight markup templating language based on HTML and C#.</span></span> <span data-ttu-id="0ec0c-115">С помощью Razor можно легко переходить между разметкой и кодом C#, чтобы определить логику отрисовки компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-115">With Razor, you can seamlessly transition between markup and C# code to define your component rendering logic.</span></span> <span data-ttu-id="0ec0c-116">При компиляции файла *. Razor* логика отрисовки записывается структурированным образом в классе .NET.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-116">When the *.razor* file is compiled, the rendering logic is captured in a structured way in a .NET class.</span></span> <span data-ttu-id="0ec0c-117">Имя скомпилированного класса берется из имени файла *. Razor* .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-117">The name of the compiled class is taken from the *.razor* file name.</span></span> <span data-ttu-id="0ec0c-118">Пространство имен берется из пространства имен по умолчанию для проекта и пути к папке, либо можно явно указать пространство имен с помощью `@namespace` директивы (Подробнее об директивах Razor ниже).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-118">The namespace is taken from the default namespace for the project and the folder path, or you can explicitly specify the namespace using the `@namespace` directive (more on Razor directives below).</span></span>

<span data-ttu-id="0ec0c-119">Логика отрисовки компонента создается с помощью обычной разметки HTML с динамической логикой, добавленной с помощью C#.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-119">A component's rendering logic is authored using normal HTML markup with dynamic logic added using C#.</span></span> <span data-ttu-id="0ec0c-120">`@`Символ используется для перехода на C#.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-120">The `@` character is used to transition to C#.</span></span> <span data-ttu-id="0ec0c-121">Razor обычно является разумным, чтобы определить, когда вы переключились обратно на HTML.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-121">Razor is typically smart about figuring out when you've switched back to HTML.</span></span> <span data-ttu-id="0ec0c-122">Например, следующий компонент отображает `<p>` тег с текущим временем:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-122">For example, the following component renders a `<p>` tag with the current time:</span></span>

```razor
<p>@DateTime.Now</p>
```

<span data-ttu-id="0ec0c-123">Чтобы явно указать начало и конец выражения C#, используйте круглые скобки:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-123">To explicitly specify the beginning and ending of a C# expression, use parentheses:</span></span>

```razor
<p>@(DateTime.Now)</p>
```

<span data-ttu-id="0ec0c-124">Razor также упрощает использование потока управления C# в логике отрисовки.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-124">Razor also makes it easy to use C# control flow in your rendering logic.</span></span> <span data-ttu-id="0ec0c-125">Например, можно выполнить условное отображение HTML-кода следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-125">For example, you can conditionally render some HTML like this:</span></span>

```razor
@if (value % 2 == 0)
{
    <p>The value was even.</p>
}
```

<span data-ttu-id="0ec0c-126">Также можно создать список элементов с помощью обычного `foreach` цикла C# следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-126">Or you can generate a list of items using a normal C# `foreach` loop like this:</span></span>

```razor
<ul>
@foreach (var item in items)
{
    <li>@item.Text</li>
}
</ul>
```

<span data-ttu-id="0ec0c-127">Директивы Razor, такие как директивы в ASP.NET Web Forms, управляют многими аспектами компиляции компонента Razor.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-127">Razor directives, like directives in ASP.NET Web Forms, control many aspects of how a Razor component is compiled.</span></span> <span data-ttu-id="0ec0c-128">Примеры включают в себя компонент:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-128">Examples include the component's:</span></span>

- <span data-ttu-id="0ec0c-129">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="0ec0c-129">Namespace</span></span>
- <span data-ttu-id="0ec0c-130">Базовый класс</span><span class="sxs-lookup"><span data-stu-id="0ec0c-130">Base class</span></span>
- <span data-ttu-id="0ec0c-131">Реализованные интерфейсы</span><span class="sxs-lookup"><span data-stu-id="0ec0c-131">Implemented interfaces</span></span>
- <span data-ttu-id="0ec0c-132">Универсальные параметры</span><span class="sxs-lookup"><span data-stu-id="0ec0c-132">Generic parameters</span></span>
- <span data-ttu-id="0ec0c-133">Импортированные пространства имен</span><span class="sxs-lookup"><span data-stu-id="0ec0c-133">Imported namespaces</span></span>
- <span data-ttu-id="0ec0c-134">Маршруты</span><span class="sxs-lookup"><span data-stu-id="0ec0c-134">Routes</span></span>

<span data-ttu-id="0ec0c-135">Директивы Razor начинаются с `@` символа и обычно используются в начале новой строки в начале файла.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-135">Razor directives start with the `@` character and are typically used at the start of a new line at the start of the file.</span></span> <span data-ttu-id="0ec0c-136">Например, `@namespace` директива определяет пространство имен компонента:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-136">For example, the `@namespace` directive defines the component's namespace:</span></span>

```razor
@namespace MyComponentNamespace
```

<span data-ttu-id="0ec0c-137">В следующей таблице перечислены различные директивы Razor, используемые в, Blazor и их эквиваленты ASP.NET Web Forms, если они существуют.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-137">The following table summarizes the various Razor directives used in Blazor and their ASP.NET Web Forms equivalents, if they exist.</span></span>

|<span data-ttu-id="0ec0c-138">Директива</span><span class="sxs-lookup"><span data-stu-id="0ec0c-138">Directive</span></span>    |<span data-ttu-id="0ec0c-139">Описание</span><span class="sxs-lookup"><span data-stu-id="0ec0c-139">Description</span></span>|<span data-ttu-id="0ec0c-140">Пример</span><span class="sxs-lookup"><span data-stu-id="0ec0c-140">Example</span></span>|<span data-ttu-id="0ec0c-141">Эквивалент веб-форм</span><span class="sxs-lookup"><span data-stu-id="0ec0c-141">Web Forms equivalent</span></span>|
|-------------|-----------|-------|--------------------|
|`@attribute` |<span data-ttu-id="0ec0c-142">Добавляет атрибут уровня класса в компонент</span><span class="sxs-lookup"><span data-stu-id="0ec0c-142">Adds a class-level attribute to the component</span></span>|`@attribute [Authorize]`|<span data-ttu-id="0ec0c-143">Нет</span><span class="sxs-lookup"><span data-stu-id="0ec0c-143">None</span></span>|
|`@code`      |<span data-ttu-id="0ec0c-144">Добавляет члены класса в компонент</span><span class="sxs-lookup"><span data-stu-id="0ec0c-144">Adds class members to the component</span></span>|`@code { ... }`|`<script runat="server">...</script>`|
|`@implements`|<span data-ttu-id="0ec0c-145">Реализует указанный интерфейс</span><span class="sxs-lookup"><span data-stu-id="0ec0c-145">Implements the specified interface</span></span>|`@implements IDisposable`|<span data-ttu-id="0ec0c-146">Использование кода программной части</span><span class="sxs-lookup"><span data-stu-id="0ec0c-146">Use code-behind</span></span>|
|`@inherits`  |<span data-ttu-id="0ec0c-147">Наследует от указанного базового класса</span><span class="sxs-lookup"><span data-stu-id="0ec0c-147">Inherits from the specified base class</span></span>|`@inherits MyComponentBase`|`<%@ Control Inherits="MyUserControlBase" %>`|
|`@inject`    |<span data-ttu-id="0ec0c-148">Внедряет службу в компонент.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-148">Injects a service into the component</span></span>|`@inject IJSRuntime JS`|<span data-ttu-id="0ec0c-149">Нет</span><span class="sxs-lookup"><span data-stu-id="0ec0c-149">None</span></span>|
|`@layout`    |<span data-ttu-id="0ec0c-150">Задает компонент макета для компонента</span><span class="sxs-lookup"><span data-stu-id="0ec0c-150">Specifies a layout component for the component</span></span>|`@layout MainLayout`|`<%@ Page MasterPageFile="~/Site.Master" %>`|
|`@namespace` |<span data-ttu-id="0ec0c-151">Задает пространство имен для компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-151">Sets the namespace for the component</span></span>|`@namespace MyNamespace`|<span data-ttu-id="0ec0c-152">Нет</span><span class="sxs-lookup"><span data-stu-id="0ec0c-152">None</span></span>|
|`@page`      |<span data-ttu-id="0ec0c-153">Указывает маршрут для компонента</span><span class="sxs-lookup"><span data-stu-id="0ec0c-153">Specifies the route for the component</span></span>|`@page "/product/{id}"`|`<%@ Page %>`|
|`@typeparam` |<span data-ttu-id="0ec0c-154">Задает параметр универсального типа для компонента</span><span class="sxs-lookup"><span data-stu-id="0ec0c-154">Specifies a generic type parameter for the component</span></span>|`@typeparam TItem`|<span data-ttu-id="0ec0c-155">Использование кода программной части</span><span class="sxs-lookup"><span data-stu-id="0ec0c-155">Use code-behind</span></span>|
|`@using`     |<span data-ttu-id="0ec0c-156">Указывает пространство имен для переноса в область</span><span class="sxs-lookup"><span data-stu-id="0ec0c-156">Specifies a namespace to bring into scope</span></span>|`@using MyComponentNamespace`|<span data-ttu-id="0ec0c-157">Добавление пространства имен в *web.config*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-157">Add namespace in *web.config*</span></span>|

<span data-ttu-id="0ec0c-158">Компоненты Razor также активно используют *атрибуты директивы* в элементах для управления различными аспектами компиляции компонентов (обработки событий, привязки данных, компонентов & ссылок на элементы и т. д.).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-158">Razor components also make extensive use of *directive attributes* on elements to control various aspects of how components get compiled (event handling, data binding, component & element references, and so on).</span></span> <span data-ttu-id="0ec0c-159">Все атрибуты директивы следуют общему универсальному синтаксису, в котором значения в круглых скобках являются необязательными:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-159">Directive attributes all follow a common generic syntax where the values in parenthesis are optional:</span></span>

```razor
@directive(-suffix(:name))(="value")
```

<span data-ttu-id="0ec0c-160">В следующей таблице перечислены различные атрибуты директив Razor, используемые в Blazor .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-160">The following table summarizes the various attributes for Razor directives used in Blazor.</span></span>

|<span data-ttu-id="0ec0c-161">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0ec0c-161">Attribute</span></span>    |<span data-ttu-id="0ec0c-162">Описание</span><span class="sxs-lookup"><span data-stu-id="0ec0c-162">Description</span></span>|<span data-ttu-id="0ec0c-163">Пример</span><span class="sxs-lookup"><span data-stu-id="0ec0c-163">Example</span></span>|
|-------------|-----------|-------|
|`@attributes`|<span data-ttu-id="0ec0c-164">Подготавливает к просмотру словарь атрибутов</span><span class="sxs-lookup"><span data-stu-id="0ec0c-164">Renders a dictionary of attributes</span></span>|`<input @attributes="ExtraAttributes" />`|
|`@bind`      |<span data-ttu-id="0ec0c-165">Создает двустороннюю привязку данных</span><span class="sxs-lookup"><span data-stu-id="0ec0c-165">Creates a two-way data binding</span></span>    |`<input @bind="username" @bind:event="oninput" />`|
|`@on{event}` |<span data-ttu-id="0ec0c-166">Добавляет обработчик событий для указанного события</span><span class="sxs-lookup"><span data-stu-id="0ec0c-166">Adds an event handler for the specified event</span></span>|`<button @onclick="IncrementCount">Click me!</button>`|
|`@key`       |<span data-ttu-id="0ec0c-167">Задает ключ, используемый алгоритмом сравнения для сохранения элементов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-167">Specifies a key to be used by the diffing algorithm for preserving elements in a collection</span></span>|`<DetailsEditor @key="person" Details="person.Details" />`|
|`@ref`       |<span data-ttu-id="0ec0c-168">Захватывает ссылку на компонент или HTML-элемент</span><span class="sxs-lookup"><span data-stu-id="0ec0c-168">Captures a reference to the component or HTML element</span></span>|`<MyDialog @ref="myDialog" />`|

<span data-ttu-id="0ec0c-169">Различные атрибуты директивы, используемые Blazor ( `@onclick` , `@bind` , и `@ref` т. д.), описаны в разделах ниже и последующих главах.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-169">The various directive attributes used by Blazor (`@onclick`, `@bind`, `@ref`, and so on) are covered in the sections below and later chapters.</span></span>

<span data-ttu-id="0ec0c-170">Многие из синтаксисов, используемых в файлах *. aspx* и *. ascx* , имеют параллельные синтаксисы в Razor.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-170">Many of the syntaxes used in *.aspx* and *.ascx* files have parallel syntaxes in Razor.</span></span> <span data-ttu-id="0ec0c-171">Ниже приведено простое сравнение синтаксиса для веб-форм ASP.NET и Razor.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-171">Below is a simple comparison of the syntaxes for ASP.NET Web Forms and Razor.</span></span>

|<span data-ttu-id="0ec0c-172">Функция</span><span class="sxs-lookup"><span data-stu-id="0ec0c-172">Feature</span></span>                      |<span data-ttu-id="0ec0c-173">веб-формы</span><span class="sxs-lookup"><span data-stu-id="0ec0c-173">Web Forms</span></span>           |<span data-ttu-id="0ec0c-174">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0ec0c-174">Syntax</span></span>               |<span data-ttu-id="0ec0c-175">Razor</span><span class="sxs-lookup"><span data-stu-id="0ec0c-175">Razor</span></span>         |<span data-ttu-id="0ec0c-176">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0ec0c-176">Syntax</span></span> |
|-----------------------------|--------------------|---------------------|--------------|-------|
|<span data-ttu-id="0ec0c-177">Директивы</span><span class="sxs-lookup"><span data-stu-id="0ec0c-177">Directives</span></span>                   |`<%@ [directive] %>`|`<%@ Page %>`        |`@[directive]`|`@page`|
|<span data-ttu-id="0ec0c-178">Блоки кода</span><span class="sxs-lookup"><span data-stu-id="0ec0c-178">Code blocks</span></span>                  |`<% %>`             |`<% int x = 123; %>` |`@{ }`        |`@{ int x = 123; }`|
|<span data-ttu-id="0ec0c-179">Выражения</span><span class="sxs-lookup"><span data-stu-id="0ec0c-179">Expressions</span></span><br><span data-ttu-id="0ec0c-180">(В кодировке HTML)</span><span class="sxs-lookup"><span data-stu-id="0ec0c-180">(HTML-encoded)</span></span>|`<%: %>`            |`<%:DateTime.Now %>` |<span data-ttu-id="0ec0c-181">Полностью `@`</span><span class="sxs-lookup"><span data-stu-id="0ec0c-181">Implicit: `@`</span></span><br><span data-ttu-id="0ec0c-182">Прямая `@()`</span><span class="sxs-lookup"><span data-stu-id="0ec0c-182">Explicit: `@()`</span></span>|`@DateTime.Now`<br>`@(DateTime.Now)`|
|<span data-ttu-id="0ec0c-183">Комментарии</span><span class="sxs-lookup"><span data-stu-id="0ec0c-183">Comments</span></span>                     |`<%-- --%>`         |`<%-- Commented --%>`|`@* *@`       |`@* Commented *@`|
|<span data-ttu-id="0ec0c-184">привязка данных,</span><span class="sxs-lookup"><span data-stu-id="0ec0c-184">Data binding</span></span>                 |`<%# %>`            |`<%# Bind("Name") %>`|`@bind`       |`<input @bind="username" />`|

<span data-ttu-id="0ec0c-185">Чтобы добавить члены в класс компонента Razor, используйте `@code` директиву.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-185">To add members to the Razor component class, use the `@code` directive.</span></span> <span data-ttu-id="0ec0c-186">Этот метод аналогичен использованию `<script runat="server">...</script>` блока в пользовательском элементе управления или странице веб-форм ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-186">This technique is similar to using a `<script runat="server">...</script>` block in an ASP.NET Web Forms user control or page.</span></span>

```razor
@code {
    int count = 0;

    void IncrementCount()
    {
        count++;
    }
}
```

<span data-ttu-id="0ec0c-187">Поскольку Razor основан на C#, он должен быть скомпилирован из проекта C# (*. csproj*).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-187">Because Razor is based on C#, it must be compiled from within a C# project (*.csproj*).</span></span> <span data-ttu-id="0ec0c-188">Файлы *. Razor* нельзя компилировать из проекта Visual Basic (*. vbproj*).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-188">You can't compile *.razor* files from a Visual Basic project (*.vbproj*).</span></span> <span data-ttu-id="0ec0c-189">Вы по-прежнему можете ссылаться на Visual Basic проекты из Blazor проекта.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-189">You can still reference Visual Basic projects from your Blazor project.</span></span> <span data-ttu-id="0ec0c-190">Обратное тоже верно.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-190">The opposite is true too.</span></span>

<span data-ttu-id="0ec0c-191">Полный справочник по синтаксис Razor см. в статье [синтаксис Razor Справочник по ASP.NET Core](/aspnet/core/mvc/views/razor).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-191">For a full Razor syntax reference, see [Razor syntax reference for ASP.NET Core](/aspnet/core/mvc/views/razor).</span></span>

## <a name="use-components"></a><span data-ttu-id="0ec0c-192">Использование компонентов</span><span class="sxs-lookup"><span data-stu-id="0ec0c-192">Use components</span></span>

<span data-ttu-id="0ec0c-193">Помимо обычного HTML, компоненты также могут использовать другие компоненты как часть логики отрисовки.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-193">Aside from normal HTML, components can also use other components as part of their rendering logic.</span></span> <span data-ttu-id="0ec0c-194">Синтаксис использования компонента в Razor подобен использованию пользовательского элемента управления в приложении веб-форм ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-194">The syntax for using a component in Razor is similar to using a user control in an ASP.NET Web Forms app.</span></span> <span data-ttu-id="0ec0c-195">Компоненты указываются с помощью тега элемента, соответствующего имени типа компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-195">Components are specified using an element tag that matches the type name of the component.</span></span> <span data-ttu-id="0ec0c-196">Например, можно добавить `Counter` компонент следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-196">For example, you can add a `Counter` component like this:</span></span>

```razor
<Counter />
```

<span data-ttu-id="0ec0c-197">В отличие от веб-форм ASP.NET, компоненты в Blazor :</span><span class="sxs-lookup"><span data-stu-id="0ec0c-197">Unlike ASP.NET Web Forms, components in Blazor:</span></span>

- <span data-ttu-id="0ec0c-198">Не используйте префикс элемента (например, `asp:` ).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-198">Don't use an element prefix (for example, `asp:`).</span></span>
- <span data-ttu-id="0ec0c-199">Не требовать регистрации на странице или в *web.config*.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-199">Don't require registration on the page or in the *web.config*.</span></span>

<span data-ttu-id="0ec0c-200">Подумайте о таких компонентах Razor, как типы .NET, так как это именно то, что они представляют.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-200">Think of Razor components like you would .NET types, because that's exactly what they are.</span></span> <span data-ttu-id="0ec0c-201">Если имеется ссылка на сборку, содержащую компонент, то компонент доступен для использования.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-201">If the assembly containing the component is referenced, then the component is available for use.</span></span> <span data-ttu-id="0ec0c-202">Чтобы перенести пространство имен компонента в область, примените `@using` директиву:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-202">To bring the component's namespace into scope, apply the `@using` directive:</span></span>

```razor
@using MyComponentLib

<Counter />
```

<span data-ttu-id="0ec0c-203">Как видно в проектах по умолчанию Blazor , директивы можно размещать `@using` в файле *_Imports. Razor* , чтобы они были импортированы во все файлы *Razor* в одном и том же каталоге и в дочерних каталогах.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-203">As seen in the default Blazor projects, it's common to put `@using` directives into a *_Imports.razor* file so that they're imported into all *.razor* files in the same directory and in child directories.</span></span>

<span data-ttu-id="0ec0c-204">Если пространство имен для компонента не находится в области, можно указать компонент, используя его полное имя типа, как в C#:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-204">If the namespace for a component isn't in scope, you can specify a component using its full type name, as you can in C#:</span></span>

```razor
<MyComponentLib.Counter />
```

## <a name="component-parameters"></a><span data-ttu-id="0ec0c-205">Параметры компонентов</span><span class="sxs-lookup"><span data-stu-id="0ec0c-205">Component parameters</span></span>

<span data-ttu-id="0ec0c-206">В ASP.NET Web Forms можно передавать параметры и данные в элементы управления с помощью общедоступных свойств.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-206">In ASP.NET Web Forms, you can flow parameters and data to controls using public properties.</span></span> <span data-ttu-id="0ec0c-207">Эти свойства можно задать в разметке с помощью атрибутов или непосредственно в коде.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-207">These properties can be set in markup using attributes or set directly in code.</span></span> <span data-ttu-id="0ec0c-208">Blazor компоненты работают аналогичным образом, хотя свойства компонентов также должны быть помечены `[Parameter]` атрибутом, который будет считаться параметрами компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-208">Blazor components work in a similar fashion, although the component properties must also be marked with the `[Parameter]` attribute to be considered component parameters.</span></span>

<span data-ttu-id="0ec0c-209">Следующий `Counter` компонент определяет параметр компонента `IncrementAmount` с именем, который можно использовать для указания величины `Counter` приращения при каждом нажатии кнопки.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-209">The following `Counter` component defines a component parameter called `IncrementAmount` that can be used to specify the amount that the `Counter` should be incremented each time the button is clicked.</span></span>

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

<span data-ttu-id="0ec0c-210">Чтобы указать параметр компонента в Blazor , используйте атрибут, как в веб-формах ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-210">To specify a component parameter in Blazor, use an attribute as you would in ASP.NET Web Forms:</span></span>

```razor
<Counter IncrementAmount="10" />
```

## <a name="event-handlers"></a><span data-ttu-id="0ec0c-211">Обработчики событий</span><span class="sxs-lookup"><span data-stu-id="0ec0c-211">Event handlers</span></span>

<span data-ttu-id="0ec0c-212">Веб-формы ASP.NET и Blazor предоставляют модель программирования на основе событий для обработки событий пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-212">Both ASP.NET Web Forms and Blazor provide an event-based programming model for handling UI events.</span></span> <span data-ttu-id="0ec0c-213">Примеры таких событий включают нажатия кнопок и ввод текста.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-213">Examples of such events include button clicks and text input.</span></span> <span data-ttu-id="0ec0c-214">В ASP.NET Web Forms используются серверные элементы управления HTML для работы с событиями пользовательского интерфейса, предоставляемыми моделью DOM, или для выполнения событий, предоставляемых серверными веб-элементами управления.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-214">In ASP.NET Web Forms, you use HTML server controls to handle UI events exposed by the DOM, or you can handle events exposed by web server controls.</span></span> <span data-ttu-id="0ec0c-215">События отображаются на сервере посредством запросов обратной передачи.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-215">The events are surfaced on the server through form post-back requests.</span></span> <span data-ttu-id="0ec0c-216">Рассмотрим следующие примеры кнопок веб-форм:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-216">Consider the following Web Forms button click example:</span></span>

<span data-ttu-id="0ec0c-217">*Counter. ascx*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-217">*Counter.ascx*</span></span>

```aspx-csharp
<asp:Button ID="ClickMeButton" runat="server" Text="Click me!" OnClick="ClickMeButton_Click" />
```

<span data-ttu-id="0ec0c-218">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-218">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void ClickMeButton_Click(object sender, EventArgs e)
    {
        Console.WriteLine("The button was clicked!");
    }
}
```

<span data-ttu-id="0ec0c-219">В Blazor можно зарегистрировать обработчики для событий пользовательского интерфейса DOM напрямую с помощью атрибутов директивы в форме `@on{event}` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-219">In Blazor, you can register handlers for DOM UI events directly using directive attributes of the form `@on{event}`.</span></span> <span data-ttu-id="0ec0c-220">`{event}`Заполнитель представляет имя события.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-220">The `{event}` placeholder represents the name of the event.</span></span> <span data-ttu-id="0ec0c-221">Например, можно прослушивать нажатия кнопок следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-221">For example, you can listen for button clicks like this:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick()
    {
        Console.WriteLine("The button was clicked!);
    }
}
```

<span data-ttu-id="0ec0c-222">Обработчики событий могут принимать необязательный аргумент, относящийся к конкретному событию, для предоставления дополнительных сведений о событии.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-222">Event handlers can accept an optional, event-specific argument to provide more information about the event.</span></span> <span data-ttu-id="0ec0c-223">Например, события мыши могут принимать `MouseEventArgs` аргумент, но это не обязательно.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-223">For example, mouse events can take a `MouseEventArgs` argument, but it isn't required.</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    void OnClick(MouseEventArgs e)
    {
        Console.WriteLine($"Mouse clicked at {e.ScreenX}, {e.ScreenY}.");
    }
}
```

<span data-ttu-id="0ec0c-224">Вместо ссылки на группу методов для обработчика событий можно использовать лямбда-выражение.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-224">Instead of referring to a method group for an event handler, you can use a lambda expression.</span></span> <span data-ttu-id="0ec0c-225">Лямбда-выражение позволяет закрывать другие значения в области.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-225">A lambda expression allows you to close over other in-scope values.</span></span>

```razor
@foreach (var buttonLabel in buttonLabels)
{
    <button @onclick="() => Console.WriteLine($"The {buttonLabel} button was clicked!")">@buttonLabel</button>
}
```

<span data-ttu-id="0ec0c-226">Обработчики событий могут выполняться синхронно или асинхронно.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-226">Event handlers can execute synchronously or asynchronously.</span></span> <span data-ttu-id="0ec0c-227">Например, следующий `OnClick` обработчик событий выполняется асинхронно:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-227">For example, the following `OnClick` event handler executes asynchronously:</span></span>

```razor
<button @onclick="OnClick">Click me!</button>

@code {
    async Task OnClick()
    {
        var result = await Http.GetAsync("api/values");
    }
}
```

<span data-ttu-id="0ec0c-228">После обработки события компонент подготавливается к просмотру для учета изменений состояния компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-228">After an event is handled, the component is rendered to account for any component state changes.</span></span> <span data-ttu-id="0ec0c-229">При использовании асинхронных обработчиков событий компонент подготавливается к просмотру сразу после завершения выполнения обработчика.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-229">With asynchronous event handlers, the component is rendered immediately after the handler execution completes.</span></span> <span data-ttu-id="0ec0c-230">После завершения асинхронного выполнения компонент *снова* готовится к просмотру `Task` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-230">The component is rendered *again* after the asynchronous `Task` completes.</span></span> <span data-ttu-id="0ec0c-231">Этот асинхронный режим выполнения позволяет визуализировать какой-либо соответствующий пользовательский интерфейс во время `Task` выполнения асинхронной операции.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-231">This asynchronous execution mode provides an opportunity to render some appropriate UI while the asynchronous `Task` is still in progress.</span></span>

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

<span data-ttu-id="0ec0c-232">Компоненты также могут определять собственные события, определяя параметр компонента типа `EventCallback<TValue>` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-232">Components can also define their own events by defining a component parameter of type `EventCallback<TValue>`.</span></span> <span data-ttu-id="0ec0c-233">Обратные вызовы событий поддерживают все разновидности обработчиков событий пользовательского интерфейса DOM: необязательные аргументы, синхронные или асинхронные, группы методов или лямбда-выражения.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-233">Event callbacks support all the variations of DOM UI event handlers: optional arguments, synchronous or asynchronous, method groups, or lambda expressions.</span></span>

```razor
<button class="btn btn-primary" @onclick="OnClick">Click me!</button>

@code {
    [Parameter]
    public EventCallback<MouseEventArgs> OnClick { get; set; }
}
```

## <a name="data-binding"></a><span data-ttu-id="0ec0c-234">привязка данных,</span><span class="sxs-lookup"><span data-stu-id="0ec0c-234">Data binding</span></span>

<span data-ttu-id="0ec0c-235">Blazor предоставляет простой механизм привязки данных из компонента пользовательского интерфейса к состоянию компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-235">Blazor provides a simple mechanism to bind data from a UI component to the component's state.</span></span> <span data-ttu-id="0ec0c-236">Этот подход отличается от функций в ASP.NET Web Forms для привязки данных из источников данных к элементам управления пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-236">This approach differs from the features in ASP.NET Web Forms for binding data from data sources to UI controls.</span></span> <span data-ttu-id="0ec0c-237">Мы обсудим обработку данных из различных источников данных в разделе " [Работа с данными](data.md) ".</span><span class="sxs-lookup"><span data-stu-id="0ec0c-237">We'll cover handling data from different data sources in the [Dealing with data](data.md) section.</span></span>

<span data-ttu-id="0ec0c-238">Чтобы создать двустороннюю привязку данных от компонента пользовательского интерфейса к состоянию компонента, используйте `@bind` атрибут директивы.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-238">To create a two-way data binding from a UI component to the component's state, use the `@bind` directive attribute.</span></span> <span data-ttu-id="0ec0c-239">В следующем примере значение флажка привязано к `isChecked` полю.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-239">In the following example, the value of the check box is bound to the `isChecked` field.</span></span>

```razor
<input type="checkbox" @bind="isChecked" />

@code {
    bool isChecked;
}
```

<span data-ttu-id="0ec0c-240">При подготовке компонента к просмотру значение флажка устанавливается равным значению `isChecked` поля.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-240">When the component is rendered, the value of the checkbox is set to the value of the `isChecked` field.</span></span> <span data-ttu-id="0ec0c-241">Когда пользователь переключает флажок, `onchange` событие срабатывает и `isChecked` для поля задается новое значение.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-241">When the user toggles the checkbox, the `onchange` event is fired and the `isChecked` field is set to the new value.</span></span> <span data-ttu-id="0ec0c-242">`@bind`Синтаксис в этом случае эквивалентен следующей разметке:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-242">The `@bind` syntax in this case is equivalent to the following markup:</span></span>

```razor
<input value="@isChecked" @onchange="(UIChangeEventArgs e) => isChecked = e.Value" />
```

<span data-ttu-id="0ec0c-243">Чтобы изменить событие, используемое для привязки, используйте `@bind:event` атрибут.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-243">To change the event used for the bind, use the `@bind:event` attribute.</span></span>

```razor
<input @bind="text" @bind:event="oninput" />
<p>@text</p>

@code {
    string text;
}
```

<span data-ttu-id="0ec0c-244">Компоненты также могут поддерживать привязку данных к их параметрам.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-244">Components can also support data binding to their parameters.</span></span> <span data-ttu-id="0ec0c-245">Для привязки данных определите параметр обратного вызова события с тем же именем, что и у привязываемого параметра.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-245">To data bind, define an event callback parameter with the same name as the bindable parameter.</span></span> <span data-ttu-id="0ec0c-246">В имя добавляется суффикс "Changed".</span><span class="sxs-lookup"><span data-stu-id="0ec0c-246">The "Changed" suffix is added to the name.</span></span>

<span data-ttu-id="0ec0c-247">*PasswordBox. Razor*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-247">*PasswordBox.razor*</span></span>

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

<span data-ttu-id="0ec0c-248">Чтобы связать привязку данных с базовым элементом пользовательского интерфейса, установите значение и обработайте событие непосредственно в элементе пользовательского интерфейса, а не с помощью `@bind` атрибута.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-248">To chain a data binding to an underlying UI element, set the value and handle the event directly on the UI element instead of using the `@bind` attribute.</span></span>

<span data-ttu-id="0ec0c-249">Чтобы выполнить привязку к параметру компонента, используйте `@bind-{Parameter}` атрибут, чтобы указать параметр, с которым необходимо выполнить привязку.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-249">To bind to a component parameter, use a `@bind-{Parameter}` attribute to specify the parameter to which you want to bind.</span></span>

```razor
<PasswordBox @bind-Password="password" />

@code {
    string password;
}
```

## <a name="state-changes"></a><span data-ttu-id="0ec0c-250">Изменения состояния</span><span class="sxs-lookup"><span data-stu-id="0ec0c-250">State changes</span></span>

<span data-ttu-id="0ec0c-251">Если состояние компонента изменилось за пределами обычного пользовательского интерфейса или обратного вызова события, компонент должен вручную сообщить, что он должен быть визуализирован повторно.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-251">If the component's state has changed outside of a normal UI event or event callback, then the component must manually signal that it needs to be rendered again.</span></span> <span data-ttu-id="0ec0c-252">Чтобы сообщить о том, что состояние компонента изменилось, вызовите `StateHasChanged` метод для компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-252">To signal that a component's state has changed, call the `StateHasChanged` method on the component.</span></span>

<span data-ttu-id="0ec0c-253">В приведенном ниже примере компонент отображает сообщение из `AppState` службы, которая может быть обновлена другими частями приложения.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-253">In the example below, a component displays a message from an `AppState` service that can be updated by other parts of the app.</span></span> <span data-ttu-id="0ec0c-254">Компонент регистрирует свой `StateHasChanged` метод с `AppState.OnChange` событием, чтобы компонент был визуализирован при каждом обновлении сообщения.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-254">The component registers its `StateHasChanged` method with the `AppState.OnChange` event so that the component is rendered whenever the message gets updated.</span></span>

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

## <a name="component-lifecycle"></a><span data-ttu-id="0ec0c-255">Жизненный цикл компонента</span><span class="sxs-lookup"><span data-stu-id="0ec0c-255">Component lifecycle</span></span>

<span data-ttu-id="0ec0c-256">Платформа веб-форм ASP.NET имеет четко определенные методы жизненного цикла для модулей, страниц и элементов управления.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-256">The ASP.NET Web Forms framework has well-defined lifecycle methods for modules, pages, and controls.</span></span> <span data-ttu-id="0ec0c-257">Например, следующий элемент управления реализует обработчики событий для `Init` `Load` `UnLoad` событий жизненного цикла, и:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-257">For example, the following control implements event handlers for the `Init`, `Load`, and `UnLoad` lifecycle events:</span></span>

<span data-ttu-id="0ec0c-258">*Counter.ascx.cs*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-258">*Counter.ascx.cs*</span></span>

```csharp
public partial class Counter : System.Web.UI.UserControl
{
    protected void Page_Init(object sender, EventArgs e) { ... }
    protected void Page_Load(object sender, EventArgs e) { ... }
    protected void Page_UnLoad(object sender, EventArgs e) { ... }
}
```

<span data-ttu-id="0ec0c-259">Blazor компоненты также имеют четко определенный жизненный цикл.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-259">Blazor components also have a well-defined lifecycle.</span></span> <span data-ttu-id="0ec0c-260">Жизненный цикл компонента можно использовать для инициализации состояния компонента и реализации дополнительных поведений компонентов.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-260">A component's lifecycle can be used to initialize component state and implement advanced component behaviors.</span></span>

<span data-ttu-id="0ec0c-261">Все Blazor методы жизненного цикла компонента имеют как синхронные, так и асинхронные версии.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-261">All of Blazor's component lifecycle methods have both synchronous and asynchronous versions.</span></span> <span data-ttu-id="0ec0c-262">Визуализация компонента является синхронной.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-262">Component rendering is synchronous.</span></span> <span data-ttu-id="0ec0c-263">Асинхронную логику нельзя выполнять в процессе подготовки компонента к просмотру.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-263">You can't run asynchronous logic as part of the component rendering.</span></span> <span data-ttu-id="0ec0c-264">Вся Асинхронная логика должна выполняться как часть `async` метода жизненного цикла.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-264">All asynchronous logic must execute as part of an `async` lifecycle method.</span></span>

### <a name="oninitialized"></a><span data-ttu-id="0ec0c-265">Oninitiald</span><span class="sxs-lookup"><span data-stu-id="0ec0c-265">OnInitialized</span></span>

<span data-ttu-id="0ec0c-266">`OnInitialized`Методы и `OnInitializedAsync` используются для инициализации компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-266">The `OnInitialized` and `OnInitializedAsync` methods are used to initialize the component.</span></span> <span data-ttu-id="0ec0c-267">Обычно компонент инициализируется после его первого отображения.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-267">A component is typically initialized after it's first rendered.</span></span> <span data-ttu-id="0ec0c-268">После инициализации компонента он может быть визуализирован несколько раз, прежде чем он будет удален в конечном итоге.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-268">After a component is initialized, it may be rendered multiple times before it's eventually disposed.</span></span> <span data-ttu-id="0ec0c-269">`OnInitialized`Метод аналогичен `Page_Load` событию на страницах и элементах управления веб-форм ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-269">The `OnInitialized` method is similar to the `Page_Load` event in ASP.NET Web Forms pages and controls.</span></span>

```csharp
protected override void OnInitialized() { ... }
protected override async Task OnInitializedAsync() { await ... }
```

### <a name="onparametersset"></a><span data-ttu-id="0ec0c-270">Onparameters, параметр</span><span class="sxs-lookup"><span data-stu-id="0ec0c-270">OnParametersSet</span></span>

<span data-ttu-id="0ec0c-271">`OnParametersSet`Методы и `OnParametersSetAsync` вызываются, когда компонент получил параметры от своего родителя, и значение присваивается свойствам.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-271">The `OnParametersSet` and `OnParametersSetAsync` methods are called when a component has received parameters from its parent and the value are assigned to properties.</span></span> <span data-ttu-id="0ec0c-272">Эти методы выполняются после инициализации компонента и при *каждом отображении компонента*.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-272">These methods are executed after component initialization and *each time the component is rendered*.</span></span>

```csharp
protected override void OnParametersSet() { ... }
protected override async Task OnParametersSetAsync() { await ... }
```

### <a name="onafterrender"></a><span data-ttu-id="0ec0c-273">онафтеррендер</span><span class="sxs-lookup"><span data-stu-id="0ec0c-273">OnAfterRender</span></span>

<span data-ttu-id="0ec0c-274">`OnAfterRender`Методы и `OnAfterRenderAsync` вызываются после завершения подготовки компонента к просмотру.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-274">The `OnAfterRender` and `OnAfterRenderAsync` methods are called after a component has finished rendering.</span></span> <span data-ttu-id="0ec0c-275">Ссылки на элементы и компоненты заполняются в этот момент (Подробнее об этих концепциях см. ниже).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-275">Element and component references are populated at this point (more on these concepts below).</span></span> <span data-ttu-id="0ec0c-276">В данный момент интерактивное взаимодействие с браузером включено.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-276">Interactivity with the browser is enabled at this point.</span></span> <span data-ttu-id="0ec0c-277">Взаимодействие с моделью DOM и выполнением JavaScript может безопасно выполняться.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-277">Interactions with the DOM and JavaScript execution can safely take place.</span></span>

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

<span data-ttu-id="0ec0c-278">`OnAfterRender` и `OnAfterRenderAsync` *не вызываются при предварительной отрисовке на сервере*.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-278">`OnAfterRender` and `OnAfterRenderAsync` *aren't called when prerendering on the server*.</span></span>

<span data-ttu-id="0ec0c-279">`firstRender`Параметр является `true` первым при подготовке компонента к просмотру; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-279">The `firstRender` parameter is `true` the first time the component is rendered; otherwise, its value is `false`.</span></span>

### <a name="idisposable"></a><span data-ttu-id="0ec0c-280">IDisposable</span><span class="sxs-lookup"><span data-stu-id="0ec0c-280">IDisposable</span></span>

<span data-ttu-id="0ec0c-281">Blazor компоненты могут реализовать `IDisposable` для удаления ресурсов при удалении компонента из пользовательского интерфейса.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-281">Blazor components can implement `IDisposable` to dispose of resources when the component is removed from the UI.</span></span> <span data-ttu-id="0ec0c-282">Компонент Razor может реализовать с `IDispose` помощью `@implements` директивы:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-282">A Razor component can implement `IDispose` by using the `@implements` directive:</span></span>

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

## <a name="capture-component-references"></a><span data-ttu-id="0ec0c-283">Ссылки на компоненты записи</span><span class="sxs-lookup"><span data-stu-id="0ec0c-283">Capture component references</span></span>

<span data-ttu-id="0ec0c-284">В ASP.NET Web Forms можно управлять экземпляром элемента управления непосредственно в коде, ссылаясь на его идентификатор.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-284">In ASP.NET Web Forms, it's common to manipulate a control instance directly in code by referring to its ID.</span></span> <span data-ttu-id="0ec0c-285">В можно Blazor также собрать ссылку на компонент и манипулировать ей, хотя она гораздо менее распространена.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-285">In Blazor, it's also possible to capture and manipulate a reference to a component, although it's much less common.</span></span>

<span data-ttu-id="0ec0c-286">Чтобы записать ссылку на компонент в Blazor , используйте `@ref` атрибут директивы.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-286">To capture a component reference in Blazor, use the `@ref` directive attribute.</span></span> <span data-ttu-id="0ec0c-287">Значение атрибута должно совпадать с именем настраиваемого поля, имеющего тот же тип, что и компонент, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-287">The value of the attribute should match the name of a settable field with the same type as the referenced component.</span></span>

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

<span data-ttu-id="0ec0c-288">При подготовке к просмотру родительского компонента поле заполняется экземпляром дочернего компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-288">When the parent component is rendered, the field is populated with the child component instance.</span></span> <span data-ttu-id="0ec0c-289">Затем можно вызывать методы в экземпляре компонента или иным образом манипулировать им.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-289">You can then call methods on, or otherwise manipulate, the component instance.</span></span>

<span data-ttu-id="0ec0c-290">Не рекомендуется манипулировать состоянием компонента непосредственно с помощью ссылок на компоненты.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-290">Manipulating component state directly using component references isn't recommended.</span></span> <span data-ttu-id="0ec0c-291">Это предотвращает автоматическое отображение компонента в нужное время.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-291">Doing so prevents the component from being rendered automatically at the correct times.</span></span>

## <a name="capture-element-references"></a><span data-ttu-id="0ec0c-292">Запись ссылок на элементы</span><span class="sxs-lookup"><span data-stu-id="0ec0c-292">Capture element references</span></span>

<span data-ttu-id="0ec0c-293">Blazor компоненты могут записывать ссылки на элемент.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-293">Blazor components can capture references to an element.</span></span> <span data-ttu-id="0ec0c-294">В отличие от серверных элементов управления HTML в веб-формах ASP.NET, модель DOM нельзя манипулировать напрямую с помощью ссылки на элемент в Blazor .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-294">Unlike HTML server controls in ASP.NET Web Forms, you can't manipulate the DOM directly using an element reference in Blazor.</span></span> <span data-ttu-id="0ec0c-295">Blazor обрабатывает большинство взаимодействий DOM с помощью алгоритма сравнения DOM.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-295">Blazor handles most DOM interactions for you using its DOM diffing algorithm.</span></span> <span data-ttu-id="0ec0c-296">Захваченные ссылки на элементы в Blazor являются непрозрачными.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-296">Captured element references in Blazor are opaque.</span></span> <span data-ttu-id="0ec0c-297">Однако они используются для передачи определенной ссылки на элемент в вызове взаимодействия JavaScript.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-297">However, they're used to pass a specific element reference in a JavaScript interop call.</span></span> <span data-ttu-id="0ec0c-298">Дополнительные сведения о взаимодействии JavaScript см. в разделе [ASP.NET Core Blazor взаимодействие JavaScript](/aspnet/core/blazor/javascript-interop).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-298">For more information about JavaScript interop, see [ASP.NET Core Blazor JavaScript interop](/aspnet/core/blazor/javascript-interop).</span></span>

## <a name="templated-components"></a><span data-ttu-id="0ec0c-299">Шаблонные компоненты</span><span class="sxs-lookup"><span data-stu-id="0ec0c-299">Templated components</span></span>

<span data-ttu-id="0ec0c-300">В ASP.NET Web Forms можно создавать *шаблонные элементы управления*.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-300">In ASP.NET Web Forms, you can create *templated controls*.</span></span> <span data-ttu-id="0ec0c-301">Шаблонные элементы управления позволяют разработчику указать часть HTML-кода, используемую для визуализации элемента управления контейнера.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-301">Templated controls enable the developer to specify a portion of the HTML used to render a container control.</span></span> <span data-ttu-id="0ec0c-302">Механизм создания шаблонных серверных элементов управления является сложным, но он позволяет создавать эффективные сценарии для отрисовки данных с настраиваемым пользователем способом.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-302">The mechanics of building templated server controls are complex, but they enable powerful scenarios for rendering data in a user customizable way.</span></span> <span data-ttu-id="0ec0c-303">Примеры элементов управления с шаблонами включают `Repeater` и `DataList` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-303">Examples of templated controls include `Repeater` and `DataList`.</span></span>

<span data-ttu-id="0ec0c-304">Blazor для компонентов также можно создавать шаблоны путем определения параметров компонентов типа `RenderFragment` или `RenderFragment<T>` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-304">Blazor components can also be templated by defining component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="0ec0c-305">`RenderFragment`Представляет фрагмент разметки Razor, который затем может быть визуализирован компонентом.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-305">A `RenderFragment` represents a chunk of Razor markup that can then be rendered by the component.</span></span> <span data-ttu-id="0ec0c-306">`RenderFragment<T>`— Это фрагмент разметки Razor, принимающий параметр, который может быть указан при подготовке к просмотру фрагмента прорисовки.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-306">A `RenderFragment<T>` is a chunk of Razor markup that takes a parameter that can be specified when the render fragment is rendered.</span></span>

### <a name="child-content"></a><span data-ttu-id="0ec0c-307">Дочернее содержимое</span><span class="sxs-lookup"><span data-stu-id="0ec0c-307">Child content</span></span>

<span data-ttu-id="0ec0c-308">Blazor компоненты могут записывать свое дочернее содержимое в виде `RenderFragment` и подготавливать содержимое в процессе подготовки к просмотру компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-308">Blazor components can capture their child content as a `RenderFragment` and render that content as part of the component rendering.</span></span> <span data-ttu-id="0ec0c-309">Чтобы записать дочернее содержимое, определите параметр компонента типа `RenderFragment` и присвойте ему имя `ChildContent` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-309">To capture child content, define a component parameter of type `RenderFragment` and name it `ChildContent`.</span></span>

<span data-ttu-id="0ec0c-310">*Чилдконтенткомпонент. Razor*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-310">*ChildContentComponent.razor*</span></span>

```razor
<h1>Component with child content</h1>

<div>@ChildContent</div>

@code {
    [Parameter]
    public RenderFragment ChildContent { get; set; }
}
```

<span data-ttu-id="0ec0c-311">После этого родительский компонент может предоставить дочернее содержимое, используя обычные синтаксис Razor.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-311">A parent component can then supply child content using normal Razor syntax.</span></span>

```razor
<ChildContentComponent>
    <ChildContent>
        <p>The time is @DateTime.Now</p>
    </ChildContent>
</ChildContentComponent>
```

### <a name="template-parameters"></a><span data-ttu-id="0ec0c-312">Параметры шаблона</span><span class="sxs-lookup"><span data-stu-id="0ec0c-312">Template parameters</span></span>

<span data-ttu-id="0ec0c-313">Компонент с шаблоном Blazor может также определять несколько параметров компонента типа `RenderFragment` или `RenderFragment<T>` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-313">A templated Blazor component can also define multiple component parameters of type `RenderFragment` or `RenderFragment<T>`.</span></span> <span data-ttu-id="0ec0c-314">Параметр для `RenderFragment<T>` можно указать при вызове.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-314">The parameter for a `RenderFragment<T>` can be specified when it's invoked.</span></span> <span data-ttu-id="0ec0c-315">Чтобы указать параметр универсального типа для компонента, используйте `@typeparam` директиву Razor.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-315">To specify a generic type parameter for a component, use the `@typeparam` Razor directive.</span></span>

<span data-ttu-id="0ec0c-316">*Симплелиствиев. Razor*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-316">*SimpleListView.razor*</span></span>

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

<span data-ttu-id="0ec0c-317">При использовании компонента шаблона можно указать параметры шаблона с помощью дочерних элементов, соответствующих именам параметров.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-317">When using a templated component, the template parameters can be specified using child elements that match the names of the parameters.</span></span> <span data-ttu-id="0ec0c-318">Аргументы компонента типа, `RenderFragment<T>` переданные как элементы, имеют неявный параметр с именем `context` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-318">Component arguments of type `RenderFragment<T>` passed as elements have an implicit parameter named `context`.</span></span> <span data-ttu-id="0ec0c-319">Имя этого параметра реализации можно изменить с помощью `Context` атрибута в дочернем элементе.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-319">You can change the name of this implement parameter using the `Context` attribute on the child element.</span></span> <span data-ttu-id="0ec0c-320">Любые параметры универсального типа можно указать с помощью атрибута, совпадающего с именем параметра типа.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-320">Any generic type parameters can be specified using an attribute that matches the name of the type parameter.</span></span> <span data-ttu-id="0ec0c-321">Параметр типа будет выведен, если это возможно:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-321">The type parameter will be inferred if possible:</span></span>

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

<span data-ttu-id="0ec0c-322">Выходные данные этого компонента выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="0ec0c-322">The output of this component looks like this:</span></span>

```html
<h1>My list</h1>
<ul>
    <li><p>The message is: message1</p></li>
    <li><p>The message is: message2</p></li>
<ul>
```

## <a name="code-behind"></a><span data-ttu-id="0ec0c-323">Файл с кодом программной части</span><span class="sxs-lookup"><span data-stu-id="0ec0c-323">Code-behind</span></span>

<span data-ttu-id="0ec0c-324">BlazorКомпонент обычно создается в одном файле *Razor* .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-324">A Blazor component is typically authored in a single *.razor* file.</span></span> <span data-ttu-id="0ec0c-325">Однако можно разделить код и разметку с помощью файла кода программной части.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-325">However, it's also possible to separate the code and markup using a code-behind file.</span></span> <span data-ttu-id="0ec0c-326">Чтобы использовать файл компонента, добавьте файл C#, соответствующий имени файла компонента, но с добавленным расширением *CS* (*Counter.Razor.CS*).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-326">To use a component file, add a C# file that matches the file name of the component file but with a *.cs* extension added (*Counter.razor.cs*).</span></span> <span data-ttu-id="0ec0c-327">Используйте файл C#, чтобы определить базовый класс для компонента.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-327">Use the C# file to define a base class for the component.</span></span> <span data-ttu-id="0ec0c-328">Можно присвоить имя базовому классу все, что вам нужно, но обычно имя класса является таким же, как и класс Component, но с `Base` добавленным расширением ( `CounterBase` ).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-328">You can name the base class anything you'd like, but it's common to name the class the same as the component class, but with a `Base` extension added (`CounterBase`).</span></span> <span data-ttu-id="0ec0c-329">Класс на основе компонентов также должен быть производным от `ComponentBase` .</span><span class="sxs-lookup"><span data-stu-id="0ec0c-329">The component-based class must also derive from `ComponentBase`.</span></span> <span data-ttu-id="0ec0c-330">Затем в файле компонента Razor добавьте `@inherits` директиву, чтобы указать базовый класс для компонента ( `@inherits CounterBase` ).</span><span class="sxs-lookup"><span data-stu-id="0ec0c-330">Then, in the Razor component file, add the `@inherits` directive to specify the base class for the component (`@inherits CounterBase`).</span></span>

<span data-ttu-id="0ec0c-331">*Счетчик. Razor*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-331">*Counter.razor*</span></span>

```razor
@inherits CounterBase

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button @onclick="IncrementCount">Click me</button>
```

<span data-ttu-id="0ec0c-332">*Counter.razor.cs*</span><span class="sxs-lookup"><span data-stu-id="0ec0c-332">*Counter.razor.cs*</span></span>

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

<span data-ttu-id="0ec0c-333">Видимость членов компонента в базовом классе должна быть `protected` или `public` видима для класса Component.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-333">The visibility of the component's members in the base class must be `protected` or `public` to be visible to the component class.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0ec0c-334">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="0ec0c-334">Additional resources</span></span>

<span data-ttu-id="0ec0c-335">Приведенная выше функция не является исчерпывающей облечения всех аспектов Blazor компонентов.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-335">The preceding isn't an exhaustive treatment of all aspects of Blazor components.</span></span> <span data-ttu-id="0ec0c-336">Дополнительные сведения о [создании и использовании ASP.NET Core компонентов Razor](/aspnet/core/blazor/components)см Blazor . в документации.</span><span class="sxs-lookup"><span data-stu-id="0ec0c-336">For more information on how to [Create and use ASP.NET Core Razor components](/aspnet/core/blazor/components), see the Blazor documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0ec0c-337">[Назад](app-startup.md)
>[Вперед](pages-routing-layouts.md)</span><span class="sxs-lookup"><span data-stu-id="0ec0c-337">[Previous](app-startup.md)
[Next](pages-routing-layouts.md)</span></span>
