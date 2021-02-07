---
description: 'Дополнительные сведения: Балансировка нагрузки'
title: Балансировка нагрузки
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 9f7946793fb9a9eec9baf531e4650f68b92151d9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732817"
---
# <a name="load-balancing"></a><span data-ttu-id="239a1-103">Балансировка нагрузки</span><span class="sxs-lookup"><span data-stu-id="239a1-103">Load Balancing</span></span>

<span data-ttu-id="239a1-104">Одним из способов увеличения емкости приложений Windows Communication Foundation (WCF) является их масштабирование путем их развертывания в ферме серверов с балансировкой нагрузки.</span><span class="sxs-lookup"><span data-stu-id="239a1-104">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="239a1-105">Для обеспечения балансировки нагрузки приложений WCF можно использовать стандартные методы балансировки нагрузки, в том числе подсистемы балансировки нагрузки по сети Windows, а также устройства балансировки нагрузки на основе оборудования.</span><span class="sxs-lookup"><span data-stu-id="239a1-105">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="239a1-106">В следующих разделах рассматриваются вопросы балансировки нагрузки приложений WCF, созданных с помощью различных предоставляемых системой привязок.</span><span class="sxs-lookup"><span data-stu-id="239a1-106">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="239a1-107">Балансировка нагрузки с базовой привязкой HTTP</span><span class="sxs-lookup"><span data-stu-id="239a1-107">Load Balancing with the Basic HTTP Binding</span></span>  

 <span data-ttu-id="239a1-108">С точки зрения балансировки нагрузки приложения WCF, которые обмениваются данными с помощью, <xref:System.ServiceModel.BasicHttpBinding> не отличаются от других распространенных типов сетевого трафика HTTP (статического содержимого HTML, страниц ASP.NET или веб-служб ASMX).</span><span class="sxs-lookup"><span data-stu-id="239a1-108">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="239a1-109">Каналы WCF, использующие эту привязку, по своей природе имеют состояние без отслеживания состояния и завершают свои подключения при закрытии канала.</span><span class="sxs-lookup"><span data-stu-id="239a1-109">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="239a1-110">Поэтому привязка <xref:System.ServiceModel.BasicHttpBinding> хорошо работает с имеющимися методами балансировки нагрузки HTTP.</span><span class="sxs-lookup"><span data-stu-id="239a1-110">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="239a1-111">По умолчанию <xref:System.ServiceModel.BasicHttpBinding> отправляет заголовок HTTP подключения в сообщениях со значением `Keep-Alive`, которое позволяет клиентам устанавливать устойчивые подключения к службам, которые поддерживают их.</span><span class="sxs-lookup"><span data-stu-id="239a1-111">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="239a1-112">Такая конфигурация увеличивает пропускную способность, потому что ранее установленные подключения можно повторно использовать для отправки новых сообщений одному и тому же серверу.</span><span class="sxs-lookup"><span data-stu-id="239a1-112">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="239a1-113">Однако повторное использований подключений может привести к тому, что клиенты будут слишком сильно связаны с конкретным сервером фермы балансировки нагрузки, что приведет к снижению эффективности балансировки нагрузки за счет равномерного распределения запросов между серверами фермы.</span><span class="sxs-lookup"><span data-stu-id="239a1-113">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="239a1-114">Если такое поведение является нежелательным, можно на сервере отключить заголовок `Keep-Alive`, присвоив свойству <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> значение <xref:System.ServiceModel.Channels.CustomBinding> или пользовательскую привязку <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="239a1-114">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="239a1-115">В следующем примере показано, как добиться этого с помощью конфигурации.</span><span class="sxs-lookup"><span data-stu-id="239a1-115">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="239a1-116">С помощью упрощенной конфигурации, представленной в платформа .NET Framework 4, такое же поведение можно выполнить с помощью следующей упрощенной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="239a1-116">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="239a1-117">Дополнительные сведения о конечных точках по умолчанию, привязках и режимах работы см. в разделах [Упрощенная конфигурация](simplified-configuration.md) и [Упрощенная конфигурация служб WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="239a1-117">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="239a1-118">Балансировка нагрузки с привязкой WSHttp и привязкой WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="239a1-118">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  

 <span data-ttu-id="239a1-119">Для привязок <xref:System.ServiceModel.WSHttpBinding> и <xref:System.ServiceModel.WSDualHttpBinding> можно обеспечить балансировку нагрузки, используя для этого методы балансировки нагрузки HTTP, реализуемые путем внесения некоторых изменений в конфигурацию привязки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="239a1-119">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="239a1-120">Отключите установку контекста безопасности или используйте сеансы безопасности с отслеживанием состояния.</span><span class="sxs-lookup"><span data-stu-id="239a1-120">Turn off Security Context Establishment or use stateful security sessions.</span></span> <span data-ttu-id="239a1-121">Установка контекста безопасности может быть отключена путем присвоения <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> свойству значения <xref:System.ServiceModel.WSHttpBinding> `false` .</span><span class="sxs-lookup"><span data-stu-id="239a1-121">Security Context Establishment can be turned off by setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="239a1-122">Если <xref:System.ServiceModel.WSDualHttpBinding> требуются сеансы безопасности, можно использовать сеансы безопасности с отслеживанием состояния, как описано в разделе [безопасные сеансы](./feature-details/secure-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="239a1-122">If you are using <xref:System.ServiceModel.WSDualHttpBinding> or security sessions are required, it is possible to use stateful security sessions as described in [Secure Sessions](./feature-details/secure-sessions.md).</span></span> <span data-ttu-id="239a1-123">Сеансы безопасности с отслеживанием состояния позволяют службе оставаться без отслеживания состояния, так как все состояния сеанса безопасности передаются с каждым запросом в составе маркера безопасности защиты.</span><span class="sxs-lookup"><span data-stu-id="239a1-123">Stateful security sessions enable the service to remain stateless, as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="239a1-124">Чтобы включить сеанс безопасности с отслеживанием состояния, необходимо использовать <xref:System.ServiceModel.Channels.CustomBinding> или определяемые пользователем <xref:System.ServiceModel.Channels.Binding> , так как необходимые параметры конфигурации не предоставляются в предоставляемых системой <xref:System.ServiceModel.WSHttpBinding> и <xref:System.ServiceModel.WSDualHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="239a1-124">To enable a stateful security session, you must use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>, as the necessary configuration settings are not exposed on the system-provided <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding>.</span></span>

- <span data-ttu-id="239a1-125">При отключении установки контекста безопасности необходимо также отключить согласование учетных данных службы.</span><span class="sxs-lookup"><span data-stu-id="239a1-125">If you turn off Security Context Establishment, you also need to turn off Service Credential Negotiation.</span></span> <span data-ttu-id="239a1-126">Чтобы отключить его, задайте <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> для свойства в значение <xref:System.ServiceModel.WSHttpBinding> `false` .</span><span class="sxs-lookup"><span data-stu-id="239a1-126">To turn it off, set the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="239a1-127">Чтобы отключить согласование учетных данных службы, может потребоваться явно указать идентификатор конечной точки на клиенте.</span><span class="sxs-lookup"><span data-stu-id="239a1-127">To disable Service Credential Negotiation, you may need to explicitly specify the endpoint identity on the client.</span></span>
  
- <span data-ttu-id="239a1-128">Не используйте надежные сеансы.</span><span class="sxs-lookup"><span data-stu-id="239a1-128">Do not use reliable sessions.</span></span> <span data-ttu-id="239a1-129">Эта возможность отключена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="239a1-129">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="239a1-130">Балансировка нагрузки привязки Net.TCP</span><span class="sxs-lookup"><span data-stu-id="239a1-130">Load Balancing the Net.TCP Binding</span></span>  

 <span data-ttu-id="239a1-131">Балансировку нагрузки привязки <xref:System.ServiceModel.NetTcpBinding> можно осуществлять с помощью методов балансировки нагрузки уровня протокола IP.</span><span class="sxs-lookup"><span data-stu-id="239a1-131">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="239a1-132">Однако для уменьшения времени задержки подключений привязка <xref:System.ServiceModel.NetTcpBinding> по умолчанию объединяет TCP-подключения.</span><span class="sxs-lookup"><span data-stu-id="239a1-132">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="239a1-133">Такая оптимизация противоречит базовому механизму балансировки нагрузки.</span><span class="sxs-lookup"><span data-stu-id="239a1-133">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="239a1-134">Основным параметром конфигурации, используемым для оптимизации <xref:System.ServiceModel.NetTcpBinding>, является время ожидания аренды, которое входит в настройки пула подключений.</span><span class="sxs-lookup"><span data-stu-id="239a1-134">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="239a1-135">В результате объединения клиентских подключений в пул эти подключения оказываются связанными с конкретными серверами фермы.</span><span class="sxs-lookup"><span data-stu-id="239a1-135">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="239a1-136">По мере увеличения времени существования таких подключений (этот показатель зависит от значения времени ожидания аренды) распределение нагрузки между различными серверами фермы становится несбалансированным.</span><span class="sxs-lookup"><span data-stu-id="239a1-136">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="239a1-137">В результате среднее время одного вызова увеличивается.</span><span class="sxs-lookup"><span data-stu-id="239a1-137">As a result the average call time increases.</span></span> <span data-ttu-id="239a1-138">Поэтому при использовании привязки <xref:System.ServiceModel.NetTcpBinding> с балансировкой нагрузки следует рассмотреть возможность уменьшения используемого привязкой времени ожидания аренды по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="239a1-138">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="239a1-139">Для начала использования балансировки нагрузки можно установить время ожидания аренды равным 30 секундам, хотя оптимальное значение будет зависеть от конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="239a1-139">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="239a1-140">Дополнительные сведения о времени ожидания аренды канала и других квотах транспорта см. в разделе [квоты транспорта](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="239a1-140">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="239a1-141">Для достижения максимальной производительности при балансировке нагрузки рекомендуется использовать <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> или <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="239a1-141">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="239a1-142">См. также</span><span class="sxs-lookup"><span data-stu-id="239a1-142">See also</span></span>

- [<span data-ttu-id="239a1-143">Рекомендации по размещению в службах IIS</span><span class="sxs-lookup"><span data-stu-id="239a1-143">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
