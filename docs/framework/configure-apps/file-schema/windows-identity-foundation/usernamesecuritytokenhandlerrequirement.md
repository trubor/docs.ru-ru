---
description: 'Дополнительные сведения: <userNameSecurityTokenHandlerRequirement>'
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: c2bca086d06738699517fe140173f321a3233a4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786503"
---
# \<userNameSecurityTokenHandlerRequirement>

<span data-ttu-id="03a35-102">Предоставляет конфигурацию для <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> класса или производных классов.</span><span class="sxs-lookup"><span data-stu-id="03a35-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="03a35-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="03a35-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03a35-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="03a35-104">Attributes and Elements</span></span>  

 <span data-ttu-id="03a35-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="03a35-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03a35-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="03a35-106">Attributes</span></span>  
  
|<span data-ttu-id="03a35-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="03a35-107">Attribute</span></span>|<span data-ttu-id="03a35-108">Описание</span><span class="sxs-lookup"><span data-stu-id="03a35-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03a35-109">мембершиппровидернаме</span><span class="sxs-lookup"><span data-stu-id="03a35-109">membershipProviderName</span></span>|<span data-ttu-id="03a35-110">Указывает <xref:System.Web.Security.MembershipProvider> , который должен использоваться обработчиком маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="03a35-110">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03a35-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="03a35-111">Child Elements</span></span>  

 <span data-ttu-id="03a35-112">None</span><span class="sxs-lookup"><span data-stu-id="03a35-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03a35-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="03a35-113">Parent Elements</span></span>  
  
|<span data-ttu-id="03a35-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="03a35-114">Element</span></span>|<span data-ttu-id="03a35-115">Описание</span><span class="sxs-lookup"><span data-stu-id="03a35-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="03a35-116">Добавляет указанный обработчик маркеров безопасности в коллекцию обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="03a35-116">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a35-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="03a35-117">Remarks</span></span>  

 <span data-ttu-id="03a35-118">`<userNameSecurityTokenHandlerRequirement>`Элемент задает <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> свойство при <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> инициализации объекта из конфигурации.</span><span class="sxs-lookup"><span data-stu-id="03a35-118">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a35-119">Пример</span><span class="sxs-lookup"><span data-stu-id="03a35-119">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
