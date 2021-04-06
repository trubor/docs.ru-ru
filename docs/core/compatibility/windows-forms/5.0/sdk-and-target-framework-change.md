---
title: Критическое изменение. В приложениях WinForms и WPF используется Microsoft.NET.Sdk
description: Ознакомьтесь с критическим изменением в .NET 5, где приложения Windows Forms и Windows Presentation Framework теперь используют пакет SDK для .NET вместо .NET Core WinForms и пакета SDK WPF.
ms.date: 09/18/2020
ms.openlocfilehash: ebd4f51d5436cec2f0463558e99a85cb261ae682
ms.sourcegitcommit: 109507b6c16704ed041efe9598c70cd3438a9fbc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106079496"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="7fda0-103">В приложениях WinForms и WPF используется Microsoft.NET.Sdk</span><span class="sxs-lookup"><span data-stu-id="7fda0-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="7fda0-104">Приложения Windows Forms и Windows Presentation Framework (WPF) теперь используют пакет SDK для .NET (`Microsoft.NET.Sdk`) вместо .NET Core WinForms и пакета SDK WPF (`Microsoft.NET.Sdk.WindowsDesktop`).</span><span class="sxs-lookup"><span data-stu-id="7fda0-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="7fda0-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="7fda0-105">Change description</span></span>

<span data-ttu-id="7fda0-106">В предыдущих версиях .NET Core в приложениях WinForms и WPF использовался отдельный [пакет SDK проекта](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span><span class="sxs-lookup"><span data-stu-id="7fda0-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="7fda0-107">Начиная с .NET 5 пакет SDK WinForms и WPF был объединен с пакетом SDK для .NET (`Microsoft.NET.Sdk`).</span><span class="sxs-lookup"><span data-stu-id="7fda0-107">Starting in .NET 5, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="7fda0-108">Кроме того, новые [моникеры целевой платформы (TFM)](../../../../standard/frameworks.md) заменяют собой `netcoreapp` и `netstandard` в .NET 5.</span><span class="sxs-lookup"><span data-stu-id="7fda0-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="7fda0-109">В следующем примере показаны изменения, которые необходимо внести для файла проекта WPF при изменении целевой платформы на .NET 5 или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="7fda0-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5 or later.</span></span>

<span data-ttu-id="7fda0-110">В предыдущих версиях .NET Core:</span><span class="sxs-lookup"><span data-stu-id="7fda0-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="7fda0-111">В .NET 5 и более поздних версиях:</span><span class="sxs-lookup"><span data-stu-id="7fda0-111">In .NET 5 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="7fda0-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="7fda0-112">Version introduced</span></span>

<span data-ttu-id="7fda0-113">Пакет SDK для .NET 5.0.100</span><span class="sxs-lookup"><span data-stu-id="7fda0-113">.NET SDK 5.0.100</span></span>

## <a name="recommended-action"></a><span data-ttu-id="7fda0-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="7fda0-114">Recommended action</span></span>

<span data-ttu-id="7fda0-115">В файле проекта WPF или Windows Forms:</span><span class="sxs-lookup"><span data-stu-id="7fda0-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="7fda0-116">Измените атрибут `Sdk` на `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="7fda0-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="7fda0-117">Установите для свойства `TargetFramework` значение `net5.0-windows`.</span><span class="sxs-lookup"><span data-stu-id="7fda0-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7fda0-118">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="7fda0-118">Affected APIs</span></span>

<span data-ttu-id="7fda0-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7fda0-119">None.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
