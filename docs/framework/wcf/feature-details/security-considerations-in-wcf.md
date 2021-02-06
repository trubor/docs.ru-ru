---
description: Дополнительные сведения см. в статье вопросы безопасности в WCF.
title: Вопросы безопасности в WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: d75ff0d6eede4a46a5b795873e83445a04532993
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632481"
---
# <a name="security-considerations-in-wcf"></a><span data-ttu-id="55a31-103">Вопросы безопасности в WCF</span><span class="sxs-lookup"><span data-stu-id="55a31-103">Security Considerations in WCF</span></span>

<span data-ttu-id="55a31-104">В подразделах этого раздела перечислены различные элементы, связанные с безопасностью, которые следует учитывать при проектировании приложения Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="55a31-104">The topics in this section list various security-related items to consider when designing a Windows Communication Foundation (WCF) application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55a31-105">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="55a31-105">In This Section</span></span>  

 [<span data-ttu-id="55a31-106">Раскрытие информации</span><span class="sxs-lookup"><span data-stu-id="55a31-106">Information Disclosure</span></span>](information-disclosure.md)  
 <span data-ttu-id="55a31-107">Описание различных способов раскрытия информации и атак, а также способов их предотвращения.</span><span class="sxs-lookup"><span data-stu-id="55a31-107">Discusses the various ways that information can be disclosed or attacked, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="55a31-108">Несанкционированное получение привилегий</span><span class="sxs-lookup"><span data-stu-id="55a31-108">Elevation of Privilege</span></span>](elevation-of-privilege.md)  
 <span data-ttu-id="55a31-109">Описание последствий предоставления злоумышленнику более широких прав по сравнению с правами, предоставленными ему изначально, и способов решения проблемы.</span><span class="sxs-lookup"><span data-stu-id="55a31-109">Discusses the effects of giving an attacker authorization permissions beyond those initially granted and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="55a31-110">Отказ в обслуживании</span><span class="sxs-lookup"><span data-stu-id="55a31-110">Denial of Service</span></span>](denial-of-service.md)  
 <span data-ttu-id="55a31-111">Описание ситуаций, когда система не может обрабатывать сообщения должным образом, и способов решения проблемы.</span><span class="sxs-lookup"><span data-stu-id="55a31-111">Discusses what happens when a system is unable to process messages appropriately and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="55a31-112">Незаконное изменение</span><span class="sxs-lookup"><span data-stu-id="55a31-112">Tampering</span></span>](tampering.md)  
 <span data-ttu-id="55a31-113">Описание изменения сообщений или доставки сообщений, а также способов решения проблемы.</span><span class="sxs-lookup"><span data-stu-id="55a31-113">Discusses the altering of messages or the delivery of messages and how to mitigate it.</span></span>  
  
 [<span data-ttu-id="55a31-114">Атаки с повторением</span><span class="sxs-lookup"><span data-stu-id="55a31-114">Replay Attacks</span></span>](replay-attacks.md)  
 <span data-ttu-id="55a31-115">Описание последствий копирования злоумышленником потока сообщений между двумя сторонами и воспроизведения этого потока для одной или нескольких сторон, а также способов решения проблемы.</span><span class="sxs-lookup"><span data-stu-id="55a31-115">Discusses what happens when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties, and how to mitigate this.</span></span>  
  
 [<span data-ttu-id="55a31-116">Соображения о защите безопасных сеансов</span><span class="sxs-lookup"><span data-stu-id="55a31-116">Security Considerations for Secure Sessions</span></span>](security-considerations-for-secure-sessions.md)  
 <span data-ttu-id="55a31-117">Описание следующих элементов, влияющих на безопасность при реализации безопасных сеансов.</span><span class="sxs-lookup"><span data-stu-id="55a31-117">Discusses the following items that affect security when implementing secure sessions.</span></span>  
  
 [<span data-ttu-id="55a31-118">Неподдерживаемые сценарии</span><span class="sxs-lookup"><span data-stu-id="55a31-118">Unsupported Scenarios</span></span>](unsupported-scenarios.md)  
 <span data-ttu-id="55a31-119">Перечисление различных сценариев, которые не поддерживают определенный аспект безопасности, и которых следует избегать или учитывать.</span><span class="sxs-lookup"><span data-stu-id="55a31-119">Lists various scenarios that do not support a particular aspect of security and should be avoided or considered.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="55a31-120">Справочник</span><span class="sxs-lookup"><span data-stu-id="55a31-120">Reference</span></span>  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="55a31-121">Связанные разделы</span><span class="sxs-lookup"><span data-stu-id="55a31-121">Related Sections</span></span>  

 [<span data-ttu-id="55a31-122">Руководство и рекомендации по безопасности</span><span class="sxs-lookup"><span data-stu-id="55a31-122">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a><span data-ttu-id="55a31-123">См. также</span><span class="sxs-lookup"><span data-stu-id="55a31-123">See also</span></span>

- [<span data-ttu-id="55a31-124">Безопасность</span><span class="sxs-lookup"><span data-stu-id="55a31-124">Security</span></span>](security.md)
