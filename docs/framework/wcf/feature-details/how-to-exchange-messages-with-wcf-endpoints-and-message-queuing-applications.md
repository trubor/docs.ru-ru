---
description: Дополнительные сведения см. в статье как обмениваться сообщениями с конечными точками WCF и приложениями очереди сообщений.
title: Практическое руководство. Обмен сообщениями с конечными точками WCF и приложениями очереди сообщений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 0b8f315b00960ec87e68e9e2b11ac9b273dbbf93
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704619"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="49108-103">Практическое руководство. Обмен сообщениями с конечными точками WCF и приложениями очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="49108-103">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>

<span data-ttu-id="49108-104">Можно интегрировать существующие приложения очереди сообщений (MSMQ) с приложениями Windows Communication Foundation (WCF) с помощью привязки интеграции MSMQ для преобразования сообщений MSMQ в сообщения WCF и из них.</span><span class="sxs-lookup"><span data-stu-id="49108-104">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="49108-105">Это позволяет вызывать приложения для приемника MSMQ из клиентов WCF, а также вызывать службы WCF из приложений отправителя MSMQ.</span><span class="sxs-lookup"><span data-stu-id="49108-105">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="49108-106">В этом разделе объясняется, как использовать <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> для связи в очереди между (1) клиентом WCF и службой приложений MSMQ, написанной с помощью System. Messaging и (2) клиента приложения MSMQ и службы WCF.</span><span class="sxs-lookup"><span data-stu-id="49108-106">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="49108-107">Полный пример, демонстрирующий вызов приложения-получателя MSMQ из клиента WCF, см. в разделе [Windows Communication Foundation к примеру очереди сообщений](../samples/wcf-to-message-queuing.md) .</span><span class="sxs-lookup"><span data-stu-id="49108-107">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="49108-108">Полный пример, демонстрирующий способ вызова службы WCF из клиента MSMQ, см. в статье [очередь сообщений для Windows Communication Foundation](../samples/message-queuing-to-wcf.md) образца.</span><span class="sxs-lookup"><span data-stu-id="49108-108">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="49108-109">Создание службы WCF, получающей сообщения от клиента MSMQ</span><span class="sxs-lookup"><span data-stu-id="49108-109">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="49108-110">Определите интерфейс, определяющий контракт службы для службы WCF, которая получает сообщения в очереди от приложения отправителя MSMQ, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="49108-110">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="49108-111">Реализуйте интерфейс и примените атрибут <xref:System.ServiceModel.ServiceBehaviorAttribute> к классу, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="49108-111">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="49108-112">Создайте файл конфигурации, задающий привязку <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="49108-112">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="49108-113">Создайте экземпляр объекта <xref:System.ServiceModel.ServiceHost>, использующий настроенную привязку.</span><span class="sxs-lookup"><span data-stu-id="49108-113">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="49108-114">Создание клиента WCF, передающего сообщения в принимающее приложение MSMQ</span><span class="sxs-lookup"><span data-stu-id="49108-114">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="49108-115">Определите интерфейс, определяющий контракт службы для клиента WCF, который отправляет сообщения в очереди получателю MSMQ, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="49108-115">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="49108-116">Определите клиентский класс, используемый клиентом WCF для вызова получателя MSMQ.</span><span class="sxs-lookup"><span data-stu-id="49108-116">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="49108-117">Создайте конфигурацию, которая задает использование привязки MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="49108-117">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="49108-118">Создайте экземпляр класса клиента и вызовите метод, определенный службой приема сообщений.</span><span class="sxs-lookup"><span data-stu-id="49108-118">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="49108-119">См. также</span><span class="sxs-lookup"><span data-stu-id="49108-119">See also</span></span>

- [<span data-ttu-id="49108-120">Общие сведения об очередях</span><span class="sxs-lookup"><span data-stu-id="49108-120">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="49108-121">Практическое руководство. Обмен сообщениями в очереди с конечными точками WCF</span><span class="sxs-lookup"><span data-stu-id="49108-121">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="49108-122">Отправка сообщений из приложения Windows Communication Foundation в приложение MSMQ</span><span class="sxs-lookup"><span data-stu-id="49108-122">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="49108-123">Установка системы очередей сообщений (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="49108-123">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="49108-124">Передача сообщений из приложения MSMQ в приложение Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="49108-124">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="49108-125">Безопасность сообщений при использовании очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="49108-125">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
