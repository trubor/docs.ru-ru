---
description: См. Дополнительные сведения о несанкционированных вызовах безопасности в секунду
title: Количество неавторизованных вызовов системы безопасности в секунду
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 60e1baf2b1ed1f3dc502608e6667266608010f0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716215"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="d2d94-103">Количество неавторизованных вызовов системы безопасности в секунду</span><span class="sxs-lookup"><span data-stu-id="d2d94-103">Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="d2d94-104">Имя счетчика: Security Calls Not Authorized Per Second.</span><span class="sxs-lookup"><span data-stu-id="d2d94-104">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d2d94-105">Описание</span><span class="sxs-lookup"><span data-stu-id="d2d94-105">Description</span></span>  

 <span data-ttu-id="d2d94-106">Число вызовов, которые не удалось авторизовать в данной операции, в секунду.</span><span class="sxs-lookup"><span data-stu-id="d2d94-106">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="d2d94-107">Значение этого счетчика увеличивается, когда метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="d2d94-107">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d2d94-108">Это показывает, что входящее сообщение было надлежащим образом защищено и поступило от допустимого пользователя, не авторизованного для выполнения определенных задач.</span><span class="sxs-lookup"><span data-stu-id="d2d94-108">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="d2d94-109">Этот счетчик имеет тип счетчика производительности [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), значение которого вычисляется с помощью следующей формулы.</span><span class="sxs-lookup"><span data-stu-id="d2d94-109">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d2d94-110">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="d2d94-110">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
