---
description: 'Дополнительные сведения о: <remove> <claimTypeRequirements> element'
title: <remove> элемента <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: 8ef05bc4-1950-4ee4-95c5-1c6a394eff7e
ms.openlocfilehash: 2ec917d27966954382e5b091fd538168b48b5ffb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786906"
---
# <a name="remove-of-claimtyperequirements-element"></a><span data-ttu-id="e6b92-103">\<remove> элемента \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="e6b92-103">\<remove> of \<claimTypeRequirements> element</span></span>

<span data-ttu-id="e6b92-104">Указывает типы утверждений в федеративных учетных данных, которые должны быть удалены.</span><span class="sxs-lookup"><span data-stu-id="e6b92-104">Specifies the types of claims to be removed in the federated credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequirements>**](claimtyperequirements-for-message.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="e6b92-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6b92-105">Syntax</span></span>  
  
```xml  
<claimTypeRequirements>
  <remove claimType="URI" />
</claimTypeRequirements>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6b92-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e6b92-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e6b92-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e6b92-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6b92-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e6b92-108">Attributes</span></span>  
  
|<span data-ttu-id="e6b92-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e6b92-109">Attribute</span></span>|<span data-ttu-id="e6b92-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e6b92-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6b92-111">claimType</span><span class="sxs-lookup"><span data-stu-id="e6b92-111">claimType</span></span>|<span data-ttu-id="e6b92-112">Универсальный код ресурса (URI), определяющий тип утверждения, которое требуется удалить.</span><span class="sxs-lookup"><span data-stu-id="e6b92-112">A URI that defines the type of a claim to be removed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6b92-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e6b92-113">Child Elements</span></span>  

 <span data-ttu-id="e6b92-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e6b92-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6b92-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e6b92-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e6b92-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="e6b92-116">Element</span></span>|<span data-ttu-id="e6b92-117">Описание</span><span class="sxs-lookup"><span data-stu-id="e6b92-117">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-for-message.md)|<span data-ttu-id="e6b92-118">Задает коллекцию обязательных типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="e6b92-118">Specifies a collection of required claim types.</span></span> <span data-ttu-id="e6b92-119">Каждый элемент имеет тип <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="e6b92-119">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span><br /><br /> <span data-ttu-id="e6b92-120">В федеративном сценарии службы предъявляют требования к входящим учетным данным.</span><span class="sxs-lookup"><span data-stu-id="e6b92-120">In a federated scenario, services state the requirements on incoming credentials.</span></span> <span data-ttu-id="e6b92-121">Например, входящие учетные данные должны обладать определенным набором типов утверждений.</span><span class="sxs-lookup"><span data-stu-id="e6b92-121">For example, the incoming credentials must possess a certain set of claim types.</span></span> <span data-ttu-id="e6b92-122">Каждый элемент в этой коллекции задает типы обязательных и необязательных утверждений, которые могут появляться в федеративных учетных данных.</span><span class="sxs-lookup"><span data-stu-id="e6b92-122">Each element in this collection specifies the types of required and optional claims expected to appear in a federated credential.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6b92-123">См. также</span><span class="sxs-lookup"><span data-stu-id="e6b92-123">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
