---
description: 'Дополнительные сведения: <claimsAuthorizationManager>'
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ae96c9e665c8533567ad87cad374919c30a6b3c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664240"
---
# \<claimsAuthorizationManager>

<span data-ttu-id="d8482-102">Регистрирует диспетчер авторизации утверждений для входящих утверждений.</span><span class="sxs-lookup"><span data-stu-id="d8482-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="d8482-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8482-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8482-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d8482-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d8482-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d8482-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8482-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d8482-106">Attributes</span></span>  
  
|<span data-ttu-id="d8482-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d8482-107">Attribute</span></span>|<span data-ttu-id="d8482-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d8482-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8482-109">type</span><span class="sxs-lookup"><span data-stu-id="d8482-109">type</span></span>|<span data-ttu-id="d8482-110">Пользовательский тип, производный от <xref:System.Security.Claims.ClaimsAuthorizationManager> класса.</span><span class="sxs-lookup"><span data-stu-id="d8482-110">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="d8482-111">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8482-111">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8482-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d8482-112">Child Elements</span></span>  

 <span data-ttu-id="d8482-113">Если `type` атрибут отсутствует или `type` атрибут ссылается на <xref:System.Security.Claims.ClaimsAuthenticationManager> класс, `<claimsAuthorizationManager>` элемент не принимает дочерние элементы, однако классы, производные от, <xref:System.Security.Claims.ClaimsAuthorizationManager> могут определять дочерние элементы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="d8482-113">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8482-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d8482-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d8482-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="d8482-115">Element</span></span>|<span data-ttu-id="d8482-116">Описание</span><span class="sxs-lookup"><span data-stu-id="d8482-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="d8482-117">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="d8482-117">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8482-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8482-118">Remarks</span></span>  

 <span data-ttu-id="d8482-119">Поведение по умолчанию, предоставляемое <xref:System.Security.Claims.ClaimsAuthorizationManager> классом, всегда разрешает входящие утверждения.</span><span class="sxs-lookup"><span data-stu-id="d8482-119">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="d8482-120">Если `type` атрибут не указан или `type` атрибут указывает <xref:System.Security.Claims.ClaimsAuthorizationManager> класс, `<claimsAuthorizationManager>` элемент не принимает дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="d8482-120">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="d8482-121">Можно указать `type` атрибут для регистрации типа, производного от класса, <xref:System.Security.Claims.ClaimsAuthorizationManager> для реализации пользовательского поведения.</span><span class="sxs-lookup"><span data-stu-id="d8482-121">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="d8482-122">Производные классы могут поддерживать конфигурацию через дочерние элементы `<claimsAuthorizationManager>` элемента путем переопределения <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> метода для работы с этими элементами.</span><span class="sxs-lookup"><span data-stu-id="d8482-122">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="d8482-123">Схема, определенная для дочерних элементов, находится в конструкторе класса.</span><span class="sxs-lookup"><span data-stu-id="d8482-123">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d8482-124">При использовании <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> класса или для предоставления управления доступом на основе утверждений в коде конфигурация удостоверения, на которую ссылается элемент, `<federationConfiguration>` настраивает диспетчер авторизации утверждений и политику, которая используется для принятия решений об авторизации.</span><span class="sxs-lookup"><span data-stu-id="d8482-124">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="d8482-125">Это справедливо даже в сценариях, которые не являются пассивными веб-сценариями, например Windows Communication Foundation приложений (WCF) или приложение, не основанное на веб-интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="d8482-125">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="d8482-126">Если приложение не является пассивным веб-приложением, то `<claimsAuthorizationManager>` к нему применяются только те элементы (и дочерние элемент политики, если таковые имеются) конфигурации удостоверения, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="d8482-126">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="d8482-127">Все остальные параметры игнорируются.</span><span class="sxs-lookup"><span data-stu-id="d8482-127">All other settings are ignored.</span></span> <span data-ttu-id="d8482-128">Дополнительные сведения см. в описании [\<federationConfiguration>](federationconfiguration.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="d8482-128">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="d8482-129">Этот элемент задает <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> свойство.</span><span class="sxs-lookup"><span data-stu-id="d8482-129">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8482-130">Пример</span><span class="sxs-lookup"><span data-stu-id="d8482-130">Example</span></span>  

 <span data-ttu-id="d8482-131">В следующем коде XML показана конфигурация для диспетчера авторизации утверждений, который реализует политику, состоящую из пар действий с ресурсами, каждый из которых указывает логические комбинации утверждений, которые должен обладать запрашивающей стороны для выполнения действия с ресурсом.</span><span class="sxs-lookup"><span data-stu-id="d8482-131">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="d8482-132">Код, реализующий диспетчер авторизации утверждений, который может использовать эту политику, можно найти в `ClaimsBasedAuthorization` примере.</span><span class="sxs-lookup"><span data-stu-id="d8482-132">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
