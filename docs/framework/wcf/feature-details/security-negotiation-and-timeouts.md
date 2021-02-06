---
description: 'Дополнительные сведения: согласование безопасности и время ожидания'
title: Согласование безопасности и тайм-ауты
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: 50055698f9a9946d0c0110a964cf9ce5b9f4fa28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632442"
---
# <a name="security-negotiation-and-timeouts"></a><span data-ttu-id="f2f2e-103">Согласование безопасности и тайм-ауты</span><span class="sxs-lookup"><span data-stu-id="f2f2e-103">Security Negotiation and Timeouts</span></span>

<span data-ttu-id="f2f2e-104">При проверке подлинности клиентов и служб Windows Communication Foundation (WCF) поддерживает режим, в котором учетные данные службы согласовываются как часть проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="f2f2e-104">When clients and services authenticate, Windows Communication Foundation (WCF) supports a mode where the service credential is negotiated as part of authentication.</span></span> <span data-ttu-id="f2f2e-105">В таких случаях между клиентом и службой может происходить взаимный обмен информацией для распространения учетных данных службы клиенту.</span><span class="sxs-lookup"><span data-stu-id="f2f2e-105">In such scenarios, a potentially multi-leg exchange occurs between the client and the service to propagate the service credential to the client.</span></span> <span data-ttu-id="f2f2e-106">Продолжительность этого взаимного обмена определяется свойством <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2f2e-106">The <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property controls how long the multi-leg exchange can take to complete.</span></span> <span data-ttu-id="f2f2e-107">Однако это время ожидания применяется, только если обмен информацией фактически продолжается дольше одного цикла "запрос-ответ".</span><span class="sxs-lookup"><span data-stu-id="f2f2e-107">However, this timeout only applies if the exchange actually takes more that a single request-response.</span></span> <span data-ttu-id="f2f2e-108">Если согласование завершается за один цикл, время ожидания не используется.</span><span class="sxs-lookup"><span data-stu-id="f2f2e-108">In cases where the negotiation completes in a single round trip, the timeout does not apply.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2f2e-109">См. также</span><span class="sxs-lookup"><span data-stu-id="f2f2e-109">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="f2f2e-110">Практическое руководство. Установка максимальной разницы в показаниях часов</span><span class="sxs-lookup"><span data-stu-id="f2f2e-110">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)
