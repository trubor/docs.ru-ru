---
title: Критическое изменение. Поле TextFormatFlags.ModifyString является устаревшим
description: Сведения о критическом изменении в .NET 5, где поле TextFormatFlags.ModifyString является устаревшим.
ms.date: 11/05/2020
ms.openlocfilehash: 9fe1e04b1ad36070b08af2affdca1e058ec74bb8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256170"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="19d95-103">Флаг TextFormatFlags.ModifyString является устаревшим</span><span class="sxs-lookup"><span data-stu-id="19d95-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="19d95-104">Поле <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> устарело в качестве предупреждения и может быть удалено в будущей версии .NET.</span><span class="sxs-lookup"><span data-stu-id="19d95-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="19d95-105">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="19d95-105">Change description</span></span>

<span data-ttu-id="19d95-106">В предыдущих версиях .NET поле перечисления <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> не помечено как устаревшее.</span><span class="sxs-lookup"><span data-stu-id="19d95-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="19d95-107">В .NET 5 и более поздних версиях оно помечено как устаревшее в качестве предупреждения.</span><span class="sxs-lookup"><span data-stu-id="19d95-107">In .NET 5 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="19d95-108">Это поле может быть удалено в будущей версии .NET.</span><span class="sxs-lookup"><span data-stu-id="19d95-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="19d95-109">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="19d95-109">Reason for change</span></span>

<span data-ttu-id="19d95-110">В некоторых ситуациях передача строки в <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> с <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> изменяет строку.</span><span class="sxs-lookup"><span data-stu-id="19d95-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="19d95-111">Это влечет за собой нарушение неизменности строки и может привести к неустранимому повреждению состояния среды выполнения .NET.</span><span class="sxs-lookup"><span data-stu-id="19d95-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="19d95-112">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="19d95-112">Version introduced</span></span>

<span data-ttu-id="19d95-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="19d95-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="19d95-114">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="19d95-114">Recommended action</span></span>

<span data-ttu-id="19d95-115">Обновите весь код, который зависит от <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19d95-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="19d95-116">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="19d95-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
