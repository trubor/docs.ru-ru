---
title: Критическое изменение. Environment.OSVersion возвращает правильную версию операционной системы
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где Environment.OSVersion возвращает фактическую версию операционной системы, а не, например, ОС, выбранную для совместимости приложений.
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760287"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="e26ca-103">Environment.OSVersion возвращает правильную версию операционной системы</span><span class="sxs-lookup"><span data-stu-id="e26ca-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="e26ca-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы (ОС), а не, например, ту ОС, которая выбрана для совместимости приложений.</span><span class="sxs-lookup"><span data-stu-id="e26ca-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="e26ca-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="e26ca-105">Change description</span></span>

<span data-ttu-id="e26ca-106">В предыдущих версиях .NET <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает версию ОС, которая может быть неверной, если приложение работает в режиме совместимости Windows.</span><span class="sxs-lookup"><span data-stu-id="e26ca-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="e26ca-107">Дополнительные сведения см. в [примечаниях к функции GetVersionExA](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span><span class="sxs-lookup"><span data-stu-id="e26ca-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="e26ca-108">Начиная с .NET 5.0 <xref:System.Environment.OSVersion?displayProperty=nameWithType> возвращает фактическую версию операционной системы.</span><span class="sxs-lookup"><span data-stu-id="e26ca-108">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e26ca-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="e26ca-109">Reason for change</span></span>

<span data-ttu-id="e26ca-110">Пользователи этого свойства предполагают, что оно будет возвращать фактическую версию операционной системы.</span><span class="sxs-lookup"><span data-stu-id="e26ca-110">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="e26ca-111">Большинство приложений .NET не указывают поддерживаемую версию в манифесте приложения и поэтому получают поддерживаемую по умолчанию версию из узла dotnet.</span><span class="sxs-lookup"><span data-stu-id="e26ca-111">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="e26ca-112">В результате оболочка совместимости редко применяется для работающего приложения.</span><span class="sxs-lookup"><span data-stu-id="e26ca-112">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="e26ca-113">Когда Windows выпускает новую версию, а более старый узел dotnet по-прежнему используется, эти приложения могут получить неверную версию ОС.</span><span class="sxs-lookup"><span data-stu-id="e26ca-113">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="e26ca-114">Возврат фактической версии более соответствует ожиданиям разработчиков этого API.</span><span class="sxs-lookup"><span data-stu-id="e26ca-114">Returning the actual version is more inline with developers' expectations of this API.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e26ca-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e26ca-115">Version introduced</span></span>

<span data-ttu-id="e26ca-116">5.0</span><span class="sxs-lookup"><span data-stu-id="e26ca-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e26ca-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e26ca-117">Recommended action</span></span>

<span data-ttu-id="e26ca-118">Проверьте и протестируйте код, который использует <xref:System.Environment.OSVersion?displayProperty=nameWithType>, чтобы убедиться, что он ведет себя должным образом.</span><span class="sxs-lookup"><span data-stu-id="e26ca-118">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e26ca-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e26ca-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
