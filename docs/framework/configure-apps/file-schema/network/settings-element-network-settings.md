---
description: 'Дополнительные сведения о <settings> элементе: Element (параметры сети)'
title: Элемент <settings> (параметры сети)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: e6ed242e68ac9a9e2c20067d66681bbcd51fcc50
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712978"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="27f8c-103">Элемент \<settings> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="27f8c-103">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="27f8c-104">Настраивает основные параметры сети для пространства имен <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27f8c-104">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="27f8c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="27f8c-105">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27f8c-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="27f8c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="27f8c-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="27f8c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27f8c-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="27f8c-108">Attributes</span></span>  

 <span data-ttu-id="27f8c-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="27f8c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27f8c-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="27f8c-110">Child Elements</span></span>  
  
|<span data-ttu-id="27f8c-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="27f8c-111">Element</span></span>|<span data-ttu-id="27f8c-112">Описание</span><span class="sxs-lookup"><span data-stu-id="27f8c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27f8c-113">httpListener</span><span class="sxs-lookup"><span data-stu-id="27f8c-113">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="27f8c-114">Настраивает параметры, используемые <xref:System.Net.HttpListener> классом.</span><span class="sxs-lookup"><span data-stu-id="27f8c-114">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="27f8c-115">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="27f8c-115">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="27f8c-116">Настраивает параметры веб-запроса.</span><span class="sxs-lookup"><span data-stu-id="27f8c-116">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="27f8c-117">Протокол</span><span class="sxs-lookup"><span data-stu-id="27f8c-117">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="27f8c-118">Включает поддержку протокола IP версии 6 (IPv6).</span><span class="sxs-lookup"><span data-stu-id="27f8c-118">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="27f8c-119">Элемент \<performanceCounter> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="27f8c-119">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="27f8c-120">Включает счетчики производительности сети.</span><span class="sxs-lookup"><span data-stu-id="27f8c-120">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="27f8c-121">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="27f8c-121">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="27f8c-122">Настраивает подключения к сетевым ресурсам.</span><span class="sxs-lookup"><span data-stu-id="27f8c-122">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="27f8c-123">фиксатор</span><span class="sxs-lookup"><span data-stu-id="27f8c-123">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="27f8c-124">Указывает, используют ли операции сокета порты завершения.</span><span class="sxs-lookup"><span data-stu-id="27f8c-124">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="27f8c-125">Элемент \<webProxyScript> (параметры сети)</span><span class="sxs-lookup"><span data-stu-id="27f8c-125">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="27f8c-126">Настраивает характеристики сценария, используемого для обнаружения веб-прокси.</span><span class="sxs-lookup"><span data-stu-id="27f8c-126">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27f8c-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="27f8c-127">Parent Elements</span></span>  
  
|<span data-ttu-id="27f8c-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="27f8c-128">Element</span></span>|<span data-ttu-id="27f8c-129">Описание</span><span class="sxs-lookup"><span data-stu-id="27f8c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27f8c-130">system.net</span><span class="sxs-lookup"><span data-stu-id="27f8c-130">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="27f8c-131">Содержит параметры сети, определяющие способ подключения .NET Framework к Интернету.</span><span class="sxs-lookup"><span data-stu-id="27f8c-131">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27f8c-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="27f8c-132">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="27f8c-133">Файлы конфигурации</span><span class="sxs-lookup"><span data-stu-id="27f8c-133">Configuration Files</span></span>  

 <span data-ttu-id="27f8c-134">Этот элемент может использоваться в файле конфигурации приложения или в файле конфигурации компьютера (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="27f8c-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f8c-135">См. также</span><span class="sxs-lookup"><span data-stu-id="27f8c-135">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="27f8c-136">Схема параметров сети</span><span class="sxs-lookup"><span data-stu-id="27f8c-136">Network Settings Schema</span></span>](index.md)
