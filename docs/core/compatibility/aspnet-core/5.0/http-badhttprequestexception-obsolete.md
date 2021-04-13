---
title: Критическое изменение. HTTP. Типы Kestrel и IIS BadHttpRequestException, помеченные как устаревшие и замененные
description: Сведения о критическом изменении в ASP.NET Core 5.0 — HTTP. Типы Kestrel и IIS BadHttpRequestException, помеченные как устаревшие и замененные
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5837018def634b732b4f273f1a794267f4d17972
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498143"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="9407a-103">HTTP. Типы Kestrel и IIS BadHttpRequestException, помеченные как устаревшие и замененные</span><span class="sxs-lookup"><span data-stu-id="9407a-103">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="9407a-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` были помечены как устаревшие и изменены, чтобы быть производными от `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span><span class="sxs-lookup"><span data-stu-id="9407a-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="9407a-105">Серверы Kestrel и IIS по-прежнему выдают старые типы исключений для обеспечения обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="9407a-105">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="9407a-106">Устаревшие типы будут удалены в будущем выпуске.</span><span class="sxs-lookup"><span data-stu-id="9407a-106">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="9407a-107">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="9407a-107">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9407a-108">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="9407a-108">Version introduced</span></span>

<span data-ttu-id="9407a-109">5.0, предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="9407a-109">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="9407a-110">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="9407a-110">Old behavior</span></span>

<span data-ttu-id="9407a-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` являются производными от <xref:System.IO.IOException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9407a-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="9407a-112">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="9407a-112">New behavior</span></span>

<span data-ttu-id="9407a-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` являются устаревшими.</span><span class="sxs-lookup"><span data-stu-id="9407a-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="9407a-114">Типы являются производными от `Microsoft.AspNetCore.Http.BadHttpRequestException`, который является производным от `System.IO.IOException`.</span><span class="sxs-lookup"><span data-stu-id="9407a-114">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9407a-115">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="9407a-115">Reason for change</span></span>

<span data-ttu-id="9407a-116">Изменение было внесено в следующих целях:</span><span class="sxs-lookup"><span data-stu-id="9407a-116">The change was made to:</span></span>

* <span data-ttu-id="9407a-117">Консолидация повторяющихся типов.</span><span class="sxs-lookup"><span data-stu-id="9407a-117">Consolidate duplicate types.</span></span>
* <span data-ttu-id="9407a-118">Унификация поведения различных серверных реализаций.</span><span class="sxs-lookup"><span data-stu-id="9407a-118">Unify behavior across server implementations.</span></span>

<span data-ttu-id="9407a-119">Теперь приложение может перехватывать базовое исключение `Microsoft.AspNetCore.Http.BadHttpRequestException` при использовании Kestrel или IIS.</span><span class="sxs-lookup"><span data-stu-id="9407a-119">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9407a-120">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="9407a-120">Recommended action</span></span>

<span data-ttu-id="9407a-121">Замените `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` и `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` на `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span><span class="sxs-lookup"><span data-stu-id="9407a-121">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9407a-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="9407a-122">Affected APIs</span></span>

- [<span data-ttu-id="9407a-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="9407a-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="9407a-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="9407a-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
