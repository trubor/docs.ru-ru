---
description: Дополнительные сведения см. в статье Создание часовых поясов без правил коррекции.
title: Практическое руководство. Создание часовых поясов без правил коррекции
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], adjustment rule
- time zones [.NET], creating
- adjustment rule [.NET]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
ms.openlocfilehash: c2d1f2d2ea21c53c6a3b41603be4f31ec5442a30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99702734"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="93cb4-103">Практическое руководство. Создание часовых поясов без правил коррекции</span><span class="sxs-lookup"><span data-stu-id="93cb4-103">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="93cb4-104">Точные сведения о часовом поясе, необходимые для приложения, могут отсутствовать в определенной системе по нескольким причинам:</span><span class="sxs-lookup"><span data-stu-id="93cb4-104">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

- <span data-ttu-id="93cb4-105">Часовой пояс никогда не был определен в реестре локальной системы.</span><span class="sxs-lookup"><span data-stu-id="93cb4-105">The time zone has never been defined in the local system's registry.</span></span>

- <span data-ttu-id="93cb4-106">Данные о часовом поясе были изменены или удалены из реестра.</span><span class="sxs-lookup"><span data-stu-id="93cb4-106">Data about the time zone has been modified or removed from the registry.</span></span>

- <span data-ttu-id="93cb4-107">Часовой пояс существует, но не содержит достоверных сведений о корректировках часового пояса для определенного периода предыстории.</span><span class="sxs-lookup"><span data-stu-id="93cb4-107">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="93cb4-108">В таких случаях можно вызвать <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> метод, чтобы определить часовой пояс, необходимый для приложения.</span><span class="sxs-lookup"><span data-stu-id="93cb4-108">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="93cb4-109">Перегрузки этого метода можно использовать для создания часового пояса с правилами коррекции или без них.</span><span class="sxs-lookup"><span data-stu-id="93cb4-109">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="93cb4-110">Если часовой пояс поддерживает переход на летнее время, можно определить корректировки с помощью фиксированных или плавающих правил коррекции.</span><span class="sxs-lookup"><span data-stu-id="93cb4-110">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="93cb4-111">(Определения этих терминов см. в подразделе «терминология часовых поясов» раздела « [Общие сведения о часовом поясе](time-zone-overview.md)».)</span><span class="sxs-lookup"><span data-stu-id="93cb4-111">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="93cb4-112">Пользовательские часовые пояса, созданные путем вызова <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> метода, не добавляются в реестр.</span><span class="sxs-lookup"><span data-stu-id="93cb4-112">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="93cb4-113">Вместо этого доступ к ним можно получить только через ссылку на объект, возвращенную <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> вызовом метода.</span><span class="sxs-lookup"><span data-stu-id="93cb4-113">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="93cb4-114">В этом разделе показано, как создать часовой пояс без правил коррекции.</span><span class="sxs-lookup"><span data-stu-id="93cb4-114">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="93cb4-115">Сведения о создании часового пояса, поддерживающего правила коррекции летнего времени, см. [в разделе Создание часовых поясов с правилами коррекции](create-time-zones-with-adjustment-rules.md).</span><span class="sxs-lookup"><span data-stu-id="93cb4-115">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="93cb4-116">Создание часового пояса без правил коррекции</span><span class="sxs-lookup"><span data-stu-id="93cb4-116">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="93cb4-117">Определите отображаемое имя часового пояса.</span><span class="sxs-lookup"><span data-stu-id="93cb4-117">Define the time zone's display name.</span></span>

   <span data-ttu-id="93cb4-118">Отображаемое имя соответствует довольно стандартному формату, в котором смещение часового пояса относительно времени в формате UTC заключено в круглые скобки. за ним следует строка, определяющая часовой пояс, один или несколько городов в часовом поясе, а также одну или несколько стран или регионов в часовом поясе.</span><span class="sxs-lookup"><span data-stu-id="93cb4-118">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="93cb4-119">Определите имя стандартного времени часового пояса.</span><span class="sxs-lookup"><span data-stu-id="93cb4-119">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="93cb4-120">Как правило, эта строка также используется в качестве идентификатора часового пояса.</span><span class="sxs-lookup"><span data-stu-id="93cb4-120">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="93cb4-121">Если вы хотите использовать другой идентификатор, отличный от стандартного имени часового пояса, определите идентификатор часового пояса.</span><span class="sxs-lookup"><span data-stu-id="93cb4-121">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="93cb4-122">Создайте экземпляр <xref:System.TimeSpan> объекта, который определяет смещение часового пояса относительно времени в формате UTC.</span><span class="sxs-lookup"><span data-stu-id="93cb4-122">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="93cb4-123">Часовые пояса со временем, превышающим время UTC, имеют положительное смещение.</span><span class="sxs-lookup"><span data-stu-id="93cb4-123">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="93cb4-124">Часовые пояса со временем, предшествующим UTC, имеют отрицательное смещение.</span><span class="sxs-lookup"><span data-stu-id="93cb4-124">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="93cb4-125">Вызовите <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> метод, чтобы создать экземпляр нового часового пояса.</span><span class="sxs-lookup"><span data-stu-id="93cb4-125">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="93cb4-126">Пример</span><span class="sxs-lookup"><span data-stu-id="93cb4-126">Example</span></span>

<span data-ttu-id="93cb4-127">В следующем примере определяется пользовательский часовой пояс для Моусон, Антарктида, для которого не заданы правила коррекции.</span><span class="sxs-lookup"><span data-stu-id="93cb4-127">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="93cb4-128">Строка, назначенная <xref:System.TimeZoneInfo.DisplayName%2A> свойству, соответствует стандартному формату, в котором за смещение часового пояса от времени UTC следует понятное описание часового пояса.</span><span class="sxs-lookup"><span data-stu-id="93cb4-128">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="93cb4-129">Компиляция кода</span><span class="sxs-lookup"><span data-stu-id="93cb4-129">Compiling the code</span></span>

<span data-ttu-id="93cb4-130">Для этого примера требуются:</span><span class="sxs-lookup"><span data-stu-id="93cb4-130">This example requires:</span></span>

- <span data-ttu-id="93cb4-131">Для импорта следующих пространств имен:</span><span class="sxs-lookup"><span data-stu-id="93cb4-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="93cb4-132">См. также</span><span class="sxs-lookup"><span data-stu-id="93cb4-132">See also</span></span>

- [<span data-ttu-id="93cb4-133">Даты, время и часовые пояса</span><span class="sxs-lookup"><span data-stu-id="93cb4-133">Dates, times, and time zones</span></span>](index.md)
- [<span data-ttu-id="93cb4-134">Общие сведения о часовых поясах</span><span class="sxs-lookup"><span data-stu-id="93cb4-134">Time zone overview</span></span>](time-zone-overview.md)
- [<span data-ttu-id="93cb4-135">Как создать Часовые пояса с правилами коррекции</span><span class="sxs-lookup"><span data-stu-id="93cb4-135">How to: Create time zones with adjustment rules</span></span>](create-time-zones-with-adjustment-rules.md)
