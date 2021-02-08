---
description: 'Дополнительные сведения: <Thread_UseAllCpuGroups элемент>'
title: Элемент <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: 3f11ba6855caab25bd261de71c80c78232f2690f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802415"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="43720-103">Элемент \<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="43720-103">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="43720-104">Указывает, распределяет ли среда выполнения управляемые потоки во всех группах ЦП.</span><span class="sxs-lookup"><span data-stu-id="43720-104">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="43720-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="43720-105">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="43720-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="43720-106">Attributes and Elements</span></span>

<span data-ttu-id="43720-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="43720-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="43720-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="43720-108">Attributes</span></span>

|<span data-ttu-id="43720-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="43720-109">Attribute</span></span>|<span data-ttu-id="43720-110">Описание</span><span class="sxs-lookup"><span data-stu-id="43720-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="43720-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="43720-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="43720-112">Указывает, распределяет ли среда выполнения управляемые потоки во всех группах ЦП.</span><span class="sxs-lookup"><span data-stu-id="43720-112">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="43720-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="43720-113">enabled Attribute</span></span>

|<span data-ttu-id="43720-114">Значение</span><span class="sxs-lookup"><span data-stu-id="43720-114">Value</span></span>|<span data-ttu-id="43720-115">Описание</span><span class="sxs-lookup"><span data-stu-id="43720-115">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="43720-116">Среда выполнения не распределяет управляемые потоки между несколькими группами ЦП.</span><span class="sxs-lookup"><span data-stu-id="43720-116">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="43720-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="43720-117">This is the default.</span></span>|
|`true`|<span data-ttu-id="43720-118">Среда выполнения распределяет управляемые потоки между несколькими группами ЦП, если компьютер имеет несколько групп ЦП и [\<GCCpuGroup>](gccpugroup-element.md) элемент включен.</span><span class="sxs-lookup"><span data-stu-id="43720-118">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="43720-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="43720-119">Child Elements</span></span>

<span data-ttu-id="43720-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="43720-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="43720-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="43720-121">Parent Elements</span></span>

|<span data-ttu-id="43720-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="43720-122">Element</span></span>|<span data-ttu-id="43720-123">Описание</span><span class="sxs-lookup"><span data-stu-id="43720-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="43720-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43720-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="43720-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="43720-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="43720-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="43720-126">Remarks</span></span>

<span data-ttu-id="43720-127">Если компьютер имеет несколько групп ЦП, включение этого элемента приводит к тому, что среда выполнения распределяет управляемые потоки по всем группам ЦП.</span><span class="sxs-lookup"><span data-stu-id="43720-127">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="43720-128">Чтобы использовать эту функцию, необходимо также включить [\<GCCpuGroup>](gccpugroup-element.md) элемент, который расширяет сборку мусора на все группы ЦП и учитывает все ядра при создании и балансировке куч.</span><span class="sxs-lookup"><span data-stu-id="43720-128">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="43720-129">Включение [\<GCCpuGroup>](gccpugroup-element.md) элемента требует включения [\<gcServer>](gcserver-element.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="43720-129">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="43720-130">Если эти элементы не включены, включение `<Thread_UseAllCpuGroups>` элемента не оказывает никакого влияния.</span><span class="sxs-lookup"><span data-stu-id="43720-130">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="43720-131">Пример</span><span class="sxs-lookup"><span data-stu-id="43720-131">Example</span></span>

<span data-ttu-id="43720-132">В следующем примере показано, как включить поддержку нескольких групп ЦП.</span><span class="sxs-lookup"><span data-stu-id="43720-132">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="43720-133">См. также</span><span class="sxs-lookup"><span data-stu-id="43720-133">See also</span></span>

- [<span data-ttu-id="43720-134">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="43720-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="43720-135">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="43720-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="43720-136">\<GCCpuGroup> Элемент</span><span class="sxs-lookup"><span data-stu-id="43720-136">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
