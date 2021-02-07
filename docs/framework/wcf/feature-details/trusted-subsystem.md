---
description: Дополнительные сведения о доверенной подсистеме
title: Доверенная подсистема
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 41c2943c7794206dba06ef8b5bbee762931ce0c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733051"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="1b38e-103">Доверенная подсистема</span><span class="sxs-lookup"><span data-stu-id="1b38e-103">Trusted Subsystem</span></span>

<span data-ttu-id="1b38e-104">Клиент обращается к одной или нескольким веб-службам, распределенным по сети.</span><span class="sxs-lookup"><span data-stu-id="1b38e-104">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="1b38e-105">Веб-службы устроены так, что доступ к дополнительным ресурсам (таким как базы данных или другие веб-службы) инкапсулируется в бизнес-логике веб-службы.</span><span class="sxs-lookup"><span data-stu-id="1b38e-105">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="1b38e-106">Эти ресурсы должны быть защищены от несанкционированного доступа.</span><span class="sxs-lookup"><span data-stu-id="1b38e-106">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="1b38e-107">На следующем рисунке показан процесс доверенной подсистемы.</span><span class="sxs-lookup"><span data-stu-id="1b38e-107">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="1b38e-108">![Доверенная подсистема](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="1b38e-108">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="1b38e-109">Показанный на рисунке процесс доверенной подсистемы пошагово описан ниже.</span><span class="sxs-lookup"><span data-stu-id="1b38e-109">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="1b38e-110">Клиент отправляет запрос (вместе с учетными данными) доверенной подсистеме.</span><span class="sxs-lookup"><span data-stu-id="1b38e-110">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="1b38e-111">Доверенная подсистема проверяет подлинность пользователя и авторизует его.</span><span class="sxs-lookup"><span data-stu-id="1b38e-111">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="1b38e-112">Доверенная подсистема отправляет сообщение запроса удаленному ресурсу.</span><span class="sxs-lookup"><span data-stu-id="1b38e-112">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="1b38e-113">Этот запрос сопровождается учетными данными доверенной подсистемы (или учетной записи службы, от имени которой выполняется процесс доверенной подсистемы).</span><span class="sxs-lookup"><span data-stu-id="1b38e-113">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="1b38e-114">Внутренний ресурс проверяет подлинность доверенной подсистемы и авторизует ее.</span><span class="sxs-lookup"><span data-stu-id="1b38e-114">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="1b38e-115">Затем он обрабатывает запрос и отправляет ответ доверенной подсистеме.</span><span class="sxs-lookup"><span data-stu-id="1b38e-115">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="1b38e-116">Доверенная подсистема обрабатывает ответ и отправляет свой ответ клиенту.</span><span class="sxs-lookup"><span data-stu-id="1b38e-116">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="1b38e-117">Характеристика</span><span class="sxs-lookup"><span data-stu-id="1b38e-117">Characteristic</span></span>|<span data-ttu-id="1b38e-118">Описание</span><span class="sxs-lookup"><span data-stu-id="1b38e-118">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1b38e-119">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="1b38e-119">Security Mode</span></span>|<span data-ttu-id="1b38e-120">Сообщение</span><span class="sxs-lookup"><span data-stu-id="1b38e-120">Message</span></span>|  
|<span data-ttu-id="1b38e-121">Совместимость</span><span class="sxs-lookup"><span data-stu-id="1b38e-121">Interoperability</span></span>|<span data-ttu-id="1b38e-122">Только Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1b38e-122">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="1b38e-123">Проверка подлинности (служба)</span><span class="sxs-lookup"><span data-stu-id="1b38e-123">Authentication (service)</span></span>|<span data-ttu-id="1b38e-124">Служба маркеров безопасности проверяет подлинность клиентов и авторизует их.</span><span class="sxs-lookup"><span data-stu-id="1b38e-124">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="1b38e-125">Проверка подлинности (клиент)</span><span class="sxs-lookup"><span data-stu-id="1b38e-125">Authentication (client)</span></span>|<span data-ttu-id="1b38e-126">Доверенная подсистема проверяет подлинность клиента, а ресурс проверяет подлинность службы доверенной подсистемы.</span><span class="sxs-lookup"><span data-stu-id="1b38e-126">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="1b38e-127">Целостность</span><span class="sxs-lookup"><span data-stu-id="1b38e-127">Integrity</span></span>|<span data-ttu-id="1b38e-128">Да</span><span class="sxs-lookup"><span data-stu-id="1b38e-128">Yes</span></span>|  
|<span data-ttu-id="1b38e-129">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="1b38e-129">Confidentiality</span></span>|<span data-ttu-id="1b38e-130">Да</span><span class="sxs-lookup"><span data-stu-id="1b38e-130">Yes</span></span>|  
|<span data-ttu-id="1b38e-131">Транспорт</span><span class="sxs-lookup"><span data-stu-id="1b38e-131">Transport</span></span>|<span data-ttu-id="1b38e-132">HTTP между клиентом и службой доверенной подсистемы.</span><span class="sxs-lookup"><span data-stu-id="1b38e-132">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="1b38e-133">NET.TCP между службой доверенной подсистемы и ресурсом (внутренней службой).</span><span class="sxs-lookup"><span data-stu-id="1b38e-133">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="1b38e-134">Привязка</span><span class="sxs-lookup"><span data-stu-id="1b38e-134">Binding</span></span>|<span data-ttu-id="1b38e-135"><xref:System.ServiceModel.WSHttpBinding> перетаскивани <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1b38e-135"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="1b38e-136">Ресурс (внутренняя служба)</span><span class="sxs-lookup"><span data-stu-id="1b38e-136">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="1b38e-137">Код</span><span class="sxs-lookup"><span data-stu-id="1b38e-137">Code</span></span>  

 <span data-ttu-id="1b38e-138">В следующем коде показано, как создать конечную точку службы для ресурса, работающую в режиме безопасности транспорта по транспортному протоколу TCP.</span><span class="sxs-lookup"><span data-stu-id="1b38e-138">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="1b38e-139">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="1b38e-139">Configuration</span></span>  

 <span data-ttu-id="1b38e-140">В следующей конфигурации настраивается та же конечная точка с использованием конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1b38e-140">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="1b38e-141">Доверенная подсистема</span><span class="sxs-lookup"><span data-stu-id="1b38e-141">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="1b38e-142">Код</span><span class="sxs-lookup"><span data-stu-id="1b38e-142">Code</span></span>  

 <span data-ttu-id="1b38e-143">В следующем коде показано, как создать конечную точку службы для доверенной подсистемы, работающую в режиме безопасности сообщения по транспортному протоколу HTTP и использующую для проверки подлинности имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="1b38e-143">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="1b38e-144">В следующем коде показана служба в доверенной подсистеме, которая обменивается данными с внутренней службой в режиме безопасности транспорта по транспортному протоколу TCP.</span><span class="sxs-lookup"><span data-stu-id="1b38e-144">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="1b38e-145">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="1b38e-145">Configuration</span></span>  

 <span data-ttu-id="1b38e-146">В следующей конфигурации настраивается та же конечная точка с использованием конфигурации.</span><span class="sxs-lookup"><span data-stu-id="1b38e-146">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="1b38e-147">Обратите внимание на две привязки: одна защищает службу, размещенную в доверенной подсистеме, а вторая обеспечивает обмен данными между доверенной подсистемой и внутренней службой.</span><span class="sxs-lookup"><span data-stu-id="1b38e-147">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="1b38e-148">Клиент</span><span class="sxs-lookup"><span data-stu-id="1b38e-148">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="1b38e-149">Код</span><span class="sxs-lookup"><span data-stu-id="1b38e-149">Code</span></span>  

 <span data-ttu-id="1b38e-150">В следующем коде показано, как создать клиент, обменивающийся данными с доверенной подсистемой в режиме безопасности сообщения по протоколу HTTP и использующий для проверки подлинности имя пользователя и пароль.</span><span class="sxs-lookup"><span data-stu-id="1b38e-150">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="1b38e-151">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="1b38e-151">Configuration</span></span>  

 <span data-ttu-id="1b38e-152">Следующий код служит для настройки клиента для использования режима безопасности сообщений по протоколу HTTP, а также имени пользователя и пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="1b38e-152">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="1b38e-153">Указать имя пользователя и пароль можно только с помощью кода (они не подлежат настройке).</span><span class="sxs-lookup"><span data-stu-id="1b38e-153">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b38e-154">См. также</span><span class="sxs-lookup"><span data-stu-id="1b38e-154">See also</span></span>

- [<span data-ttu-id="1b38e-155">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="1b38e-155">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="1b38e-156">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1b38e-156">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
