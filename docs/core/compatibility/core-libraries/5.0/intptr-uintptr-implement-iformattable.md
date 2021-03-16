---
title: Критическое изменение. IntPtr и UIntPtr реализуют IFormattable
description: Ознакомьтесь с критическим изменением .NET 5 в основных библиотеках .NET, где IntPtr и UIntPtr теперь реализуют IFormattable.
ms.date: 11/01/2020
ms.openlocfilehash: adfb68807d5fa5f0c750fb41ef75951f63a4b2d5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257444"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="8a9a0-103">IntPtr и UIntPtr реализуют IFormattable</span><span class="sxs-lookup"><span data-stu-id="8a9a0-103">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="8a9a0-104"><xref:System.IntPtr> и <xref:System.UIntPtr> теперь реализуют <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-104"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="8a9a0-105">Функции, которые проверяют наличие поддержки <xref:System.IFormattable>, теперь могут возвращать разные результаты для этих типов, поскольку они могут передавать описатель формата, а также язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-105">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

## <a name="change-description"></a><span data-ttu-id="8a9a0-106">Описание изменений</span><span class="sxs-lookup"><span data-stu-id="8a9a0-106">Change description</span></span>

<span data-ttu-id="8a9a0-107">В предыдущих версиях .NET <xref:System.IntPtr> и <xref:System.UIntPtr> не реализуют <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-107">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="8a9a0-108">Функции, которые проверяют наличие поддержки <xref:System.IFormattable>, могут возвращаться к простому вызову <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> или <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, что означает, что описатели формата, а также языки и региональные параметры не учитываются.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-108">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="8a9a0-109">В .NET 5 и более поздних версиях <xref:System.IntPtr> и <xref:System.UIntPtr> реализуют <xref:System.IFormattable>.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-109">In .NET 5 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="8a9a0-110">Функции, которые проверяют наличие поддержки <xref:System.IFormattable>, теперь могут возвращать разные результаты для этих типов, поскольку они могут передавать описатель формата, а также язык и региональные параметры.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-110">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="8a9a0-111">Это изменение влияет на такие сценарии, как интерполяция строк и <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-111">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="8a9a0-112">Причина изменения</span><span class="sxs-lookup"><span data-stu-id="8a9a0-112">Reason for change</span></span>

<span data-ttu-id="8a9a0-113"><xref:System.IntPtr> и <xref:System.UIntPtr> теперь имеют языковую поддержку в C# помощью ключевых слов `nint` и `nuint`.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-113"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="8a9a0-114">Резервные типы были обновлены для обеспечения ближайшей четности (по возможности) с функциями, предоставляемыми другими примитивными типами, такими как <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-114">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="8a9a0-115">Представленная версия</span><span class="sxs-lookup"><span data-stu-id="8a9a0-115">Version introduced</span></span>

<span data-ttu-id="8a9a0-116">5.0</span><span class="sxs-lookup"><span data-stu-id="8a9a0-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="8a9a0-117">Рекомендованное действие</span><span class="sxs-lookup"><span data-stu-id="8a9a0-117">Recommended action</span></span>

<span data-ttu-id="8a9a0-118">Если вы не хотите использовать описатель формата или настраиваемые язык и региональные параметры при отображении значений этих типов, можно вызвать перегрузки <xref:System.IntPtr.ToString?displayProperty=nameWithType> и <xref:System.UIntPtr.ToString?displayProperty=nameWithType> для `ToString()`.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-118">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="8a9a0-119">Затронутые API</span><span class="sxs-lookup"><span data-stu-id="8a9a0-119">Affected APIs</span></span>

<span data-ttu-id="8a9a0-120">Невозможно обнаружить с помощью анализа API.</span><span class="sxs-lookup"><span data-stu-id="8a9a0-120">Not detectable via API analysis.</span></span>

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
