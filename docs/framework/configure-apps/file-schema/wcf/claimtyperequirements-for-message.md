---
description: <claimTypeRequirements>Дополнительные сведения о:<message>
title: <claimTypeRequirements> для <message>;
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: a393a075c64f4a46e5ac055b3c417514861c9661
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638903"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="4b3b2-103">\<claimTypeRequirements> для \<message>;</span><span class="sxs-lookup"><span data-stu-id="4b3b2-103">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="4b3b2-104">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="4b3b2-104">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="4b3b2-105">Коллекция используется службой, чтобы задать обязательные и необязательные утверждения, которые должны содержаться в выданном маркере, используемом клиентом для доступа к службе.</span><span class="sxs-lookup"><span data-stu-id="4b3b2-105">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="4b3b2-106">Служба предоставляет обязательные типы утверждений в метаданных, если публикация WDSL включена, но WCF не требует, чтобы выданный маркер содержал заданные типы утверждений.</span><span class="sxs-lookup"><span data-stu-id="4b3b2-106">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="4b3b2-107">Службы, для которых необходимо принудительное наличие обязательных типов утверждений, должны использовать политику авторизации.</span><span class="sxs-lookup"><span data-stu-id="4b3b2-107">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="4b3b2-108">В федеративных клиентах эта коллекция содержит список обязательных и необязательных утверждений, который отправляется службе маркеров безопасности в запросе клиента для выданного маркера.</span><span class="sxs-lookup"><span data-stu-id="4b3b2-108">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b3b2-109">См. также</span><span class="sxs-lookup"><span data-stu-id="4b3b2-109">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
