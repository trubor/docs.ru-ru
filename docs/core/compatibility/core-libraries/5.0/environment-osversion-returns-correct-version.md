---
title: Критическое изменение. Environment.OSVersion возвращает правильную версию операционной системы
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где Environment.OSVersion возвращает фактическую версию операционной системы, а не, например, ОС, выбранную для совместимости приложений.
ms.date: 11/01/2020
ms.openlocfilehash: c810d9a7a028a0c60c30d69e78a9b9c695d933ef
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009525"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="42d6e-103">Environment.OSVersion возвращает правильную версию операционной системы</span><span class="sxs-lookup"><span data-stu-id="42d6e-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="42d6e-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы (ОС), а не, например, ту ОС, которая выбрана для совместимости приложений.</span><span class="sxs-lookup"><span data-stu-id="42d6e-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="42d6e-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="42d6e-105">Change description</span></span>

<span data-ttu-id="42d6e-106">В предыдущих версиях .NET <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает версию ОС, которая может быть неверной, если приложение работает в режиме совместимости Windows.</span><span class="sxs-lookup"><span data-stu-id="42d6e-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="42d6e-107">Дополнительные сведения см. в [примечаниях к функции GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="42d6e-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="42d6e-108">В macOS <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает базовую версию ядра Darwin.</span><span class="sxs-lookup"><span data-stu-id="42d6e-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="42d6e-109">Начиная с .NET 5.0 <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы для Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="42d6e-109">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="42d6e-110">В следующей таблице приведены различия в поведении.</span><span class="sxs-lookup"><span data-stu-id="42d6e-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="42d6e-111">Предыдущие версии .NET</span><span class="sxs-lookup"><span data-stu-id="42d6e-111">Previous .NET versions</span></span> | <span data-ttu-id="42d6e-112">.NET 5.+</span><span class="sxs-lookup"><span data-stu-id="42d6e-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="42d6e-113">Windows</span><span class="sxs-lookup"><span data-stu-id="42d6e-113">Windows</span></span> | <span data-ttu-id="42d6e-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="42d6e-114">6.2.9200.0</span></span> | <span data-ttu-id="42d6e-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="42d6e-115">10.0.19042.0</span></span> |
| <span data-ttu-id="42d6e-116">macOS</span><span class="sxs-lookup"><span data-stu-id="42d6e-116">macOS</span></span> | <span data-ttu-id="42d6e-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="42d6e-117">19.6.0.0</span></span> | <span data-ttu-id="42d6e-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="42d6e-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="42d6e-119">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="42d6e-119">Reason for change</span></span>

<span data-ttu-id="42d6e-120">Пользователи этого свойства предполагают, что оно будет возвращать фактическую версию операционной системы.</span><span class="sxs-lookup"><span data-stu-id="42d6e-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="42d6e-121">Большинство приложений .NET не указывают поддерживаемую версию в манифесте приложения и поэтому получают поддерживаемую по умолчанию версию из узла dotnet.</span><span class="sxs-lookup"><span data-stu-id="42d6e-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="42d6e-122">В результате оболочка совместимости редко применяется для работающего приложения.</span><span class="sxs-lookup"><span data-stu-id="42d6e-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="42d6e-123">Когда Windows выпускает новую версию, а более старый узел dotnet по-прежнему используется, эти приложения могут получить неверную версию ОС.</span><span class="sxs-lookup"><span data-stu-id="42d6e-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="42d6e-124">Возврат фактической версии более соответствует ожиданиям разработчиков этого API.</span><span class="sxs-lookup"><span data-stu-id="42d6e-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="42d6e-125">С появлением <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> и <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> в .NET 5.0 <xref:System.Environment.OSVersion?displayProperty=nameWithType> были изменены для согласованности с Windows и macOS.</span><span class="sxs-lookup"><span data-stu-id="42d6e-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="42d6e-126">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="42d6e-126">Version introduced</span></span>

<span data-ttu-id="42d6e-127">5.0</span><span class="sxs-lookup"><span data-stu-id="42d6e-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="42d6e-128">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="42d6e-128">Recommended action</span></span>

<span data-ttu-id="42d6e-129">Проверьте и протестируйте код, который использует <xref:System.Environment.OSVersion?displayProperty=nameWithType>, чтобы убедиться, что он ведет себя должным образом.</span><span class="sxs-lookup"><span data-stu-id="42d6e-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="42d6e-130">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="42d6e-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
