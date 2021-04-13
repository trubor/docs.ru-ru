---
title: 'Критическое изменение. Blazor: Функция ProtectedBrowserStorage перемещена на общую платформу'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Функция ProtectedBrowserStorage перемещена на общую платформу
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 36ba6c16ac970aa8acb0d0faab42b151addae888
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497844"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="8c209-103">Blazor: Функция ProtectedBrowserStorage перемещена на общую платформу</span><span class="sxs-lookup"><span data-stu-id="8c209-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="8c209-104">В ASP.NET Core 5.0 RC2 функция `ProtectedBrowserStorage` перемещена в общую платформу ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c209-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8c209-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8c209-105">Version introduced</span></span>

<span data-ttu-id="8c209-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="8c209-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="8c209-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="8c209-107">Old behavior</span></span>

<span data-ttu-id="8c209-108">В ASP.NET Core 5.0 предварительной версии 8 эта функция доступна в составе пакета [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions), но ее можно использовать только в Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="8c209-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="8c209-109">В ASP.NET Core 5.0 RC1 эта функция доступна как часть пакета [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage), который ссылается на общую платформу `Microsoft.AspNetCore.App`.</span><span class="sxs-lookup"><span data-stu-id="8c209-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="8c209-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="8c209-110">New behavior</span></span>

<span data-ttu-id="8c209-111">В ASP.NET Core 5.0 RC2 ссылка на пакет NuGet больше не требуется для обращения к этой функции и ее использования.</span><span class="sxs-lookup"><span data-stu-id="8c209-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8c209-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="8c209-112">Reason for change</span></span>

<span data-ttu-id="8c209-113">Переход на общую платформу больше соответствует ожиданиям клиентов.</span><span class="sxs-lookup"><span data-stu-id="8c209-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8c209-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8c209-114">Recommended action</span></span>

<span data-ttu-id="8c209-115">При обновлении с ASP.NET Core 5.0 RC1 выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8c209-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="8c209-116">удалите ссылку на пакет `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` из проекта;</span><span class="sxs-lookup"><span data-stu-id="8c209-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="8c209-117">Замените `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` на `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span><span class="sxs-lookup"><span data-stu-id="8c209-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="8c209-118">удалите вызов `AddProtectedBrowserStorage` из класса `Startup`.</span><span class="sxs-lookup"><span data-stu-id="8c209-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="8c209-119">При обновлении с ASP.NET Core 5.0 предварительной версии 8 выполните следующие действия:</span><span class="sxs-lookup"><span data-stu-id="8c209-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="8c209-120">удалите ссылку на пакет `Microsoft.AspNetCore.Components.Web.Extensions` из проекта;</span><span class="sxs-lookup"><span data-stu-id="8c209-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="8c209-121">Замените `using Microsoft.AspNetCore.Components.Web.Extensions;` на `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span><span class="sxs-lookup"><span data-stu-id="8c209-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="8c209-122">удалите вызов `AddProtectedBrowserStorage` из класса `Startup`.</span><span class="sxs-lookup"><span data-stu-id="8c209-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8c209-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8c209-123">Affected APIs</span></span>

<span data-ttu-id="8c209-124">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="8c209-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
