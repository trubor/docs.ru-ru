---
description: 'Дополнительные сведения: использование Сервицесроттлингбехавиор для управления производительностью службы WCF'
title: Использование ServiceThrottlingBehavior для управления производительностью службы WCF
ms.date: 03/30/2017
helpviewer_keywords:
- behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
ms.openlocfilehash: 4a53c89c6b17402b7dd32120d049426052e4f9e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704424"
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a><span data-ttu-id="6c5f0-103">Использование ServiceThrottlingBehavior для управления производительностью службы WCF</span><span class="sxs-lookup"><span data-stu-id="6c5f0-103">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>

<span data-ttu-id="6c5f0-104">Класс <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> представляет свойства, которые можно использовать для ограничения количества экземпляров или сеансов, создаваемых на уровне приложения.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-104">The <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class exposes properties that you can use to limit how many instances or sessions are created at the application level.</span></span> <span data-ttu-id="6c5f0-105">Используя такое поведение, можно точно настроить производительность приложения Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6c5f0-105">Using this behavior, you can fine-tune the performance of your Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a><span data-ttu-id="6c5f0-106">Управление экземплярами службы и одновременными вызовами</span><span class="sxs-lookup"><span data-stu-id="6c5f0-106">Controlling Service Instances and Concurrent Calls</span></span>  

 <span data-ttu-id="6c5f0-107">С помощью свойства <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> задайте максимальное количество одновременно обрабатываемых сообщений в классе <xref:System.ServiceModel.ServiceHost>, а с помощью свойства <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> задайте максимальное количество объектов <xref:System.ServiceModel.InstanceContext> в службе.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-107">Use the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> property to specify the maximum number of messages actively processing across a <xref:System.ServiceModel.ServiceHost> class, and the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> property to specify the maximum number of <xref:System.ServiceModel.InstanceContext> objects in the service.</span></span>  
  
 <span data-ttu-id="6c5f0-108">Поскольку определение параметров для этих свойств обычно происходит после реального опыта работы приложения с загрузкой, параметры <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> свойств обычно задаются в файле конфигурации приложения с помощью [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-108">Because determining the settings for these properties usually takes place after real-world experience running the application against loads, the settings for the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> properties is typically specified in an application configuration file using the [\<serviceThrottling>](../../configure-apps/file-schema/wcf/servicethrottling.md) element.</span></span>  
  
 <span data-ttu-id="6c5f0-109">В следующем примере кода показано использование класса <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> из файла конфигурации приложения, который, в качестве упрощенного примера, задает для свойств <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> и <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> значение 1.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-109">The following code example shows the use of the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> class from an application configuration file that sets the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> properties to 1 as a trivial example.</span></span> <span data-ttu-id="6c5f0-110">Фактические условия определяют оптимальные параметры для каждого конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-110">Real-world experience determines the optimal settings for any particular application.</span></span>  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 <span data-ttu-id="6c5f0-111">Точное поведение времени выполнения зависит от значений свойств <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> и <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>, которые управляют количеством сообщений, которые могут обрабатываться в операции одновременно, и временем существования службы <xref:System.ServiceModel.InstanceContext> относительно сеансов входящих каналов, соответственно.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-111">The exact run-time behavior depends upon the values of the <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> and <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> properties, which control how many messages can execute inside an operation at once and the lifetimes of the service <xref:System.ServiceModel.InstanceContext> relative to incoming channel sessions, respectively.</span></span>  
  
 <span data-ttu-id="6c5f0-112">Дополнительные сведения см. в разделах <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> и <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span><span class="sxs-lookup"><span data-stu-id="6c5f0-112">For details, see <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, and <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c5f0-113">См. также</span><span class="sxs-lookup"><span data-stu-id="6c5f0-113">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
