---
description: 'Дополнительные сведения о: <gcServer> element'
title: gcServer, элемент
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: bed347699786682421292392a8d2449b7aac61d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754541"
---
# <a name="gcserver-element"></a><span data-ttu-id="066de-103">Элемент \<gcServer></span><span class="sxs-lookup"><span data-stu-id="066de-103">\<gcServer> element</span></span>

<span data-ttu-id="066de-104">Указывает, выполняет ли среда CLR сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="066de-104">Specifies whether the common language runtime runs server garbage collection.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer>

## <a name="syntax"></a><span data-ttu-id="066de-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="066de-105">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="066de-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="066de-106">Attributes and elements</span></span>

<span data-ttu-id="066de-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="066de-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="066de-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="066de-108">Attributes</span></span>

|<span data-ttu-id="066de-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="066de-109">Attribute</span></span>|<span data-ttu-id="066de-110">Описание</span><span class="sxs-lookup"><span data-stu-id="066de-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="066de-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="066de-111">Required attribute.</span></span><br /><br /><span data-ttu-id="066de-112">Указывает, выполняет ли среда выполнения сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="066de-112">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="066de-113">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="066de-113">enabled attribute</span></span>

|<span data-ttu-id="066de-114">Значение</span><span class="sxs-lookup"><span data-stu-id="066de-114">Value</span></span>|<span data-ttu-id="066de-115">Описание</span><span class="sxs-lookup"><span data-stu-id="066de-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="066de-116">Не выполняет сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="066de-116">Does not run server garbage collection.</span></span> <span data-ttu-id="066de-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="066de-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="066de-118">Выполняет сборку мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="066de-118">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="066de-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="066de-119">Child elements</span></span>

<span data-ttu-id="066de-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="066de-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="066de-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="066de-121">Parent elements</span></span>

|<span data-ttu-id="066de-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="066de-122">Element</span></span>|<span data-ttu-id="066de-123">Описание</span><span class="sxs-lookup"><span data-stu-id="066de-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="066de-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="066de-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="066de-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="066de-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="066de-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="066de-126">Remarks</span></span>

<span data-ttu-id="066de-127">Среда CLR поддерживает два типа сборки мусора: сборку мусора рабочей станции, которая доступна во всех системах, и сборку мусора сервера, которая доступна в многопроцессорных системах.</span><span class="sxs-lookup"><span data-stu-id="066de-127">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="066de-128">Используйте элемент **gcServer** для управления типом сборки мусора, ВЫПОЛНЯЕМой средой CLR.</span><span class="sxs-lookup"><span data-stu-id="066de-128">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="066de-129">Используйте свойство <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>, чтобы определить, включена ли сборка мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="066de-129">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="066de-130">Для однопроцессорных компьютеров сборка мусора рабочей станции по умолчанию должна быть самым быстрым вариантом.</span><span class="sxs-lookup"><span data-stu-id="066de-130">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="066de-131">Для двухпроцессорных компьютеров можно использовать сборку мусора как рабочей станции, так и сервера.</span><span class="sxs-lookup"><span data-stu-id="066de-131">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="066de-132">Сборка мусора сервера должно быть самым быстрым вариантом при наличии более двух процессоров.</span><span class="sxs-lookup"><span data-stu-id="066de-132">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="066de-133">Чаще всего многопроцессорные серверные системы отключают серверную сборку мусора и используют СБОРЩИКи рабочих станций, если на одном компьютере работает много экземпляров серверного приложения.</span><span class="sxs-lookup"><span data-stu-id="066de-133">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="066de-134">Этот элемент может использоваться только в файле конфигурации приложения; в файле конфигурации компьютера он игнорируется.</span><span class="sxs-lookup"><span data-stu-id="066de-134">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="066de-135">В платформе .NET Framework версии 4 и более ранних версиях параллельная сборка мусора недоступна, если включена серверная сборка мусора.</span><span class="sxs-lookup"><span data-stu-id="066de-135">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="066de-136">С версии .NET Framework 4.5 серверная сборка мусора является параллельной.</span><span class="sxs-lookup"><span data-stu-id="066de-136">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="066de-137">Чтобы использовать непараллельную сборку мусора сервера, установите для элемента **gcServer** значение `true` , а для [элемента gcConcurrent](gcconcurrent-element.md) — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="066de-137">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="066de-138">Начиная с платформа .NET Framework 4.6.2 можно также использовать следующие элементы для настройки GC сервера:</span><span class="sxs-lookup"><span data-stu-id="066de-138">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="066de-139">[Гкноаффинитизе](gcnoaffinitize-element.md), который указывает, существует ли сходство между кучами и процессорами серверной сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="066de-139">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="066de-140">По умолчанию для каждого процессора существует одна куча сервера GC.</span><span class="sxs-lookup"><span data-stu-id="066de-140">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="066de-141">[Гчеапкаунт](gcheapcount-element.md), ограничивающее количество куч, используемых процессом.</span><span class="sxs-lookup"><span data-stu-id="066de-141">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="066de-142">[Гчеапаффинитиземаск](gcheapaffinitizemask-element.md), который определяет сходство между доступными кучами сервера GC и отдельными процессорами.</span><span class="sxs-lookup"><span data-stu-id="066de-142">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="066de-143">Пример</span><span class="sxs-lookup"><span data-stu-id="066de-143">Example</span></span>

<span data-ttu-id="066de-144">В следующем примере включается сборка мусора сервера:</span><span class="sxs-lookup"><span data-stu-id="066de-144">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="066de-145">См. также</span><span class="sxs-lookup"><span data-stu-id="066de-145">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="066de-146">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="066de-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="066de-147">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="066de-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="066de-148">Отключение параллельной сборки мусора</span><span class="sxs-lookup"><span data-stu-id="066de-148">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
