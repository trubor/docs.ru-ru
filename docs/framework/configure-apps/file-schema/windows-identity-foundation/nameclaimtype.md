---
description: 'Дополнительные сведения: <nameClaimType>'
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: d5bc2f96c2753febdb61c3495b7067c0e31e52d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664058"
---
# \<nameClaimType>

<span data-ttu-id="a3cf7-102">Задает тип утверждения, указывающий <xref:System.Security.Principal.IIdentity.Name%2A> свойство.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="a3cf7-103">Тип утверждения используется для поиска <xref:System.Security.Claims.Claim> в коллекции <xref:System.Security.Claims.ClaimsIdentity> объектов, возвращаемых <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> методом этого обработчика маркеров.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="a3cf7-104">Затем значение соответствующего утверждения задается в качестве имени объекта, <xref:System.Security.Principal.IIdentity> созданного из этого обработчика маркеров.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="a3cf7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3cf7-105">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3cf7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a3cf7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a3cf7-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3cf7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a3cf7-108">Attributes</span></span>  
  
|<span data-ttu-id="a3cf7-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a3cf7-109">Attribute</span></span>|<span data-ttu-id="a3cf7-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a3cf7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3cf7-111">value</span><span class="sxs-lookup"><span data-stu-id="a3cf7-111">value</span></span>|<span data-ttu-id="a3cf7-112">Строка, указывающая URI, который представляет тип утверждения для утверждения, используемого для <xref:System.Security.Principal.IIdentity.Name%2A> Свойства.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-112">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="a3cf7-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3cf7-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a3cf7-114">Child Elements</span></span>  

 <span data-ttu-id="a3cf7-115">None</span><span class="sxs-lookup"><span data-stu-id="a3cf7-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3cf7-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a3cf7-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a3cf7-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="a3cf7-117">Element</span></span>|<span data-ttu-id="a3cf7-118">Описание</span><span class="sxs-lookup"><span data-stu-id="a3cf7-118">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="a3cf7-119">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> класса, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класса или производного класса любого из этих классов.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-119">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3cf7-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="a3cf7-120">Remarks</span></span>  

 <span data-ttu-id="a3cf7-121">`<nameClaimType>`Элемент задает <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> свойство при <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> инициализации объекта из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a3cf7-121">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3cf7-122">Пример</span><span class="sxs-lookup"><span data-stu-id="a3cf7-122">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3cf7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="a3cf7-123">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
