---
description: 'Дополнительные сведения о: <GCHeapAffinitizeMask> element'
title: Гчеапаффинитиземаск, элемент
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: ea6be3fa3d973f228576db69d0700b1f7ddba585
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786984"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="16037-103">Элемент \<GCHeapAffinitizeMask></span><span class="sxs-lookup"><span data-stu-id="16037-103">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="16037-104">Определяет сходство между кучами сборщика мусора и отдельными процессорами.</span><span class="sxs-lookup"><span data-stu-id="16037-104">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="16037-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16037-105">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16037-106">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="16037-106">Attributes and elements</span></span>

<span data-ttu-id="16037-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="16037-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="16037-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="16037-108">Attributes</span></span>

|<span data-ttu-id="16037-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="16037-109">Attribute</span></span>|<span data-ttu-id="16037-110">Описание</span><span class="sxs-lookup"><span data-stu-id="16037-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="16037-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="16037-111">Required attribute.</span></span><br /><br /><span data-ttu-id="16037-112">Указывает сходство между кучами сборщика мусора и отдельными процессорами.</span><span class="sxs-lookup"><span data-stu-id="16037-112">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="16037-113">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="16037-113">enabled attribute</span></span>

|<span data-ttu-id="16037-114">Значение</span><span class="sxs-lookup"><span data-stu-id="16037-114">Value</span></span>|<span data-ttu-id="16037-115">Описание</span><span class="sxs-lookup"><span data-stu-id="16037-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="16037-116">Десятичное значение, которое образует битовую маску для определения сходства между кучами сервера GC и отдельными процессорами.</span><span class="sxs-lookup"><span data-stu-id="16037-116">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="16037-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="16037-117">Child elements</span></span>

<span data-ttu-id="16037-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="16037-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="16037-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="16037-119">Parent elements</span></span>

|<span data-ttu-id="16037-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="16037-120">Element</span></span>|<span data-ttu-id="16037-121">Описание</span><span class="sxs-lookup"><span data-stu-id="16037-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="16037-122">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16037-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="16037-123">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="16037-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="16037-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="16037-124">Remarks</span></span>

<span data-ttu-id="16037-125">По умолчанию потоки GC сервера жестко привязаны с соответствующими ПРОЦЕССОРами, чтобы существовала одна Куча сборщика мусора, один поток GC сервера и один поток GC для каждого процессора.</span><span class="sxs-lookup"><span data-stu-id="16037-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="16037-126">Начиная с платформа .NET Framework 4.6.2, можно использовать элемент **гчеапаффинитиземаск** для управления соответствием между кучами и процессорами сервера GC, если число куч ограничено элементом **гчеапкаунт** .</span><span class="sxs-lookup"><span data-stu-id="16037-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="16037-127">**Гчеапаффинитиземаск** обычно используется вместе с двумя другими флагами:</span><span class="sxs-lookup"><span data-stu-id="16037-127">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="16037-128">[Гкноаффинитизе](gcnoaffinitize-element.md), который управляет тем, привязаны ли потоки или КУЧИ сервера GC с ЦП.</span><span class="sxs-lookup"><span data-stu-id="16037-128">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="16037-129">`enabled`Для использования параметра гчеапаффинитиземаск атрибут элемента [гкноаффинитизе](gcnoaffinitize-element.md) должен быть `false` (его значение по умолчанию  ).</span><span class="sxs-lookup"><span data-stu-id="16037-129">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="16037-130">[Гчеапкаунт](gcheapcount-element.md), ограничивающее количество куч, используемых процессом для сервера GC.</span><span class="sxs-lookup"><span data-stu-id="16037-130">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="16037-131">По умолчанию для каждого процессора существует одна куча.</span><span class="sxs-lookup"><span data-stu-id="16037-131">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="16037-132">**nnnn** — это битовая маска, выраженная в виде десятичного значения.</span><span class="sxs-lookup"><span data-stu-id="16037-132">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="16037-133">Бит 0 байт 0 представляет процессор 0, бит 1 байт 0 представляет процессор 1 и т. д.</span><span class="sxs-lookup"><span data-stu-id="16037-133">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="16037-134">Пример:</span><span class="sxs-lookup"><span data-stu-id="16037-134">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="16037-135">Значение 1023 — 0x3FF или 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="16037-135">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="16037-136">Процесс использует 10 процессоров, от процессора 0 до процессора 9.</span><span class="sxs-lookup"><span data-stu-id="16037-136">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="16037-137">Пример</span><span class="sxs-lookup"><span data-stu-id="16037-137">Example</span></span>

<span data-ttu-id="16037-138">В следующем примере показано, что приложение использует серверную сборку мусора с 10 кучами и потоками.</span><span class="sxs-lookup"><span data-stu-id="16037-138">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="16037-139">Так как вы не хотите, чтобы эти кучи перекрывались с кучами из других приложений, работающих в системе, используйте **гчеапаффинитиземаск** , чтобы указать, что процесс должен использовать процессоры от 0 до 9.</span><span class="sxs-lookup"><span data-stu-id="16037-139">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="16037-140">См. также</span><span class="sxs-lookup"><span data-stu-id="16037-140">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="16037-141">Гкноаффинитизе, элемент</span><span class="sxs-lookup"><span data-stu-id="16037-141">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="16037-142">Гчеапкаунт, элемент</span><span class="sxs-lookup"><span data-stu-id="16037-142">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="16037-143">Основы сборки мусора</span><span class="sxs-lookup"><span data-stu-id="16037-143">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="16037-144">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="16037-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="16037-145">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="16037-145">Configuration File Schema</span></span>](../index.md)
