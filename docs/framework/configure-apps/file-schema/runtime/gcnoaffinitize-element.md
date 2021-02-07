---
description: 'Дополнительные сведения о: <GCNoAffinitize> element'
title: Гкноаффинитизе, элемент
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 139c0fd9e1ec829a3569b77a85e6526bec765e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754554"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="e7067-103">Элемент \<GCNoAffinitize></span><span class="sxs-lookup"><span data-stu-id="e7067-103">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="e7067-104">Указывает, следует ли привязать потоки сервера GC с ЦП.</span><span class="sxs-lookup"><span data-stu-id="e7067-104">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="e7067-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e7067-105">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7067-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="e7067-106">Attributes and elements</span></span>

<span data-ttu-id="e7067-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e7067-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7067-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e7067-108">Attributes</span></span>

|<span data-ttu-id="e7067-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e7067-109">Attribute</span></span>|<span data-ttu-id="e7067-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e7067-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e7067-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e7067-111">Required attribute.</span></span><br /><br /><span data-ttu-id="e7067-112">Указывает, привязаны ли потоки или кучи серверной сборки мусора с процессорами, доступными на компьютере.</span><span class="sxs-lookup"><span data-stu-id="e7067-112">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="e7067-113">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="e7067-113">enabled attribute</span></span>

|<span data-ttu-id="e7067-114">Значение</span><span class="sxs-lookup"><span data-stu-id="e7067-114">Value</span></span>|<span data-ttu-id="e7067-115">Описание</span><span class="sxs-lookup"><span data-stu-id="e7067-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="e7067-116">Потоки GC сервера аффинитизес с ЦП.</span><span class="sxs-lookup"><span data-stu-id="e7067-116">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="e7067-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e7067-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="e7067-118">Не привязать потоки GC сервера с процессорами.</span><span class="sxs-lookup"><span data-stu-id="e7067-118">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e7067-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e7067-119">Child elements</span></span>

<span data-ttu-id="e7067-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e7067-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e7067-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e7067-121">Parent elements</span></span>

|<span data-ttu-id="e7067-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="e7067-122">Element</span></span>|<span data-ttu-id="e7067-123">Описание</span><span class="sxs-lookup"><span data-stu-id="e7067-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e7067-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7067-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e7067-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="e7067-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e7067-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="e7067-126">Remarks</span></span>

<span data-ttu-id="e7067-127">По умолчанию потоки GC сервера жестко привязаны с соответствующими процессорами.</span><span class="sxs-lookup"><span data-stu-id="e7067-127">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="e7067-128">Каждый из доступных процессоров системы имеет собственную кучу сборщика мусора и поток.</span><span class="sxs-lookup"><span data-stu-id="e7067-128">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="e7067-129">Обычно это предпочтительный параметр, так как он оптимизирует использование кэша.</span><span class="sxs-lookup"><span data-stu-id="e7067-129">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="e7067-130">Начиная с платформа .NET Framework 4.6.2, установив для атрибута элемента **гкноаффинитизе** значение `enabled` `true` , можно указать, что потоки и процессоры GC сервера не должны быть тесно связаны.</span><span class="sxs-lookup"><span data-stu-id="e7067-130">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="e7067-131">Можно указать только элемент конфигурации **гкноаффинитизе** , чтобы не ПРИВЯЗАТЬ потоки GC сервера с процессорами.</span><span class="sxs-lookup"><span data-stu-id="e7067-131">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="e7067-132">Кроме того, его можно использовать вместе с элементом [гчеапкаунт](gcheapcount-element.md) для управления числом куч и потоков GC, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="e7067-132">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="e7067-133">Если `enabled` атрибут элемента **гкноаффинитизе** имеет `false` (значение по умолчанию), можно также использовать элемент [гчеапкаунт](gcheapcount-element.md) , чтобы указать количество потоков и куч GC вместе с элементом [гчеапаффинитиземаск](gcheapaffinitizemask-element.md) , чтобы указать процессоры, к которым будут привязаныся потоки и кучи GC.</span><span class="sxs-lookup"><span data-stu-id="e7067-133">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="e7067-134">Пример</span><span class="sxs-lookup"><span data-stu-id="e7067-134">Example</span></span>

<span data-ttu-id="e7067-135">В следующем примере не привязать потоки GC сервера.</span><span class="sxs-lookup"><span data-stu-id="e7067-135">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="e7067-136">В следующем примере не привязать потоки сервера GC и ограничивает число куч/потоков GC до 10:</span><span class="sxs-lookup"><span data-stu-id="e7067-136">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="e7067-137">См. также</span><span class="sxs-lookup"><span data-stu-id="e7067-137">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e7067-138">Гчеапаффинитиземаск, элемент</span><span class="sxs-lookup"><span data-stu-id="e7067-138">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="e7067-139">Гчеапкаунт, элемент</span><span class="sxs-lookup"><span data-stu-id="e7067-139">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="e7067-140">Основы сборки мусора</span><span class="sxs-lookup"><span data-stu-id="e7067-140">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="e7067-141">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="e7067-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e7067-142">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e7067-142">Configuration File Schema</span></span>](../index.md)
