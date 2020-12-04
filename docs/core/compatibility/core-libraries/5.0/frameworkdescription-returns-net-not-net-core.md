---
title: Критическое изменение. Значение FrameworkDescription изменено с .NET Core на .NET
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где RuntimeInformation.FrameworkDescription теперь возвращает ".NET" вместо ".NET Core".
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759832"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="a52ea-103">Значение FrameworkDescription изменено с .NET Core на .NET</span><span class="sxs-lookup"><span data-stu-id="a52ea-103">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="a52ea-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> теперь возвращает ".NET" вместо ".NET Core".</span><span class="sxs-lookup"><span data-stu-id="a52ea-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

## <a name="change-description"></a><span data-ttu-id="a52ea-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="a52ea-105">Change description</span></span>

<span data-ttu-id="a52ea-106">В предыдущих версиях .NET <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> возвращает ".NET Core" в составе строки описания, например `.NET Core 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="a52ea-106">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="a52ea-107">Начиная с .NET 5.0 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> возвращает ".NET" в составе строки описания, например `.NET 5.0.0`.</span><span class="sxs-lookup"><span data-stu-id="a52ea-107">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a52ea-108">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="a52ea-108">Reason for change</span></span>

<span data-ttu-id="a52ea-109">В .NET 5 в качестве краткого моникера целевой платформы вместо `netcoreapp` используется `net`.</span><span class="sxs-lookup"><span data-stu-id="a52ea-109">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="a52ea-110">В целях обеспечения согласованности также было обновлено описание платформы.</span><span class="sxs-lookup"><span data-stu-id="a52ea-110">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="a52ea-111">Это изменение носит косметический характер, так как `FrameworkName` кодируется только в свойстве <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a52ea-111">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a52ea-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="a52ea-112">Version introduced</span></span>

<span data-ttu-id="a52ea-113">5.0</span><span class="sxs-lookup"><span data-stu-id="a52ea-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a52ea-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="a52ea-114">Recommended action</span></span>

<span data-ttu-id="a52ea-115">Обновите код, в котором выполняется поиск ".NET Core" в строке, возвращаемой <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span><span class="sxs-lookup"><span data-stu-id="a52ea-115">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a52ea-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="a52ea-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
