---
description: Дополнительные сведения см. в статье упорядоченная обработка сообщений в режиме единого параллелизма.
title: Упорядоченная обработка сообщений в режиме единого параллелизма
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 2dd876f1831dda8b388108f238810be333e693be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99733688"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="61995-103">Упорядоченная обработка сообщений в режиме единого параллелизма</span><span class="sxs-lookup"><span data-stu-id="61995-103">Ordered Processing of Messages in Single Concurrency Mode</span></span>

<span data-ttu-id="61995-104">WCF не предоставляет никаких гарантий относительно порядка обработки сообщений, если только базовый канал не является сеансом.</span><span class="sxs-lookup"><span data-stu-id="61995-104">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="61995-105">Например, служба WCF, использующая Мсмкинпутчаннел, которая не является каналом с сеансом, не сможет обрабатывать сообщения по порядку.</span><span class="sxs-lookup"><span data-stu-id="61995-105">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="61995-106">Существуют некоторые обстоятельства, в которых разработчику может потребоваться поведение при обработке заказа, но не нужно использовать сеансы.</span><span class="sxs-lookup"><span data-stu-id="61995-106">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="61995-107">В этом разделе описано, как настроить такое поведение, когда служба запущена в режиме единого параллелизма.</span><span class="sxs-lookup"><span data-stu-id="61995-107">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="61995-108">Упорядоченная обработка сообщений</span><span class="sxs-lookup"><span data-stu-id="61995-108">In-order Message Processing</span></span>  

 <span data-ttu-id="61995-109">В <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> добавлен новый атрибут <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span><span class="sxs-lookup"><span data-stu-id="61995-109">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="61995-110">Если <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> задано значение true и <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> задается значение <xref:System.ServiceModel.ConcurrencyMode.Single>, сообщения, отправленные службе, будут обработаны по порядку.</span><span class="sxs-lookup"><span data-stu-id="61995-110">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="61995-111">В следующем фрагменте кода показано, как задать эти атрибуты.</span><span class="sxs-lookup"><span data-stu-id="61995-111">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="61995-112">Если <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> имеет любое другое значение, выдается исключение <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="61995-112">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61995-113">См. также</span><span class="sxs-lookup"><span data-stu-id="61995-113">See also</span></span>

- [<span data-ttu-id="61995-114">Сеансы, экземпляры и параллелизм</span><span class="sxs-lookup"><span data-stu-id="61995-114">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="61995-115">Параллелизм</span><span class="sxs-lookup"><span data-stu-id="61995-115">Concurrency</span></span>](../samples/concurrency.md)
