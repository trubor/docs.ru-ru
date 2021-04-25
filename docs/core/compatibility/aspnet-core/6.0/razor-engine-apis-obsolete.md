---
title: 'Критическое изменение. Razor: API-интерфейсы RazorEngine помечены как устаревшие'
description: 'Сведения о критическом изменении в ASP.NET Core 6.0. Razor: API-интерфейсы RazorEngine помечены как устаревшие'
no-loc:
- Razor
ms.author: scaddie
ms.date: 02/09/2021
ms.openlocfilehash: 75ccc8e2640dda29749de40946e90c2b897a7245
ms.sourcegitcommit: fdfa01f6cd3aa4c36b6e8a1830693ff22d35aeea
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/13/2021
ms.locfileid: "107292253"
---
# <a name="razor-razorengine-apis-marked-obsolete"></a><span data-ttu-id="452bf-103">Razor: API-интерфейсы RazorEngine помечены как устаревшие</span><span class="sxs-lookup"><span data-stu-id="452bf-103">Razor: RazorEngine APIs marked obsolete</span></span>

<span data-ttu-id="452bf-104">Типы, связанные с типом <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> в Blazor, помечены как устаревшие.</span><span class="sxs-lookup"><span data-stu-id="452bf-104">Types related to the <xref:Microsoft.AspNetCore.Razor.Language.RazorEngine> type in Blazor have been marked as obsolete.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="452bf-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="452bf-105">Version introduced</span></span>

<span data-ttu-id="452bf-106">ASP.NET Core 6.0 (предварительная версия 1)</span><span class="sxs-lookup"><span data-stu-id="452bf-106">ASP.NET Core 6.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="452bf-107">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="452bf-107">Old behavior</span></span>

<span data-ttu-id="452bf-108">Интерфейсы API `RazorEngine` не являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="452bf-108">The `RazorEngine` APIs aren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="452bf-109">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="452bf-109">New behavior</span></span>

<span data-ttu-id="452bf-110">API `RazorEngine` являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="452bf-110">The `RazorEngine` APIs are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="452bf-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="452bf-111">Reason for change</span></span>

<span data-ttu-id="452bf-112">Вместо типа `RazorEngine` теперь следует использовать тип <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine>.</span><span class="sxs-lookup"><span data-stu-id="452bf-112">The `RazorEngine` type has been deprecated in favor of the <xref:Microsoft.AspNetCore.Razor.Language.RazorProjectEngine> type.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="452bf-113">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="452bf-113">Recommended action</span></span>

<span data-ttu-id="452bf-114">Перенос исходного кода из типа `RazorEngine` в тип `RazorProjectEngine`.</span><span class="sxs-lookup"><span data-stu-id="452bf-114">Migrate source code from the `RazorEngine` type to the `RazorProjectEngine` type.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="452bf-115">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="452bf-115">Affected APIs</span></span>

- `Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- [<span data-ttu-id="452bf-116">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span><span class="sxs-lookup"><span data-stu-id="452bf-116">Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.functionsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="452bf-117">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span><span class="sxs-lookup"><span data-stu-id="452bf-117">Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.inheritsdirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="452bf-118">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span><span class="sxs-lookup"><span data-stu-id="452bf-118">Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.extensions.sectiondirective.register?view=aspnetcore-3.0&preserve-view=true)
- [<span data-ttu-id="452bf-119">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span><span class="sxs-lookup"><span data-stu-id="452bf-119">Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder</span></span>](/dotnet/api/microsoft.aspnetcore.razor.language.irazorenginebuilder?view=aspnetcore-3.0&preserve-view=true)

<!--

## Category

ASP.NET Core

## Affected APIs

- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.InjectDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.ModelDirective.Register`
- `Overload:Microsoft.AspNetCore.Mvc.Razor.Extensions.PageDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.FunctionsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.InheritsDirective.Register`
- `Overload:Microsoft.AspNetCore.Razor.Language.Extensions.SectionDirective.Register`
- `T:Microsoft.AspNetCore.Razor.Language.IRazorEngineBuilder`

-->
