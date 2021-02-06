---
description: 'Дополнительные сведения: <roleClaimType>'
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 69b86489b0a970addb7fc7c11dd88be52ac68e95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652683"
---
# \<roleClaimType>

<span data-ttu-id="cb6ce-102">Указывает тип утверждения, определяющего утверждения типа роли в коллекции <xref:System.Security.Claims.ClaimsIdentity> объектов, возвращаемых <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> методом обработчика маркеров.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="cb6ce-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cb6ce-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb6ce-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="cb6ce-104">Attributes and Elements</span></span>  

 <span data-ttu-id="cb6ce-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb6ce-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="cb6ce-106">Attributes</span></span>  
  
|<span data-ttu-id="cb6ce-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="cb6ce-107">Attribute</span></span>|<span data-ttu-id="cb6ce-108">Описание</span><span class="sxs-lookup"><span data-stu-id="cb6ce-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb6ce-109">value</span><span class="sxs-lookup"><span data-stu-id="cb6ce-109">value</span></span>|<span data-ttu-id="cb6ce-110">Строка, указывающая URI, который представляет тип утверждения, используемого для типа утверждения роли.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-110">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb6ce-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="cb6ce-111">Child Elements</span></span>  

 <span data-ttu-id="cb6ce-112">None</span><span class="sxs-lookup"><span data-stu-id="cb6ce-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb6ce-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="cb6ce-113">Parent Elements</span></span>  
  
|<span data-ttu-id="cb6ce-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="cb6ce-114">Element</span></span>|<span data-ttu-id="cb6ce-115">Описание</span><span class="sxs-lookup"><span data-stu-id="cb6ce-115">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="cb6ce-116">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> класса, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класса или производного класса любого из этих классов.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-116">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb6ce-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="cb6ce-117">Remarks</span></span>  

 <span data-ttu-id="cb6ce-118">`<roleClaimType>`Элемент задает <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> свойство при <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> инициализации объекта из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="cb6ce-118">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb6ce-119">Пример</span><span class="sxs-lookup"><span data-stu-id="cb6ce-119">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb6ce-120">См. также</span><span class="sxs-lookup"><span data-stu-id="cb6ce-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
