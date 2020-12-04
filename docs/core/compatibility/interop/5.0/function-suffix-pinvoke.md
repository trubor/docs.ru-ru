---
title: Критическое изменение. Отсутствует проверка суффикса A/W на платформах, отличных от Windows
description: Сведения о критическом изменении взаимодействия в .NET 5.0, где суффиксы больше не добавляются к именам экспортируемых функций во время проверки для P/Invokes на платформах, отличных от Windows.
ms.date: 08/13/2020
ms.openlocfilehash: a4c612a81796faf80fa257df21232a54f7b95431
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759820"
---
# <a name="no-aw-suffix-probing-on-non-windows-platforms"></a><span data-ttu-id="26f33-103">Отсутствует проверка суффикса A/W на платформах, отличных от Windows</span><span class="sxs-lookup"><span data-stu-id="26f33-103">No A/W suffix probing on non-Windows platforms</span></span>

<span data-ttu-id="26f33-104">Среды выполнения .NET больше не добавляют суффиксы `A` или `W` к именам экспортируемых функций во время проверки для P/Invokes на платформах, отличных от Windows.</span><span class="sxs-lookup"><span data-stu-id="26f33-104">The .NET runtimes no longer add an `A` or `W` suffix to function export names during probing for P/Invokes on non-Windows platforms.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="26f33-105">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="26f33-105">Version introduced</span></span>

<span data-ttu-id="26f33-106">5.0</span><span class="sxs-lookup"><span data-stu-id="26f33-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="26f33-107">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="26f33-107">Change description</span></span>

<span data-ttu-id="26f33-108">[По соглашению Windows](/windows/win32/intl/conventions-for-function-prototypes), к именам функций Windows SDK, которые соответствуют кодовой странице Windows и версиям Юникода, добавляются суффиксы `A` и `W` соответственно.</span><span class="sxs-lookup"><span data-stu-id="26f33-108">[Windows has a convention](/windows/win32/intl/conventions-for-function-prototypes) of adding an `A` or `W` suffix to Windows SDK function names, which correspond to the Windows code page and Unicode versions, respectively.</span></span>

<span data-ttu-id="26f33-109">В предыдущих версиях .NET в средах выполнения CoreCLR и Mono к именам экспорта добавлялись суффиксы `A` или `W` во время обнаружения экспорта для P/Invokes *на всех платформах*.</span><span class="sxs-lookup"><span data-stu-id="26f33-109">In previous versions of .NET, both the CoreCLR and Mono runtimes add an `A` or `W` suffix to the export name during export discovery for P/Invokes *on all platforms*.</span></span>

<span data-ttu-id="26f33-110">В .NET 5.0 и более поздней версии суффиксы `A` или `W` добавляется к именам экспорта во время обнаружения экспорта *только в Windows*.</span><span class="sxs-lookup"><span data-stu-id="26f33-110">In .NET 5.0 and later versions, an `A` or `W` suffix is added to the export name during export discovery *on Windows only*.</span></span> <span data-ttu-id="26f33-111">На платформах UNIX суффикс не добавляется.</span><span class="sxs-lookup"><span data-stu-id="26f33-111">On Unix platforms, the suffix is not added.</span></span> <span data-ttu-id="26f33-112">Семантика обеих сред выполнения на платформе Windows остается неизменной.</span><span class="sxs-lookup"><span data-stu-id="26f33-112">The semantics of both runtimes on the Windows platform remain unchanged.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="26f33-113">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="26f33-113">Reason for change</span></span>

<span data-ttu-id="26f33-114">Это изменение было внесено с целью упрощения проверки на нескольких платформах.</span><span class="sxs-lookup"><span data-stu-id="26f33-114">This change was made to simplify cross-platform probing.</span></span> <span data-ttu-id="26f33-115">Это изменение не должно привести к дополнительным издержкам, так как платформы, отличные от Windows, не содержат такой семантики.</span><span class="sxs-lookup"><span data-stu-id="26f33-115">It's overhead that shouldn't be incurred, given that non-Windows platforms don't contain this semantic.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="26f33-116">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="26f33-116">Recommended action</span></span>

<span data-ttu-id="26f33-117">Чтобы ослабить эффект этого изменения, можно вручную добавить требуемый суффикс на платформах, отличных от Windows.</span><span class="sxs-lookup"><span data-stu-id="26f33-117">To mitigate the change, you can manually add the desired suffix on non-Windows platforms.</span></span> <span data-ttu-id="26f33-118">Пример:</span><span class="sxs-lookup"><span data-stu-id="26f33-118">For example:</span></span>

```csharp
[DllImport(...)]
extern static void SetWindowTextW();
```

## <a name="affected-apis"></a><span data-ttu-id="26f33-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="26f33-119">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Runtime.InteropServices.DllImportAttribute`

### Category

Interop

-->
