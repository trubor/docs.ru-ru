---
description: 'Дополнительные сведения о: Гклохсрешолд element'
title: Гклохсрешолд, элемент
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: 5d4ef4e6aaf44642c2307dc27ac2e99e966d3ad0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652813"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="148b1-103">Гклохсрешолд, элемент</span><span class="sxs-lookup"><span data-stu-id="148b1-103">GCLOHThreshold element</span></span>

<span data-ttu-id="148b1-104">Указывает пороговый размер (в байтах), который заставляет сборщик мусора разместить объекты в куче больших объектов (LOH).</span><span class="sxs-lookup"><span data-stu-id="148b1-104">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="148b1-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="148b1-105">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="148b1-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="148b1-106">Attributes</span></span>

|<span data-ttu-id="148b1-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="148b1-107">Attribute</span></span>|<span data-ttu-id="148b1-108">Описание</span><span class="sxs-lookup"><span data-stu-id="148b1-108">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="148b1-109">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="148b1-109">Required attribute.</span></span><br /><br /><span data-ttu-id="148b1-110">Указывает пороговый размер, который приводит к тому, что объекты попадают в кучу больших объектов.</span><span class="sxs-lookup"><span data-stu-id="148b1-110">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="148b1-111">Включенный атрибут</span><span class="sxs-lookup"><span data-stu-id="148b1-111">enabled attribute</span></span>

|<span data-ttu-id="148b1-112">Значение</span><span class="sxs-lookup"><span data-stu-id="148b1-112">Value</span></span>|<span data-ttu-id="148b1-113">Описание</span><span class="sxs-lookup"><span data-stu-id="148b1-113">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="148b1-114">Пороговый размер (в байтах), который приводит к тому, что объекты попадают в кучу больших объектов.</span><span class="sxs-lookup"><span data-stu-id="148b1-114">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="148b1-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="148b1-115">Child elements</span></span>

<span data-ttu-id="148b1-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="148b1-116">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="148b1-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="148b1-117">Parent elements</span></span>

|<span data-ttu-id="148b1-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="148b1-118">Element</span></span>|<span data-ttu-id="148b1-119">Описание</span><span class="sxs-lookup"><span data-stu-id="148b1-119">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="148b1-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="148b1-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="148b1-121">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="148b1-121">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="148b1-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="148b1-122">Remarks</span></span>

<span data-ttu-id="148b1-123">Этот параметр появился в платформа .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="148b1-123">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="148b1-124">См. также</span><span class="sxs-lookup"><span data-stu-id="148b1-124">See also</span></span>

- [<span data-ttu-id="148b1-125">Схема параметров времени выполнения</span><span class="sxs-lookup"><span data-stu-id="148b1-125">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="148b1-126">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="148b1-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="148b1-127">Основы сборки мусора</span><span class="sxs-lookup"><span data-stu-id="148b1-127">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="148b1-128">Параметры конфигурации среды выполнения NET Core для GC</span><span class="sxs-lookup"><span data-stu-id="148b1-128">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
