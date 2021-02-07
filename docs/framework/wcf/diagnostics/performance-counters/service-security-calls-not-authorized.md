---
description: 'Дополнительные сведения: служба: несанкционированные вызовы безопасности'
title: 'Служба: количество неавторизованных вызовов системы безопасности'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: 2185f478d534696ea308e06d8411df6888420914
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735755"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="d9e5f-103">Служба: количество неавторизованных вызовов системы безопасности</span><span class="sxs-lookup"><span data-stu-id="d9e5f-103">Service: Security Calls Not Authorized</span></span>

<span data-ttu-id="d9e5f-104">Имя счетчика: Security Calls Not Authorized.</span><span class="sxs-lookup"><span data-stu-id="d9e5f-104">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d9e5f-105">Описание</span><span class="sxs-lookup"><span data-stu-id="d9e5f-105">Description</span></span>  

 <span data-ttu-id="d9e5f-106">Значение этого счетчика увеличивается, когда метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="d9e5f-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d9e5f-107">Это показывает, что входящее сообщение было надлежащим образом защищено и поступило от допустимого пользователя, не авторизованного для выполнения определенных задач.</span><span class="sxs-lookup"><span data-stu-id="d9e5f-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
