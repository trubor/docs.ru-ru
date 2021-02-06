---
description: 'Дополнительные сведения: <comContracts>'
title: <comContracts>
ms.date: 03/30/2017
ms.assetid: 42e74148-223d-4888-a8ed-1d928527eb09
ms.openlocfilehash: 263210b4499274fe009a6b1b1e46c1f09dd007ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638656"
---
# \<comContracts>

<span data-ttu-id="ffa32-102">Раздел конфигурации `comContracts` содержит элементы, которые позволяют задавать различные свойства контракта службы интеграции COM+.</span><span class="sxs-lookup"><span data-stu-id="ffa32-102">The `comContracts` configuration section contains elements that allow you to specify various properties of a COM+ integration service contract.</span></span>  
  
## <a name="specifying-namespace-and-contract"></a><span data-ttu-id="ffa32-103">Задание пространства имен и контракта</span><span class="sxs-lookup"><span data-stu-id="ffa32-103">Specifying Namespace and Contract</span></span>  

 <span data-ttu-id="ffa32-104">Контракты службы интеграции COM+ в настоящее время ограничены `http://tempuri.org` пространством имен, а имя контракта является производным от поддерживающего COM-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ffa32-104">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="ffa32-105">Однако можно указать альтернативы, используя раздел `comContracts` в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="ffa32-105">You can, however, specify alternatives by using the `comContracts` section in the configuration file.</span></span>  
  
 <span data-ttu-id="ffa32-106">Например, для указания пространства имен, имени контракта службы и параметра для принудительного использования сеансовых привязок можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="ffa32-106">For example, you can use the following configuration to specify the namespace and contract name of the service contract, as well as an option to enforce usage on sessionful bindings.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="ffa32-107">После инициализации службы указанные пространства имен и имена контрактов применяются к созданным описаниям служб.</span><span class="sxs-lookup"><span data-stu-id="ffa32-107">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
 <span data-ttu-id="ffa32-108">Если раздел пуст, при инициализации службы применяется пространство имен по умолчанию и имя контракта, взятое из идентификатора поддерживающего COM-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ffa32-108">When this section is empty, the service initialization applies a default namespace and contract name taken from the supporting COM interface ID.</span></span>  
  
 <span data-ttu-id="ffa32-109">Кроме того, элемент можно использовать [\<exposedMethod>](exposedmethod.md) для указания методов COM+, предоставляемых, когда интерфейс в компоненте com+ предоставляется как веб-служба.</span><span class="sxs-lookup"><span data-stu-id="ffa32-109">In addition, you can use the [\<exposedMethod>](exposedmethod.md) element to specify COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span> <span data-ttu-id="ffa32-110">Можно также использовать [\<persistableTypes>](persistabletypes.md) для указания сохраняемых типов, используемых при интеграции.</span><span class="sxs-lookup"><span data-stu-id="ffa32-110">You can also use the [\<persistableTypes>](persistabletypes.md) to specify persistable types used in integration.</span></span> <span data-ttu-id="ffa32-111">Наконец, можно использовать [\<userDefinedType>](userdefinedtype.md) элемент для включения определяемых пользователем типов (UDT), которые должны быть включены в контракт службы.</span><span class="sxs-lookup"><span data-stu-id="ffa32-111">Finally, you can use the [\<userDefinedType>](userdefinedtype.md) element to include User Defined Types (UDT) that are to be included in the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffa32-112">См. также</span><span class="sxs-lookup"><span data-stu-id="ffa32-112">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<exposedMethod>](exposedmethod.md)
- [\<persistableTypes>](persistabletypes.md)
- [\<userDefinedType>](userdefinedtype.md)
- [\<comContract>](comcontract.md)
- [<span data-ttu-id="ffa32-113">Интеграция с приложениями COM+</span><span class="sxs-lookup"><span data-stu-id="ffa32-113">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="ffa32-114">Практическое руководство. Настройка параметров службы COM+</span><span class="sxs-lookup"><span data-stu-id="ffa32-114">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
