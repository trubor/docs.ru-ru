---
description: 'Дополнительные сведения: утверждения и запрет доступа к ресурсам'
title: Утверждения и запрет доступа к ресурсам
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 0bbef26b0df06305db4ce460da4ba6177c79f56a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734975"
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="52458-103">Утверждения и запрет доступа к ресурсам</span><span class="sxs-lookup"><span data-stu-id="52458-103">Claims and Denying Access to Resources</span></span>

<span data-ttu-id="52458-104">Windows Communication Foundation (WCF) поддерживает механизм авторизации на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="52458-104">Windows Communication Foundation (WCF) supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="52458-105">Системы могут предоставлять доступ к ресурсам на основе утверждений или отказывать в доступе к ресурсам на основе утверждений.</span><span class="sxs-lookup"><span data-stu-id="52458-105">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="52458-106">Такие системы должны сначала проверять контекст <xref:System.IdentityModel.Policy.AuthorizationContext> на наличие утверждений, запрещающих доступ, а лишь затем - на наличие утверждений, разрешающих доступ.</span><span class="sxs-lookup"><span data-stu-id="52458-106">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="52458-107">Например, система может отказать в доступе к ресурсу всем пользователям, имеющим утверждение типа `Age`, право <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> и значение ресурса `Under 21`, если для данного удостоверения также имеется утверждение типа `Name`, право <xref:System.IdentityModel.Claims.Rights.Identity%2A> и значение ресурса `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="52458-107">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="52458-108">Иными словами, система отказывает в доступе пользователям младше 21 года и предоставляет доступ пользователю с именем Mallory.</span><span class="sxs-lookup"><span data-stu-id="52458-108">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="52458-109">Для правильно реализации такой семантики важно сначала проверять утверждение `Age`, чтобы определить, что пользователю исполнился 21 год.</span><span class="sxs-lookup"><span data-stu-id="52458-109">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="52458-110">В противном случае, если пользователь Мэллори младше 21 года, он получит доступ к ресурсам только на том основании, что он соответствует утверждению `Name`.</span><span class="sxs-lookup"><span data-stu-id="52458-110">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52458-111">См. также</span><span class="sxs-lookup"><span data-stu-id="52458-111">See also</span></span>

- [<span data-ttu-id="52458-112">Управление утверждениями и авторизацией с помощью модели удостоверения</span><span class="sxs-lookup"><span data-stu-id="52458-112">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
- [<span data-ttu-id="52458-113">Утверждения и маркеры</span><span class="sxs-lookup"><span data-stu-id="52458-113">Claims and Tokens</span></span>](claims-and-tokens.md)
