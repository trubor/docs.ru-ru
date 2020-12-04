---
title: Критическое изменение. Распознавание URI UNC-путей в UNIX
description: Сведения о критическом изменении .NET 5.0 в основных библиотеках .NET, где класс URI теперь распознает строки, начинающиеся с двух косых черт, как пути в формате UNC в операционных системах UNIX.
ms.date: 11/01/2020
ms.openlocfilehash: 0d5d9cd8dd869f24e94d15724e5e16eaddf6ed47
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759638"
---
# <a name="uri-recognition-of-unc-paths-on-unix"></a><span data-ttu-id="cb911-103">Распознавание URI UNC-путей в UNIX</span><span class="sxs-lookup"><span data-stu-id="cb911-103">Uri recognition of UNC paths on Unix</span></span>

<span data-ttu-id="cb911-104">Класс <xref:System.Uri> теперь распознает строки, начинающиеся с двух косых черт (`//`) как пути в формате UNC в операционных системах UNIX.</span><span class="sxs-lookup"><span data-stu-id="cb911-104">The <xref:System.Uri> class now recognizes strings that start with two forward slashes (`//`) as universal naming convention (UNC) paths on Unix operating systems.</span></span> <span data-ttu-id="cb911-105">Это изменение делает поведение для таких строк согласованным на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="cb911-105">This change makes the behavior for such strings consistent across all platforms.</span></span>

## <a name="change-description"></a><span data-ttu-id="cb911-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="cb911-106">Change description</span></span>

<span data-ttu-id="cb911-107">В предыдущих версиях .NET класс <xref:System.Uri> распознавал строки, начинающиеся с двух косых черт, например `//contoso`, как абсолютные пути к файлам в операционных системах UNIX.</span><span class="sxs-lookup"><span data-stu-id="cb911-107">In previous versions of .NET, the <xref:System.Uri> class recognizes strings that start with two forward slashes, for example, `//contoso`, as absolute file paths on Unix operating systems.</span></span> <span data-ttu-id="cb911-108">Однако в Windows такие строки распознаются как UNC-пути.</span><span class="sxs-lookup"><span data-stu-id="cb911-108">However, on Windows, such strings are recognized as UNC paths.</span></span>

<span data-ttu-id="cb911-109">Начиная с .NET 5.0 класс <xref:System.Uri> распознает строки, начинающиеся с двух косых черт, как UNC-пути на всех платформах, включая UNIX.</span><span class="sxs-lookup"><span data-stu-id="cb911-109">Starting in .NET 5.0,  the <xref:System.Uri> class recognizes strings that start with two forward slashes as UNC paths on all platforms, including Unix.</span></span> <span data-ttu-id="cb911-110">Кроме того, свойства ведут себя в соответствии с семантикой UNC:</span><span class="sxs-lookup"><span data-stu-id="cb911-110">In addition, properties behave according to UNC semantics:</span></span>

- <span data-ttu-id="cb911-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> возвращает `true`.</span><span class="sxs-lookup"><span data-stu-id="cb911-111"><xref:System.Uri.IsUnc?displayProperty=nameWithType> returns `true`.</span></span>
- <span data-ttu-id="cb911-112">Символы обратной косой черты в пути заменяются прямой косой чертой.</span><span class="sxs-lookup"><span data-stu-id="cb911-112">Backslashes in the path are replaced with forward slashes.</span></span> <span data-ttu-id="cb911-113">Например, `//first\second` преобразуется в `//first/second`.</span><span class="sxs-lookup"><span data-stu-id="cb911-113">For example, `//first\second` becomes `//first/second`.</span></span>
- <span data-ttu-id="cb911-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> не кодирует символы процентами.</span><span class="sxs-lookup"><span data-stu-id="cb911-114"><xref:System.Uri.LocalPath?displayProperty=nameWithType> doesn't percent-encode characters.</span></span> <span data-ttu-id="cb911-115">Например, `//first/\uFFF0` *не* преобразуется в `//first/%EF%BF%B0`.</span><span class="sxs-lookup"><span data-stu-id="cb911-115">For example, `//first/\uFFF0` is *not* converted to `//first/%EF%BF%B0`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="cb911-116">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="cb911-116">Version introduced</span></span>

<span data-ttu-id="cb911-117">5.0</span><span class="sxs-lookup"><span data-stu-id="cb911-117">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="cb911-118">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="cb911-118">Recommended action</span></span>

<span data-ttu-id="cb911-119">От разработчика не требуется никаких действий.</span><span class="sxs-lookup"><span data-stu-id="cb911-119">No action is required on the part of the developer.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="cb911-120">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="cb911-120">Affected APIs</span></span>

- <xref:System.Uri?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `T:System.Uri`

-->
