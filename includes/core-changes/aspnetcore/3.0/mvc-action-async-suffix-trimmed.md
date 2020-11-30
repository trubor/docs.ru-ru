---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032825"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a><span data-ttu-id="00bd0-101">MVC. Асинхронный суффикс получается усечением имен действий контроллера</span><span class="sxs-lookup"><span data-stu-id="00bd0-101">MVC: Async suffix trimmed from controller action names</span></span>

<span data-ttu-id="00bd0-102">В системе адресации [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849) ASP.NET Core MVC по умолчанию обрезает суффиксы `Async` в именах действий.</span><span class="sxs-lookup"><span data-stu-id="00bd0-102">As part of addressing [dotnet/aspnetcore#4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core MVC trims the suffix `Async` from action names by default.</span></span> <span data-ttu-id="00bd0-103">Начиная с ASP.NET Core 3,0, это изменение влияет на процессы маршрутизации и создания ссылок.</span><span class="sxs-lookup"><span data-stu-id="00bd0-103">Starting with ASP.NET Core 3.0, this change affects both routing and link generation.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="00bd0-104">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="00bd0-104">Version introduced</span></span>

<span data-ttu-id="00bd0-105">3.0</span><span class="sxs-lookup"><span data-stu-id="00bd0-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="00bd0-106">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="00bd0-106">Old behavior</span></span>

<span data-ttu-id="00bd0-107">Рассмотрим следующий контроллер ASP.NET Core MVC:</span><span class="sxs-lookup"><span data-stu-id="00bd0-107">Consider the following ASP.NET Core MVC controller:</span></span>

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

<span data-ttu-id="00bd0-108">Действие маршрутизируется через `Product/ListAsync`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-108">The action is routable via `Product/ListAsync`.</span></span> <span data-ttu-id="00bd0-109">Для создания ссылки необходимо указать суффикс `Async`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-109">Link generation requires specifying the `Async` suffix.</span></span> <span data-ttu-id="00bd0-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="00bd0-110">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a><span data-ttu-id="00bd0-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="00bd0-111">New behavior</span></span>

<span data-ttu-id="00bd0-112">В ASP.NET Core 3,0 это действие маршрутизируется через `Product/List`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-112">In ASP.NET Core 3.0, the action is routable via `Product/List`.</span></span> <span data-ttu-id="00bd0-113">В коде создания ссылок следует опускать суффикс `Async`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-113">Link generation code should omit the `Async` suffix.</span></span> <span data-ttu-id="00bd0-114">Пример:</span><span class="sxs-lookup"><span data-stu-id="00bd0-114">For example:</span></span>

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

<span data-ttu-id="00bd0-115">Это изменение не влияет на имена, указанные с атрибутом `[ActionName]`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-115">This change doesn't affect names specified using the `[ActionName]` attribute.</span></span> <span data-ttu-id="00bd0-116">Это поведение можно отключить, присвоив свойству `MvcOptions.SuppressAsyncSuffixInActionNames` значение `false` в `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="00bd0-116">The new behavior can be disabled by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a><span data-ttu-id="00bd0-117">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="00bd0-117">Reason for change</span></span>

<span data-ttu-id="00bd0-118">По соглашению асинхронные методы .NET получают суффиксы `Async`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-118">By convention, asynchronous .NET methods are suffixed with `Async`.</span></span> <span data-ttu-id="00bd0-119">Но если метод определяет действие MVC, нежелательно использовать суффикс `Async`.</span><span class="sxs-lookup"><span data-stu-id="00bd0-119">However, when a method defines an MVC action, it's undesirable to use the `Async` suffix.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="00bd0-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="00bd0-120">Recommended action</span></span>

<span data-ttu-id="00bd0-121">Если приложение зависит от того, сохранит ли действие MVC суффикс имени `Async`, выберите один из следующих способов устранения рисков:</span><span class="sxs-lookup"><span data-stu-id="00bd0-121">If your app depends on MVC actions preserving the name's `Async` suffix, choose one of the following mitigations:</span></span>

- <span data-ttu-id="00bd0-122">примените атрибут `[ActionName]`, чтобы сохранить исходное имя;</span><span class="sxs-lookup"><span data-stu-id="00bd0-122">Use the `[ActionName]` attribute to preserve the original name.</span></span>
- <span data-ttu-id="00bd0-123">полностью отключите переименование, задав для `MvcOptions.SuppressAsyncSuffixInActionNames` значение `false` в `Startup.ConfigureServices`:</span><span class="sxs-lookup"><span data-stu-id="00bd0-123">Disable the renaming entirely by setting `MvcOptions.SuppressAsyncSuffixInActionNames` to `false` in `Startup.ConfigureServices`:</span></span>

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a><span data-ttu-id="00bd0-124">Категория</span><span class="sxs-lookup"><span data-stu-id="00bd0-124">Category</span></span>

<span data-ttu-id="00bd0-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="00bd0-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00bd0-126">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="00bd0-126">Affected APIs</span></span>

<span data-ttu-id="00bd0-127">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="00bd0-127">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
