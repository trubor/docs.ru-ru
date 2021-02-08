---
description: 'Дополнительные сведения: <extensions>'
title: <extensions>
ms.date: 03/30/2017
ms.assetid: bcfe5c44-04ef-4a20-96a5-90bfadf39623
ms.openlocfilehash: d54f30b50a43e01d32e9fceea65137c8967cb527
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782082"
---
# \<extensions>

<span data-ttu-id="f7f5c-102">Этот элемент конфигурации содержит коллекцию элементов XML, в которой находятся пользовательские метаданные, публикуемые вместе со стандартными обнаруживаемыми метаданными (EPR, ContractTypeName, BindingName, Scope и ListenURI).</span><span class="sxs-lookup"><span data-stu-id="f7f5c-102">This configuration element contains a collection of XML elements that contain custom metadata to be published along with the standard discoverable metadata (EPR, ContractTypeName, BindingName, Scope and ListenURI).</span></span> <span data-ttu-id="f7f5c-103">Далее приводится пример использования этого элемента конфигурации.</span><span class="sxs-lookup"><span data-stu-id="f7f5c-103">The following is an example of using this configuration element.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enable="true">
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="f7f5c-104">См. также</span><span class="sxs-lookup"><span data-stu-id="f7f5c-104">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
