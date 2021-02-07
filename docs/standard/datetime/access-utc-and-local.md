---
description: Дополнительные сведения см. в статье как получить доступ к стандартным объектам времени в формате UTC и местному часовому поясу.
title: Практическое руководство. Доступ к предварительно определенным объектам UTC и объектам местных часовых поясов
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET], retrieving
- time zones [.NET], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: 74e3ca601ac0b3a6a684569b0931f8566b5d5d26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702760"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="128ff-103">Практическое руководство. Доступ к предварительно определенным объектам UTC и объектам местных часовых поясов</span><span class="sxs-lookup"><span data-stu-id="128ff-103">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="128ff-104"><xref:System.TimeZoneInfo>Класс предоставляет два свойства, <xref:System.TimeZoneInfo.Utc%2A> и <xref:System.TimeZoneInfo.Local%2A> , которые предоставляют коду доступ к предопределенным объектам часового пояса.</span><span class="sxs-lookup"><span data-stu-id="128ff-104">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="128ff-105">В этом разделе рассматривается порядок работы с объектами <xref:System.TimeZoneInfo>, возвращаемыми этими свойствами.</span><span class="sxs-lookup"><span data-stu-id="128ff-105">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="128ff-106">Получение объекта TimeZoneInfo времени UTC</span><span class="sxs-lookup"><span data-stu-id="128ff-106">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="128ff-107">Используйте `static` свойство ( `Shared` в Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> для доступа к всеобщему скоординированному времени.</span><span class="sxs-lookup"><span data-stu-id="128ff-107">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="128ff-108">Вместо того чтобы назначать <xref:System.TimeZoneInfo> объект, возвращаемый свойством, в объектную переменную, продолжайте обращаться к времени в формате UTC через <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> свойство.</span><span class="sxs-lookup"><span data-stu-id="128ff-108">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="128ff-109">Получение местного часового пояса</span><span class="sxs-lookup"><span data-stu-id="128ff-109">To access the local time zone</span></span>

1. <span data-ttu-id="128ff-110">Используйте `static` свойство ( `Shared` в Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> для доступа к часовому поясу локальной системы.</span><span class="sxs-lookup"><span data-stu-id="128ff-110">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="128ff-111">Вместо того чтобы назначать <xref:System.TimeZoneInfo> объект, возвращаемый свойством, в объектную переменную, продолжайте обращаться к местному часовому поясу через <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> свойство.</span><span class="sxs-lookup"><span data-stu-id="128ff-111">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="128ff-112">Пример</span><span class="sxs-lookup"><span data-stu-id="128ff-112">Example</span></span>

<span data-ttu-id="128ff-113">В следующем коде свойства <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> и <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> используются для преобразования времени из восточного стандартного часового пояса США и Канады, а также для вывода названия часового пояса на консоль.</span><span class="sxs-lookup"><span data-stu-id="128ff-113">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="128ff-114">Необходимо всегда обращаться к локальному часовому поясу через <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> свойство, а не назначать местный часовой пояс <xref:System.TimeZoneInfo> переменной объекта.</span><span class="sxs-lookup"><span data-stu-id="128ff-114">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="128ff-115">Аналогичным образом следует всегда обращаться к всеобщему скоординированному времени через <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> свойство, не назначив часовой пояс в <xref:System.TimeZoneInfo> объектную переменную.</span><span class="sxs-lookup"><span data-stu-id="128ff-115">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="128ff-116">Это предотвращает <xref:System.TimeZoneInfo> недействительность аннулирования переменной объекта при вызове <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> метода.</span><span class="sxs-lookup"><span data-stu-id="128ff-116">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="128ff-117">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="128ff-117">Compiling the code</span></span>

<span data-ttu-id="128ff-118">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="128ff-118">This example requires:</span></span>

- <span data-ttu-id="128ff-119">, Что <xref:System> пространство имен должно быть импортировано с помощью `using` оператора (требуется в коде C#).</span><span class="sxs-lookup"><span data-stu-id="128ff-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="128ff-120">См. также</span><span class="sxs-lookup"><span data-stu-id="128ff-120">See also</span></span>

- [<span data-ttu-id="128ff-121">Даты, время и часовые пояса</span><span class="sxs-lookup"><span data-stu-id="128ff-121">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="128ff-122">Поиск часового пояса, заданного в локальной системе</span><span class="sxs-lookup"><span data-stu-id="128ff-122">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
- [<span data-ttu-id="128ff-123">Как создать объект TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="128ff-123">How to: Instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)
