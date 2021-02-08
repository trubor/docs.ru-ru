---
description: 'Дополнительные сведения о: <GCHeapCount> element'
title: Гчеапкаунт, элемент
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 9e1e000d647435fe7a8c4b1a8f7549f06c2a3b38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786971"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="37023-103">Элемент \<GCHeapCount></span><span class="sxs-lookup"><span data-stu-id="37023-103">\<GCHeapCount> element</span></span>

<span data-ttu-id="37023-104">Указывает число куч/потоков, используемых для сборки мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="37023-104">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="37023-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="37023-105">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="37023-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="37023-106">Attributes and elements</span></span>

<span data-ttu-id="37023-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="37023-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="37023-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="37023-108">Attributes</span></span>

|<span data-ttu-id="37023-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="37023-109">Attribute</span></span>|<span data-ttu-id="37023-110">Описание</span><span class="sxs-lookup"><span data-stu-id="37023-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="37023-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="37023-111">Required attribute.</span></span><br /><br /><span data-ttu-id="37023-112">Указывает число куч, используемых для сборки мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="37023-112">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="37023-113">Фактическое число куч — это минимальное количество куч, которое вы указали, и количество процессоров, которое может использовать процесс.</span><span class="sxs-lookup"><span data-stu-id="37023-113">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="37023-114">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="37023-114">enabled attribute</span></span>

|<span data-ttu-id="37023-115">Значение</span><span class="sxs-lookup"><span data-stu-id="37023-115">Value</span></span>|<span data-ttu-id="37023-116">Описание</span><span class="sxs-lookup"><span data-stu-id="37023-116">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="37023-117">Число куч, используемых для сервера GC.</span><span class="sxs-lookup"><span data-stu-id="37023-117">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="37023-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="37023-118">Child elements</span></span>

<span data-ttu-id="37023-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="37023-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="37023-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="37023-120">Parent elements</span></span>

|<span data-ttu-id="37023-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="37023-121">Element</span></span>|<span data-ttu-id="37023-122">Описание</span><span class="sxs-lookup"><span data-stu-id="37023-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="37023-123">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37023-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="37023-124">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="37023-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="37023-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="37023-125">Remarks</span></span>

<span data-ttu-id="37023-126">По умолчанию потоки GC сервера жестко привязаны с соответствующими ПРОЦЕССОРами, чтобы существовала одна Куча сборщика мусора, один поток GC сервера и один поток GC для каждого процессора.</span><span class="sxs-lookup"><span data-stu-id="37023-126">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="37023-127">Начиная с платформа .NET Framework 4.6.2, можно использовать элемент **гчеапкаунт** для ограничения числа куч, используемых приложением для сборки мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="37023-127">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="37023-128">Ограничение числа куч, используемых для сервера GC, особенно полезно для систем, работающих с несколькими экземплярами серверного приложения.</span><span class="sxs-lookup"><span data-stu-id="37023-128">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="37023-129">**Гчеапкаунт** обычно используется вместе с двумя другими флагами:</span><span class="sxs-lookup"><span data-stu-id="37023-129">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="37023-130">[Гкноаффинитизе](gcnoaffinitize-element.md), который управляет тем, привязаны ли потоки или КУЧИ сервера GC с ЦП.</span><span class="sxs-lookup"><span data-stu-id="37023-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="37023-131">[Гчеапаффинитиземаск](gcheapaffinitizemask-element.md), который управляет сходством потоков и куч сборки мусора с ЦП.</span><span class="sxs-lookup"><span data-stu-id="37023-131">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="37023-132">Если задано значение **гчеапкаунт** и параметр **гкноаффинитизе** отключен (значение по умолчанию), то существует сходство между потоками и кучами *nn* GC и первыми *nn* процессорами.</span><span class="sxs-lookup"><span data-stu-id="37023-132">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="37023-133">С помощью элемента **гчеапаффинитиземаск** можно указать, какие процессоры используются в кучах сервера процесса.</span><span class="sxs-lookup"><span data-stu-id="37023-133">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="37023-134">В противном случае, если в системе выполняется несколько серверных процессов, их использование процессора будет перекрываться.</span><span class="sxs-lookup"><span data-stu-id="37023-134">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="37023-135">Если задано значение **гчеапкаунт** и включен параметр **гкноаффинитизе** , сборщик мусора ограничивает количество процессоров, используемых для GC сервера, но не привязать КУЧИ и процессоры GC.</span><span class="sxs-lookup"><span data-stu-id="37023-135">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="37023-136">Пример</span><span class="sxs-lookup"><span data-stu-id="37023-136">Example</span></span>

<span data-ttu-id="37023-137">В следующем примере показано, что приложение использует серверную сборку мусора с 10 кучами и потоками.</span><span class="sxs-lookup"><span data-stu-id="37023-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="37023-138">Так как вы не хотите, чтобы эти кучи перекрывались с кучами из других приложений, работающих в системе, используйте **гчеапаффинитиземаск** , чтобы указать, что процесс должен использовать процессоры от 0 до 9.</span><span class="sxs-lookup"><span data-stu-id="37023-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="37023-139">В следующем примере не привязать потоки сервера GC и ограничивает число куч/потоков GC до 10.</span><span class="sxs-lookup"><span data-stu-id="37023-139">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="37023-140">См. также</span><span class="sxs-lookup"><span data-stu-id="37023-140">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="37023-141">Гкноаффинитизе, элемент</span><span class="sxs-lookup"><span data-stu-id="37023-141">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="37023-142">Гчеапаффинитиземаск, элемент</span><span class="sxs-lookup"><span data-stu-id="37023-142">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="37023-143">Основы сборки мусора</span><span class="sxs-lookup"><span data-stu-id="37023-143">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="37023-144">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="37023-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="37023-145">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="37023-145">Configuration File Schema</span></span>](../index.md)
