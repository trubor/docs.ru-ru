---
description: 'Дополнительные сведения: <serviceThrottling>'
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: eb65f6d60a266a367789d87e4e6ea10ebfd2c7a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786685"
---
# \<serviceThrottling>

<span data-ttu-id="3bf63-102">Задает механизм настройки службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3bf63-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="3bf63-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3bf63-103">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bf63-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3bf63-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3bf63-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3bf63-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bf63-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3bf63-106">Attributes</span></span>  
  
|<span data-ttu-id="3bf63-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3bf63-107">Attribute</span></span>|<span data-ttu-id="3bf63-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3bf63-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bf63-109">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="3bf63-109">maxConcurrentCalls</span></span>|<span data-ttu-id="3bf63-110">Положительное целое число, ограничивающее количество сообщений, обрабатываемых в текущий момент в <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3bf63-110">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="3bf63-111">Вызовы, превышающие этот предел, ставятся в очередь.</span><span class="sxs-lookup"><span data-stu-id="3bf63-111">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="3bf63-112">Установка этого значения на 0 эквивалентна его установке на Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="3bf63-112">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="3bf63-113">Значение по умолчанию: 16 \* количество процессоров.</span><span class="sxs-lookup"><span data-stu-id="3bf63-113">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="3bf63-114">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="3bf63-114">maxConcurrentInstances</span></span>|<span data-ttu-id="3bf63-115">Положительное целое число, ограничивающее количество объектов <xref:System.ServiceModel.InstanceContext>, одновременно выполняющихся в <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3bf63-115">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="3bf63-116">Запросы на создание дополнительных экземпляров ставятся в очередь и выполняются, когда происходит отступление от предельной величины.</span><span class="sxs-lookup"><span data-stu-id="3bf63-116">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="3bf63-117">Значение по умолчанию: сумма maxConcurrentSessions и MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="3bf63-117">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="3bf63-118">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="3bf63-118">maxConcurrentSessions</span></span>|<span data-ttu-id="3bf63-119">Положительное целое число, ограничивающее количество сеансов, которое может принять объект <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="3bf63-119">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="3bf63-120">Служба принимает соединения сверх предела, но только каналы, количество которых меньше предельного значения, являются активными (сообщения считываются из канала).</span><span class="sxs-lookup"><span data-stu-id="3bf63-120">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="3bf63-121">Установка этого значения на 0 эквивалентна его установке на Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="3bf63-121">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="3bf63-122">Значение по умолчанию: 100 \* количество процессоров.</span><span class="sxs-lookup"><span data-stu-id="3bf63-122">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bf63-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3bf63-123">Child Elements</span></span>  

 <span data-ttu-id="3bf63-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="3bf63-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bf63-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3bf63-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3bf63-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="3bf63-126">Element</span></span>|<span data-ttu-id="3bf63-127">Описание</span><span class="sxs-lookup"><span data-stu-id="3bf63-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="3bf63-128">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="3bf63-128">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bf63-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="3bf63-129">Remarks</span></span>  

 <span data-ttu-id="3bf63-130">Элементы регулирования ограничивают число одновременных вызовов, экземпляров или сеансов, чтобы предотвратить чрезмерное потребление ресурсов.</span><span class="sxs-lookup"><span data-stu-id="3bf63-130">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="3bf63-131">Каждый раз при достижении значений атрибутов происходит запись трассировки.</span><span class="sxs-lookup"><span data-stu-id="3bf63-131">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="3bf63-132">Первая трассировка записывается как предупреждение.</span><span class="sxs-lookup"><span data-stu-id="3bf63-132">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bf63-133">Пример</span><span class="sxs-lookup"><span data-stu-id="3bf63-133">Example</span></span>  

 <span data-ttu-id="3bf63-134">В следующем примере конфигурации служба допускает максимум 2 одновременно выполняющихся вызова, а максимальное количество одновременно присутствующих экземпляров равно 10.</span><span class="sxs-lookup"><span data-stu-id="3bf63-134">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="3bf63-135">Подробный пример выполнения этого примера см. в разделе [регулирование](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="3bf63-135">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="3bf63-136">См. также</span><span class="sxs-lookup"><span data-stu-id="3bf63-136">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="3bf63-137">Использование ServiceThrottlingBehavior для управления производительностью службы WCF</span><span class="sxs-lookup"><span data-stu-id="3bf63-137">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
