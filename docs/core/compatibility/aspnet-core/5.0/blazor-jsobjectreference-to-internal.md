---
title: 'Критическое изменение. Blazor: Типы JSObjectReference и JSInProcessObjectReference изменены на internal'
description: Сведения о критическом изменении в ASP.NET Core 5.0 — Blazor. Типы JSObjectReference и JSInProcessObjectReference изменены на internal
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 44e4c902ff22e18fa9ab8b484952082e5b81be94
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497857"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="a4791-103">Blazor: Типы JSObjectReference и JSInProcessObjectReference изменены на internal</span><span class="sxs-lookup"><span data-stu-id="a4791-103">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="a4791-104">Новые типы `Microsoft.JSInterop.JSObjectReference` и `Microsoft.JSInterop.JSInProcessObjectReference`, появившиеся в ASP.NET Core 5.0 RC1, помечены как `internal`.</span><span class="sxs-lookup"><span data-stu-id="a4791-104">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a4791-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a4791-105">Version introduced</span></span>

<span data-ttu-id="a4791-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="a4791-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a4791-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="a4791-107">Old behavior</span></span>

<span data-ttu-id="a4791-108">`JSObjectReference` можно получить из вызова взаимодействия JavaScript через `IJSRuntime`.</span><span class="sxs-lookup"><span data-stu-id="a4791-108">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="a4791-109">Пример:</span><span class="sxs-lookup"><span data-stu-id="a4791-109">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a><span data-ttu-id="a4791-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="a4791-110">New behavior</span></span>

<span data-ttu-id="a4791-111">`JSObjectReference` использует модификатор доступа [internal](../../../../csharp/language-reference/keywords/internal.md).</span><span class="sxs-lookup"><span data-stu-id="a4791-111">`JSObjectReference` uses the [internal](../../../../csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="a4791-112">Вместо этого необходимо использовать интерфейс `public` `IJSObjectReference`.</span><span class="sxs-lookup"><span data-stu-id="a4791-112">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="a4791-113">Пример:</span><span class="sxs-lookup"><span data-stu-id="a4791-113">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="a4791-114">`JSInProcessObjectReference` также помечен как `internal` и изменен на `IJSInProcessObjectReference`.</span><span class="sxs-lookup"><span data-stu-id="a4791-114">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a4791-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a4791-115">Reason for change</span></span>

<span data-ttu-id="a4791-116">Это изменение делает функцию взаимодействия JavaScript более совместимой с другими шаблонами в Blazor.</span><span class="sxs-lookup"><span data-stu-id="a4791-116">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="a4791-117">`IJSObjectReference` можно использовать как `IJSRuntime` в контексте назначения и методов и расширения.</span><span class="sxs-lookup"><span data-stu-id="a4791-117">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a4791-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a4791-118">Recommended action</span></span>

<span data-ttu-id="a4791-119">Измените вхождения `JSObjectReference` и `JSInProcessObjectReference` на `IJSObjectReference` и `IJSInProcessObjectReference`соответственно.</span><span class="sxs-lookup"><span data-stu-id="a4791-119">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a4791-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a4791-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
