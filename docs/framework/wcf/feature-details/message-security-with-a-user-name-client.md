---
description: 'Дополнительные сведения: защита сообщений с помощью клиента имени пользователя'
title: Безопасность сообщений при использовании клиентом учетных данных пользователя
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 4502635df3b52ba069c19fca7a73cc9395dd105d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756114"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="7e951-103">Безопасность сообщений при использовании клиентом учетных данных пользователя</span><span class="sxs-lookup"><span data-stu-id="7e951-103">Message Security with a User Name Client</span></span>

<span data-ttu-id="7e951-104">На следующем рисунке показана служба Windows Communication Foundation (WCF) и клиент защищены с помощью безопасности на уровне сообщений.</span><span class="sxs-lookup"><span data-stu-id="7e951-104">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="7e951-105">Служба проходит проверку подлинности с использованием сертификата X.509.</span><span class="sxs-lookup"><span data-stu-id="7e951-105">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="7e951-106">Подлинность клиента проверяется с помощью имени и пароля пользователя.</span><span class="sxs-lookup"><span data-stu-id="7e951-106">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="7e951-107">Пример приложения см. в разделе [Message Security имя пользователя](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="7e951-107">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="7e951-108">![Безопасность сообщений с использованием проверки подлинности имени пользователя](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="7e951-108">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="7e951-109">Характеристика</span><span class="sxs-lookup"><span data-stu-id="7e951-109">Characteristic</span></span>|<span data-ttu-id="7e951-110">Описание</span><span class="sxs-lookup"><span data-stu-id="7e951-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7e951-111">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="7e951-111">Security Mode</span></span>|<span data-ttu-id="7e951-112">Сообщение</span><span class="sxs-lookup"><span data-stu-id="7e951-112">Message</span></span>|  
|<span data-ttu-id="7e951-113">Совместимость</span><span class="sxs-lookup"><span data-stu-id="7e951-113">Interoperability</span></span>|<span data-ttu-id="7e951-114">Только Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="7e951-114">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="7e951-115">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="7e951-115">Authentication (Server)</span></span>|<span data-ttu-id="7e951-116">Первоначальное согласование возможно только после проверки подлинности сервера</span><span class="sxs-lookup"><span data-stu-id="7e951-116">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="7e951-117">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="7e951-117">Authentication (Client)</span></span>|<span data-ttu-id="7e951-118">Имя пользователя/пароль</span><span class="sxs-lookup"><span data-stu-id="7e951-118">User name/password</span></span>|  
|<span data-ttu-id="7e951-119">Целостность</span><span class="sxs-lookup"><span data-stu-id="7e951-119">Integrity</span></span>|<span data-ttu-id="7e951-120">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="7e951-120">Yes, using shared security context</span></span>|  
|<span data-ttu-id="7e951-121">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="7e951-121">Confidentiality</span></span>|<span data-ttu-id="7e951-122">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="7e951-122">Yes, using shared security context</span></span>|  
|<span data-ttu-id="7e951-123">Транспорт</span><span class="sxs-lookup"><span data-stu-id="7e951-123">Transport</span></span>|<span data-ttu-id="7e951-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="7e951-124">HTTP</span></span>|  
|<span data-ttu-id="7e951-125">Привязка</span><span class="sxs-lookup"><span data-stu-id="7e951-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="7e951-126">Служба</span><span class="sxs-lookup"><span data-stu-id="7e951-126">Service</span></span>  

 <span data-ttu-id="7e951-127">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="7e951-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7e951-128">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="7e951-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="7e951-129">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="7e951-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="7e951-130">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="7e951-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7e951-131">Код</span><span class="sxs-lookup"><span data-stu-id="7e951-131">Code</span></span>  

 <span data-ttu-id="7e951-132">В следующем коде показано, как создать конечную точку службы, которая использует безопасность сообщений.</span><span class="sxs-lookup"><span data-stu-id="7e951-132">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="7e951-133">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="7e951-133">Configuration</span></span>  

 <span data-ttu-id="7e951-134">Вместо кода можно использовать следующую конфигурацию:</span><span class="sxs-lookup"><span data-stu-id="7e951-134">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
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
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="7e951-135">Клиент</span><span class="sxs-lookup"><span data-stu-id="7e951-135">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="7e951-136">Код</span><span class="sxs-lookup"><span data-stu-id="7e951-136">Code</span></span>  

 <span data-ttu-id="7e951-137">Следующий код служит для создания клиента.</span><span class="sxs-lookup"><span data-stu-id="7e951-137">The following code creates the client.</span></span> <span data-ttu-id="7e951-138">Привязка осуществляется к безопасности режима сообщений, и типу учетных данных клиента присваивается значение `UserName`.</span><span class="sxs-lookup"><span data-stu-id="7e951-138">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="7e951-139">Указать имя пользователя и пароль можно только с помощью кода (они не подлежат настройке).</span><span class="sxs-lookup"><span data-stu-id="7e951-139">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="7e951-140">Здесь не показан код, который возвращает имя пользователя и пароль, потому что это происходит на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="7e951-140">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="7e951-141">Например, диалоговое окно Windows Forms используется для того, чтобы запросить пользователя о данных.</span><span class="sxs-lookup"><span data-stu-id="7e951-141">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="7e951-142">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="7e951-142">Configuration</span></span>  

 <span data-ttu-id="7e951-143">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="7e951-143">The following code configures the client.</span></span> <span data-ttu-id="7e951-144">Привязка осуществляется к безопасности режима сообщений, и типу учетных данных клиента присваивается значение `UserName`.</span><span class="sxs-lookup"><span data-stu-id="7e951-144">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="7e951-145">Указать имя пользователя и пароль можно только с помощью кода (они не подлежат настройке).</span><span class="sxs-lookup"><span data-stu-id="7e951-145">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7e951-146">См. также</span><span class="sxs-lookup"><span data-stu-id="7e951-146">See also</span></span>

- [<span data-ttu-id="7e951-147">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="7e951-147">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="7e951-148">Безопасность сообщений с использованием имени пользователя</span><span class="sxs-lookup"><span data-stu-id="7e951-148">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="7e951-149">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="7e951-149">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="7e951-150">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7e951-150">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
