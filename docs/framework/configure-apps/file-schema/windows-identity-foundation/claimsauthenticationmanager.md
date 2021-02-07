---
description: 'Дополнительные сведения: <claimsAuthenticationManager>'
title: <claimsAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
author: BrucePerlerMS
ms.openlocfilehash: 5a94861d6b2684b9f66c7d5e14f72aa419a0c66f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664253"
---
# \<claimsAuthenticationManager>

<span data-ttu-id="9173a-102">Регистрирует диспетчер проверки подлинности утверждений для входящих утверждений.</span><span class="sxs-lookup"><span data-stu-id="9173a-102">Registers a claims authentication manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="9173a-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9173a-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9173a-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9173a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9173a-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9173a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9173a-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9173a-106">Attributes</span></span>  
  
|<span data-ttu-id="9173a-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9173a-107">Attribute</span></span>|<span data-ttu-id="9173a-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9173a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9173a-109">type</span><span class="sxs-lookup"><span data-stu-id="9173a-109">type</span></span>|<span data-ttu-id="9173a-110">Указывает пользовательский тип, производный от <xref:System.Security.Claims.ClaimsAuthenticationManager> класса.</span><span class="sxs-lookup"><span data-stu-id="9173a-110">Specifies a custom type that derives from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class.</span></span> <span data-ttu-id="9173a-111">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы].</span><span class="sxs-lookup"><span data-stu-id="9173a-111">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9173a-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9173a-112">Child Elements</span></span>  

 <span data-ttu-id="9173a-113">Если `type` атрибут отсутствует или `type` атрибут ссылается на <xref:System.Security.Claims.ClaimsAuthenticationManager> класс, `<claimsAuthenticationManager>` элемент не принимает дочерние элементы, однако классы, производные от, <xref:System.Security.Claims.ClaimsAuthenticationManager> могут определять дочерние элементы конфигурации.</span><span class="sxs-lookup"><span data-stu-id="9173a-113">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthenticationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9173a-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9173a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9173a-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="9173a-115">Element</span></span>|<span data-ttu-id="9173a-116">Описание</span><span class="sxs-lookup"><span data-stu-id="9173a-116">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="9173a-117">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="9173a-117">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9173a-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="9173a-118">Remarks</span></span>  

 <span data-ttu-id="9173a-119">Поведение по умолчанию, предоставляемое <xref:System.Security.Claims.ClaimsAuthenticationManager> классом, отображает входящие утверждения.</span><span class="sxs-lookup"><span data-stu-id="9173a-119">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthenticationManager> class echoes the incoming claims.</span></span> <span data-ttu-id="9173a-120">Если `type` атрибут не указан или `type` атрибут указывает <xref:System.Security.Claims.ClaimsAuthenticationManager> класс, `<claimsAuthenticationManager>` элемент не принимает дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="9173a-120">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthenticationManager>` element does not take child elements.</span></span> <span data-ttu-id="9173a-121">Можно указать `type` атрибут для регистрации типа, производного от класса, <xref:System.Security.Claims.ClaimsAuthenticationManager> для реализации пользовательского поведения.</span><span class="sxs-lookup"><span data-stu-id="9173a-121">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthenticationManager> class to implement custom behavior.</span></span> <span data-ttu-id="9173a-122">Производные классы могут поддерживать конфигурацию через дочерние элементы `<claimsAuthenticationManager>` элемента путем переопределения <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> метода для работы с этими элементами.</span><span class="sxs-lookup"><span data-stu-id="9173a-122">Derived classes can support configuration through child elements of the `<claimsAuthenticationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="9173a-123">Схема, определенная для дочерних элементов, находится в конструкторе класса.</span><span class="sxs-lookup"><span data-stu-id="9173a-123">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
 <span data-ttu-id="9173a-124">`<claimsAuthenticationManager>`Элемент задает <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> свойство.</span><span class="sxs-lookup"><span data-stu-id="9173a-124">The `<claimsAuthenticationManager>` element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9173a-125">Пример</span><span class="sxs-lookup"><span data-stu-id="9173a-125">Example</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>
    </identityConfiguration>  
</system.identityModel>  
```
