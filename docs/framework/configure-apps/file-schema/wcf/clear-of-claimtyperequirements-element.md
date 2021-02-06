---
description: 'Дополнительные сведения о: <clear> <claimTypeRequirements> element'
title: <clear> элемента <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
ms.openlocfilehash: d25dad5afcec352f040ea4f8c08e5ffa2bc16d19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638890"
---
# <a name="clear-of-claimtyperequirements-element"></a><span data-ttu-id="44099-103">\<clear> элемента \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="44099-103">\<clear> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="44099-104">Указывает, что все типы утверждений в федеративных учетных данных должны быть удалены.</span><span class="sxs-lookup"><span data-stu-id="44099-104">Specifies that all the claim types to be removed in the federated credential.</span></span> <span data-ttu-id="44099-105">Это обеспечивает запуск пустой коллекции.</span><span class="sxs-lookup"><span data-stu-id="44099-105">This ensures that the collection starts empty.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="44099-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="44099-106">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <clear />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44099-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="44099-107">Attributes and Elements</span></span>  

 <span data-ttu-id="44099-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="44099-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44099-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="44099-109">Attributes</span></span>  

 <span data-ttu-id="44099-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="44099-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="44099-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="44099-111">Child Elements</span></span>  

 <span data-ttu-id="44099-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="44099-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44099-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="44099-113">Parent Elements</span></span>  
  
|<span data-ttu-id="44099-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="44099-114">Element</span></span>|<span data-ttu-id="44099-115">Описание</span><span class="sxs-lookup"><span data-stu-id="44099-115">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="44099-116">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="44099-116">Specifies a collection of required claim types.</span></span> <span data-ttu-id="44099-117">Каждый элемент имеет тип <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="44099-117">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="44099-118">В федеративном сценарии службы предъявляют требования к входящим учетным данным.</span><span class="sxs-lookup"><span data-stu-id="44099-118">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="44099-119">Например, входящие учетные данные должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="44099-119">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="44099-120">Каждый элемент в этой коллекции задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="44099-120">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44099-121">См. также</span><span class="sxs-lookup"><span data-stu-id="44099-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
