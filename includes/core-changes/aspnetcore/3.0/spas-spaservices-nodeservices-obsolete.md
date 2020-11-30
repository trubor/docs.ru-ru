---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032899"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="41a11-101">Одностраничные приложения. SpaServices и NodeServices отмечены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="41a11-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="41a11-102">Содержимое указанных ниже пакетов NuGet стало полностью ненужным, начиная с версии ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="41a11-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="41a11-103">Поэтому они отмечены как устаревшие:</span><span class="sxs-lookup"><span data-stu-id="41a11-103">Consequently, the following packages are being marked as obsolete:</span></span>

- <span data-ttu-id="41a11-104">[Microsoft.AspNetCore.SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/);</span><span class="sxs-lookup"><span data-stu-id="41a11-104">[Microsoft.AspNetCore.SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)</span></span>
- <span data-ttu-id="41a11-105">[Microsoft.AspNetCore.NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/).</span><span class="sxs-lookup"><span data-stu-id="41a11-105">[Microsoft.AspNetCore.NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)</span></span>

<span data-ttu-id="41a11-106">По той же причине следующие модули npm отмечены как нерекомендуемые:</span><span class="sxs-lookup"><span data-stu-id="41a11-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- <span data-ttu-id="41a11-107">[aspnet-angular](https://www.npmjs.com/package/aspnet-angular);</span><span class="sxs-lookup"><span data-stu-id="41a11-107">[aspnet-angular](https://www.npmjs.com/package/aspnet-angular)</span></span>
- <span data-ttu-id="41a11-108">[aspnet-prerendering](https://www.npmjs.com/package/aspnet-prerendering);</span><span class="sxs-lookup"><span data-stu-id="41a11-108">[aspnet-prerendering](https://www.npmjs.com/package/aspnet-prerendering)</span></span>
- <span data-ttu-id="41a11-109">[aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack);</span><span class="sxs-lookup"><span data-stu-id="41a11-109">[aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)</span></span>
- <span data-ttu-id="41a11-110">[aspnet-webpack-react](https://www.npmjs.com/package/aspnet-webpack-react);</span><span class="sxs-lookup"><span data-stu-id="41a11-110">[aspnet-webpack-react](https://www.npmjs.com/package/aspnet-webpack-react)</span></span>
- <span data-ttu-id="41a11-111">[domain-task](https://www.npmjs.com/package/domain-task).</span><span class="sxs-lookup"><span data-stu-id="41a11-111">[domain-task](https://www.npmjs.com/package/domain-task)</span></span>

<span data-ttu-id="41a11-112">Все указанные выше пакеты и модули npm будут удалены в версии .NET 5.</span><span class="sxs-lookup"><span data-stu-id="41a11-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="41a11-113">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="41a11-113">Version introduced</span></span>

<span data-ttu-id="41a11-114">3.0</span><span class="sxs-lookup"><span data-stu-id="41a11-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="41a11-115">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="41a11-115">Old behavior</span></span>

<span data-ttu-id="41a11-116">Нерекомендуемые пакеты и модули NPM предназначались для интеграции ASP.NET Core с разными платформами одностраничных приложений (SPA).</span><span class="sxs-lookup"><span data-stu-id="41a11-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="41a11-117">К ним относятся Angular, React и React с Redux.</span><span class="sxs-lookup"><span data-stu-id="41a11-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="41a11-118">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="41a11-118">New behavior</span></span>

<span data-ttu-id="41a11-119">В пакете NuGet [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) реализован новый механизм интеграции.</span><span class="sxs-lookup"><span data-stu-id="41a11-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="41a11-120">Этот пакет остается основой для шаблонов проектов Angular и React, начиная с ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="41a11-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="41a11-121">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="41a11-121">Reason for change</span></span>

<span data-ttu-id="41a11-122">ASP.NET Core поддерживает интеграцию с несколькими платформами одностраничных приложений (SPA), включая Angular, React и React с Redux.</span><span class="sxs-lookup"><span data-stu-id="41a11-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="41a11-123">Изначально интеграция с этими платформами устанавливалась с помощью специальных компонентов ASP.NET Core, которые обрабатывали такие сценарии, как предварительная визуализация на стороне сервера и интеграция с пакетом Webpack.</span><span class="sxs-lookup"><span data-stu-id="41a11-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="41a11-124">Но отраслевые стандарты постепенно изменились.</span><span class="sxs-lookup"><span data-stu-id="41a11-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="41a11-125">На каждой из этих платформ SPA подготовлены собственные стандартные интерфейсы командной строки.</span><span class="sxs-lookup"><span data-stu-id="41a11-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="41a11-126">Например, Angular CLI и create-react-app.</span><span class="sxs-lookup"><span data-stu-id="41a11-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="41a11-127">При выпуске ASP.NET Core 2.1 в мае 2018 года наши разработчики внесли обновления в соответствии с этим изменением стандартов.</span><span class="sxs-lookup"><span data-stu-id="41a11-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="41a11-128">Мы предоставили новый и более простой способ для интеграции с цепочками инструментов разных платформ SPA.</span><span class="sxs-lookup"><span data-stu-id="41a11-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="41a11-129">Новый механизм интеграции реализован в пакете `Microsoft.AspNetCore.SpaServices.Extensions` и стал основой для шаблонов проектов Angular и React, начиная с ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="41a11-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="41a11-130">Чтобы не оставалось сомнений, что старые специальные компоненты ASP.NET Core стали не нужны и их использование не рекомендуется, внесены следующие изменения:</span><span class="sxs-lookup"><span data-stu-id="41a11-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="41a11-131">механизм интеграции, существовавший до версии 2.1, отмечен как устаревший;</span><span class="sxs-lookup"><span data-stu-id="41a11-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="41a11-132">вспомогательные пакеты npm отмечены как нерекомендуемые.</span><span class="sxs-lookup"><span data-stu-id="41a11-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="41a11-133">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="41a11-133">Recommended action</span></span>

<span data-ttu-id="41a11-134">Если вы применяете эти пакеты, обновите приложения, чтобы они использовали следующие функции:</span><span class="sxs-lookup"><span data-stu-id="41a11-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="41a11-135">содержащиеся в пакете `Microsoft.AspNetCore.SpaServices.Extensions`;</span><span class="sxs-lookup"><span data-stu-id="41a11-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="41a11-136">предоставленные той платформой SPA, которую вы используете.</span><span class="sxs-lookup"><span data-stu-id="41a11-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="41a11-137">Чтобы поддерживать такие функции, как предварительная визуализация на стороне сервера и горячая перезагрузка модулей, изучите документацию по соответствующей платформе SPA.</span><span class="sxs-lookup"><span data-stu-id="41a11-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="41a11-138">Функциональность `Microsoft.AspNetCore.SpaServices.Extensions`*не* считается устаревшей и будет поддерживаться далее.</span><span class="sxs-lookup"><span data-stu-id="41a11-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="41a11-139">Категория</span><span class="sxs-lookup"><span data-stu-id="41a11-139">Category</span></span>

<span data-ttu-id="41a11-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="41a11-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="41a11-141">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="41a11-141">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
