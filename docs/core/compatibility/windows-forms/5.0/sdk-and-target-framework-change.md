---
title: Критическое изменение. В приложениях WinForms и WPF используется Microsoft.NET.Sdk
description: Ознакомьтесь с критическим изменением в .NET 5, где приложения Windows Forms и Windows Presentation Framework теперь используют пакет SDK для .NET вместо .NET Core WinForms и пакета SDK WPF.
ms.date: 09/18/2020
ms.openlocfilehash: 408233f6f8801fb3d4e53beab28c26a777a4a3e1
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256209"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="41d9b-103">В приложениях WinForms и WPF используется Microsoft.NET.Sdk</span><span class="sxs-lookup"><span data-stu-id="41d9b-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="41d9b-104">Приложения Windows Forms и Windows Presentation Framework (WPF) теперь используют пакет SDK для .NET (`Microsoft.NET.Sdk`) вместо .NET Core WinForms и пакета SDK WPF (`Microsoft.NET.Sdk.WindowsDesktop`).</span><span class="sxs-lookup"><span data-stu-id="41d9b-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="41d9b-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="41d9b-105">Change description</span></span>

<span data-ttu-id="41d9b-106">В предыдущих версиях .NET Core в приложениях WinForms и WPF использовался отдельный [пакет SDK проекта](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span><span class="sxs-lookup"><span data-stu-id="41d9b-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="41d9b-107">Начиная с .NET 5 пакет SDK WinForms и WPF был объединен с пакетом SDK для .NET (`Microsoft.NET.Sdk`).</span><span class="sxs-lookup"><span data-stu-id="41d9b-107">Starting in .NET 5, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="41d9b-108">Кроме того, новые [моникеры целевой платформы (TFM)](../../../../standard/frameworks.md) заменяют собой `netcoreapp` и `netstandard` в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="41d9b-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="41d9b-109">В следующем примере показаны изменения, которые необходимо внести для файла проекта WPF при изменении целевой платформы на .NET 5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="41d9b-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5 or later.</span></span>

<span data-ttu-id="41d9b-110">В предыдущих версиях .NET Core:</span><span class="sxs-lookup"><span data-stu-id="41d9b-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="41d9b-111">В .NET 5 и более поздних версиях:</span><span class="sxs-lookup"><span data-stu-id="41d9b-111">In .NET 5 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="41d9b-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="41d9b-112">Version introduced</span></span>

<span data-ttu-id="41d9b-113">Пакет SDK для .NET 5.0.100</span><span class="sxs-lookup"><span data-stu-id="41d9b-113">.NET SDK 5.0.100</span></span>

## <a name="recommended-action"></a><span data-ttu-id="41d9b-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="41d9b-114">Recommended action</span></span>

<span data-ttu-id="41d9b-115">В файле проекта WPF или Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="41d9b-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="41d9b-116">Измените атрибут `Sdk` на `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="41d9b-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="41d9b-117">Установите для свойства `TargetFramework` значение `net5.0-windows`.</span><span class="sxs-lookup"><span data-stu-id="41d9b-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="41d9b-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="41d9b-118">Affected APIs</span></span>

<span data-ttu-id="41d9b-119">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="41d9b-119">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
