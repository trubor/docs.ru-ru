---
title: Критическое изменение. Из .NET удалена встроенная поддержка WinRT
description: Узнайте о критических изменениях взаимодействия в .NET 5, где из .NET удалена встроенная поддержка WinRT.
ms.date: 10/13/2020
ms.openlocfilehash: 986b810b74c7e7d7514ec2b734bfab45e29b87fa
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256690"
---
# <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="88647-103">Из .NET удалена встроенная поддержка WinRT</span><span class="sxs-lookup"><span data-stu-id="88647-103">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="88647-104">Из .NET удалена встроенная поддержка использования [API-интерфейсов в среде выполнения Windows (WinRT)](/uwp/winrt-cref/winrt-type-system).</span><span class="sxs-lookup"><span data-stu-id="88647-104">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="88647-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="88647-105">Version introduced</span></span>

<span data-ttu-id="88647-106">5.0</span><span class="sxs-lookup"><span data-stu-id="88647-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="88647-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="88647-107">Change description</span></span>

<span data-ttu-id="88647-108">Ранее CoreCLR поддерживал использование [файлов метаданных Windows (WinMD)](/uwp/winrt-cref/winmd-files) для активации и использования типов WinRT.</span><span class="sxs-lookup"><span data-stu-id="88647-108">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="88647-109">Начиная с версии .NET 5 поддержка прямого использования файлов WinMD в CoreCLR прекращена.</span><span class="sxs-lookup"><span data-stu-id="88647-109">Starting in .NET 5, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="88647-110">При попытке добавить ссылку на неподдерживаемую сборку отображается <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="88647-110">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="88647-111">При активации класса WinRT отображается <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="88647-111">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="88647-112">Это критическое изменение добавлено по следующим причинам:</span><span class="sxs-lookup"><span data-stu-id="88647-112">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="88647-113">Таким образом, разрабатывать и совершенствовать WinRT можно отдельно от среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="88647-113">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="88647-114">Для симметрии с системами взаимодействия, которые предоставляются для других операционных систем, таких как iOS и Android.</span><span class="sxs-lookup"><span data-stu-id="88647-114">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="88647-115">Для использования преимуществ других функций .NET, таких как функции C#, компоновка промежуточного языка (IL) и компиляция перед выполнением.</span><span class="sxs-lookup"><span data-stu-id="88647-115">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="88647-116">Для упрощения базы кода в среде выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="88647-116">To simplify the .NET runtime codebase.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="88647-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="88647-117">Recommended action</span></span>

- <span data-ttu-id="88647-118">Удалите ссылки на [пакет Microsoft.Windows.SDK.Contracts](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span><span class="sxs-lookup"><span data-stu-id="88647-118">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="88647-119">Вместо этого укажите версию API-интерфейсов Windows, доступ к которым требуется получать с помощью свойства `TargetFramework` проекта.</span><span class="sxs-lookup"><span data-stu-id="88647-119">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="88647-120">Пример:</span><span class="sxs-lookup"><span data-stu-id="88647-120">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="88647-121">Используйте цепочку инструментов [C#/WinRT](/windows/uwp/csharp-winrt/) для создания или настройки API-интерфейсов и типов WinRT в .NET 5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="88647-121">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5 and later versions.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="88647-122">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="88647-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

### Category

Interop

-->
