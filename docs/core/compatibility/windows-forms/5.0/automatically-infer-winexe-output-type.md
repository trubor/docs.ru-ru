---
title: Критическое изменение. Свойству OutputType задано значение WinExe для приложений WPF и WinForms
description: Сведения о критическом изменении в .NET 5.0, где свойству OutputType автоматически задается значение WinExe для приложений Windows Forms.
ms.date: 09/18/2020
ms.openlocfilehash: 072c5b11c8304eb540e176ce9747930789f28505
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760021"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="0b193-103">Свойству OutputType задано значение WinExe для приложений WPF и WinForms</span><span class="sxs-lookup"><span data-stu-id="0b193-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="0b193-104">Свойству `OutputType` автоматически задано значение `WinExe` для приложений Windows Presentation Foundation (WPF) и Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0b193-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="0b193-105">Если свойство `OutputType` имеет значение `WinExe`, окно консоли не открывается при выполнении приложения.</span><span class="sxs-lookup"><span data-stu-id="0b193-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="0b193-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="0b193-106">Change description</span></span>

<span data-ttu-id="0b193-107">В предыдущих версиях .NET используется значение, указанное для `OutputType` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="0b193-107">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="0b193-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="0b193-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="0b193-109">Начиная с .NET 5.0 свойству `OutputType` автоматически задается значение `WinExe` для приложений WPF и Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0b193-109">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="0b193-110">Пример:</span><span class="sxs-lookup"><span data-stu-id="0b193-110">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a><span data-ttu-id="0b193-111">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="0b193-111">Reason for change</span></span>

<span data-ttu-id="0b193-112">Предполагается, что большинство пользователей не хотят, чтобы окно консоли открывалось при выполнении приложения WPF или Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0b193-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="0b193-113">Кроме того, [поскольку теперь эти типы приложений используют пакет SDK для .NET](sdk-and-target-framework-change.md) вместо пакета SDK для Windows Desktop, будет задано правильное значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="0b193-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="0b193-114">При добавлении поддержки для использования iOS и Android в качестве целевых платформ будет проще работать с несколькими платформами, если все они используют один и тот же тип выходных данных.</span><span class="sxs-lookup"><span data-stu-id="0b193-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="0b193-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="0b193-115">Version introduced</span></span>

<span data-ttu-id="0b193-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0b193-116">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="0b193-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="0b193-117">Recommended action</span></span>

<span data-ttu-id="0b193-118">Никаких действий выполнять не требуется.</span><span class="sxs-lookup"><span data-stu-id="0b193-118">No action is required in your part.</span></span> <span data-ttu-id="0b193-119">Однако если вы хотите восстановить старое поведение, задайте свойству `DisableWinExeOutputInference` значение `true` в файле проекта.</span><span class="sxs-lookup"><span data-stu-id="0b193-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="0b193-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="0b193-120">Affected APIs</span></span>

<span data-ttu-id="0b193-121">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="0b193-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
