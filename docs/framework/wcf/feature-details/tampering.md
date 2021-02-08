---
description: 'Дополнительные сведения: вмешательство'
title: незаконное изменение;
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 3b14fef66e5c98737d8d2f6a8b889f16c83020f9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793328"
---
# <a name="tampering"></a><span data-ttu-id="44ba4-103">незаконное изменение;</span><span class="sxs-lookup"><span data-stu-id="44ba4-103">Tampering</span></span>

<span data-ttu-id="44ba4-104">*Незаконное* изменение — это процесс изменения сообщения или доставки сообщения, а также использование измененного сообщения для назначения, отличного от того, для чего оно предназначено.</span><span class="sxs-lookup"><span data-stu-id="44ba4-104">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="44ba4-105">Не отключайте WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="44ba4-105">Do Not Disable WS-Addressing</span></span>  

 <span data-ttu-id="44ba4-106">Спецификация WS-Addressing расставляет заголовки адресов на каждом сообщении, по которым получатель сообщения проверяет отправителя сообщения.</span><span class="sxs-lookup"><span data-stu-id="44ba4-106">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="44ba4-107">Чтобы отключить эту возможность, необходимо задать для свойства <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> значение <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="44ba4-107">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="44ba4-108">Если для режима безопасности задано значение Message и WS-Addressing отключена, злоумышленник сможет отправить запрос клиента другой службе, при этом вторая служба не сможет определить, что сообщение поступило от исходного клиента.</span><span class="sxs-lookup"><span data-stu-id="44ba4-108">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="44ba4-109">Фактически, первая служба при взаимодействии со второй может выдавать себя за клиента.</span><span class="sxs-lookup"><span data-stu-id="44ba4-109">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="44ba4-110">Во избежание этого никогда не задавайте свойству <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> значение <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> и старайтесь не использовать <xref:System.ServiceModel.Channels.MessageVersion>, например статическое свойство <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A>, задающее свойству <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> значение <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="44ba4-110">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44ba4-111">См. также</span><span class="sxs-lookup"><span data-stu-id="44ba4-111">See also</span></span>

- [<span data-ttu-id="44ba4-112">Вопросы безопасности</span><span class="sxs-lookup"><span data-stu-id="44ba4-112">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="44ba4-113">Раскрытие информации</span><span class="sxs-lookup"><span data-stu-id="44ba4-113">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="44ba4-114">Несанкционированное получение привилегий</span><span class="sxs-lookup"><span data-stu-id="44ba4-114">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="44ba4-115">Отказ в обслуживании</span><span class="sxs-lookup"><span data-stu-id="44ba4-115">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="44ba4-116">Неподдерживаемые сценарии</span><span class="sxs-lookup"><span data-stu-id="44ba4-116">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
- [<span data-ttu-id="44ba4-117">Атаки с повторением</span><span class="sxs-lookup"><span data-stu-id="44ba4-117">Replay Attacks</span></span>](replay-attacks.md)
