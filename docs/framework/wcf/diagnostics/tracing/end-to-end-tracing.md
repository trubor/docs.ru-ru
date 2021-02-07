---
description: 'Дополнительные сведения: сквозная трассировка'
title: Сквозная трассировка
ms.date: 03/30/2017
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
ms.openlocfilehash: c1c4a38d4ef8c445994d42abeafbb25da9a5f326
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99759436"
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="a72a7-103">Сквозная трассировка</span><span class="sxs-lookup"><span data-stu-id="a72a7-103">End-to-End Tracing</span></span>

<span data-ttu-id="a72a7-104">Трассировка "до конца" (E2E) позволяет разработчикам следовать за выполнением кода в инфраструктуре Windows Communication Foundation (WCF), чтобы определить причину сбоя пути кода или предоставить подробную трассировку для планирования емкости и анализа производительности.</span><span class="sxs-lookup"><span data-stu-id="a72a7-104">End to End (e2e) Tracing allows developers to follow the execution of code in the Windows Communication Foundation (WCF) infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> <span data-ttu-id="a72a7-105">Windows Communication Foundation (WCF) предоставляет три механизма корреляции, помогающие диагностировать причину ошибки: действия, передачи и распространения.</span><span class="sxs-lookup"><span data-stu-id="a72a7-105">Windows Communication Foundation (WCF) provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="a72a7-106">В разделе Сценарии сквозной [трассировки](end-to-end-tracing-scenarios.md) приведен список комплексных сценариев трассировки, а также соответствующие действия и структура трассировки.</span><span class="sxs-lookup"><span data-stu-id="a72a7-106">See [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a72a7-107">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="a72a7-107">In This Section</span></span>  

 <span data-ttu-id="a72a7-108">[Действие](activity.md): описывает трассировки действий в модели трассировки Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a72a7-108">[Activity](activity.md):  Describes activity traces in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
 <span data-ttu-id="a72a7-109">[Перемещение](transfer.md). описывает перемещение в модели трассировки Windows Communication Foundation (WCF) и использование функции перемещения для корреляции действий в конечных точках.</span><span class="sxs-lookup"><span data-stu-id="a72a7-109">[Transfer](transfer.md):  Describes transfer in the Windows Communication Foundation (WCF) tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="a72a7-110">[Распространение](propagation.md). описывает распространение действий в модели трассировки Windows Communication Foundation (WCF) и использование распространения для корреляции действий между конечными точками.</span><span class="sxs-lookup"><span data-stu-id="a72a7-110">[Propagation](propagation.md):  Describes activity propagation in the Windows Communication Foundation (WCF) tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="a72a7-111">Сводка типов трассировок</span><span class="sxs-lookup"><span data-stu-id="a72a7-111">Trace Type Summary</span></span>](trace-type-summary.md)  
  
 <span data-ttu-id="a72a7-112">Краткий обзор всех типов трассировок действий</span><span class="sxs-lookup"><span data-stu-id="a72a7-112">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a72a7-113">См. также</span><span class="sxs-lookup"><span data-stu-id="a72a7-113">See also</span></span>

- [<span data-ttu-id="a72a7-114">Настройка трассировки</span><span class="sxs-lookup"><span data-stu-id="a72a7-114">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="a72a7-115">Использование программы Service Trace Viewer для просмотра скоррелированных трассировок и устранения неполадок</span><span class="sxs-lookup"><span data-stu-id="a72a7-115">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="a72a7-116">Сценарии сквозной трассировки</span><span class="sxs-lookup"><span data-stu-id="a72a7-116">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="a72a7-117">Программа Service Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="a72a7-117">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
