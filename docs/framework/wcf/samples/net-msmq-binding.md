---
description: 'Дополнительные сведения: привязка к сети MSMQ'
title: Привязка MSMQ на платформе .NET
ms.date: 03/30/2017
ms.assetid: fe4bb696-f57c-4cb3-9b7e-9d95fe6b8323
ms.openlocfilehash: 9934fa05cf31ab3e9fb0c081184b11b6dd39428e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752123"
---
# <a name="net-msmq-binding"></a><span data-ttu-id="5ad87-103">Привязка MSMQ на платформе .NET</span><span class="sxs-lookup"><span data-stu-id="5ad87-103">Net MSMQ Binding</span></span>

<span data-ttu-id="5ad87-104">Этот раздел содержит образцы, которые демонстрируют использование привязки атрибутов MSMQ элемента конечной точки.</span><span class="sxs-lookup"><span data-stu-id="5ad87-104">This section contains samples that demonstrate using MSMQ binding attributes of an endpoint element.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ad87-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="5ad87-105">In This Section</span></span>  

 [<span data-ttu-id="5ad87-106">Привязка MSMQ с поддержкой транзакций</span><span class="sxs-lookup"><span data-stu-id="5ad87-106">Transacted MSMQ Binding</span></span>](transacted-msmq-binding.md)  
 <span data-ttu-id="5ad87-107">Показывает, как осуществлять транзакционное взаимодействие с использованием очередей с помощью очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="5ad87-107">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ).</span></span>  
  
 [<span data-ttu-id="5ad87-108">Неустойчивое взаимодействие с использованием очереди</span><span class="sxs-lookup"><span data-stu-id="5ad87-108">Volatile Queued Communication</span></span>](volatile-queued-communication.md)  
 <span data-ttu-id="5ad87-109">Демонстрирует неустойчивое взаимодействие с использованием очередей через MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5ad87-109">Demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="5ad87-110">Очереди недоставленных сообщений</span><span class="sxs-lookup"><span data-stu-id="5ad87-110">Dead Letter Queues</span></span>](dead-letter-queues.md)  
 <span data-ttu-id="5ad87-111">Демонстрирует обработку недоставленных сообщений.</span><span class="sxs-lookup"><span data-stu-id="5ad87-111">Demonstrates how to handle and process messages that have failed delivery.</span></span>  
  
 [<span data-ttu-id="5ad87-112">Обработка подозрительных сообщений в MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="5ad87-112">Poison Message Handling in MSMQ 4.0</span></span>](poison-message-handling-in-msmq-4-0.md)  
 <span data-ttu-id="5ad87-113">Демонстрирует обработку подозрительных сообщений в службе с использованием MSMQ 4.0.</span><span class="sxs-lookup"><span data-stu-id="5ad87-113">Demonstrates how to perform poison message handling in a service using MSMQ 4.0.</span></span>  
  
 [<span data-ttu-id="5ad87-114">Сеансы и очереди</span><span class="sxs-lookup"><span data-stu-id="5ad87-114">Sessions and Queues</span></span>](sessions-and-queues.md)  
 <span data-ttu-id="5ad87-115">Показывает, как с помощью транспорта очереди сообщений (MSMQ) отправить и принять набор взаимосвязанных сообщений при взаимодействии с использованием очередей.</span><span class="sxs-lookup"><span data-stu-id="5ad87-115">Demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span>  
  
 [<span data-ttu-id="5ad87-116">Двусторонний обмен данными</span><span class="sxs-lookup"><span data-stu-id="5ad87-116">Two-Way Communication</span></span>](two-way-communication.md)  
 <span data-ttu-id="5ad87-117">Демонстрирует транзакционное двустороннее взаимодействие с использованием очередей через MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5ad87-117">Demonstrates how to perform transacted two-way queued communication over MSMQ.</span></span>
  
 [<span data-ttu-id="5ad87-118">SRMP</span><span class="sxs-lookup"><span data-stu-id="5ad87-118">SRMP</span></span>](srmp.md)  
 <span data-ttu-id="5ad87-119">Показывает, как осуществлять транзакционное взаимодействие по HTTP с помощью очереди сообщений (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="5ad87-119">Demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 [<span data-ttu-id="5ad87-120">Безопасность сообщений при использовании очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="5ad87-120">Message Security over Message Queuing</span></span>](message-security-over-message-queuing.md)  
 <span data-ttu-id="5ad87-121">Демонстрирует реализацию приложения, использующего протокол WS-Security и проверку подлинности с использованием сертификата X.509v3 для клиента и требующего проверки подлинности сервера с использованием сертификата X.509v3 сервера через MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5ad87-121">Demonstrates how to implement an application that uses WS-Security with X.509v3 certificate authentication for the client and requires server authentication using the server's X.509v3 certificate over MSMQ.</span></span>
