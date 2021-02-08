---
description: 'Дополнительные сведения о: пример конфигурации'
title: Образец конфигурации
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: e11237fbc32b203c9b661288dbccab01745928d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778390"
---
# <a name="configuration-sample"></a><span data-ttu-id="5c8fe-103">Образец конфигурации</span><span class="sxs-lookup"><span data-stu-id="5c8fe-103">Configuration Sample</span></span>

<span data-ttu-id="5c8fe-104">Этот образец демонстрирует, как при помощи файла конфигурации можно сделать службу доступной для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-104">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c8fe-105">Данный образец реализует возможность обнаружения в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-105">This sample implements discovery in configuration.</span></span> <span data-ttu-id="5c8fe-106">Пример, в котором реализовано обнаружение в коде, см. в разделе [Basic](basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5c8fe-106">For a sample that implements discovery in code, see [Basic](basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5c8fe-107">Образцы уже могут быть установлены на компьютере.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5c8fe-108">Перед продолжением проверьте следующий каталог (по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="5c8fe-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5c8fe-109">Если этот каталог не существует, перейдите к [примерам Windows Communication Foundation (WCF) и Windows Workflow Foundation (WF) для платформа .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , чтобы скачать все Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5c8fe-110">Этот образец расположен в следующем каталоге.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="5c8fe-111">Конфигурация службы</span><span class="sxs-lookup"><span data-stu-id="5c8fe-111">Service Configuration</span></span>  

 <span data-ttu-id="5c8fe-112">Файл конфигурации в данном образце иллюстрирует две возможности.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-112">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="5c8fe-113">Обеспечение доступности обнаружения службы через стандартную конечную точку <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-113">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="5c8fe-114">Настройка информации, связанной с обнаружением, для конечной точки приложения службы, а также настройка некоторых параметров, связанных с обнаружением, для стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-114">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="5c8fe-115">Чтобы включить функцию обнаружения, в файле конфигурации приложения службы необходимо произвести следующие изменения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-115">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="5c8fe-116">Необходимо добавить конечную точку обнаружения к элементу `<service>`.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-116">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="5c8fe-117">Это стандартная конечная точка <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-117">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="5c8fe-118">Это системная конечная точка, которую среда выполнения связывает со службой обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-118">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="5c8fe-119">Служба обнаружения использует эту конечную точку для прослушивания сообщений.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-119">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="5c8fe-120">Добавим поведение `<serviceDiscovery>` в раздел `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-120">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="5c8fe-121">Это позволит обнаруживать службу во время выполнения, используя ранее упомянутую конечную точку обнаружения для прослушивания сообщений `Probe` и `Resolve`.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-121">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="5c8fe-122">После выполнения этих двух добавлений служба доступна для обнаружения на указанной конечной точке обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-122">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="5c8fe-123">В следующем фрагменте конфигурации показана служба с указанной конечной точкой приложения и конечной точкой обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-123">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"
                    kind="udpDiscoveryEndpoint"
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="5c8fe-124">Чтобы воспользоваться объявлениями, необходимо добавить конечную точку объявления.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-124">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="5c8fe-125">Для этого нужно изменить файл конфигурации, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-125">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="5c8fe-126">При добавлении конечной точки объявления к службе обнаружения создается клиент объявления по умолчанию для службы.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-126">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="5c8fe-127">Это гарантирует, что служба отправит объявление о режиме «в сети» или «не в сети» соответственно при открытии и закрытии службы.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-127">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="5c8fe-128">Можно не ограничиваться приведенными простыми шагами и изменить в файле конфигурации дополнительные поведения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-128">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="5c8fe-129">Информацией, относящейся к обнаружению, можно управлять с использованием определенных конечных точек.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-129">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="5c8fe-130">Таким образом пользователь может указать, доступна ли конечная точка для обнаружения, а также пометить ее атрибутом <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> и добавить пользовательские XML-метаданные.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-130">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="5c8fe-131">Для этого необходимо добавить в конечную точку приложения свойство `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-131">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="5c8fe-132">В этом случае в конечную точку приложения добавляется следующее свойство.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-132">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="5c8fe-133">Теперь с помощью элемента конфигурации поведения можно управлять атрибутами, связанными с обнаружением.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-133">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="5c8fe-134">В этом случае в конечную точку приложения добавляются две области.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-134">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="5c8fe-135">Дополнительные сведения об областях см. в разделе [Обнаружение Find и FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="5c8fe-135">For more information about scopes, see [Discovery Find and FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="5c8fe-136">Можно также управлять определенными сведениями о конечной точке обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-136">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="5c8fe-137">Это выполняется с помощью объекта <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-137">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="5c8fe-138">В данном образце изменяется версия используемого протокола, а также добавляется атрибут `maxResponseDelay`, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-138">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="5c8fe-139">Далее приведен полный листинг файла конфигурации, используемого в этом примере.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-139">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="5c8fe-140">Конфигурация клиента</span><span class="sxs-lookup"><span data-stu-id="5c8fe-140">Client Configuration</span></span>  

 <span data-ttu-id="5c8fe-141">Для включения функции обнаружения в конфигурации приложения для клиента используется конечная точка `standardEndpoint` типа `dynamicEndpoint`, как показано в следующем фрагменте.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-141">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="5c8fe-142">Если клиент использует конечную точку типа `dynamicEndpoint`, обнаружение осуществляется средой выполнения автоматически.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-142">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="5c8fe-143">При обнаружении используются различные параметры, например те, которые определены в разделе `discoveryClientSettings`, задающем тип используемой конечной точки обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-143">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="5c8fe-144">Критерии поиска, используемые для поиска служб:</span><span class="sxs-lookup"><span data-stu-id="5c8fe-144">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="5c8fe-145">Данный образец расширяет эту возможность и изменяет используемый клиентом объект <xref:System.ServiceModel.Discovery.FindCriteria>, а также некоторые свойства стандартной конечной точки `updDiscoveryEndpoint`, применяемой для обнаружения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-145">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="5c8fe-146">Измененный объект <xref:System.ServiceModel.Discovery.FindCriteria> использует область и указанный алгоритм `scopeMatchBy`, а также пользовательские критерии завершения.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-146">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="5c8fe-147">Кроме того, образец также показывает, как клиент может отправлять XML-элементы с помощью сообщений `Probe`.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-147">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="5c8fe-148">Наконец, вносятся некоторые изменения в конечную точку <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>. В частности, меняется версия используемого протокола и параметры UDP, как показано в приведенном далее файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-148">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="5c8fe-149">Далее приведен полный листинг конфигурации клиента для этого образца.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-149">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>
</configuration>
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5c8fe-150">Использование этого образца</span><span class="sxs-lookup"><span data-stu-id="5c8fe-150">To use this sample</span></span>  
  
1. <span data-ttu-id="5c8fe-151">В этом образце используются конечные точки HTTP, и для работы этого образца необходимо добавить соответствующие списки управления доступом по URL-адресу.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-151">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="5c8fe-152">Дополнительные сведения см. в разделе [Настройка HTTP и HTTPS](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="5c8fe-152">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="5c8fe-153">Нужные списки управления доступом будут добавлены после выполнения следующей команды с повышенными привилегиями.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-153">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="5c8fe-154">Если команда не работает, следует указать домен и имя пользователя в следующих аргументах.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-154">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="5c8fe-155">Создайте решение.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-155">Build the solution.</span></span>  
  
3. <span data-ttu-id="5c8fe-156">Выполните исполняемый файл службы из каталога сборки.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-156">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="5c8fe-157">Выполните исполняемый файл клиента.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-157">Run the client executable.</span></span> <span data-ttu-id="5c8fe-158">Учтите, что клиент может определить расположение службы.</span><span class="sxs-lookup"><span data-stu-id="5c8fe-158">Note that the client is able to locate the service.</span></span>  
