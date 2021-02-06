---
description: 'Дополнительные сведения о конечной точке: несанкционированные вызовы безопасности'
title: 'Конечная точка: количество неавторизованных вызовов системы безопасности'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: 258c984e8a7986594b6da6f5c2a8c030907f82ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655478"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="404d0-103">Конечная точка: количество неавторизованных вызовов системы безопасности</span><span class="sxs-lookup"><span data-stu-id="404d0-103">Endpoint: Security Calls Not Authorized</span></span>

<span data-ttu-id="404d0-104">Имя счетчика: Security Calls Not Authorized.</span><span class="sxs-lookup"><span data-stu-id="404d0-104">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="404d0-105">Описание</span><span class="sxs-lookup"><span data-stu-id="404d0-105">Description</span></span>  

 <span data-ttu-id="404d0-106">Значение этого счетчика увеличивается, когда метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="404d0-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="404d0-107">Это показывает, что входящее сообщение было надлежащим образом защищено и поступило от допустимого пользователя, не авторизованного для выполнения определенных задач.</span><span class="sxs-lookup"><span data-stu-id="404d0-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
