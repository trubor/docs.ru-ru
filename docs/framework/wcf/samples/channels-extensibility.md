---
description: Дополнительные сведения о расширяемости каналов
title: Расширяемость каналов
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 08c93ffa2e7c4645e4c49be619c0cb065ecdbff7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704073"
---
# <a name="channels-extensibility"></a><span data-ttu-id="2167a-103">Расширяемость каналов</span><span class="sxs-lookup"><span data-stu-id="2167a-103">Channels Extensibility</span></span>

<span data-ttu-id="2167a-104">В этом разделе содержатся образцы, демонстрирующие пользовательские каналы.</span><span class="sxs-lookup"><span data-stu-id="2167a-104">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2167a-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="2167a-105">In This Section</span></span>  

 [<span data-ttu-id="2167a-106">Локальный канал</span><span class="sxs-lookup"><span data-stu-id="2167a-106">Local Channel</span></span>](local-channel.md)  
 <span data-ttu-id="2167a-107">Демонстрирует локальный канал, канал транспорта WCF, который используется для связи в пределах одного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="2167a-107">Demonstrates the local channel, a WCF transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="2167a-108">Надежный защищенный профиль</span><span class="sxs-lookup"><span data-stu-id="2167a-108">Reliable Secure Profile</span></span>](reliable-secure-profile.md)  
 <span data-ttu-id="2167a-109">Демонстрирует, как создать WCF и надежный защищенный профиль (RSP).</span><span class="sxs-lookup"><span data-stu-id="2167a-109">Demonstrates how to compose WCF and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="2167a-110">Настраиваемый диспетчер каналов</span><span class="sxs-lookup"><span data-stu-id="2167a-110">Custom Channel Dispatcher</span></span>](custom-channel-dispatcher.md)  
 <span data-ttu-id="2167a-111">Демонстрирует построение пользовательского стека каналов путем непосредственной реализации <xref:System.ServiceModel.ServiceHostBase>, а также создание пользовательского диспетчера каналов в среде веб-узла.</span><span class="sxs-lookup"><span data-stu-id="2167a-111">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="2167a-112">Фрагментирование канала</span><span class="sxs-lookup"><span data-stu-id="2167a-112">Chunking Channel</span></span>](chunking-channel.md)  
 <span data-ttu-id="2167a-113">Показывает, как ограничить объем памяти, используемой для буферизации больших сообщений, отправляемых с помощью WCF.</span><span class="sxs-lookup"><span data-stu-id="2167a-113">Demonstrates how to limit the amount of memory used to buffer large messages sent using WCF.</span></span>
  
 [<span data-ttu-id="2167a-114">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="2167a-114">HttpCookieSession</span></span>](httpcookiesession.md)  
 <span data-ttu-id="2167a-115">Демонстрирует, как построить пользовательский канал протокола, который использует для управления сеансами протокол HTTP.</span><span class="sxs-lookup"><span data-stu-id="2167a-115">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="2167a-116">Пользовательский перехватчик сообщений</span><span class="sxs-lookup"><span data-stu-id="2167a-116">Custom Message Interceptor</span></span>](custom-message-interceptor.md)  
 <span data-ttu-id="2167a-117">Показано, как реализовать пользовательский элемент привязки, который создает фабрики и прослушиватели каналов для перехвата всех входящих и исходящих сообщений в определенной точке стека времени выполнения.</span><span class="sxs-lookup"><span data-stu-id="2167a-117">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
