---
description: 'Дополнительные сведения о: <GCCpuGroup> element'
title: Элемент <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: d4b3aa7084cbc2cb23b273bea95ffaec6e3a74d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786997"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="c201f-103">Элемент \<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="c201f-103">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="c201f-104">Определяет, поддерживает ли сборка мусора несколько групп ЦП.</span><span class="sxs-lookup"><span data-stu-id="c201f-104">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="c201f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c201f-105">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c201f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c201f-106">Attributes and Elements</span></span>

<span data-ttu-id="c201f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c201f-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c201f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c201f-108">Attributes</span></span>

|<span data-ttu-id="c201f-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c201f-109">Attribute</span></span>|<span data-ttu-id="c201f-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c201f-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c201f-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="c201f-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="c201f-112">Определяет, поддерживает ли сборка мусора несколько групп ЦП.</span><span class="sxs-lookup"><span data-stu-id="c201f-112">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="c201f-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="c201f-113">enabled Attribute</span></span>

|<span data-ttu-id="c201f-114">Значение</span><span class="sxs-lookup"><span data-stu-id="c201f-114">Value</span></span>|<span data-ttu-id="c201f-115">Описание</span><span class="sxs-lookup"><span data-stu-id="c201f-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c201f-116">Сборка мусора не поддерживает несколько групп ЦП.</span><span class="sxs-lookup"><span data-stu-id="c201f-116">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="c201f-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c201f-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="c201f-118">Сборка мусора поддерживает несколько групп ЦП, если включена сборка мусора сервера.</span><span class="sxs-lookup"><span data-stu-id="c201f-118">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c201f-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c201f-119">Child Elements</span></span>

<span data-ttu-id="c201f-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c201f-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c201f-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c201f-121">Parent Elements</span></span>

|<span data-ttu-id="c201f-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="c201f-122">Element</span></span>|<span data-ttu-id="c201f-123">Описание</span><span class="sxs-lookup"><span data-stu-id="c201f-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c201f-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c201f-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c201f-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="c201f-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c201f-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="c201f-126">Remarks</span></span>

<span data-ttu-id="c201f-127">Если на компьютере установлено несколько групп ЦП и включена сборка мусора сервера (см. [\<gcServer>](gcserver-element.md) элемент), включение этого элемента расширяет сбор мусора во всех группах ЦП и учитывает все ядра при создании и балансировке куч.</span><span class="sxs-lookup"><span data-stu-id="c201f-127">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="c201f-128">Этот элемент применяется только к потокам сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="c201f-128">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="c201f-129">Чтобы среда выполнения распространяла пользовательские потоки во всех группах ЦП, необходимо также включить [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) элемент.</span><span class="sxs-lookup"><span data-stu-id="c201f-129">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="c201f-130">Пример</span><span class="sxs-lookup"><span data-stu-id="c201f-130">Example</span></span>

<span data-ttu-id="c201f-131">В следующем примере показано, как включить сбор мусора для нескольких групп ЦП.</span><span class="sxs-lookup"><span data-stu-id="c201f-131">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c201f-132">См. также</span><span class="sxs-lookup"><span data-stu-id="c201f-132">See also</span></span>

- [<span data-ttu-id="c201f-133">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="c201f-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c201f-134">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="c201f-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c201f-135">Отключение параллельной сборки мусора</span><span class="sxs-lookup"><span data-stu-id="c201f-135">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="c201f-136">Сборка мусора рабочей станции и сборка мусора сервера</span><span class="sxs-lookup"><span data-stu-id="c201f-136">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
