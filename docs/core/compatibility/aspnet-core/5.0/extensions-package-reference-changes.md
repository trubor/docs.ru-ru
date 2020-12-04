---
title: Критическое изменение. Расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet
description: Сведения о критическом изменении в ASP.NET Core 5.0 — расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759726"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="e1d72-103">Расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet</span><span class="sxs-lookup"><span data-stu-id="e1d72-103">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="e1d72-104">При переносе некоторых пакетов NuGet `Microsoft.Extensions.*` из репозитория [dotnet/extensions](https://github.com/dotnet/extensions) в [dotnet/runtime](https://github.com/dotnet/runtime), как описано на странице [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), изменения в пакетах применяются к некоторым перенесенным пакетам.</span><span class="sxs-lookup"><span data-stu-id="e1d72-104">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="e1d72-105">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="e1d72-105">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e1d72-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e1d72-106">Version introduced</span></span>

<span data-ttu-id="e1d72-107">5.0, предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="e1d72-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="e1d72-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="e1d72-108">Old behavior</span></span>

<span data-ttu-id="e1d72-109">Некоторые пакеты `Microsoft.Extensions.*` включают ссылки на пакеты для API, использовавшиеся приложением.</span><span class="sxs-lookup"><span data-stu-id="e1d72-109">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="e1d72-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="e1d72-110">New behavior</span></span>

<span data-ttu-id="e1d72-111">Приложению может потребоваться добавить зависимости пакета `Microsoft.Extensions.*`.</span><span class="sxs-lookup"><span data-stu-id="e1d72-111">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e1d72-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="e1d72-112">Reason for change</span></span>

<span data-ttu-id="e1d72-113">Политики упаковки были обновлены для согласованности с репозиторием *dotnet/runtime*.</span><span class="sxs-lookup"><span data-stu-id="e1d72-113">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="e1d72-114">В новой политике неиспользуемые ссылки на пакеты удаляются из файлов *NUPKG* во время упаковки.</span><span class="sxs-lookup"><span data-stu-id="e1d72-114">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e1d72-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e1d72-115">Recommended action</span></span>

<span data-ttu-id="e1d72-116">Пользователи затронутых пакетов должны добавить прямую зависимость от удаленной зависимости пакета в своем проекте, если используются API из удаленной зависимости пакета.</span><span class="sxs-lookup"><span data-stu-id="e1d72-116">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="e1d72-117">В следующей таблице перечислены затронутые пакеты и соответствующие изменения.</span><span class="sxs-lookup"><span data-stu-id="e1d72-117">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="e1d72-118">Имя пакета</span><span class="sxs-lookup"><span data-stu-id="e1d72-118">Package name</span></span>|<span data-ttu-id="e1d72-119">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="e1d72-119">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="e1d72-120">Microsoft.Extensions.Configuration.Binder</span><span class="sxs-lookup"><span data-stu-id="e1d72-120">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="e1d72-121">Удалена ссылка на `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="e1d72-121">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="e1d72-122">Microsoft.Extensions.Configuration.Json</span><span class="sxs-lookup"><span data-stu-id="e1d72-122">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="e1d72-123">Удалена ссылка на `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="e1d72-123">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="e1d72-124">Microsoft.Extensions.Hosting.Abstractions</span><span class="sxs-lookup"><span data-stu-id="e1d72-124">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="e1d72-125">Удалена ссылка на `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="e1d72-125">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="e1d72-126">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="e1d72-126">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="e1d72-127">Удалена ссылка на `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="e1d72-127">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="e1d72-128">Microsoft.Extensions.Logging.Console</span><span class="sxs-lookup"><span data-stu-id="e1d72-128">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="e1d72-129">Удалена ссылка на `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="e1d72-129">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="e1d72-130">Microsoft.Extensions.Logging.EventLog</span><span class="sxs-lookup"><span data-stu-id="e1d72-130">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="e1d72-131">Удалена ссылка на `System.Diagnostics.EventLog` для моникера целевой платформы .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="e1d72-131">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="e1d72-132">Microsoft.Extensions.Logging.EventSource</span><span class="sxs-lookup"><span data-stu-id="e1d72-132">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="e1d72-133">Удалена ссылка на `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="e1d72-133">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="e1d72-134">Microsoft.Extensions.Options</span><span class="sxs-lookup"><span data-stu-id="e1d72-134">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="e1d72-135">Удалена ссылка на `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="e1d72-135">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="e1d72-136">Например, ссылка на пакет `Microsoft.Extensions.Configuration` была удалена из `Microsoft.Extensions.Configuration.Binder`.</span><span class="sxs-lookup"><span data-stu-id="e1d72-136">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="e1d72-137">В пакете не использовался API из зависимости.</span><span class="sxs-lookup"><span data-stu-id="e1d72-137">No API from the dependency was used in the package.</span></span> <span data-ttu-id="e1d72-138">Пользователи `Microsoft.Extensions.Configuration.Binder`, которые зависят от API из `Microsoft.Extensions.Configuration`, должны добавить прямую ссылку на него в своем проекте.</span><span class="sxs-lookup"><span data-stu-id="e1d72-138">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e1d72-139">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e1d72-139">Affected APIs</span></span>

<span data-ttu-id="e1d72-140">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="e1d72-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
