---
title: Критическое изменение. В приложениях WinForms и WPF используется Microsoft.NET.Sdk
description: Ознакомьтесь с критическим изменением в .NET 5.0, где приложения Windows Forms и Windows Presentation Framework теперь используют пакет SDK для .NET вместо .NET Core WinForms и пакета SDK WPF.
ms.date: 09/18/2020
ms.openlocfilehash: 5f25be44c390abc173f155351d8cb007a6b370b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759871"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="e2427-103">В приложениях WinForms и WPF используется Microsoft.NET.Sdk</span><span class="sxs-lookup"><span data-stu-id="e2427-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="e2427-104">Приложения Windows Forms и Windows Presentation Framework (WPF) теперь используют пакет SDK для .NET (`Microsoft.NET.Sdk`) вместо .NET Core WinForms и пакета SDK WPF (`Microsoft.NET.Sdk.WindowsDesktop`).</span><span class="sxs-lookup"><span data-stu-id="e2427-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="e2427-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="e2427-105">Change description</span></span>

<span data-ttu-id="e2427-106">В предыдущих версиях .NET Core в приложениях WinForms и WPF использовался отдельный [пакет SDK проекта](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span><span class="sxs-lookup"><span data-stu-id="e2427-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="e2427-107">Начиная с .NET 5.0 пакет SDK WinForms и WPF был объединен с пакетом SDK для .NET (`Microsoft.NET.Sdk`).</span><span class="sxs-lookup"><span data-stu-id="e2427-107">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="e2427-108">Кроме того, новые [моникеры целевой платформы (TFM)](../../../../standard/frameworks.md) заменяют собой `netcoreapp` и `netstandard` в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="e2427-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="e2427-109">В следующем примере показаны изменения, которые необходимо внести для файла проекта WPF при изменении целевой платформы на .NET 5.0 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="e2427-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="e2427-110">В предыдущих версиях .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e2427-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="e2427-111">В .NET 5.0 и более поздних версиях:</span><span class="sxs-lookup"><span data-stu-id="e2427-111">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="e2427-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="e2427-112">Version introduced</span></span>

<span data-ttu-id="e2427-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="e2427-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e2427-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="e2427-114">Recommended action</span></span>

<span data-ttu-id="e2427-115">В файле проекта WPF или Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="e2427-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="e2427-116">Измените атрибут `Sdk` на `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="e2427-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="e2427-117">Установите для свойства `TargetFramework` значение `net5.0-windows`.</span><span class="sxs-lookup"><span data-stu-id="e2427-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e2427-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="e2427-118">Affected APIs</span></span>

<span data-ttu-id="e2427-119">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="e2427-119">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
