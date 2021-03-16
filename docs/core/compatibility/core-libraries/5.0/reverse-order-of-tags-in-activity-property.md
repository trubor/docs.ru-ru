---
title: Критическое изменение. Порядок тегов в действии Activity.Tags обращен
description: Сведения о критическом изменении в .NET 5 в основных библиотеках .NET, где Activity.Tags теперь сохраняет элементы в списке в соответствии с порядком их добавления.
ms.date: 11/01/2020
ms.openlocfilehash: f37f44cbe2ea467f0962cd8971d5bf38ce958dfd
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257132"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="f4905-103">Порядок тегов в действии Activity.Tags обращен</span><span class="sxs-lookup"><span data-stu-id="f4905-103">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="f4905-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> теперь сохраняет элементы в списке в соответствии с порядком их добавления, то есть первый добавленный элемент отображается в списке первым.</span><span class="sxs-lookup"><span data-stu-id="f4905-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="f4905-105">Это изменение было внесено в соответствии со [спецификацией атрибутов OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span><span class="sxs-lookup"><span data-stu-id="f4905-105">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

## <a name="change-description"></a><span data-ttu-id="f4905-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f4905-106">Change description</span></span>

<span data-ttu-id="f4905-107">В предыдущих версиях .NET <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> сохраняет элементы в порядке, обратном их добавлению.</span><span class="sxs-lookup"><span data-stu-id="f4905-107">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="f4905-108">Это значит, что первый добавленный элемент является последним в списке.</span><span class="sxs-lookup"><span data-stu-id="f4905-108">That is, the first item added is last in the list.</span></span> <span data-ttu-id="f4905-109">Начиная с .NET 5 порядок элементов теперь обратный, и первый добавленный элемент всегда находится в списке первым.</span><span class="sxs-lookup"><span data-stu-id="f4905-109">Starting in .NET 5, the order of the items is reversed, and the first item added is always first in the list.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f4905-110">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f4905-110">Version introduced</span></span>

<span data-ttu-id="f4905-111">5.0</span><span class="sxs-lookup"><span data-stu-id="f4905-111">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f4905-112">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f4905-112">Recommended action</span></span>

<span data-ttu-id="f4905-113">Если приложение зависит от порядка элементов в списке <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> и выполняется обновление до .NET 5 или более поздней версии, необходимо изменить эту часть кода.</span><span class="sxs-lookup"><span data-stu-id="f4905-113">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5 or later, you'll need to change this part of your code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f4905-114">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f4905-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
