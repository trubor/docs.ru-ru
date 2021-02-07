---
description: Дополнительные сведения о том, как проверять и изменять сообщения в службе.
title: Практическое руководство. Проверка и изменение сообщений в службе
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 5fd3a5e49bdd35a3095e5855b399533337e133a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668881"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="06523-103">Практическое руководство. Проверка и изменение сообщений в службе</span><span class="sxs-lookup"><span data-stu-id="06523-103">How to: Inspect and Modify Messages on the Service</span></span>

<span data-ttu-id="06523-104">Вы можете проверять или изменять входящие или исходящие сообщения в клиенте Windows Communication Foundation (WCF), реализовав <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> и вставив его в среду выполнения службы.</span><span class="sxs-lookup"><span data-stu-id="06523-104">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="06523-105">Дополнительные сведения см. в разделе [Расширение диспетчеров](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="06523-105">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="06523-106">Эквивалентную функцию в службе выполняет интерфейс <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06523-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="06523-107">Проверка или изменение сообщений</span><span class="sxs-lookup"><span data-stu-id="06523-107">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="06523-108">Реализовать интерфейс <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06523-108">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="06523-109">Реализуйте интерфейс <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> или <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> в зависимости от области, в которую нужно легко вставить инспектор сообщений служб.</span><span class="sxs-lookup"><span data-stu-id="06523-109">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="06523-110">Вставьте поведение до вызова метода <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> в класс <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="06523-110">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="06523-111">Дополнительные сведения см. [в разделе Настройка и расширение среды выполнения с помощью поведений](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="06523-111">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06523-112">Пример</span><span class="sxs-lookup"><span data-stu-id="06523-112">Example</span></span>  

 <span data-ttu-id="06523-113">В следующих примерах кода показаны, по порядку:</span><span class="sxs-lookup"><span data-stu-id="06523-113">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="06523-114">реализация инспектора службы;</span><span class="sxs-lookup"><span data-stu-id="06523-114">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="06523-115">поведение службы, вставляющее инспектор;</span><span class="sxs-lookup"><span data-stu-id="06523-115">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="06523-116">файл конфигурации, загружающий и запускающий поведение в приложении службы.</span><span class="sxs-lookup"><span data-stu-id="06523-116">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="06523-117">См. также</span><span class="sxs-lookup"><span data-stu-id="06523-117">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="06523-118">Настройка и расширение среды выполнения с помощью поведений</span><span class="sxs-lookup"><span data-stu-id="06523-118">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
