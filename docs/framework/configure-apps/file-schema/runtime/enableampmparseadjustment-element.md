---
description: 'Дополнительные сведения о: <EnableAmPmParseAdjustment> element'
title: Элемент <EnableAmPmParseAdjustment>
ms.date: 03/30/2017
ms.assetid: fda998a5-f538-4f8b-a18c-ee7f35e16938
ms.openlocfilehash: 86fd04ab536f44f0cffdb5a37f4718fc03698485
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787062"
---
# <a name="enableampmparseadjustment-element"></a><span data-ttu-id="4c1e1-103">Элемент \<EnableAmPmParseAdjustment></span><span class="sxs-lookup"><span data-stu-id="4c1e1-103">\<EnableAmPmParseAdjustment> Element</span></span>

<span data-ttu-id="4c1e1-104">Определяет, используют ли методы синтаксического анализа даты и времени настроенный набор правил для синтаксического анализа строк даты, содержащих день, месяц, час и обозначение AM/PM.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-104">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain a day, month, hour, and AM/PM designator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<EnableAmPmParseAdjustment>**  
  
## <a name="syntax"></a><span data-ttu-id="4c1e1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4c1e1-105">Syntax</span></span>  
  
```xml  
<EnableAmPmParseAdjustment enabled="0"|"1" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c1e1-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4c1e1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4c1e1-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c1e1-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4c1e1-108">Attributes</span></span>  
  
|<span data-ttu-id="4c1e1-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4c1e1-109">Attribute</span></span>|<span data-ttu-id="4c1e1-110">Описание</span><span class="sxs-lookup"><span data-stu-id="4c1e1-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="4c1e1-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4c1e1-112">Указывает, используют ли методы синтаксического анализа даты и времени настроенный набор правил для анализа строк даты, содержащих только день, месяц, час и обозначение AM/PM.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-112">Specifies whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="enabled-attribute"></a><span data-ttu-id="4c1e1-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="4c1e1-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="4c1e1-114">Значение</span><span class="sxs-lookup"><span data-stu-id="4c1e1-114">Value</span></span>|<span data-ttu-id="4c1e1-115">Описание</span><span class="sxs-lookup"><span data-stu-id="4c1e1-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4c1e1-116">0</span><span class="sxs-lookup"><span data-stu-id="4c1e1-116">0</span></span>|<span data-ttu-id="4c1e1-117">Методы синтаксического анализа даты и времени не используют скорректированные правила для анализа строк даты, содержащих только день, месяц, час и обозначение AM/PM.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-117">Date and time parsing methods do not use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
|<span data-ttu-id="4c1e1-118">1</span><span class="sxs-lookup"><span data-stu-id="4c1e1-118">1</span></span>|<span data-ttu-id="4c1e1-119">Методы синтаксического анализа даты и времени используют скорректированные правила для анализа строк даты, содержащих только день, месяц, час и обозначение AM/PM.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-119">Date and time parsing methods use adjusted rules for parsing date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c1e1-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4c1e1-120">Child Elements</span></span>  

 <span data-ttu-id="4c1e1-121">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c1e1-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4c1e1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4c1e1-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="4c1e1-123">Element</span></span>|<span data-ttu-id="4c1e1-124">Описание</span><span class="sxs-lookup"><span data-stu-id="4c1e1-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4c1e1-125">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="4c1e1-126">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c1e1-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="4c1e1-127">Remarks</span></span>  

 <span data-ttu-id="4c1e1-128">`<EnableAmPmParseAdjustment>`Элемент определяет, как следующие методы анализируют строку даты, которая содержит числовой день и месяц, за которыми следует час и обозначение AM/PM (например, "4/10 6 AM"):</span><span class="sxs-lookup"><span data-stu-id="4c1e1-128">The `<EnableAmPmParseAdjustment>` element controls how the following methods parse a date string that contains a numeric day and month followed by an hour and an AM/PM designator (such as "4/10 6 AM"):</span></span>  
  
- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTime.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.DateTimeOffset.TryParse%2A?displayProperty=nameWithType>  
  
- <xref:System.Convert.ToDateTime%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="4c1e1-129">Другие шаблоны не затрагиваются.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-129">No other patterns are affected.</span></span>  
  
 <span data-ttu-id="4c1e1-130">`<EnableAmPmParseAdjustment>`Элемент не влияет на <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType> методы,, <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType> <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType> и <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4c1e1-130">The `<EnableAmPmParseAdjustment>` element has no effect on the  <xref:System.DateTime.ParseExact%2A?displayProperty=nameWithType>,  <xref:System.DateTime.TryParseExact%2A?displayProperty=nameWithType>, <xref:System.DateTimeOffset.ParseExact%2A?displayProperty=nameWithType>, and <xref:System.DateTimeOffset.TryParseExact%2A?displayProperty=nameWithType> methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4c1e1-131">В .NET Core и .NET Native настроенные правила анализа AM/PM включены по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-131">In .NET Core and .NET Native, the adjusted AM/PM parsing rules are enabled by default.</span></span>  
  
 <span data-ttu-id="4c1e1-132">Если правило коррекции синтаксического анализа не включено, первая цифра строки интерпретируется как час 12-часового времени, а оставшаяся часть строки, за исключением обозначения AM/PM, игнорируется.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-132">If the parsing adjustment rule is not enabled, the first digit of the string is interpreted as the hour of the 12-hour clock, and the remainder of the string except for the AM/PM designator is ignored.</span></span> <span data-ttu-id="4c1e1-133">Дата и время, возвращаемые методом анализа, состоят из текущей даты и часа дня, извлеченных из строки даты.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-133">The date and time returned by the parsing method consists of the current date and the hour of the day extracted from the date string.</span></span>  
  
 <span data-ttu-id="4c1e1-134">Если правило коррекции синтаксического анализа включено, метод синтаксического анализа интерпретирует день и месяц как принадлежащий текущему году и интерпретирует время как час 12-часового времени.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-134">If the parsing adjustment rule is enabled, parsing method interpret the day and month as belonging to the current year, and interpret the time as the hour of the 12-hour clock.</span></span>  
  
 <span data-ttu-id="4c1e1-135">В следующей таблице показано различие в <xref:System.DateTime> значении, когда <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> метод используется для синтаксического анализа строки "" 4/10 6 AM "со `<EnableAmPmParseAdjustment>` свойством элемента, `enabled` имеющим значение" 0 "или" 1 ".</span><span class="sxs-lookup"><span data-stu-id="4c1e1-135">The following table illustrates the difference in the <xref:System.DateTime> value when the <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> method is used to parse the string ""4/10 6 AM" with the `<EnableAmPmParseAdjustment>` element's `enabled` property  set to "0" or "1".</span></span> <span data-ttu-id="4c1e1-136">Предполагается, что сегодняшняя дата — 5 января 2017, а дата отображается так, как если бы она была отформатирована с использованием строки формата "G" указанного языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="4c1e1-136">It assumes that today's date is January 5, 2017, and displays the date as if it is formatted using the specified culture's "G" format string.</span></span>  
  
|<span data-ttu-id="4c1e1-137">Название языка и региональных параметров</span><span class="sxs-lookup"><span data-stu-id="4c1e1-137">Culture name</span></span>|<span data-ttu-id="4c1e1-138">Enabled = "0"</span><span class="sxs-lookup"><span data-stu-id="4c1e1-138">enabled="0"</span></span>|<span data-ttu-id="4c1e1-139">Enabled = "1"</span><span class="sxs-lookup"><span data-stu-id="4c1e1-139">enabled="1"</span></span>|  
|------------------|------------------|------------------|  
|<span data-ttu-id="4c1e1-140">en-US</span><span class="sxs-lookup"><span data-stu-id="4c1e1-140">en-US</span></span>|<span data-ttu-id="4c1e1-141">1/5/2017 4:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="4c1e1-141">1/5/2017 4:00:00 AM</span></span>|<span data-ttu-id="4c1e1-142">4/10/2017 6:00:00 AM</span><span class="sxs-lookup"><span data-stu-id="4c1e1-142">4/10/2017 6:00:00 AM</span></span>|  
|<span data-ttu-id="4c1e1-143">en-GB</span><span class="sxs-lookup"><span data-stu-id="4c1e1-143">en-GB</span></span>|<span data-ttu-id="4c1e1-144">5/1/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="4c1e1-144">5/1/2017 6:00:00</span></span>|<span data-ttu-id="4c1e1-145">10/4/2017 6:00:00</span><span class="sxs-lookup"><span data-stu-id="4c1e1-145">10/4/2017 6:00:00</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c1e1-146">См. также</span><span class="sxs-lookup"><span data-stu-id="4c1e1-146">See also</span></span>

- [<span data-ttu-id="4c1e1-147">\<runtime> Элемент</span><span class="sxs-lookup"><span data-stu-id="4c1e1-147">\<runtime> Element</span></span>](runtime-element.md)
- [<span data-ttu-id="4c1e1-148">\<configuration> Элемент</span><span class="sxs-lookup"><span data-stu-id="4c1e1-148">\<configuration> Element</span></span>](../configuration-element.md)
