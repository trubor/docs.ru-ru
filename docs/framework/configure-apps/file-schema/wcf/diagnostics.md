---
description: 'Дополнительные сведения: <diagnostics>'
title: <diagnostics>
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: d1651d949cdc095e630e9cde0bacbe51a5eb6062
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782160"
---
# \<diagnostics>

<span data-ttu-id="13265-102">Элемент `diagnostics` определяет параметры, которые могут быть использованы администратором для проверки и контроля времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="13265-102">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="13265-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13265-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics etwProviderId="String"
               performanceCounters="Off/ServiceOnly/All/Default"
               wmiProviderEnabled="Boolean">
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
    <messageLogging logEntireMessage="Boolean"
                    logMalformedMessages="Boolean"
                    logMessagesAtServiceLevel="Boolean"
                    logMessagesAtTransportLevel="Boolean"
                    maxMessagesToLog="Integer"
                    maxSizeOfMessageToLog="Integer">
      <filters>
        <clear />
      </filters>
    </messageLogging>
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13265-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="13265-104">Attributes and Elements</span></span>  

 <span data-ttu-id="13265-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="13265-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13265-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="13265-106">Attributes</span></span>  
  
|<span data-ttu-id="13265-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="13265-107">Attribute</span></span>|<span data-ttu-id="13265-108">Описание</span><span class="sxs-lookup"><span data-stu-id="13265-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13265-109">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="13265-109">etwProviderId</span></span>|<span data-ttu-id="13265-110">Строка, которая задает идентификатор для поставщика отслеживания событий, который записывает события в сеансы ETW.</span><span class="sxs-lookup"><span data-stu-id="13265-110">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="13265-111">performanceCounters</span><span class="sxs-lookup"><span data-stu-id="13265-111">performanceCounters</span></span>|<span data-ttu-id="13265-112">Указывает, включены ли счетчики производительности для сборки.</span><span class="sxs-lookup"><span data-stu-id="13265-112">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="13265-113">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="13265-113">Valid values are</span></span><br /><br /> <span data-ttu-id="13265-114">-Off: счетчики производительности отключены.</span><span class="sxs-lookup"><span data-stu-id="13265-114">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="13265-115">-Сервицеонли: включены только счетчики производительности, относящиеся к этой службе.</span><span class="sxs-lookup"><span data-stu-id="13265-115">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="13265-116">-ALL: счетчики производительности можно просматривать во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="13265-116">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="13265-117">-Default: создается отдельный экземпляр счетчика производительности _WCF_Admin.</span><span class="sxs-lookup"><span data-stu-id="13265-117">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="13265-118">Данный экземпляр используется, чтобы включить коллекцию данных SQM для использования инфраструктурой.</span><span class="sxs-lookup"><span data-stu-id="13265-118">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="13265-119">Значения счетчика для данного экземпляра не обновляются и, соответственно, остаются нулевыми.</span><span class="sxs-lookup"><span data-stu-id="13265-119">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="13265-120">Если для WCF не задана конфигурация, это значение используется по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="13265-120">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="13265-121">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="13265-121">wmiProviderEnabled</span></span>|<span data-ttu-id="13265-122">Логическое значение, определяющее, включен ли поставщик WMI для сборки.</span><span class="sxs-lookup"><span data-stu-id="13265-122">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="13265-123">Данный поставщик WMI требуется пользователю, чтобы на время выполнения получить доступ к функциональным возможностям проверки и контроля Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="13265-123">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="13265-124">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="13265-124">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13265-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="13265-125">Child Elements</span></span>  
  
|<span data-ttu-id="13265-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="13265-126">Element</span></span>|<span data-ttu-id="13265-127">Описание</span><span class="sxs-lookup"><span data-stu-id="13265-127">Description</span></span>|  
|-------------|-----------------|  
|[\<endToEndTracing>](endtoendtracing.md)|<span data-ttu-id="13265-128">Элемент конфигурации, который позволяет включать и отключать различные аспекты сквозной отслеживания во время выполнения приложения службы.</span><span class="sxs-lookup"><span data-stu-id="13265-128">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[\<messageLogging>](messagelogging.md)|<span data-ttu-id="13265-129">Описывает параметры ведения журнала сообщений WCF.</span><span class="sxs-lookup"><span data-stu-id="13265-129">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13265-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="13265-130">Parent Elements</span></span>  
  
|<span data-ttu-id="13265-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="13265-131">Element</span></span>|<span data-ttu-id="13265-132">Описание</span><span class="sxs-lookup"><span data-stu-id="13265-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13265-133">serviceModel</span><span class="sxs-lookup"><span data-stu-id="13265-133">serviceModel</span></span>|<span data-ttu-id="13265-134">Корневой элемент всех элементов конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="13265-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13265-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="13265-135">Remarks</span></span>  

 <span data-ttu-id="13265-136">В разделе `diagnostics` определяются параметры диагностики для всех служб, содержащихся в сборке.</span><span class="sxs-lookup"><span data-stu-id="13265-136">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="13265-137">Отдельные параметры диагностики можно определить на уровне службы, только если сборка содержит одну службу.</span><span class="sxs-lookup"><span data-stu-id="13265-137">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="13265-138">Атрибуты заданы в соответствии с требованиями раздела.</span><span class="sxs-lookup"><span data-stu-id="13265-138">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13265-139">Пример</span><span class="sxs-lookup"><span data-stu-id="13265-139">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"
             performanceCounters="all">
  <messageLogging logEntireMessage="true"
                  logMalformedMessages="true"
                  logMessagesAtServiceLevel="true"
                  logMessagesAtTransportLevel="true"
                  maxMessagesToLog="42"
                  maxSizeOfMessageToLog="42">
    <filters>
      <clear />
    </filters>
  </messageLogging>
</diagnostics>
```  
  
## <a name="see-also"></a><span data-ttu-id="13265-140">См. также</span><span class="sxs-lookup"><span data-stu-id="13265-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
