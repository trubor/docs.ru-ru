---
description: 'Дополнительные сведения: безопасность сообщений с помощью взаимных сертификатов'
title: Безопасность сообщений с использованием взаимных сертификатов
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: c894f457dcd0fdc449c2f94eaee15004300df5fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726992"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="32e9f-103">Безопасность сообщений с использованием взаимных сертификатов</span><span class="sxs-lookup"><span data-stu-id="32e9f-103">Message Security with Mutual Certificates</span></span>

<span data-ttu-id="32e9f-104">В следующем сценарии показана служба Windows Communication Foundation (WCF) и клиент защищены с помощью режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="32e9f-104">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="32e9f-105">Проверка подлинности клиента и службы выполняется с помощью сертификатов.</span><span class="sxs-lookup"><span data-stu-id="32e9f-105">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="32e9f-106">Данный сценарий поддерживает возможность взаимодействия, поскольку в нем используется WS-Security с профилем маркера сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="32e9f-106">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32e9f-107">Данный сценарий не выполняет согласование сертификата службы.</span><span class="sxs-lookup"><span data-stu-id="32e9f-107">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="32e9f-108">Сертификат службы должен быть предоставлен клиенту перед началом любой связи.</span><span class="sxs-lookup"><span data-stu-id="32e9f-108">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="32e9f-109">Сертификат сервера может быть распределен приложением или предоставлен во внеполосной связи.</span><span class="sxs-lookup"><span data-stu-id="32e9f-109">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="32e9f-110">![Безопасность сообщений с помощью взаимных сертификатов](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="32e9f-110">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="32e9f-111">Характеристика</span><span class="sxs-lookup"><span data-stu-id="32e9f-111">Characteristic</span></span>|<span data-ttu-id="32e9f-112">Описание</span><span class="sxs-lookup"><span data-stu-id="32e9f-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="32e9f-113">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="32e9f-113">Security Mode</span></span>|<span data-ttu-id="32e9f-114">Сообщение</span><span class="sxs-lookup"><span data-stu-id="32e9f-114">Message</span></span>|  
|<span data-ttu-id="32e9f-115">Совместимость</span><span class="sxs-lookup"><span data-stu-id="32e9f-115">Interoperability</span></span>|<span data-ttu-id="32e9f-116">Да, с клиентами и службами, совместимыми с профилем маркера WS-Security и сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="32e9f-116">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="32e9f-117">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="32e9f-117">Authentication</span></span>|<span data-ttu-id="32e9f-118">Взаимная проверка подлинности сервера и клиента.</span><span class="sxs-lookup"><span data-stu-id="32e9f-118">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="32e9f-119">Целостность</span><span class="sxs-lookup"><span data-stu-id="32e9f-119">Integrity</span></span>|<span data-ttu-id="32e9f-120">Да</span><span class="sxs-lookup"><span data-stu-id="32e9f-120">Yes</span></span>|  
|<span data-ttu-id="32e9f-121">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="32e9f-121">Confidentiality</span></span>|<span data-ttu-id="32e9f-122">Да</span><span class="sxs-lookup"><span data-stu-id="32e9f-122">Yes</span></span>|  
|<span data-ttu-id="32e9f-123">Транспорт</span><span class="sxs-lookup"><span data-stu-id="32e9f-123">Transport</span></span>|<span data-ttu-id="32e9f-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="32e9f-124">HTTP</span></span>|  
|<span data-ttu-id="32e9f-125">Привязка</span><span class="sxs-lookup"><span data-stu-id="32e9f-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="32e9f-126">Служба</span><span class="sxs-lookup"><span data-stu-id="32e9f-126">Service</span></span>  

 <span data-ttu-id="32e9f-127">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="32e9f-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="32e9f-128">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="32e9f-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="32e9f-129">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="32e9f-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="32e9f-130">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="32e9f-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="32e9f-131">Код</span><span class="sxs-lookup"><span data-stu-id="32e9f-131">Code</span></span>  

 <span data-ttu-id="32e9f-132">В следующем коде показано, как создать конечную точку службы, которая использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="32e9f-132">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="32e9f-133">Служба требует прохождения проверки подлинности сертификата.</span><span class="sxs-lookup"><span data-stu-id="32e9f-133">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="32e9f-134">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="32e9f-134">Configuration</span></span>  

 <span data-ttu-id="32e9f-135">Вместо кода для создания той же службы можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="32e9f-135">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="32e9f-136">Клиент</span><span class="sxs-lookup"><span data-stu-id="32e9f-136">Client</span></span>  

 <span data-ttu-id="32e9f-137">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="32e9f-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="32e9f-138">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="32e9f-138">Do one of the following:</span></span>  
  
- <span data-ttu-id="32e9f-139">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="32e9f-139">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="32e9f-140">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="32e9f-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="32e9f-141">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="32e9f-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="32e9f-142">Пример:</span><span class="sxs-lookup"><span data-stu-id="32e9f-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="32e9f-143">Код</span><span class="sxs-lookup"><span data-stu-id="32e9f-143">Code</span></span>  

 <span data-ttu-id="32e9f-144">Следующий код служит для создания клиента.</span><span class="sxs-lookup"><span data-stu-id="32e9f-144">The following code creates the client.</span></span> <span data-ttu-id="32e9f-145">Режим безопасности установлен в Message, и типу учетных данных клиента присвоено значение Certificate.</span><span class="sxs-lookup"><span data-stu-id="32e9f-145">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="32e9f-146">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="32e9f-146">Configuration</span></span>  

 <span data-ttu-id="32e9f-147">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="32e9f-147">The following configures the client.</span></span> <span data-ttu-id="32e9f-148">Сертификат клиента должен быть указан с помощью [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="32e9f-148">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="32e9f-149">Кроме того, сертификат службы указывается с помощью [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="32e9f-149">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32e9f-150">См. также</span><span class="sxs-lookup"><span data-stu-id="32e9f-150">See also</span></span>

- [<span data-ttu-id="32e9f-151">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="32e9f-151">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="32e9f-152">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="32e9f-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="32e9f-153">[Как создавать и устанавливать временные сертификаты в WCF для обеспечения безопасности транспорта во время разработки](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="32e9f-153">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
