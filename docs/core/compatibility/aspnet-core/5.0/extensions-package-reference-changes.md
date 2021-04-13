---
title: Критическое изменение. Расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet
description: Сведения о критическом изменении в ASP.NET Core 5.0 — расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 82ee5129d6422d0a5ea4a0f14632a42e779f6ded
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106497740"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a><span data-ttu-id="0b63e-103">Расширения. Изменения ссылок на пакеты, затрагивающие некоторые пакеты NuGet</span><span class="sxs-lookup"><span data-stu-id="0b63e-103">Extensions: Package reference changes affecting some NuGet packages</span></span>

<span data-ttu-id="0b63e-104">При переносе некоторых пакетов NuGet `Microsoft.Extensions.*` из репозитория [dotnet/extensions](https://github.com/dotnet/extensions) в [dotnet/runtime](https://github.com/dotnet/runtime), как описано на странице [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), изменения в пакетах применяются к некоторым перенесенным пакетам.</span><span class="sxs-lookup"><span data-stu-id="0b63e-104">With the migration of some `Microsoft.Extensions.*` NuGet packages from the [dotnet/extensions](https://github.com/dotnet/extensions) repository to [dotnet/runtime](https://github.com/dotnet/runtime), as described in [aspnet/Announcements#411](https://github.com/aspnet/Announcements/issues/411), packaging changes are being applied to some of the migrated packages.</span></span> <span data-ttu-id="0b63e-105">Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span><span class="sxs-lookup"><span data-stu-id="0b63e-105">For discussion on this issue, see [dotnet/aspnetcore#21033](https://github.com/dotnet/aspnetcore/issues/21033).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0b63e-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0b63e-106">Version introduced</span></span>

<span data-ttu-id="0b63e-107">5.0, предварительная версия 4</span><span class="sxs-lookup"><span data-stu-id="0b63e-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="0b63e-108">Старое поведение</span><span class="sxs-lookup"><span data-stu-id="0b63e-108">Old behavior</span></span>

<span data-ttu-id="0b63e-109">Некоторые пакеты `Microsoft.Extensions.*` включают ссылки на пакеты для API, использовавшиеся приложением.</span><span class="sxs-lookup"><span data-stu-id="0b63e-109">Some `Microsoft.Extensions.*` packages included package references for APIs on which your app relied.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="0b63e-110">Новое поведение</span><span class="sxs-lookup"><span data-stu-id="0b63e-110">New behavior</span></span>

<span data-ttu-id="0b63e-111">Приложению может потребоваться добавить зависимости пакета `Microsoft.Extensions.*`.</span><span class="sxs-lookup"><span data-stu-id="0b63e-111">Your app may have to add `Microsoft.Extensions.*` package dependencies.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="0b63e-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="0b63e-112">Reason for change</span></span>

<span data-ttu-id="0b63e-113">Политики упаковки были обновлены для согласованности с репозиторием *dotnet/runtime*.</span><span class="sxs-lookup"><span data-stu-id="0b63e-113">Packaging policies were updated to better align with the *dotnet/runtime* repository.</span></span> <span data-ttu-id="0b63e-114">В новой политике неиспользуемые ссылки на пакеты удаляются из файлов *NUPKG* во время упаковки.</span><span class="sxs-lookup"><span data-stu-id="0b63e-114">Under the new policy, unused package references are removed from *.nupkg* files during packaging.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0b63e-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0b63e-115">Recommended action</span></span>

<span data-ttu-id="0b63e-116">Пользователи затронутых пакетов должны добавить прямую зависимость от удаленной зависимости пакета в своем проекте, если используются API из удаленной зависимости пакета.</span><span class="sxs-lookup"><span data-stu-id="0b63e-116">Consumers of the affected packages should add a direct dependency on the removed package dependency in their project if APIs from removed package dependency are used.</span></span> <span data-ttu-id="0b63e-117">В следующей таблице перечислены затронутые пакеты и соответствующие изменения.</span><span class="sxs-lookup"><span data-stu-id="0b63e-117">The following table lists the affected packages and the corresponding changes.</span></span>

|<span data-ttu-id="0b63e-118">Имя пакета</span><span class="sxs-lookup"><span data-stu-id="0b63e-118">Package name</span></span>|<span data-ttu-id="0b63e-119">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0b63e-119">Change description</span></span>|
|------------|------------------|
|[<span data-ttu-id="0b63e-120">Microsoft.Extensions.Configuration.Binder</span><span class="sxs-lookup"><span data-stu-id="0b63e-120">Microsoft.Extensions.Configuration.Binder</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|<span data-ttu-id="0b63e-121">Удалена ссылка на `Microsoft.Extensions.Configuration`</span><span class="sxs-lookup"><span data-stu-id="0b63e-121">Removed reference to `Microsoft.Extensions.Configuration`</span></span>|
|[<span data-ttu-id="0b63e-122">Microsoft.Extensions.Configuration.Json</span><span class="sxs-lookup"><span data-stu-id="0b63e-122">Microsoft.Extensions.Configuration.Json</span></span>](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |<span data-ttu-id="0b63e-123">Удалена ссылка на `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="0b63e-123">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="0b63e-124">Microsoft.Extensions.Hosting.Abstractions</span><span class="sxs-lookup"><span data-stu-id="0b63e-124">Microsoft.Extensions.Hosting.Abstractions</span></span>](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|<span data-ttu-id="0b63e-125">Удалена ссылка на `Microsoft.Extensions.Logging.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="0b63e-125">Removed reference to `Microsoft.Extensions.Logging.Abstractions`</span></span>|
|[<span data-ttu-id="0b63e-126">Microsoft.Extensions.Logging</span><span class="sxs-lookup"><span data-stu-id="0b63e-126">Microsoft.Extensions.Logging</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |<span data-ttu-id="0b63e-127">Удалена ссылка на `Microsoft.Extensions.Configuration.Binder`</span><span class="sxs-lookup"><span data-stu-id="0b63e-127">Removed reference to `Microsoft.Extensions.Configuration.Binder`</span></span>|
|[<span data-ttu-id="0b63e-128">Microsoft.Extensions.Logging.Console</span><span class="sxs-lookup"><span data-stu-id="0b63e-128">Microsoft.Extensions.Logging.Console</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |<span data-ttu-id="0b63e-129">Удалена ссылка на `Microsoft.Extensions.Configuration.Abstractions`</span><span class="sxs-lookup"><span data-stu-id="0b63e-129">Removed reference to `Microsoft.Extensions.Configuration.Abstractions`</span></span>|
|[<span data-ttu-id="0b63e-130">Microsoft.Extensions.Logging.EventLog</span><span class="sxs-lookup"><span data-stu-id="0b63e-130">Microsoft.Extensions.Logging.EventLog</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |<span data-ttu-id="0b63e-131">Удалена ссылка на `System.Diagnostics.EventLog` для моникера целевой платформы .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="0b63e-131">Removed reference to `System.Diagnostics.EventLog` for the .NET Framework 4.6.1 target framework moniker</span></span>|
|[<span data-ttu-id="0b63e-132">Microsoft.Extensions.Logging.EventSource</span><span class="sxs-lookup"><span data-stu-id="0b63e-132">Microsoft.Extensions.Logging.EventSource</span></span>](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |<span data-ttu-id="0b63e-133">Удалена ссылка на `System.Threading.Tasks.Extensions`</span><span class="sxs-lookup"><span data-stu-id="0b63e-133">Removed reference to `System.Threading.Tasks.Extensions`</span></span>|
|[<span data-ttu-id="0b63e-134">Microsoft.Extensions.Options</span><span class="sxs-lookup"><span data-stu-id="0b63e-134">Microsoft.Extensions.Options</span></span>](https://nuget.org/packages/Microsoft.Extensions.Options)                          |<span data-ttu-id="0b63e-135">Удалена ссылка на `System.ComponentModel.Annotations`</span><span class="sxs-lookup"><span data-stu-id="0b63e-135">Removed reference to `System.ComponentModel.Annotations`</span></span>|

<span data-ttu-id="0b63e-136">Например, ссылка на пакет `Microsoft.Extensions.Configuration` была удалена из `Microsoft.Extensions.Configuration.Binder`.</span><span class="sxs-lookup"><span data-stu-id="0b63e-136">For example, the package reference to `Microsoft.Extensions.Configuration` was removed from `Microsoft.Extensions.Configuration.Binder`.</span></span> <span data-ttu-id="0b63e-137">В пакете не использовался API из зависимости.</span><span class="sxs-lookup"><span data-stu-id="0b63e-137">No API from the dependency was used in the package.</span></span> <span data-ttu-id="0b63e-138">Пользователи `Microsoft.Extensions.Configuration.Binder`, которые зависят от API из `Microsoft.Extensions.Configuration`, должны добавить прямую ссылку на него в своем проекте.</span><span class="sxs-lookup"><span data-stu-id="0b63e-138">Users of `Microsoft.Extensions.Configuration.Binder` who depend on APIs from `Microsoft.Extensions.Configuration` should add a direct reference to it in their project.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="0b63e-139">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0b63e-139">Affected APIs</span></span>

<span data-ttu-id="0b63e-140">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="0b63e-140">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
