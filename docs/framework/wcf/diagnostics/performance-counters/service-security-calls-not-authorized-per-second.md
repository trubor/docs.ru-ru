---
description: 'См. Дополнительные сведения о службе: количество вызовов безопасности, не прошедших авторизацию, в секунду'
title: 'Служба: количество неавторизованных вызовов системы безопасности в секунду'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 7203b62a1dd2f01aabd8502c992d357742ddc4e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635705"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="9a769-103">Служба: количество неавторизованных вызовов системы безопасности в секунду</span><span class="sxs-lookup"><span data-stu-id="9a769-103">Service: Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="9a769-104">Имя счетчика: Security Calls Not Authorized Per Second</span><span class="sxs-lookup"><span data-stu-id="9a769-104">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="9a769-105">Описание</span><span class="sxs-lookup"><span data-stu-id="9a769-105">Description</span></span>  

 <span data-ttu-id="9a769-106">Число входящих сообщений в секунду, надлежаще защищенных и поступивших от допустимого пользователя, не авторизованного для выполнения определенных задач.</span><span class="sxs-lookup"><span data-stu-id="9a769-106">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="9a769-107">Значение этого счетчика увеличивается, когда метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="9a769-107">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="9a769-108">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="9a769-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9a769-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9a769-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
