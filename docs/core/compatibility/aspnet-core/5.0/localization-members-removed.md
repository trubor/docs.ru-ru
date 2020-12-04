---
title: Критическое изменение. Локализация. Удален класс ResourceManagerWithCultureStringLocalizer и элемент интерфейса WithCulture
description: Сведения о критическом изменении в ASP.NET Core 5.0 — локализация. Удален класс ResourceManagerWithCultureStringLocalizer и элемент интерфейса WithCulture
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: cba8458f20bad77ad6c125448f192939387ba405
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759937"
---
# <a name="localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed"></a><span data-ttu-id="69412-103">Локализация. Удален класс ResourceManagerWithCultureStringLocalizer и элемент интерфейса WithCulture</span><span class="sxs-lookup"><span data-stu-id="69412-103">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>

<span data-ttu-id="69412-104">Класс [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) и метод [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) удалены в .NET 5.0, предварительная версия 1.</span><span class="sxs-lookup"><span data-stu-id="69412-104">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were removed in .NET 5.0 Preview 1.</span></span>

<span data-ttu-id="69412-105">Контекст см. в разделах [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) и [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span><span class="sxs-lookup"><span data-stu-id="69412-105">For context, see [aspnet/Announcements#346](https://github.com/aspnet/Announcements/issues/346) and [dotnet/aspnetcore#3324](https://github.com/dotnet/aspnetcore/issues/3324).</span></span> <span data-ttu-id="69412-106">Обсуждение этого изменения см. на странице [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span><span class="sxs-lookup"><span data-stu-id="69412-106">For discussion on this change, see [dotnet/aspnetcore#7756](https://github.com/dotnet/aspnetcore/issues/7756).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="69412-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="69412-107">Version introduced</span></span>

<span data-ttu-id="69412-108">5.0 Предварительная версия 1</span><span class="sxs-lookup"><span data-stu-id="69412-108">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="69412-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="69412-109">Old behavior</span></span>

<span data-ttu-id="69412-110">Класс `ResourceManagerWithCultureStringLocalizer` и метод `ResourceManagerStringLocalizer.WithCulture` являются [устаревшими в .NET Core 3.0, предварительная версия 3, и более поздних версиях](../../../../core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span><span class="sxs-lookup"><span data-stu-id="69412-110">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method are [obsolete in .NET Core 3.0 Preview 3 and later](../../../../core/compatibility/2.2-3.0.md#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="69412-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="69412-111">New behavior</span></span>

<span data-ttu-id="69412-112">Класс `ResourceManagerWithCultureStringLocalizer` и метод `ResourceManagerStringLocalizer.WithCulture` были удалены в .NET 5.0, предварительная версия 1.</span><span class="sxs-lookup"><span data-stu-id="69412-112">The `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method have been removed in .NET 5.0 Preview 1.</span></span> <span data-ttu-id="69412-113">Сведения о внесенных изменениях см. в запросе на вытягивание [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span><span class="sxs-lookup"><span data-stu-id="69412-113">For an inventory of the changes made, see the pull request at [dotnet/extensions#2562](https://github.com/dotnet/extensions/pull/2562/files).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="69412-114">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="69412-114">Reason for change</span></span>

<span data-ttu-id="69412-115">Класс [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) и метод [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) часто создают путаницу для пользователей локализации.</span><span class="sxs-lookup"><span data-stu-id="69412-115">The [ResourceManagerWithCultureStringLocalizer](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1) class and [ResourceManagerStringLocalizer.WithCulture](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1) method were often sources of confusion for users of localization.</span></span> <span data-ttu-id="69412-116">Особенно это проявляется при создании пользовательской реализации <xref:Microsoft.Extensions.Localization.IStringLocalizer>.</span><span class="sxs-lookup"><span data-stu-id="69412-116">The confusion was especially high when creating a custom <xref:Microsoft.Extensions.Localization.IStringLocalizer> implementation.</span></span> <span data-ttu-id="69412-117">Этот класс и метод создают ощущение, что экземпляр `IStringLocalizer` должен существовать для каждого языка и ресурса.</span><span class="sxs-lookup"><span data-stu-id="69412-117">This class and method give consumers the impression that an `IStringLocalizer` instance is expected to be "per-language, per-resource".</span></span> <span data-ttu-id="69412-118">На самом деле экземпляры различаются только для ресурсов.</span><span class="sxs-lookup"><span data-stu-id="69412-118">In reality, the instance should only be "per-resource".</span></span> <span data-ttu-id="69412-119">Во время выполнения свойство <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> определяет используемый язык.</span><span class="sxs-lookup"><span data-stu-id="69412-119">At run time, the <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> property determines the language to be used.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="69412-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="69412-120">Recommended action</span></span>

<span data-ttu-id="69412-121">Прекратите использовать класс `ResourceManagerWithCultureStringLocalizer` и метод `ResourceManagerStringLocalizer.WithCulture`.</span><span class="sxs-lookup"><span data-stu-id="69412-121">Stop using the `ResourceManagerWithCultureStringLocalizer` class and the `ResourceManagerStringLocalizer.WithCulture` method.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="69412-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="69412-122">Affected APIs</span></span>

- [<span data-ttu-id="69412-123">ResourceManagerWithCultureStringLocalizer</span><span class="sxs-lookup"><span data-stu-id="69412-123">ResourceManagerWithCultureStringLocalizer</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerwithculturestringlocalizer?view=dotnet-plat-ext-3.1)
- [<span data-ttu-id="69412-124">ResourceManagerStringLocalizer.WithCulture</span><span class="sxs-lookup"><span data-stu-id="69412-124">ResourceManagerStringLocalizer.WithCulture</span></span>](/dotnet/api/microsoft.extensions.localization.resourcemanagerstringlocalizer.withculture?view=dotnet-plat-ext-3.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->
