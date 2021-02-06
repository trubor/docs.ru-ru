---
description: 'Дополнительные сведения о: <performanceCounters> element'
title: Элемент <performanceCounters>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: 3a9a6c42575be3fc7fb5c5d80ffecd940894e164
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639579"
---
# <a name="performancecounters-element"></a><span data-ttu-id="247ec-103">Элемент \<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="247ec-103">\<performanceCounters> Element</span></span>

<span data-ttu-id="247ec-104">Задает размер глобальной памяти, совместно используемой счетчиками производительности.</span><span class="sxs-lookup"><span data-stu-id="247ec-104">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="247ec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="247ec-105">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="247ec-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="247ec-106">Attributes and Elements</span></span>

<span data-ttu-id="247ec-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="247ec-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="247ec-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="247ec-108">Attributes</span></span>

|<span data-ttu-id="247ec-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="247ec-109">Attribute</span></span>|<span data-ttu-id="247ec-110">Описание</span><span class="sxs-lookup"><span data-stu-id="247ec-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="247ec-111">филемаппингсизе</span><span class="sxs-lookup"><span data-stu-id="247ec-111">filemappingsize</span></span>|<span data-ttu-id="247ec-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="247ec-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="247ec-113">Он указывает размер глобальной памяти в байтах, используемой счетчиками производительности.</span><span class="sxs-lookup"><span data-stu-id="247ec-113">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="247ec-114">Значение по умолчанию — 524288.</span><span class="sxs-lookup"><span data-stu-id="247ec-114">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="247ec-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="247ec-115">Child Elements</span></span>

<span data-ttu-id="247ec-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="247ec-116">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="247ec-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="247ec-117">Parent Elements</span></span>

|<span data-ttu-id="247ec-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="247ec-118">Element</span></span>|<span data-ttu-id="247ec-119">Описание</span><span class="sxs-lookup"><span data-stu-id="247ec-119">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="247ec-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="247ec-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="247ec-121">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="247ec-121">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="247ec-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="247ec-122">Remarks</span></span>

<span data-ttu-id="247ec-123">Для публикации данных производительности счетчики производительности используют размещенный в памяти файл или общую память.</span><span class="sxs-lookup"><span data-stu-id="247ec-123">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="247ec-124">Размер общей памяти определяет, сколько экземпляров можно использовать одновременно.</span><span class="sxs-lookup"><span data-stu-id="247ec-124">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="247ec-125">Существует два типа общей памяти: глобальная общая память и отдельная общая память.</span><span class="sxs-lookup"><span data-stu-id="247ec-125">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="247ec-126">Глобальная общая память используется всеми категориями счетчиков производительности, установленными с платформа .NET Framework версиями 1,0 или 1,1.</span><span class="sxs-lookup"><span data-stu-id="247ec-126">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="247ec-127">Категории счетчиков производительности, установленные с платформа .NET Framework версии 2,0, используют отдельную общую память, при этом каждая категория счетчиков производительности имеет собственную память.</span><span class="sxs-lookup"><span data-stu-id="247ec-127">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="247ec-128">Размер глобальной общей памяти можно задать только с помощью файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="247ec-128">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="247ec-129">Размер по умолчанию — 524 288 bДа, максимальный размер — 33 554 432 байт, а минимальный размер — 32 768 байт.</span><span class="sxs-lookup"><span data-stu-id="247ec-129">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="247ec-130">Так как глобальная общая память совместно используется всеми процессами и категориями, первый создатель определяет размер.</span><span class="sxs-lookup"><span data-stu-id="247ec-130">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="247ec-131">Если вы определяете размер в файле конфигурации приложения, этот размер используется только в том случае, если приложение является первым приложением, которое приводит к выполнению счетчиков производительности.</span><span class="sxs-lookup"><span data-stu-id="247ec-131">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="247ec-132">Следовательно, правильное расположение для указания `filemappingsize` значения — это файл Machine.config.</span><span class="sxs-lookup"><span data-stu-id="247ec-132">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="247ec-133">Отдельные счетчики производительности не могут освободить память в глобальной общей памяти, поэтому в конечном итоге исчерпана глобальная общая память, если создано большое количество экземпляров счетчиков производительности с разными именами.</span><span class="sxs-lookup"><span data-stu-id="247ec-133">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="247ec-134">Для размера отдельной общей памяти необходимо сначала указать значение DWORD Филемаппингсизе в разделе реестра HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\ *\<category name>* \перформанце, за которым следует значение, указанное для глобальной общей памяти в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="247ec-134">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="247ec-135">Если значение Филемаппингсизе не существует, то отдельный размер общей памяти устанавливается равным четвертому (1/4) глобальному параметру в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="247ec-135">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="247ec-136">См. также</span><span class="sxs-lookup"><span data-stu-id="247ec-136">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
