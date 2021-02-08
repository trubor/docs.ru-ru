---
description: 'Дополнительные сведения о: <NET. TCP>'
title: <net.tcp>
ms.date: 03/30/2017
ms.assetid: 8bc2f2be-11c1-4bab-9018-1d21ae568d94
ms.openlocfilehash: b7b36e0309139508011e5abceab97cc6f6f9a53d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786945"
---
# \<net.tcp>

<span data-ttu-id="5d226-103">Задает параметры конфигурации для службы общего доступа к портам Net.Tcp, которая позволяет нескольким процессам совместно использовать один и тот же порт протокола TCP.</span><span class="sxs-lookup"><span data-stu-id="5d226-103">Specifies configuration settings for the NET.TCP Port Sharing Service, which allows multiple processes to share the same TCP port.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.tcp>**  
  
## <a name="syntax"></a><span data-ttu-id="5d226-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d226-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="Integer"
             maxPendingAccepts="Integer"
             maxPendingConnections="Integer"
             receiveTimeout="TimeSpan"
             teredoEnabled="Boolean">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only)-->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="5d226-105">Тип</span><span class="sxs-lookup"><span data-stu-id="5d226-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d226-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5d226-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5d226-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5d226-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d226-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5d226-108">Attributes</span></span>  
  
|<span data-ttu-id="5d226-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5d226-109">Attribute</span></span>|<span data-ttu-id="5d226-110">Описание</span><span class="sxs-lookup"><span data-stu-id="5d226-110">Description</span></span>|  
|---------------|-----------------|  
|`listenBacklog`|<span data-ttu-id="5d226-111">Целое число, указывающее максимальное количество необработанных соединений, принимаемых из общего соединения, но еще не отправленных в службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5d226-111">An integer that specifies the maximum outstanding connections that are accepted from the shared connection, but are not yet dispatched to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="5d226-112">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="5d226-112">The default is 10.</span></span>|  
|`maxPendingAccepts`|<span data-ttu-id="5d226-113">Целое число, которое определяет максимальное количество одновременных необработанных принимающих потоков в конечной точке для общей службы.</span><span class="sxs-lookup"><span data-stu-id="5d226-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="5d226-114">Значение по умолчанию — 2</span><span class="sxs-lookup"><span data-stu-id="5d226-114">The default is 2.</span></span>|  
|`MaxPendingConnections`|<span data-ttu-id="5d226-115">Максимальное число подключений, принятия которых приложением может ожидать прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="5d226-115">The maximum number of connections that the listener can have waiting to be accepted by the application.</span></span> <span data-ttu-id="5d226-116">После превышения значения этой квоты новые входящие подключения сбрасываются, а не ожидают принятия.</span><span class="sxs-lookup"><span data-stu-id="5d226-116">When this quota value is exceeded, new incoming connections are dropped rather than waiting to be accepted.</span></span> <span data-ttu-id="5d226-117">Возможности подключения (такие как безопасность сообщения) могут вынудить клиента открыть несколько подключений.</span><span class="sxs-lookup"><span data-stu-id="5d226-117">Connection features such as message security can cause a client to open more than one connection.</span></span> <span data-ttu-id="5d226-118">При установке значения квоты администраторы службы должны учитывать возможность установления дополнительных подключений.</span><span class="sxs-lookup"><span data-stu-id="5d226-118">Service administrators should account for these additional connections when setting this quota value.</span></span> <span data-ttu-id="5d226-119">Значение по умолчанию равно 10.</span><span class="sxs-lookup"><span data-stu-id="5d226-119">The default is 10.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5d226-120">Значение <xref:System.TimeSpan>, определяющее время ожидания для чтения данных кадрирования и проведения распределения подключений из базовых подключений.</span><span class="sxs-lookup"><span data-stu-id="5d226-120">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="5d226-121">Значение по умолчанию - 00:00:10.</span><span class="sxs-lookup"><span data-stu-id="5d226-121">The default is "00:00:10".</span></span>|  
|`teredoEnabled`|<span data-ttu-id="5d226-122">Логическое значение, указывающее, использует ли служба совместного использования портов службу Microsoft Teredo для прослушивания TCP-портов от имени служб WCF.</span><span class="sxs-lookup"><span data-stu-id="5d226-122">A Boolean value that indicates whether the port sharing service uses Microsoft Teredo service to listen on TCP ports on behalf of WCF services.</span></span> <span data-ttu-id="5d226-123">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="5d226-123">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d226-124">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5d226-124">Child Elements</span></span>  
  
|<span data-ttu-id="5d226-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="5d226-125">Element</span></span>|<span data-ttu-id="5d226-126">Описание</span><span class="sxs-lookup"><span data-stu-id="5d226-126">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="5d226-127">Коллекция элементов конфигурации, которая содержит `securityIdentifier` атрибут для указания учетных записей пользователей для процессов, размещающий службы WCF, и которым предоставляется доступ к службе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="5d226-127">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d226-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5d226-128">Parent Elements</span></span>  
  
|<span data-ttu-id="5d226-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="5d226-129">Element</span></span>|<span data-ttu-id="5d226-130">Описание</span><span class="sxs-lookup"><span data-stu-id="5d226-130">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="5d226-131">Содержит параметры конфигурации для процесса прослушивателя SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="5d226-131">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d226-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="5d226-132">Remarks</span></span>  

 <span data-ttu-id="5d226-133">Дополнительные сведения о совместном использовании портов см. в разделе [общий доступ к портам Net. TCP](../../../wcf/feature-details/net-tcp-port-sharing.md).</span><span class="sxs-lookup"><span data-stu-id="5d226-133">For more information on port sharing, see [Net.TCP Port Sharing](../../../wcf/feature-details/net-tcp-port-sharing.md).</span></span> <span data-ttu-id="5d226-134">Сведения о настройке службы общего доступа к портам см. в разделе [Настройка службы совместного использования портов net. TCP](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span><span class="sxs-lookup"><span data-stu-id="5d226-134">To understand how to configure the port sharing service, see [Configuring the Net.TCP Port Sharing Service](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d226-135">См. также</span><span class="sxs-lookup"><span data-stu-id="5d226-135">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection>
- [<span data-ttu-id="5d226-136">Совместное использование портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5d226-136">Net.TCP Port Sharing</span></span>](../../../wcf/feature-details/net-tcp-port-sharing.md)
- [<span data-ttu-id="5d226-137">Настройка службы совместного использования портов Net.TCP</span><span class="sxs-lookup"><span data-stu-id="5d226-137">Configuring the Net.TCP Port Sharing Service</span></span>](../../../wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
