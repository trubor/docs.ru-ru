---
description: Дополнительные сведения о безопасности сообщений с помощью клиента сертификатов
title: Безопасность сообщений при использовании клиентом сертификата
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: f1924510c5860b377568da204bbd9154e4970c24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99727068"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="744d5-103">Безопасность сообщений при использовании клиентом сертификата</span><span class="sxs-lookup"><span data-stu-id="744d5-103">Message Security with a Certificate Client</span></span>

<span data-ttu-id="744d5-104">В следующем сценарии показана защита клиента Windows Communication Foundation (WCF) и службы с помощью режима безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="744d5-104">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="744d5-105">Проверка подлинности клиента и службы выполняется с помощью сертификатов.</span><span class="sxs-lookup"><span data-stu-id="744d5-105">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="744d5-106">Дополнительные сведения см. в разделе [Безопасность распределенных приложений](distributed-application-security.md).</span><span class="sxs-lookup"><span data-stu-id="744d5-106">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![Снимок экрана, на котором показан клиент с сертификатом.](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="744d5-108">Пример приложения см. в разделе [сертификат безопасности сообщения](../samples/message-security-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="744d5-108">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="744d5-109">Характеристика</span><span class="sxs-lookup"><span data-stu-id="744d5-109">Characteristic</span></span>|<span data-ttu-id="744d5-110">Описание</span><span class="sxs-lookup"><span data-stu-id="744d5-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="744d5-111">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="744d5-111">Security Mode</span></span>|<span data-ttu-id="744d5-112">Сообщение</span><span class="sxs-lookup"><span data-stu-id="744d5-112">Message</span></span>|  
|<span data-ttu-id="744d5-113">Совместимость</span><span class="sxs-lookup"><span data-stu-id="744d5-113">Interoperability</span></span>|<span data-ttu-id="744d5-114">Только WCF</span><span class="sxs-lookup"><span data-stu-id="744d5-114">WCF only</span></span>|  
|<span data-ttu-id="744d5-115">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="744d5-115">Authentication (Server)</span></span>|<span data-ttu-id="744d5-116">Использование сертификатов служб</span><span class="sxs-lookup"><span data-stu-id="744d5-116">Using service certificate</span></span>|  
|<span data-ttu-id="744d5-117">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="744d5-117">Authentication (Client)</span></span>|<span data-ttu-id="744d5-118">Использование сертификатов клиента</span><span class="sxs-lookup"><span data-stu-id="744d5-118">Using client certificate</span></span>|  
|<span data-ttu-id="744d5-119">Целостность</span><span class="sxs-lookup"><span data-stu-id="744d5-119">Integrity</span></span>|<span data-ttu-id="744d5-120">Да</span><span class="sxs-lookup"><span data-stu-id="744d5-120">Yes</span></span>|  
|<span data-ttu-id="744d5-121">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="744d5-121">Confidentiality</span></span>|<span data-ttu-id="744d5-122">Да</span><span class="sxs-lookup"><span data-stu-id="744d5-122">Yes</span></span>|  
|<span data-ttu-id="744d5-123">Транспорт</span><span class="sxs-lookup"><span data-stu-id="744d5-123">Transport</span></span>|<span data-ttu-id="744d5-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="744d5-124">HTTP</span></span>|  
|<span data-ttu-id="744d5-125">Привязка</span><span class="sxs-lookup"><span data-stu-id="744d5-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="744d5-126">Служба</span><span class="sxs-lookup"><span data-stu-id="744d5-126">Service</span></span>  

 <span data-ttu-id="744d5-127">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="744d5-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="744d5-128">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="744d5-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="744d5-129">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="744d5-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="744d5-130">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="744d5-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="744d5-131">Код</span><span class="sxs-lookup"><span data-stu-id="744d5-131">Code</span></span>  

 <span data-ttu-id="744d5-132">В следующем коде показано создание конечной точки службы, которая использует безопасность сообщений для установления защищенного контекста.</span><span class="sxs-lookup"><span data-stu-id="744d5-132">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="744d5-133">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="744d5-133">Configuration</span></span>  

 <span data-ttu-id="744d5-134">Вместо кода можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="744d5-134">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="744d5-135">Клиент</span><span class="sxs-lookup"><span data-stu-id="744d5-135">Client</span></span>  

 <span data-ttu-id="744d5-136">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="744d5-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="744d5-137">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="744d5-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="744d5-138">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="744d5-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="744d5-139">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="744d5-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="744d5-140">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="744d5-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="744d5-141">Пример:</span><span class="sxs-lookup"><span data-stu-id="744d5-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="744d5-142">Код</span><span class="sxs-lookup"><span data-stu-id="744d5-142">Code</span></span>  

 <span data-ttu-id="744d5-143">Следующий код служит для создания клиента.</span><span class="sxs-lookup"><span data-stu-id="744d5-143">The following code creates the client.</span></span> <span data-ttu-id="744d5-144">Привязка осуществляется к безопасности режима сообщений, и типу учетных данных клиента присваивается значение `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="744d5-144">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="744d5-145">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="744d5-145">Configuration</span></span>  

 <span data-ttu-id="744d5-146">В следующей конфигурации задается сертификат клиента с помощью поведения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="744d5-146">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="744d5-147">Дополнительные сведения см. в разделе [Работа с сертификатами](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="744d5-147">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="744d5-148">Код также использует `identity` элемент> <, чтобы указать службу доменных имен (DNS) ожидаемого удостоверения сервера.</span><span class="sxs-lookup"><span data-stu-id="744d5-148">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="744d5-149">Дополнительные сведения об удостоверении см. в статье [удостоверение службы и проверка подлинности](service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="744d5-149">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="744d5-150">См. также</span><span class="sxs-lookup"><span data-stu-id="744d5-150">See also</span></span>

- [<span data-ttu-id="744d5-151">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="744d5-151">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="744d5-152">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="744d5-152">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="744d5-153">Работа с сертификатами</span><span class="sxs-lookup"><span data-stu-id="744d5-153">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="744d5-154">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="744d5-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
