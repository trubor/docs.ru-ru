---
description: 'Дополнительные сведения: трассировка'
title: Трассировка
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 373e308357016f128c2eacfc34111d4b4e72b6fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759423"
---
# <a name="tracing"></a><span data-ttu-id="63278-103">Трассировка</span><span class="sxs-lookup"><span data-stu-id="63278-103">Tracing</span></span>

<span data-ttu-id="63278-104">Windows Communication Foundation (WCF) предоставляет инструментарий приложений и диагностические данные для мониторинга сбоя и анализа.</span><span class="sxs-lookup"><span data-stu-id="63278-104">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="63278-105">Трассировку можно использовать вместо отладчика для понимания того, как ведет себя приложение или почему оно дает сбои.</span><span class="sxs-lookup"><span data-stu-id="63278-105">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="63278-106">Можно также устанавливать корреляцию между сбоями и обработкой, выполняемой различными компонентами, для сквозного анализа работы приложения.</span><span class="sxs-lookup"><span data-stu-id="63278-106">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="63278-107">WCF выводит следующие данные для диагностической трассировки:</span><span class="sxs-lookup"><span data-stu-id="63278-107">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="63278-108">Трассировки основных этапов процесса по всем компонентам приложений, таких как вызовы операций, исключения кода, предупреждения и прочие значительные события обработки.</span><span class="sxs-lookup"><span data-stu-id="63278-108">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="63278-109">События ошибок Windows при сбоях возможности трассировки.</span><span class="sxs-lookup"><span data-stu-id="63278-109">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63278-110">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="63278-110">In This Section</span></span>  

 [<span data-ttu-id="63278-111">Настройка трассировки</span><span class="sxs-lookup"><span data-stu-id="63278-111">Configuring Tracing</span></span>](configuring-tracing.md)  
  
 <span data-ttu-id="63278-112">В этом разделе описывается, как настраивать трассировку на разных уровнях в соответствии с конкретными потребностями.</span><span class="sxs-lookup"><span data-stu-id="63278-112">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="63278-113">Сквозная трассировка</span><span class="sxs-lookup"><span data-stu-id="63278-113">End-to-End Tracing</span></span>](end-to-end-tracing.md)  
  
 <span data-ttu-id="63278-114">В этом разделе описывается использование распространения и трассировки действий для сквозной корреляции, полезной при отладке.</span><span class="sxs-lookup"><span data-stu-id="63278-114">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="63278-115">Использование трассировки для устранения неполадок приложения</span><span class="sxs-lookup"><span data-stu-id="63278-115">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="63278-116">В этом разделе описывается использование трассировки для отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="63278-116">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="63278-117">Проблемы безопасности и полезные советы при трассировке</span><span class="sxs-lookup"><span data-stu-id="63278-117">Security Concerns and Useful Tips for Tracing</span></span>](security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="63278-118">В этом разделе описываются способы защиты конфиденциальных сведений от раскрытия, а также приводятся полезные советы по использованию WebHost.</span><span class="sxs-lookup"><span data-stu-id="63278-118">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="63278-119">Справочные сведения о трассировке</span><span class="sxs-lookup"><span data-stu-id="63278-119">Traces Reference</span></span>](traces-reference.md)  
  
 <span data-ttu-id="63278-120">В этом разделе перечислены все трассировки, созданные WCF.</span><span class="sxs-lookup"><span data-stu-id="63278-120">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63278-121">См. также</span><span class="sxs-lookup"><span data-stu-id="63278-121">See also</span></span>

- [<span data-ttu-id="63278-122">Программа Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="63278-122">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
