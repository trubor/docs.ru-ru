---
description: 'Дополнительные сведения: несанкционированные вызовы безопасности'
title: Неавторизованные вызовы системы безопасности
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 80dc161f2be5a678e80860410f1b6adbde7bfb71
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803416"
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="b0af8-103">Неавторизованные вызовы системы безопасности</span><span class="sxs-lookup"><span data-stu-id="b0af8-103">Security Calls Not Authorized</span></span>

<span data-ttu-id="b0af8-104">Имя счетчика: Security Calls Not Authorized.</span><span class="sxs-lookup"><span data-stu-id="b0af8-104">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b0af8-105">Описание</span><span class="sxs-lookup"><span data-stu-id="b0af8-105">Description</span></span>  

 <span data-ttu-id="b0af8-106">Значение этого счетчика увеличивается, когда метод <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> возвращает значение `false`.</span><span class="sxs-lookup"><span data-stu-id="b0af8-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="b0af8-107">Это показывает, что входящее сообщение было надлежащим образом защищено и поступило от допустимого пользователя, не авторизованного для выполнения определенных задач.</span><span class="sxs-lookup"><span data-stu-id="b0af8-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
