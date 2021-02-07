---
description: Дополнительные сведения о <элементе System. Web> (веб-параметры)
title: Элемент <system.web> (веб-параметры)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 2adcd3eba1eb6d67bcb4dc82243cd70d31d64fe9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681907"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="17d38-103">Элемент \<system.web> (веб-параметры)</span><span class="sxs-lookup"><span data-stu-id="17d38-103">\<system.web> Element (Web Settings)</span></span>

<span data-ttu-id="17d38-104">Содержит сведения о том, как уровень размещения ASP.NET управляет поведением всего процесса.</span><span class="sxs-lookup"><span data-stu-id="17d38-104">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.web>**  
  
## <a name="syntax"></a><span data-ttu-id="17d38-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17d38-105">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17d38-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="17d38-106">Attributes and Elements</span></span>  

<span data-ttu-id="17d38-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="17d38-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17d38-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="17d38-108">Attributes</span></span>  

<span data-ttu-id="17d38-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="17d38-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="17d38-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="17d38-110">Child Elements</span></span>  
  
|<span data-ttu-id="17d38-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="17d38-111">Element</span></span>|<span data-ttu-id="17d38-112">Описание</span><span class="sxs-lookup"><span data-stu-id="17d38-112">Description</span></span>|  
|-------------|-----------------|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="17d38-113">Задает параметры конфигурации для пулов приложений IIS в файле aspnet.config.</span><span class="sxs-lookup"><span data-stu-id="17d38-113">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17d38-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="17d38-114">Parent Elements</span></span>  
  
|<span data-ttu-id="17d38-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="17d38-115">Element</span></span>|<span data-ttu-id="17d38-116">Описание</span><span class="sxs-lookup"><span data-stu-id="17d38-116">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="17d38-117">Указывает корневой элемент в каждом файле конфигурации, который используется средой CLR и платформа .NET Framework приложениями.</span><span class="sxs-lookup"><span data-stu-id="17d38-117">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17d38-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="17d38-118">Remarks</span></span>  

<span data-ttu-id="17d38-119">`system.web`Элемент и его дочерний `applicationPool` элемент были добавлены в платформа .NET Framework в платформа .NET Framework 3,5 с пакетом обновления 1 (SP1).</span><span class="sxs-lookup"><span data-stu-id="17d38-119">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="17d38-120">При запуске IIS 7,0 или более поздних версий в интегрированном режиме эта комбинация элементов позволяет настроить, как ASP.NET управляет потоками и как она помещает запросы в очередь, когда ASP.NET размещается в пуле приложений IIS.</span><span class="sxs-lookup"><span data-stu-id="17d38-120">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="17d38-121">При запуске IIS 7,0 или более поздних версий в классическом или режиме ISAPI эти параметры игнорируются.</span><span class="sxs-lookup"><span data-stu-id="17d38-121">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17d38-122">Пример</span><span class="sxs-lookup"><span data-stu-id="17d38-122">Example</span></span>  

<span data-ttu-id="17d38-123">В следующем примере показано, как настроить поведение ASP.NET на уровне процесса в файле aspnet.config, если ASP.NET размещается в пуле приложений IIS.</span><span class="sxs-lookup"><span data-stu-id="17d38-123">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="17d38-124">В примере предполагается, что службы IIS работают в режиме интеграции и что приложение использует платформа .NET Framework 3,5 с пакетом обновления 1 (SP1) или более поздней версии.</span><span class="sxs-lookup"><span data-stu-id="17d38-124">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="17d38-125">Такое поведение не происходит в версиях платформа .NET Framework более ранних, чем платформа .NET Framework 3,5 с пакетом обновления 1 (SP1).</span><span class="sxs-lookup"><span data-stu-id="17d38-125">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="17d38-126">Значения в примере являются значениями по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="17d38-126">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="17d38-127">Сведения об элементе</span><span class="sxs-lookup"><span data-stu-id="17d38-127">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17d38-128">Пространство имен</span><span class="sxs-lookup"><span data-stu-id="17d38-128">Namespace</span></span>||  
|<span data-ttu-id="17d38-129">Имя схемы</span><span class="sxs-lookup"><span data-stu-id="17d38-129">Schema Name</span></span>||  
|<span data-ttu-id="17d38-130">Файл проверки</span><span class="sxs-lookup"><span data-stu-id="17d38-130">Validation File</span></span>||  
|<span data-ttu-id="17d38-131">Может быть пустым</span><span class="sxs-lookup"><span data-stu-id="17d38-131">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="17d38-132">См. также</span><span class="sxs-lookup"><span data-stu-id="17d38-132">See also</span></span>

- [<span data-ttu-id="17d38-133">\<applicationPool> Элемент (веб-параметры)</span><span class="sxs-lookup"><span data-stu-id="17d38-133">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
