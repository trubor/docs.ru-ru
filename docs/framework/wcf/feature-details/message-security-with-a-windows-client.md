---
description: Дополнительные сведения см. в статье безопасность сообщений с помощью клиента Windows.
title: Безопасность сообщений с клиентом Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: 97d415f68b4374ab2b18360347d7753f6be51313
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756101"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="084ff-103">Безопасность сообщений с клиентом Windows</span><span class="sxs-lookup"><span data-stu-id="084ff-103">Message Security with a Windows Client</span></span>

<span data-ttu-id="084ff-104">В этом сценарии показан клиент Windows Communication Foundation (WCF) и сервер, защищенный режимом безопасности сообщений.</span><span class="sxs-lookup"><span data-stu-id="084ff-104">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="084ff-105">Клиент и служба проходят проверку подлинности с использованием учетных данных Windows.</span><span class="sxs-lookup"><span data-stu-id="084ff-105">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="084ff-106">![Безопасность сообщений с помощью клиента Windows](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="084ff-106">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="084ff-107">Характеристика</span><span class="sxs-lookup"><span data-stu-id="084ff-107">Characteristic</span></span>|<span data-ttu-id="084ff-108">Описание</span><span class="sxs-lookup"><span data-stu-id="084ff-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="084ff-109">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="084ff-109">Security Mode</span></span>|<span data-ttu-id="084ff-110">Сообщение</span><span class="sxs-lookup"><span data-stu-id="084ff-110">Message</span></span>|  
|<span data-ttu-id="084ff-111">Совместимость</span><span class="sxs-lookup"><span data-stu-id="084ff-111">Interoperability</span></span>|<span data-ttu-id="084ff-112">Только WCF</span><span class="sxs-lookup"><span data-stu-id="084ff-112">WCF Only</span></span>|  
|<span data-ttu-id="084ff-113">Проверка подлинности (сервера)</span><span class="sxs-lookup"><span data-stu-id="084ff-113">Authentication (Server)</span></span>|<span data-ttu-id="084ff-114">Взаимная проверка подлинности сервера и клиента</span><span class="sxs-lookup"><span data-stu-id="084ff-114">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="084ff-115">Проверка подлинности (клиента)</span><span class="sxs-lookup"><span data-stu-id="084ff-115">Authentication (Client)</span></span>|<span data-ttu-id="084ff-116">Взаимная проверка подлинности сервера и клиента</span><span class="sxs-lookup"><span data-stu-id="084ff-116">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="084ff-117">Целостность</span><span class="sxs-lookup"><span data-stu-id="084ff-117">Integrity</span></span>|<span data-ttu-id="084ff-118">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="084ff-118">Yes, using shared security context</span></span>|  
|<span data-ttu-id="084ff-119">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="084ff-119">Confidentiality</span></span>|<span data-ttu-id="084ff-120">Да, используется общий контекст безопасности</span><span class="sxs-lookup"><span data-stu-id="084ff-120">Yes, using shared security context</span></span>|  
|<span data-ttu-id="084ff-121">Транспорт</span><span class="sxs-lookup"><span data-stu-id="084ff-121">Transport</span></span>|<span data-ttu-id="084ff-122">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="084ff-122">NET.TCP</span></span>|  
|<span data-ttu-id="084ff-123">Привязка</span><span class="sxs-lookup"><span data-stu-id="084ff-123">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="084ff-124">Служба</span><span class="sxs-lookup"><span data-stu-id="084ff-124">Service</span></span>  

 <span data-ttu-id="084ff-125">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="084ff-125">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="084ff-126">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="084ff-126">Do one of the following:</span></span>  
  
- <span data-ttu-id="084ff-127">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="084ff-127">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="084ff-128">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="084ff-128">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="084ff-129">Код</span><span class="sxs-lookup"><span data-stu-id="084ff-129">Code</span></span>  

 <span data-ttu-id="084ff-130">В следующем коде показано создание конечной точки службы, которая использует безопасность сообщений для установления защищенного контекста с компьютером Windows.</span><span class="sxs-lookup"><span data-stu-id="084ff-130">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="084ff-131">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="084ff-131">Configuration</span></span>  

 <span data-ttu-id="084ff-132">Вместо кода для настройки службы можно использовать следующую конфигурацию:</span><span class="sxs-lookup"><span data-stu-id="084ff-132">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="084ff-133">Клиент</span><span class="sxs-lookup"><span data-stu-id="084ff-133">Client</span></span>  

 <span data-ttu-id="084ff-134">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="084ff-134">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="084ff-135">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="084ff-135">Do one of the following:</span></span>  
  
- <span data-ttu-id="084ff-136">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="084ff-136">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="084ff-137">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="084ff-137">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="084ff-138">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="084ff-138">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="084ff-139">Пример:</span><span class="sxs-lookup"><span data-stu-id="084ff-139">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="084ff-140">Код</span><span class="sxs-lookup"><span data-stu-id="084ff-140">Code</span></span>  

 <span data-ttu-id="084ff-141">Следующий код служит для создания клиента.</span><span class="sxs-lookup"><span data-stu-id="084ff-141">The following code creates a client.</span></span> <span data-ttu-id="084ff-142">Привязка осуществляется к безопасности режима сообщений, и типу учетных данных клиента присваивается значение `Windows`.</span><span class="sxs-lookup"><span data-stu-id="084ff-142">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="084ff-143">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="084ff-143">Configuration</span></span>  

 <span data-ttu-id="084ff-144">Следующая конфигурация используется для задания свойств клиента.</span><span class="sxs-lookup"><span data-stu-id="084ff-144">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="084ff-145">См. также</span><span class="sxs-lookup"><span data-stu-id="084ff-145">See also</span></span>

- [<span data-ttu-id="084ff-146">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="084ff-146">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="084ff-147">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="084ff-147">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
