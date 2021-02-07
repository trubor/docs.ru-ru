---
description: 'Дополнительные сведения о: <appDomainResourceMonitoring> element'
title: Элемент <appDomainResourceMonitoring>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
ms.openlocfilehash: aee85386e6d0af2ca4fd30c0ad8fe69bae240315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719296"
---
# <a name="appdomainresourcemonitoring-element"></a><span data-ttu-id="ce570-103">Элемент \<appDomainResourceMonitoring></span><span class="sxs-lookup"><span data-stu-id="ce570-103">\<appDomainResourceMonitoring> Element</span></span>

<span data-ttu-id="ce570-104">Указывает среде собирать статистику для всех доменов приложений в процессе за весь период его существования.</span><span class="sxs-lookup"><span data-stu-id="ce570-104">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainResourceMonitoring>**  
  
## <a name="syntax"></a><span data-ttu-id="ce570-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ce570-105">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce570-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ce570-106">Attributes and Elements</span></span>  

 <span data-ttu-id="ce570-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ce570-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce570-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ce570-108">Attributes</span></span>  
  
|<span data-ttu-id="ce570-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ce570-109">Attribute</span></span>|<span data-ttu-id="ce570-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ce570-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ce570-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ce570-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ce570-112">Указывает, собирает ли среда выполнения статистические данные для отслеживания ресурсов домена приложения.</span><span class="sxs-lookup"><span data-stu-id="ce570-112">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ce570-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ce570-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="ce570-114">Значение</span><span class="sxs-lookup"><span data-stu-id="ce570-114">Value</span></span>|<span data-ttu-id="ce570-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ce570-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="ce570-116">Собираются статистические данные для отслеживания ресурсов домена приложения.</span><span class="sxs-lookup"><span data-stu-id="ce570-116">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="ce570-117">Статистика по мониторингу ресурсов домена приложений не собирается.</span><span class="sxs-lookup"><span data-stu-id="ce570-117">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce570-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ce570-118">Child Elements</span></span>  

 <span data-ttu-id="ce570-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ce570-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce570-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ce570-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ce570-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="ce570-121">Element</span></span>|<span data-ttu-id="ce570-122">Описание</span><span class="sxs-lookup"><span data-stu-id="ce570-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ce570-123">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce570-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ce570-124">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="ce570-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce570-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce570-125">Remarks</span></span>  

 <span data-ttu-id="ce570-126">Мониторинг ресурсов домена приложений доступен через класс домена управляемого приложения, интерфейс размещения [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) и трассировку событий для Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="ce570-126">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="ce570-127">При включении мониторинга статистика собирается для всех доменов приложений в процессе в течение жизненного цикла процесса.</span><span class="sxs-lookup"><span data-stu-id="ce570-127">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="ce570-128">Чтобы включить мониторинг из управляемого кода, используйте <xref:System.AppDomain.MonitoringIsEnabled%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="ce570-128">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="ce570-129">Этот элемент конфигурации доступен только в платформа .NET Framework 4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="ce570-129">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce570-130">Пример</span><span class="sxs-lookup"><span data-stu-id="ce570-130">Example</span></span>  

 <span data-ttu-id="ce570-131">В следующем примере показано, как включить отслеживание ресурсов домена приложения.</span><span class="sxs-lookup"><span data-stu-id="ce570-131">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce570-132">См. также</span><span class="sxs-lookup"><span data-stu-id="ce570-132">See also</span></span>

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ce570-133">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ce570-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ce570-134">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ce570-134">Configuration File Schema</span></span>](../index.md)
