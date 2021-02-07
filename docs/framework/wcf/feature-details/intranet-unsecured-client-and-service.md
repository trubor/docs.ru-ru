---
description: 'Дополнительные сведения: незащищенный клиент и служба в интрасети'
title: Незащищенные интранет-клиент и служба
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f450f5d4-3547-47ec-9320-2809e6a12634
ms.openlocfilehash: a03abc5b8eb0317c4d5d19347b3974d615570069
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704528"
---
# <a name="intranet-unsecured-client-and-service"></a><span data-ttu-id="8db7d-103">Незащищенные интранет-клиент и служба</span><span class="sxs-lookup"><span data-stu-id="8db7d-103">Intranet Unsecured Client and Service</span></span>

<span data-ttu-id="8db7d-104">На следующем рисунке показана простая служба Windows Communication Foundation (WCF), разработанная для предоставления информации о защищенной частной сети приложению WCF.</span><span class="sxs-lookup"><span data-stu-id="8db7d-104">The following illustration depicts a simple Windows Communication Foundation (WCF) service developed to provide information on a secure private network to a WCF application.</span></span> <span data-ttu-id="8db7d-105">Безопасность не требуется, поскольку данные имеют низкую важность, ожидается безопасность сети, или безопасность обеспечивается уровнем, который находится под инфраструктурой WCF.</span><span class="sxs-lookup"><span data-stu-id="8db7d-105">Security is not required because the data is of low importance, the network is expected to be inherently secure, or security is provided by a layer below the WCF infrastructure.</span></span>  
  
 ![Сценарий незащищенного клиента и службы в интрасети.](./media/intranet-unsecured-client-and-service/unsecured-web-client-service.gif)  
  
|<span data-ttu-id="8db7d-107">Характеристика</span><span class="sxs-lookup"><span data-stu-id="8db7d-107">Characteristic</span></span>|<span data-ttu-id="8db7d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="8db7d-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="8db7d-109">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="8db7d-109">Security Mode</span></span>|<span data-ttu-id="8db7d-110">None</span><span class="sxs-lookup"><span data-stu-id="8db7d-110">None</span></span>|  
|<span data-ttu-id="8db7d-111">Транспорт</span><span class="sxs-lookup"><span data-stu-id="8db7d-111">Transport</span></span>|<span data-ttu-id="8db7d-112">TCP</span><span class="sxs-lookup"><span data-stu-id="8db7d-112">TCP</span></span>|  
|<span data-ttu-id="8db7d-113">Привязка</span><span class="sxs-lookup"><span data-stu-id="8db7d-113">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
|<span data-ttu-id="8db7d-114">Совместимость</span><span class="sxs-lookup"><span data-stu-id="8db7d-114">Interoperability</span></span>|<span data-ttu-id="8db7d-115">Только WCF</span><span class="sxs-lookup"><span data-stu-id="8db7d-115">WCF only</span></span>|  
|<span data-ttu-id="8db7d-116">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="8db7d-116">Authentication</span></span>|<span data-ttu-id="8db7d-117">None</span><span class="sxs-lookup"><span data-stu-id="8db7d-117">None</span></span>|  
|<span data-ttu-id="8db7d-118">Целостность</span><span class="sxs-lookup"><span data-stu-id="8db7d-118">Integrity</span></span>|<span data-ttu-id="8db7d-119">None</span><span class="sxs-lookup"><span data-stu-id="8db7d-119">None</span></span>|  
|<span data-ttu-id="8db7d-120">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="8db7d-120">Confidentiality</span></span>|<span data-ttu-id="8db7d-121">None</span><span class="sxs-lookup"><span data-stu-id="8db7d-121">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="8db7d-122">Служба</span><span class="sxs-lookup"><span data-stu-id="8db7d-122">Service</span></span>  

 <span data-ttu-id="8db7d-123">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="8db7d-123">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8db7d-124">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="8db7d-124">Do one of the following:</span></span>  
  
- <span data-ttu-id="8db7d-125">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8db7d-125">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="8db7d-126">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="8db7d-126">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8db7d-127">Код</span><span class="sxs-lookup"><span data-stu-id="8db7d-127">Code</span></span>  

 <span data-ttu-id="8db7d-128">В следующем коде показано создание конечной точки без обеспечения безопасности.</span><span class="sxs-lookup"><span data-stu-id="8db7d-128">The following code shows how to create an endpoint with no security:</span></span>  
  
 [!code-csharp[C_UnsecuredService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#2)]
 [!code-vb[C_UnsecuredService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="8db7d-129">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="8db7d-129">Configuration</span></span>  

 <span data-ttu-id="8db7d-130">В следующем коде настраивается та же конечная точка с использованием конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8db7d-130">The following code sets up the same endpoint using configuration:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration=""
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
                  bindingConfiguration="tcp_Unsecured"
                  name="netTcp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="tcp_Unsecured">  
          <security mode="None" />  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="8db7d-131">Клиент</span><span class="sxs-lookup"><span data-stu-id="8db7d-131">Client</span></span>  

 <span data-ttu-id="8db7d-132">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="8db7d-132">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="8db7d-133">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="8db7d-133">Do one of the following:</span></span>  
  
- <span data-ttu-id="8db7d-134">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="8db7d-134">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="8db7d-135">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="8db7d-135">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="8db7d-136">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8db7d-136">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="8db7d-137">Пример:</span><span class="sxs-lookup"><span data-stu-id="8db7d-137">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="8db7d-138">Код</span><span class="sxs-lookup"><span data-stu-id="8db7d-138">Code</span></span>  

 <span data-ttu-id="8db7d-139">В следующем коде показан базовый клиент WCF, обращающийся к незащищенной конечной точке по протоколу TCP.</span><span class="sxs-lookup"><span data-stu-id="8db7d-139">The following code shows a basic WCF client that accesses an unsecured endpoint using the TCP protocol.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#2)]
 [!code-vb[C_UnsecuredClient#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="8db7d-140">Конфигурация</span><span class="sxs-lookup"><span data-stu-id="8db7d-140">Configuration</span></span>  

 <span data-ttu-id="8db7d-141">Следующий код конфигурации применяется к клиенту.</span><span class="sxs-lookup"><span data-stu-id="8db7d-141">The following configuration code applies to the client:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator "  
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"
                name="NetTcpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8db7d-142">См. также</span><span class="sxs-lookup"><span data-stu-id="8db7d-142">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- [<span data-ttu-id="8db7d-143">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="8db7d-143">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="8db7d-144">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8db7d-144">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
