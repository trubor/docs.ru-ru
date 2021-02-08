---
description: 'Подробнее: аналитика трассировки с помощью ETW'
title: Аналитическое отслеживание ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: fd40d40de2508fd251c793e4455c1e656a1cbbf6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798801"
---
# <a name="analytic-tracing-with-etw"></a><span data-ttu-id="b2d30-103">Аналитическое отслеживание ETW</span><span class="sxs-lookup"><span data-stu-id="b2d30-103">Analytic Tracing with ETW</span></span>

<span data-ttu-id="b2d30-104">Аналитическая трассировка Windows Communication Foundation (WCF) предоставляет способ сбора диагностических сведений во время выполнения службы WCF.</span><span class="sxs-lookup"><span data-stu-id="b2d30-104">Windows Communication Foundation (WCF) analytic tracing offers a way to capture diagnostic information during the execution of a WCF service.</span></span> <span data-ttu-id="b2d30-105">События аналитической трассировки WCF создаются в ключевых точках стека WCF, чтобы разрешить устранение неполадок служб WCF в рабочей среде.</span><span class="sxs-lookup"><span data-stu-id="b2d30-105">WCF analytic tracing events are emitted at key points in the WCF stack to allow troubleshooting of WCF services in a production environment.</span></span> <span data-ttu-id="b2d30-106">Аналитическая трассировка служб WCF оказывает минимальное влияние на производительность сервера продукта, на котором размещены [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] службы WCF, так как эти события очень эффективны в сеансе трассировки событий для Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="b2d30-106">Analytic tracing for WCF services has minimal impact on the performance of a product server that hosts [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] WCF services as these events are very efficiently emitted to an Event Tracing for Windows (ETW) session.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2d30-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="b2d30-107">In This Section</span></span>  

 [<span data-ttu-id="b2d30-108">Общие сведения об аналитическом отслеживании</span><span class="sxs-lookup"><span data-stu-id="b2d30-108">Analytic Tracing Overview</span></span>](analytic-tracing-overview.md)  
 <span data-ttu-id="b2d30-109">Описывает, как работает аналитическая трассировка WCF [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b2d30-109">Discusses how WCF analytic tracing works in [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="b2d30-110">Динамическое включение аналитического отслеживания</span><span class="sxs-lookup"><span data-stu-id="b2d30-110">Dynamically Enabling Analytic Tracing</span></span>](dynamically-enabling-analytic-tracing.md)  
 <span data-ttu-id="b2d30-111">Описывает, как динамически включить и отключить трассировку с помощью ETW.</span><span class="sxs-lookup"><span data-stu-id="b2d30-111">Discusses how to enable or disable tracing dynamically using ETW.</span></span>  
  
 [<span data-ttu-id="b2d30-112">Настройка отслеживания потока сообщений</span><span class="sxs-lookup"><span data-stu-id="b2d30-112">Configuring Message Flow Tracing</span></span>](configuring-message-flow-tracing.md)  
 <span data-ttu-id="b2d30-113">Описывает процесс настройки трассировки потока сообщений.</span><span class="sxs-lookup"><span data-stu-id="b2d30-113">Describes how to configure message flow tracing.</span></span>  
  
 [<span data-ttu-id="b2d30-114">Ссылка на событие аналитического отслеживания</span><span class="sxs-lookup"><span data-stu-id="b2d30-114">Analytic Trace Event Reference</span></span>](analytic-trace-event-reference.md)  
 <span data-ttu-id="b2d30-115">Содержит таблицу идентификаторов событий с уровнями событий, сообщениями событий и ключевыми словами.</span><span class="sxs-lookup"><span data-stu-id="b2d30-115">Shows a table of event IDs with their event levels, event messages and keywords.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d30-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b2d30-116">See also</span></span>

- [<span data-ttu-id="b2d30-117">Службы WCF и средство отслеживания событий для Windows</span><span class="sxs-lookup"><span data-stu-id="b2d30-117">WCF Services and Event Tracing for Windows</span></span>](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [<span data-ttu-id="b2d30-118">Отслеживание событий в системе трассировки событий Windows</span><span class="sxs-lookup"><span data-stu-id="b2d30-118">Tracking Events into Event Tracing in Windows</span></span>](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
