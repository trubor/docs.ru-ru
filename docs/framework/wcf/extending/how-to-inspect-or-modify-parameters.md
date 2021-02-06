---
description: Дополнительные сведения см. в статье как проверять или изменять параметры.
title: Практическое руководство. Проверка или изменение параметров
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: 90358f2fbd7366b11135ec2ebd044f7864d8a1e0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99653788"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="c7c08-103">Практическое руководство. Проверка или изменение параметров</span><span class="sxs-lookup"><span data-stu-id="c7c08-103">How to: Inspect or Modify Parameters</span></span>

<span data-ttu-id="c7c08-104">Вы можете проверить или изменить входящие или исходящие сообщения для одной операции в клиентском объекте Windows Communication Foundation (WCF) или WCF, реализовав <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> интерфейс и вставив его в клиентскую среду или службу среды выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="c7c08-104">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="c7c08-105">Как правило, для добавления инспекторов параметров для отдельной операции используется поведение операции; другие поведения могут использоваться для обеспечения быстрого доступа к среде выполнения в более широкой области действия.</span><span class="sxs-lookup"><span data-stu-id="c7c08-105">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="c7c08-106">Дополнительные сведения см. в разделе [расширение клиентов](extending-clients.md) и [Расширение диспетчеров](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="c7c08-106">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="c7c08-107">Проверка или изменение параметров</span><span class="sxs-lookup"><span data-stu-id="c7c08-107">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="c7c08-108">Реализовать интерфейс <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7c08-108">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="c7c08-109">Реализуйте поведение <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> или <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (в зависимости от того, какая требуется область действия), чтобы добавить инспектор параметров в свойство <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> или <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7c08-109">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="c7c08-110">Вставьте поведение до вызова метода <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> или <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> в производство каналов <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c7c08-110">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7c08-111">Дополнительные сведения см. [в разделе Настройка и расширение среды выполнения с помощью поведений](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c7c08-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7c08-112">Пример</span><span class="sxs-lookup"><span data-stu-id="c7c08-112">Example</span></span>  

 <span data-ttu-id="c7c08-113">В следующих примерах кода показаны, по порядку:</span><span class="sxs-lookup"><span data-stu-id="c7c08-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="c7c08-114">реализация инспектора параметров;</span><span class="sxs-lookup"><span data-stu-id="c7c08-114">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="c7c08-115">реализация поведения, вставляющего инспектор параметров с помощью <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> и <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>;</span><span class="sxs-lookup"><span data-stu-id="c7c08-115">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="c7c08-116">файл конфигурации, который загружает и запускает поведение конечной точки в клиентском приложении для вставки инспектора параметров в клиент.</span><span class="sxs-lookup"><span data-stu-id="c7c08-116">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c7c08-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c7c08-117">See also</span></span>

- [<span data-ttu-id="c7c08-118">Настройка и расширение среды выполнения с помощью поведений</span><span class="sxs-lookup"><span data-stu-id="c7c08-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
