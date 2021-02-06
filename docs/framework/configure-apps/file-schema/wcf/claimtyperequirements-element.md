---
description: 'Дополнительные сведения о: <claimTypeRequirements> element'
title: <claimTypeRequirements> - элемент
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 9553c129c246a5f4980d597406bee19ea949bdcc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638916"
---
# <a name="claimtyperequirements-element"></a><span data-ttu-id="38e48-103">Элемент \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="38e48-103">\<claimTypeRequirements> element</span></span>

<span data-ttu-id="38e48-104">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="38e48-104">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="38e48-105">В федеративном сценарии службы предъявляют требования к входящим учетным данным.</span><span class="sxs-lookup"><span data-stu-id="38e48-105">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="38e48-106">Например, входящие учетные данные должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="38e48-106">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="38e48-107">Каждый дочерний элемент в этой коллекции задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="38e48-107">Each child element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>  
  
 <span data-ttu-id="38e48-108">Требование типа утверждения состоит из универсального кода ресурса (URI) типа утверждения, запрашиваемого в выданном маркере, и логического параметра, который определяет, является ли обязательным этот тип утверждения в выданном маркере.</span><span class="sxs-lookup"><span data-stu-id="38e48-108">A claim type requirement consists of the URI of the claim type requested in the issued token along with a Boolean parameter that indicates whether that claim type is required in the issued token, or is optional.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e48-109">См. также</span><span class="sxs-lookup"><span data-stu-id="38e48-109">See also</span></span>

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="38e48-110">Идентификация и проверка подлинности службы</span><span class="sxs-lookup"><span data-stu-id="38e48-110">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="38e48-111">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="38e48-111">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="38e48-112">Возможности безопасности при использовании пользовательских привязок</span><span class="sxs-lookup"><span data-stu-id="38e48-112">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="38e48-113">Федерация и выданные маркеры</span><span class="sxs-lookup"><span data-stu-id="38e48-113">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-claimtyperequirements.md)
- [<span data-ttu-id="38e48-114">Привязки</span><span class="sxs-lookup"><span data-stu-id="38e48-114">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="38e48-115">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="38e48-115">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="38e48-116">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="38e48-116">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="38e48-117">Практическое руководство. Создание пользовательской привязки с использованием элемента SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="38e48-117">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="38e48-118">Безопасность пользовательской привязки</span><span class="sxs-lookup"><span data-stu-id="38e48-118">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
