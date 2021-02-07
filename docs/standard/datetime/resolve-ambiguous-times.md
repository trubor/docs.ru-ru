---
description: Дополнительные сведения см. в статье как устранить неоднозначность времени.
title: Практическое руководство. Разрешение проблемы неоднозначности времени
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], ambiguous time
- ambiguous time [.NET]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: 743aff3303669efcf20e233b1f5b2d520475d5f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702526"
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="cc4c7-103">Практическое руководство. Разрешение проблемы неоднозначности времени</span><span class="sxs-lookup"><span data-stu-id="cc4c7-103">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="cc4c7-104">Неоднозначное время — это время, которое соответствует более чем одному значению времени в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-104">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="cc4c7-105">Это происходит, когда часы переводятся назад, как при переходе в одном часовом поясе с летнего времени на его стандартное время.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-105">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="cc4c7-106">При обработке неоднозначного времени можно выполнить одно из следующих действий:</span><span class="sxs-lookup"><span data-stu-id="cc4c7-106">When handling an ambiguous time, you can do one of the following:</span></span>

- <span data-ttu-id="cc4c7-107">Сделать предположение о том, насколько время соответствует времени в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-107">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="cc4c7-108">Например, можно предположить, что неоднозначное время всегда выражается в стандартном времени часового пояса.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-108">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

- <span data-ttu-id="cc4c7-109">Если неоднозначное время является элементом данных, введенных пользователем, то можно предложить пользователю устранить неоднозначность.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-109">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="cc4c7-110">В этом разделе показано, как устранить неоднозначное время, предполагая, что оно представляет стандартное время часового пояса.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-110">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="cc4c7-111">Сопоставление неоднозначного времени стандартному времени часового пояса</span><span class="sxs-lookup"><span data-stu-id="cc4c7-111">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="cc4c7-112">Вызовите <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> метод, чтобы определить, является ли время неоднозначным.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-112">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="cc4c7-113">Если время неоднозначно, вычтите время из <xref:System.TimeSpan> объекта, возвращенного свойством часового пояса <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .</span><span class="sxs-lookup"><span data-stu-id="cc4c7-113">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="cc4c7-114">Вызовите `static` `Shared` метод (в Visual Basic .NET), <xref:System.DateTime.SpecifyKind%2A> чтобы задать свойству значения даты и времени в формате UTC значение <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cc4c7-114">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="cc4c7-115">Пример</span><span class="sxs-lookup"><span data-stu-id="cc4c7-115">Example</span></span>

<span data-ttu-id="cc4c7-116">В следующем примере показано, как преобразовать неоднозначное время в формат UTC, предполагая, что он представляет стандартное время местного часового пояса.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-116">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="cc4c7-117">Пример состоит из метода с именем `ResolveAmbiguousTime` , который определяет, <xref:System.DateTime> является ли передаваемое ему значение неоднозначным.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-117">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="cc4c7-118">Если значение неоднозначно, метод возвращает <xref:System.DateTime> значение, представляющее соответствующее время в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-118">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="cc4c7-119">Метод обрабатывает это преобразование, вычитая значение свойства местного часового пояса <xref:System.TimeZoneInfo.BaseUtcOffset%2A> из местного времени.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-119">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="cc4c7-120">Как правило, неоднозначное время обрабатывается путем вызова <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> метода для получения массива <xref:System.TimeSpan> объектов, содержащих неоднозначное смещение времени в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-120">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="cc4c7-121">Однако в этом примере происходит произвольное предположение, что неоднозначное время следует всегда сопоставлять со стандартным временем часового пояса.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-121">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="cc4c7-122"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>Свойство возвращает смещение между временем UTC и стандартным временем часового пояса.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-122">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="cc4c7-123">В этом примере все ссылки на местный часовой пояс выполняются через <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> свойство; местный часовой пояс никогда не назначается объектной переменной.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-123">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="cc4c7-124">Это рекомендуемый подход, поскольку вызов <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> метода делает недействительными все объекты, которым назначен местный часовой пояс.</span><span class="sxs-lookup"><span data-stu-id="cc4c7-124">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="cc4c7-125">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="cc4c7-125">Compiling the code</span></span>

<span data-ttu-id="cc4c7-126">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="cc4c7-126">This example requires:</span></span>

- <span data-ttu-id="cc4c7-127">, Что <xref:System> пространство имен должно быть импортировано с помощью `using` оператора (требуется в коде C#).</span><span class="sxs-lookup"><span data-stu-id="cc4c7-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc4c7-128">См. также</span><span class="sxs-lookup"><span data-stu-id="cc4c7-128">See also</span></span>

- [<span data-ttu-id="cc4c7-129">Даты, время и часовые пояса</span><span class="sxs-lookup"><span data-stu-id="cc4c7-129">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="cc4c7-130">Как разрешить пользователям устранять неоднозначность времени</span><span class="sxs-lookup"><span data-stu-id="cc4c7-130">How to: Let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)
