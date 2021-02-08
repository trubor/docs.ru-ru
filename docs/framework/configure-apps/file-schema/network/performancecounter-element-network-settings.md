---
description: 'Дополнительные сведения о <performanceCounters> элементе: Element (параметры сети)'
title: Элемент <performanceCounters> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: a923ba2420bd15e33f4564a196854fdf9e130e12
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804118"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="2cf3c-103">Элемент \<performanceCounters> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="2cf3c-103">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="2cf3c-104">Включает или отключает счетчики производительности сети.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-104">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="2cf3c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2cf3c-105">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cf3c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2cf3c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2cf3c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cf3c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2cf3c-108">Attributes</span></span>  
  
|<span data-ttu-id="2cf3c-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2cf3c-109">Attribute</span></span>|<span data-ttu-id="2cf3c-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2cf3c-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2cf3c-111">Указывает, включены ли счетчики производительности сети.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-111">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="2cf3c-112">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-112">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cf3c-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2cf3c-113">Child Elements</span></span>  

 <span data-ttu-id="2cf3c-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cf3c-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2cf3c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2cf3c-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="2cf3c-116">Element</span></span>|<span data-ttu-id="2cf3c-117">Описание</span><span class="sxs-lookup"><span data-stu-id="2cf3c-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cf3c-118">параметры</span><span class="sxs-lookup"><span data-stu-id="2cf3c-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="2cf3c-119">Настраивает основные параметры сети для пространства имен <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf3c-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="2cf3c-120">Remarks</span></span>  

 <span data-ttu-id="2cf3c-121">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2cf3c-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="2cf3c-122">Счетчики производительности сети необходимо включить для использования в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-122">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="2cf3c-123">Все счетчики производительности сети включаются и отключаются с помощью одного параметра в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-123">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="2cf3c-124">Включить или отключить отдельные счетчики производительности сети невозможно.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-124">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="2cf3c-125">Дополнительные сведения о конкретных счетчиках производительности сети см. в разделе [Сетевые счетчики производительности](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span><span class="sxs-lookup"><span data-stu-id="2cf3c-125">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="2cf3c-126">Значение по умолчанию — сетевые счетчики производительности отключены.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-126">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="2cf3c-127"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>Свойство можно использовать для получения текущего значения атрибута **Enabled** из применимых файлов конфигурации.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-127">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cf3c-128">Пример</span><span class="sxs-lookup"><span data-stu-id="2cf3c-128">Example</span></span>  

 <span data-ttu-id="2cf3c-129">В следующем примере показано, как настроить <xref:System.Net> и связанные пространства имен для включения сетевых счетчиков производительности.</span><span class="sxs-lookup"><span data-stu-id="2cf3c-129">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cf3c-130">См. также</span><span class="sxs-lookup"><span data-stu-id="2cf3c-130">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2cf3c-131">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="2cf3c-131">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2cf3c-132">Счетчики производительности сети</span><span class="sxs-lookup"><span data-stu-id="2cf3c-132">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
