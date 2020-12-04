---
title: 'Критическое изменение. Blazor: Обновлен список поддерживаемых веб-браузеров'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Обновлен список поддерживаемых веб-браузеров
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 63b35aa8cb73bfb82c565007704375bac3737299
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759988"
---
# <a name="blazor-updated-browser-support"></a><span data-ttu-id="7ec2f-103">Blazor: Обновлен список поддерживаемых веб-браузеров</span><span class="sxs-lookup"><span data-stu-id="7ec2f-103">Blazor: Updated browser support</span></span>

<span data-ttu-id="7ec2f-104">В ASP.NET Core 5.0 появились [новые функции Blazor](https://github.com/dotnet/aspnetcore/issues/21514), некоторые из которых несовместимы со старыми браузерами.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-104">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="7ec2f-105">Список браузеров, поддерживаемых Blazor в ASP.NET Core 5.0, обновлен соответствующим образом.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-105">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="7ec2f-106">Обсуждение этого вопроса см. на странице GitHub [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span><span class="sxs-lookup"><span data-stu-id="7ec2f-106">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7ec2f-107">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7ec2f-107">Version introduced</span></span>

<span data-ttu-id="7ec2f-108">5.0</span><span class="sxs-lookup"><span data-stu-id="7ec2f-108">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7ec2f-109">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="7ec2f-109">Old behavior</span></span>

<span data-ttu-id="7ec2f-110">Blazor Server поддерживает Microsoft Internet Explorer 11 с достаточным количеством заполнений.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-110">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="7ec2f-111">Blazor Server и Blazor WebAssembly также работают в [устаревшей версии Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span><span class="sxs-lookup"><span data-stu-id="7ec2f-111">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="7ec2f-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="7ec2f-112">New behavior</span></span>

<span data-ttu-id="7ec2f-113">Blazor Server в ASP.NET Core 5.0 не поддерживается в Microsoft Internet Explorer 11.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-113">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="7ec2f-114">Blazor Server и Blazor WebAssembly работают с ограниченной функциональностью в устаревшей версии Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-114">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7ec2f-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="7ec2f-115">Reason for change</span></span>

<span data-ttu-id="7ec2f-116">Новые функции Blazor в ASP.NET Core 5.0 несовместимы с этими старыми браузерами, кроме того, уровень их использования снижается.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-116">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="7ec2f-117">Дополнительные сведения см. в следующих ресурсах:</span><span class="sxs-lookup"><span data-stu-id="7ec2f-117">For more information, see the following resources:</span></span>

* [<span data-ttu-id="7ec2f-118">Поддержка Windows устаревшей версии Microsoft Edge также прекращается 9 марта 2021 г.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-118">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="7ec2f-119">Приложения и службы Microsoft 365 перестанут поддерживать Microsoft Internet Explorer 11 17 августа 2021 г.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-119">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a><span data-ttu-id="7ec2f-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7ec2f-120">Recommended action</span></span>

<span data-ttu-id="7ec2f-121">Обновите эти старые браузеры до [нового Microsoft Edge, основанного на Chromium](https://www.microsoft.com/edge).</span><span class="sxs-lookup"><span data-stu-id="7ec2f-121">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="7ec2f-122">Для приложений Blazor, которым требуется поддержка этих старых браузеров, используйте ASP.NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="7ec2f-122">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="7ec2f-123">Список поддерживаемых браузеров для Blazor в ASP.NET Core 3.1 не изменился и описан в разделе о [поддерживаемых платформах](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span><span class="sxs-lookup"><span data-stu-id="7ec2f-123">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7ec2f-124">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7ec2f-124">Affected APIs</span></span>

<span data-ttu-id="7ec2f-125">None</span><span class="sxs-lookup"><span data-stu-id="7ec2f-125">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
