---
title: Критическое изменение. Значение TargetFramework изменено с netcoreapp на net
description: Сведения о критическом изменении в .NET 5, где значение свойства TargetFramework MSBuild изменено с netcoreapp3.1 на net5.0.
ms.date: 10/17/2020
ms.openlocfilehash: 88bfe7602c83f61b56f11c4e0336702571369e3c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256495"
---
# <a name="targetframework-change-from-netcoreapp-to-net"></a><span data-ttu-id="c8d1c-103">Значение TargetFramework изменено с netcoreapp на net</span><span class="sxs-lookup"><span data-stu-id="c8d1c-103">TargetFramework change from netcoreapp to net</span></span>

<span data-ttu-id="c8d1c-104">Значение свойства MSBuild `TargetFramework` изменено с `netcoreapp3.1` на `net5.0`.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-104">The value for the MSBuild `TargetFramework` property changed from `netcoreapp3.1` to `net5.0`.</span></span> <span data-ttu-id="c8d1c-105">Это может привести к ошибкам в коде, который основан на анализе значения `TargetFramework`.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-105">This can break code that relies on parsing the value of `TargetFramework`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c8d1c-106">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="c8d1c-106">Version introduced</span></span>

<span data-ttu-id="c8d1c-107">5.0</span><span class="sxs-lookup"><span data-stu-id="c8d1c-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="c8d1c-108">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="c8d1c-108">Change description</span></span>

<span data-ttu-id="c8d1c-109">В версиях .NET Core с 1.0 по 3.1 значение свойства MSBuild `TargetFramework` начинается с `netcoreapp`, например `netcoreapp3.1` для приложений, предназначенных для платформы .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-109">In .NET Core 1.0 - 3.1, the value for the MSBuild `TargetFramework` property starts with `netcoreapp`, for example, `netcoreapp3.1` for apps that target .NET Core 3.1.</span></span> <span data-ttu-id="c8d1c-110">Начиная с версии .NET 5 это значение упрощено и начинается с `net`, например `net5.0` для .NET 5.0.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-110">Starting in .NET 5, this value is simplified to just start with `net`, for example, `net5.0` for .NET 5.0.</span></span>

<span data-ttu-id="c8d1c-111">Дополнительные сведения см. в разделе [Будущее .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) и [Имена целевых платформ в .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span><span class="sxs-lookup"><span data-stu-id="c8d1c-111">For more information, see [The future of .NET Standard](https://devblogs.microsoft.com/dotnet/the-future-of-net-standard/) and [Target framework names in .NET 5](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c8d1c-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="c8d1c-112">Reason for change</span></span>

- <span data-ttu-id="c8d1c-113">Упрощает значение `TargetFramework`.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-113">Simplifies the `TargetFramework` value.</span></span>
- <span data-ttu-id="c8d1c-114">Позволяет включать `TargetPlatform` в свойство `TargetFramework` в проектах.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-114">Enables projects to include a `TargetPlatform` in the `TargetFramework` property.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c8d1c-115">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="c8d1c-115">Recommended action</span></span>

<span data-ttu-id="c8d1c-116">Если вы используете логику, в которой выполняется синтаксический анализ значения `TargetFramework`, необходимо обновить ее.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-116">If you have logic that parses the value of `TargetFramework`, you'll need to update it.</span></span> <span data-ttu-id="c8d1c-117">Например, в следующем условии MSBuild используется значение `TargetFramework`.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-117">For example, the following MSBuild condition relies on the value of `TargetFramework`.</span></span>

```xml
<PropertyGroup Condition="$(TargetFramework.StartsWith('netcoreapp'))">
```

<span data-ttu-id="c8d1c-118">В соответствии с этим требованием можно обновить код, чтобы сравнить идентификатор целевой платформы.</span><span class="sxs-lookup"><span data-stu-id="c8d1c-118">For this requirement, you can update the code to compare the target framework identifier instead.</span></span>

```xml
<PropertyGroup Condition="'$([MSBuild]::GetTargetFrameworkIdentifier('$(TargetFramework)'))' == '.NETCoreApp'">
```

## <a name="affected-apis"></a><span data-ttu-id="c8d1c-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="c8d1c-119">Affected APIs</span></span>

<span data-ttu-id="c8d1c-120">Н/Д</span><span class="sxs-lookup"><span data-stu-id="c8d1c-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
