---
description: 'Дополнительные сведения: незащищенный клиент и служба в Интернете'
title: Незащищенные интернет-клиент и служба
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97a10d79-3e7d-4bd1-9a99-fd9807fd70bc
ms.openlocfilehash: 8b402b276c80b2e1c148de0837d8644aad7a2d4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802779"
---
# <a name="internet-unsecured-client-and-service"></a><span data-ttu-id="12f26-103">Незащищенные интернет-клиент и служба</span><span class="sxs-lookup"><span data-stu-id="12f26-103">Internet Unsecured Client and Service</span></span>

<span data-ttu-id="12f26-104">На следующем рисунке показан пример общедоступного, незащищенного Windows Communication Foundation (WCF) клиента и службы.</span><span class="sxs-lookup"><span data-stu-id="12f26-104">The following illustration shows an example of a public, unsecured Windows Communication Foundation (WCF) client and service:</span></span>  
  
 ![Снимок экрана, на котором показан незащищенный Интернет](./media/internet-unsecured-client-and-service/public-unsecured-internet.gif)  
  
|<span data-ttu-id="12f26-106">Характеристика</span><span class="sxs-lookup"><span data-stu-id="12f26-106">Characteristic</span></span>|<span data-ttu-id="12f26-107">Описание</span><span class="sxs-lookup"><span data-stu-id="12f26-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="12f26-108">Режим безопасности</span><span class="sxs-lookup"><span data-stu-id="12f26-108">Security Mode</span></span>|<span data-ttu-id="12f26-109">None</span><span class="sxs-lookup"><span data-stu-id="12f26-109">None</span></span>|  
|<span data-ttu-id="12f26-110">Транспорт</span><span class="sxs-lookup"><span data-stu-id="12f26-110">Transport</span></span>|<span data-ttu-id="12f26-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="12f26-111">HTTP</span></span>|  
|<span data-ttu-id="12f26-112">Привязка</span><span class="sxs-lookup"><span data-stu-id="12f26-112">Binding</span></span>|<span data-ttu-id="12f26-113"><xref:System.ServiceModel.BasicHttpBinding> в коде или в [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) элементе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="12f26-113"><xref:System.ServiceModel.BasicHttpBinding> in code, or the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element in configuration.</span></span>|  
|<span data-ttu-id="12f26-114">Совместимость</span><span class="sxs-lookup"><span data-stu-id="12f26-114">Interoperability</span></span>|<span data-ttu-id="12f26-115">С существующими службами и клиентами веб-служб</span><span class="sxs-lookup"><span data-stu-id="12f26-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="12f26-116">Аутентификация</span><span class="sxs-lookup"><span data-stu-id="12f26-116">Authentication</span></span>|<span data-ttu-id="12f26-117">None</span><span class="sxs-lookup"><span data-stu-id="12f26-117">None</span></span>|  
|<span data-ttu-id="12f26-118">Целостность</span><span class="sxs-lookup"><span data-stu-id="12f26-118">Integrity</span></span>|<span data-ttu-id="12f26-119">None</span><span class="sxs-lookup"><span data-stu-id="12f26-119">None</span></span>|  
|<span data-ttu-id="12f26-120">Конфиденциальность</span><span class="sxs-lookup"><span data-stu-id="12f26-120">Confidentiality</span></span>|<span data-ttu-id="12f26-121">None</span><span class="sxs-lookup"><span data-stu-id="12f26-121">None</span></span>|  
  
## <a name="service"></a><span data-ttu-id="12f26-122">Служба</span><span class="sxs-lookup"><span data-stu-id="12f26-122">Service</span></span>  

 <span data-ttu-id="12f26-123">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="12f26-123">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="12f26-124">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="12f26-124">Do one of the following:</span></span>  
  
- <span data-ttu-id="12f26-125">Создайте автономную службу, используя код без конфигурации.</span><span class="sxs-lookup"><span data-stu-id="12f26-125">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="12f26-126">Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.</span><span class="sxs-lookup"><span data-stu-id="12f26-126">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="12f26-127">Код</span><span class="sxs-lookup"><span data-stu-id="12f26-127">Code</span></span>  

 <span data-ttu-id="12f26-128">В следующем коде показано создание конечной точки без безопасности.</span><span class="sxs-lookup"><span data-stu-id="12f26-128">The following code shows how to create an endpoint with no security.</span></span> <span data-ttu-id="12f26-129">По умолчанию режим безопасности <xref:System.ServiceModel.BasicHttpBinding> задан режим <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span><span class="sxs-lookup"><span data-stu-id="12f26-129">By default, the <xref:System.ServiceModel.BasicHttpBinding> has the security mode set to <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span>  
  
 [!code-csharp[C_UnsecuredService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredservice/cs/source.cs#1)]
 [!code-vb[C_UnsecuredService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredservice/vb/source.vb#1)]  
  
### <a name="service-configuration"></a><span data-ttu-id="12f26-130">Конфигурация службы</span><span class="sxs-lookup"><span data-stu-id="12f26-130">Service Configuration</span></span>  

 <span data-ttu-id="12f26-131">В следующем коде настраивается та же конечная точка с использованием конфигурации.</span><span class="sxs-lookup"><span data-stu-id="12f26-131">The following code sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="basicHttpBinding"  
                  bindingConfiguration="Basic_Unsecured"
                  name="BasicHttp_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="Basic_Unsecured" />  
      </basicHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="12f26-132">Клиент</span><span class="sxs-lookup"><span data-stu-id="12f26-132">Client</span></span>  

 <span data-ttu-id="12f26-133">Предполагается, что представленные ниже код и конфигурация выполняются независимо.</span><span class="sxs-lookup"><span data-stu-id="12f26-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="12f26-134">Выполните одно из следующих действий.</span><span class="sxs-lookup"><span data-stu-id="12f26-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="12f26-135">Создайте автономный клиент, используя код (и код клиента).</span><span class="sxs-lookup"><span data-stu-id="12f26-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="12f26-136">Создайте клиент, который не определяет никаких адресов конечных точек.</span><span class="sxs-lookup"><span data-stu-id="12f26-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="12f26-137">Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.</span><span class="sxs-lookup"><span data-stu-id="12f26-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="12f26-138">Пример:</span><span class="sxs-lookup"><span data-stu-id="12f26-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="12f26-139">Код</span><span class="sxs-lookup"><span data-stu-id="12f26-139">Code</span></span>  

 <span data-ttu-id="12f26-140">В следующем коде показан базовый клиент WCF, обращающийся к незащищенной конечной точке.</span><span class="sxs-lookup"><span data-stu-id="12f26-140">The following code shows a basic WCF client that accesses an unsecured endpoint.</span></span>  
  
 [!code-csharp[C_UnsecuredClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_unsecuredclient/cs/source.cs#1)]
 [!code-vb[C_UnsecuredClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_unsecuredclient/vb/source.vb#1)]  
  
### <a name="client-configuration"></a><span data-ttu-id="12f26-141">Конфигурация клиента</span><span class="sxs-lookup"><span data-stu-id="12f26-141">Client Configuration</span></span>  

 <span data-ttu-id="12f26-142">Следующий код служит для настройки клиента.</span><span class="sxs-lookup"><span data-stu-id="12f26-142">The following code configures the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="BasicHttpBinding_ICalculator" >  
          <security mode="None">  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://localhost/Calculator/Unsecured"  
          binding="basicHttpBinding"
          bindingConfiguration="BasicHttpBinding_ICalculator"  
          contract="ICalculator"
          name="BasicHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12f26-143">См. также</span><span class="sxs-lookup"><span data-stu-id="12f26-143">See also</span></span>

- [<span data-ttu-id="12f26-144">Типовые сценарии безопасности</span><span class="sxs-lookup"><span data-stu-id="12f26-144">Common Security Scenarios</span></span>](common-security-scenarios.md)
- [<span data-ttu-id="12f26-145">Обзор безопасности</span><span class="sxs-lookup"><span data-stu-id="12f26-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="12f26-146">[Модель безопасности для Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="12f26-146">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
