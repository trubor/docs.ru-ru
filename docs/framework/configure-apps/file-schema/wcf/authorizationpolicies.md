---
description: 'Дополнительные сведения: <authorizationPolicies>'
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 4b0f341a1bb6ebb4918a5d71aba82270c31ba863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749835"
---
# \<authorizationPolicies>

<span data-ttu-id="74d4d-102">Этот раздел конфигурации содержит коллекцию типов политик авторизации, которые можно добавить с помощью ключевого слова `add`.</span><span class="sxs-lookup"><span data-stu-id="74d4d-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="74d4d-103">Каждая политика авторизации содержит один обязательный атрибут `policyType`, который имеет строковый тип.</span><span class="sxs-lookup"><span data-stu-id="74d4d-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="74d4d-104">Данный атрибут определяет политику авторизации, которая позволяет преобразовывать один набор входных требований в другой набор требований.</span><span class="sxs-lookup"><span data-stu-id="74d4d-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="74d4d-105">В зависимости от этого может быть предоставлено управление доступом или отказано в предоставлении управления доступом.</span><span class="sxs-lookup"><span data-stu-id="74d4d-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="74d4d-106">Дополнительные сведения о принципах работы политики авторизации см. в разделе <xref:System.IdentityModel.Policy.IAuthorizationPolicy> и [Политика авторизации](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="74d4d-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d4d-107">См. также</span><span class="sxs-lookup"><span data-stu-id="74d4d-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="74d4d-108">Авторизация доступа к операциям службы</span><span class="sxs-lookup"><span data-stu-id="74d4d-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="74d4d-109">Практическое руководство. Создание пользовательского диспетчера авторизации для службы</span><span class="sxs-lookup"><span data-stu-id="74d4d-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="74d4d-110">Политика авторизации</span><span class="sxs-lookup"><span data-stu-id="74d4d-110">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
