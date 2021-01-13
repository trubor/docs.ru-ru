---
title: 'Критическое изменение. Blazor: Изменения в логике маршрутизации в приложениях Blazor'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Изменения в логике маршрутизации в приложениях Blazor
author: scottaddie
ms.author: scaddie
ms.date: 12/14/2020
ms.openlocfilehash: 4ab8289565c88b17eb204a11724bb12a09b033c2
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513511"
---
# <a name="blazor-route-precedence-logic-changed-in-blazor-apps"></a><span data-ttu-id="53228-103">Blazor: в приложениях изменена логика очередности маршрутов</span><span class="sxs-lookup"><span data-stu-id="53228-103">Blazor: Route precedence logic changed in Blazor apps</span></span>

<span data-ttu-id="53228-104">Ошибка в реализации маршрутизации Blazor влияет на порядок определения приоритета маршрутов.</span><span class="sxs-lookup"><span data-stu-id="53228-104">A bug in the Blazor routing implementation affected how the precedence of routes was determined.</span></span> <span data-ttu-id="53228-105">Эта ошибка влияет на все маршруты перехвата или маршруты с необязательными параметрами в приложении Blazor.</span><span class="sxs-lookup"><span data-stu-id="53228-105">This bug affects catch-all routes or routes with optional parameters within your Blazor app.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="53228-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="53228-106">Version introduced</span></span>

<span data-ttu-id="53228-107">5.0.1</span><span class="sxs-lookup"><span data-stu-id="53228-107">5.0.1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="53228-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="53228-108">Old behavior</span></span>

<span data-ttu-id="53228-109">При ошибочном поведении маршруты с более низким приоритетом рассматриваются и сопоставляются с маршрутами с более высоким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="53228-109">With the erroneous behavior, routes with lower precedence are considered and matched over routes with higher precedence.</span></span> <span data-ttu-id="53228-110">Например, маршрут `{*slug}` сопоставляется до `/customer/{id}`.</span><span class="sxs-lookup"><span data-stu-id="53228-110">For example, the `{*slug}` route is matched before `/customer/{id}`.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="53228-111">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="53228-111">New behavior</span></span>

<span data-ttu-id="53228-112">Текущее поведение более близко соответствует поведению маршрутизации, определенному в приложениях ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="53228-112">The current behavior more closely matches the routing behavior defined in ASP.NET Core apps.</span></span> <span data-ttu-id="53228-113">Платформа сначала определяет приоритет маршрута для каждого сегмента.</span><span class="sxs-lookup"><span data-stu-id="53228-113">The framework determines the route precedence for each segment first.</span></span> <span data-ttu-id="53228-114">Длина маршрута используется только в качестве второго критерия для разрыва связей.</span><span class="sxs-lookup"><span data-stu-id="53228-114">The route's length is used only as a second criteria to break ties.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="53228-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="53228-115">Reason for change</span></span>

<span data-ttu-id="53228-116">Исходное поведение считается ошибкой в реализации.</span><span class="sxs-lookup"><span data-stu-id="53228-116">The original behavior is considered a bug in the implementation.</span></span> <span data-ttu-id="53228-117">Система маршрутизации в приложениях Blazor должна вести себя так же, как и система маршрутизации в остальной части ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="53228-117">As a goal, the routing system in Blazor apps should behave the same way as the routing system in the rest of ASP.NET Core.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="53228-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="53228-118">Recommended action</span></span>

<span data-ttu-id="53228-119">При обновлении с предыдущих версий Blazor до версии 5.x используйте атрибут `PreferExactMatches` в компоненте `Router`.</span><span class="sxs-lookup"><span data-stu-id="53228-119">If upgrading from previous versions of Blazor to 5.x, use the `PreferExactMatches` attribute on the `Router` component.</span></span> <span data-ttu-id="53228-120">Этот атрибут можно использовать для выбора правильного поведения.</span><span class="sxs-lookup"><span data-stu-id="53228-120">This attribute can be used to opt into the correct behavior.</span></span> <span data-ttu-id="53228-121">Пример:</span><span class="sxs-lookup"><span data-stu-id="53228-121">For example:</span></span>

```razor
<Router AppAssembly="@typeof(Program).Assembly" PreferExactMatches="true">
```

<span data-ttu-id="53228-122">Если `PreferExactMatches` имеет значение `true`, то при сопоставлении маршрутов предпочтение отдается точным совпадениям, а не подстановочным знакам.</span><span class="sxs-lookup"><span data-stu-id="53228-122">When `PreferExactMatches` is set to `true`, route matching prefers exact matches over wildcards.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="53228-123">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="53228-123">Affected APIs</span></span>

<span data-ttu-id="53228-124">None</span><span class="sxs-lookup"><span data-stu-id="53228-124">None</span></span>

<!--

## Category

ASP.NET Core

## Affected APIs

Not detectable via API analysis

-->
