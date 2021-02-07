---
description: 'Дополнительные сведения о: <relativeBindForResources> element'
title: Элемент <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: f08d8f8a8fc4bb14d28762254dca99788d44a858
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712926"
---
# <a name="relativebindforresources-element"></a><span data-ttu-id="18daa-103">Элемент \<relativeBindForResources></span><span class="sxs-lookup"><span data-stu-id="18daa-103">\<relativeBindForResources> Element</span></span>

<span data-ttu-id="18daa-104">Оптимизирует поиск вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="18daa-104">Optimizes the probe for satellite assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
## <a name="syntax"></a><span data-ttu-id="18daa-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18daa-105">Syntax</span></span>  
  
```xml
<relativeBindForResources
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18daa-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="18daa-106">Attributes and Elements</span></span>  

 <span data-ttu-id="18daa-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="18daa-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18daa-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="18daa-108">Attributes</span></span>  
  
|<span data-ttu-id="18daa-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="18daa-109">Attribute</span></span>|<span data-ttu-id="18daa-110">Описание</span><span class="sxs-lookup"><span data-stu-id="18daa-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="18daa-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="18daa-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="18daa-112">Указывает, оптимизирует ли среда CLR проверку на наличие вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="18daa-112">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="18daa-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="18daa-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="18daa-114">Значение</span><span class="sxs-lookup"><span data-stu-id="18daa-114">Value</span></span>|<span data-ttu-id="18daa-115">Описание</span><span class="sxs-lookup"><span data-stu-id="18daa-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="18daa-116">Среда выполнения не оптимизирует зонд для вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="18daa-116">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="18daa-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="18daa-117">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="18daa-118">Среда выполнения оптимизирует зонд для вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="18daa-118">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18daa-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="18daa-119">Child Elements</span></span>  

 <span data-ttu-id="18daa-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="18daa-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18daa-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="18daa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="18daa-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="18daa-122">Element</span></span>|<span data-ttu-id="18daa-123">Описание</span><span class="sxs-lookup"><span data-stu-id="18daa-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18daa-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18daa-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="18daa-125">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="18daa-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18daa-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="18daa-126">Remarks</span></span>  

 <span data-ttu-id="18daa-127">Как правило, диспетчер ресурсов зонды для ресурсов, как описано в разделе [Упаковка и развертывание ресурсов](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) .</span><span class="sxs-lookup"><span data-stu-id="18daa-127">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="18daa-128">Это означает, что при диспетчер ресурсов зондах для конкретной локализованной версии ресурса она может искать в глобальном кэше сборок, искать в папке, зависящей от языка и региональных параметров, в базе кода приложения, запрашивать установщик Windows для вспомогательных сборок и создавать <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> событие.</span><span class="sxs-lookup"><span data-stu-id="18daa-128">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="18daa-129">`<relativeBindForResources>`Элемент оптимизирует способ диспетчер ресурсов проверки для вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="18daa-129">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="18daa-130">Это может повысить производительность при проверке ресурсов при следующих условиях.</span><span class="sxs-lookup"><span data-stu-id="18daa-130">It can improve performance when probing for resources under the following conditions:</span></span>  
  
- <span data-ttu-id="18daa-131">При развертывании вспомогательной сборки в том же расположении, что и сборка кода.</span><span class="sxs-lookup"><span data-stu-id="18daa-131">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="18daa-132">Иными словами, если сборка кода установлена в глобальном кэше сборок, вспомогательные сборки также должны быть установлены там.</span><span class="sxs-lookup"><span data-stu-id="18daa-132">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="18daa-133">Если сборка кода установлена в базе кода приложения, вспомогательные сборки также должны быть установлены в папке, зависящей от языка и региональных параметров, в базе кода.</span><span class="sxs-lookup"><span data-stu-id="18daa-133">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
- <span data-ttu-id="18daa-134">Если установщик Windows не используется или используется редко для установки вспомогательных сборок по требованию.</span><span class="sxs-lookup"><span data-stu-id="18daa-134">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
- <span data-ttu-id="18daa-135">Когда код приложения не обрабатывает <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> событие.</span><span class="sxs-lookup"><span data-stu-id="18daa-135">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="18daa-136">Установка `enabled` атрибута `<relativeBindForResources>` элемента для `true` оптимизации проверки диспетчер ресурсов для вспомогательных сборок выполняется следующим образом:</span><span class="sxs-lookup"><span data-stu-id="18daa-136">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
- <span data-ttu-id="18daa-137">Он использует расположение сборки родительского кода для проверки вспомогательной сборки.</span><span class="sxs-lookup"><span data-stu-id="18daa-137">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
- <span data-ttu-id="18daa-138">Он не запрашивает установщик Windows для вспомогательных сборок.</span><span class="sxs-lookup"><span data-stu-id="18daa-138">It does not query Windows Installer for satellite assemblies.</span></span>  
  
- <span data-ttu-id="18daa-139">Он не вызывает <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> событие.</span><span class="sxs-lookup"><span data-stu-id="18daa-139">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18daa-140">См. также</span><span class="sxs-lookup"><span data-stu-id="18daa-140">See also</span></span>

- [<span data-ttu-id="18daa-141">Упаковка и развертывание ресурсов</span><span class="sxs-lookup"><span data-stu-id="18daa-141">Packaging and Deploying Resources</span></span>](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="18daa-142">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="18daa-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="18daa-143">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="18daa-143">Configuration File Schema</span></span>](../index.md)
