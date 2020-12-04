---
title: Критическое изменение. Поле TextFormatFlags.ModifyString является устаревшим
description: Сведения о критическом изменении в .NET 5.0, где поле TextFormatFlags.ModifyString является устаревшим
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759681"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="f0f47-103">Флаг TextFormatFlags.ModifyString является устаревшим</span><span class="sxs-lookup"><span data-stu-id="f0f47-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="f0f47-104">Поле <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> устарело в качестве предупреждения и может быть удалено в будущей версии .NET.</span><span class="sxs-lookup"><span data-stu-id="f0f47-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="f0f47-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="f0f47-105">Change description</span></span>

<span data-ttu-id="f0f47-106">В предыдущих версиях .NET поле перечисления <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> не помечено как устаревшее.</span><span class="sxs-lookup"><span data-stu-id="f0f47-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="f0f47-107">В .NET 5.0 и более поздних версиях оно помечено как устаревшее в качестве предупреждения.</span><span class="sxs-lookup"><span data-stu-id="f0f47-107">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="f0f47-108">Это поле может быть удалено в будущей версии .NET.</span><span class="sxs-lookup"><span data-stu-id="f0f47-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f0f47-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="f0f47-109">Reason for change</span></span>

<span data-ttu-id="f0f47-110">В некоторых ситуациях передача строки в <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> с <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> изменяет строку.</span><span class="sxs-lookup"><span data-stu-id="f0f47-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="f0f47-111">Это влечет за собой нарушение неизменности строки и может привести к неустранимому повреждению состояния среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="f0f47-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f0f47-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="f0f47-112">Version introduced</span></span>

<span data-ttu-id="f0f47-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f0f47-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f0f47-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="f0f47-114">Recommended action</span></span>

<span data-ttu-id="f0f47-115">Обновите весь код, который зависит от <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f0f47-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f0f47-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="f0f47-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
