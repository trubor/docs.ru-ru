---
title: Критическое изменение. Environment.OSVersion возвращает правильную версию операционной системы
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где Environment.OSVersion возвращает фактическую версию операционной системы, а не, например, ОС, выбранную для совместимости приложений.
ms.date: 11/01/2020
ms.openlocfilehash: 05ec886061263ea43a2d956b8ce0ecc06e2bf3ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257535"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="ce3b3-103">Environment.OSVersion возвращает правильную версию операционной системы</span><span class="sxs-lookup"><span data-stu-id="ce3b3-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="ce3b3-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы (ОС), а не, например, ту ОС, которая выбрана для совместимости приложений.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="ce3b3-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="ce3b3-105">Change description</span></span>

<span data-ttu-id="ce3b3-106">В предыдущих версиях .NET <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает версию ОС, которая может быть неверной, если приложение работает в режиме совместимости Windows.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="ce3b3-107">Дополнительные сведения см. в [примечаниях к функции GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="ce3b3-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="ce3b3-108">В macOS <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает базовую версию ядра Darwin.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="ce3b3-109">Начиная с .NET 5 <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы для Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-109">Starting in .NET 5, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="ce3b3-110">В следующей таблице приведены различия в поведении.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="ce3b3-111">Предыдущие версии .NET</span><span class="sxs-lookup"><span data-stu-id="ce3b3-111">Previous .NET versions</span></span> | <span data-ttu-id="ce3b3-112">.NET 5.+</span><span class="sxs-lookup"><span data-stu-id="ce3b3-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="ce3b3-113">Windows</span><span class="sxs-lookup"><span data-stu-id="ce3b3-113">Windows</span></span> | <span data-ttu-id="ce3b3-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="ce3b3-114">6.2.9200.0</span></span> | <span data-ttu-id="ce3b3-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="ce3b3-115">10.0.19042.0</span></span> |
| <span data-ttu-id="ce3b3-116">macOS</span><span class="sxs-lookup"><span data-stu-id="ce3b3-116">macOS</span></span> | <span data-ttu-id="ce3b3-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="ce3b3-117">19.6.0.0</span></span> | <span data-ttu-id="ce3b3-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="ce3b3-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="ce3b3-119">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="ce3b3-119">Reason for change</span></span>

<span data-ttu-id="ce3b3-120">Пользователи этого свойства предполагают, что оно будет возвращать фактическую версию операционной системы.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="ce3b3-121">Большинство приложений .NET не указывают поддерживаемую версию в манифесте приложения и поэтому получают поддерживаемую по умолчанию версию из узла dotnet.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="ce3b3-122">В результате оболочка совместимости редко применяется для работающего приложения.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="ce3b3-123">Когда Windows выпускает новую версию, а более старый узел dotnet по-прежнему используется, эти приложения могут получить неверную версию ОС.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="ce3b3-124">Возврат фактической версии более соответствует ожиданиям разработчиков этого API.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="ce3b3-125">С появлением <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> и <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> в .NET 5 <xref:System.Environment.OSVersion?displayProperty=nameWithType> были изменены для согласованности с Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ce3b3-126">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="ce3b3-126">Version introduced</span></span>

<span data-ttu-id="ce3b3-127">5.0</span><span class="sxs-lookup"><span data-stu-id="ce3b3-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ce3b3-128">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="ce3b3-128">Recommended action</span></span>

<span data-ttu-id="ce3b3-129">Проверьте и протестируйте код, который использует <xref:System.Environment.OSVersion?displayProperty=nameWithType>, чтобы убедиться, что он ведет себя должным образом.</span><span class="sxs-lookup"><span data-stu-id="ce3b3-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ce3b3-130">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="ce3b3-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
