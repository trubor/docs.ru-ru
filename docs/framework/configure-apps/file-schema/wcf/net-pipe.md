---
description: 'Дополнительные сведения о: <NET. pipe>'
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: d95aebc62ab92b91c1633a99d8311b55bfaaf0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684078"
---
# \<net.pipe>

<span data-ttu-id="f3789-103">Задает параметры конфигурации для службы активации именованных каналов, которая управляет временем существования соединения для именованного канала, а также обрабатывает запросы на активацию, которые поступают по именованным каналам.</span><span class="sxs-lookup"><span data-stu-id="f3789-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="f3789-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3789-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="f3789-105">Тип</span><span class="sxs-lookup"><span data-stu-id="f3789-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3789-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f3789-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f3789-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f3789-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3789-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f3789-108">Attributes</span></span>  
  
|<span data-ttu-id="f3789-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f3789-109">Attribute</span></span>|<span data-ttu-id="f3789-110">Описание</span><span class="sxs-lookup"><span data-stu-id="f3789-110">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="f3789-111">Целое число, которое определяет максимальное количество одновременных необработанных принимающих потоков в конечной точке для общей службы.</span><span class="sxs-lookup"><span data-stu-id="f3789-111">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="f3789-112">Значение по умолчанию — 2</span><span class="sxs-lookup"><span data-stu-id="f3789-112">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="f3789-113">Целое число, задающее максимальное количество соединений, которые могут ожидать распределения.</span><span class="sxs-lookup"><span data-stu-id="f3789-113">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="f3789-114">Значение по умолчанию — 100.</span><span class="sxs-lookup"><span data-stu-id="f3789-114">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f3789-115">Значение <xref:System.TimeSpan>, определяющее время ожидания для чтения данных кадрирования и проведения распределения подключений из базовых подключений.</span><span class="sxs-lookup"><span data-stu-id="f3789-115">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="f3789-116">Значение по умолчанию - 00:00:10.</span><span class="sxs-lookup"><span data-stu-id="f3789-116">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3789-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f3789-117">Child Elements</span></span>  
  
|<span data-ttu-id="f3789-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="f3789-118">Element</span></span>|<span data-ttu-id="f3789-119">Описание</span><span class="sxs-lookup"><span data-stu-id="f3789-119">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="f3789-120">Коллекция элементов конфигурации, которая содержит `securityIdentifier` атрибут для указания учетных записей пользователей для процессов, размещающий службы WCF, и которым предоставляется доступ к службе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="f3789-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3789-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f3789-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f3789-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="f3789-122">Element</span></span>|<span data-ttu-id="f3789-123">Описание</span><span class="sxs-lookup"><span data-stu-id="f3789-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="f3789-124">Содержит параметры конфигурации для процесса прослушивателя SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="f3789-124">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3789-125">См. также</span><span class="sxs-lookup"><span data-stu-id="f3789-125">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>
