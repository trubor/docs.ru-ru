---
description: 'Дополнительные сведения: <add>'
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: c79fb66fb4e87f15c2bf7f2c02e57f473c7262a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681868"
---
# \<add>

<span data-ttu-id="b1b98-102">Добавляет указанный обработчик маркеров безопасности в коллекцию обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="b1b98-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b1b98-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b1b98-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1b98-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b1b98-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b1b98-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b1b98-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1b98-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b1b98-106">Attributes</span></span>  
  
|<span data-ttu-id="b1b98-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b1b98-107">Attribute</span></span>|<span data-ttu-id="b1b98-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b1b98-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1b98-109">type</span><span class="sxs-lookup"><span data-stu-id="b1b98-109">type</span></span>|<span data-ttu-id="b1b98-110">Имя типа CLR обработчика токенов, который необходимо добавить.</span><span class="sxs-lookup"><span data-stu-id="b1b98-110">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="b1b98-111">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="b1b98-111">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1b98-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b1b98-112">Child Elements</span></span>  
  
|<span data-ttu-id="b1b98-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="b1b98-113">Element</span></span>|<span data-ttu-id="b1b98-114">Описание</span><span class="sxs-lookup"><span data-stu-id="b1b98-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="b1b98-115">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> класса, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класса или производного класса любого из этих классов.</span><span class="sxs-lookup"><span data-stu-id="b1b98-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="b1b98-116">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> класса или производных классов.</span><span class="sxs-lookup"><span data-stu-id="b1b98-116">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="b1b98-117">Предоставляет конфигурацию для <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> класса или производных классов.</span><span class="sxs-lookup"><span data-stu-id="b1b98-117">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="b1b98-118">Предоставляет необязательную конфигурацию для <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> класса или производных классов.</span><span class="sxs-lookup"><span data-stu-id="b1b98-118">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1b98-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b1b98-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b1b98-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="b1b98-120">Element</span></span>|<span data-ttu-id="b1b98-121">Описание</span><span class="sxs-lookup"><span data-stu-id="b1b98-121">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="b1b98-122">Указывает коллекцию обработчиков маркеров безопасности, зарегистрированных в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="b1b98-122">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1b98-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="b1b98-123">Remarks</span></span>  

 <span data-ttu-id="b1b98-124">`<add>`Элемент может принимать один дочерний элемент, указывающий конфигурацию для обработчика маркеров.</span><span class="sxs-lookup"><span data-stu-id="b1b98-124">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="b1b98-125">Это зависит от того, поддерживает ли эта функция класс обработчика, на который ссылается `type` атрибут `<add>` элемента.</span><span class="sxs-lookup"><span data-stu-id="b1b98-125">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="b1b98-126">Классы обработчиков маркеров, которые предоставляют эту функцию, должны предоставлять конструктор, принимающий <xref:System.Xml.XmlElement> объект.</span><span class="sxs-lookup"><span data-stu-id="b1b98-126">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="b1b98-127">Некоторые из встроенных классов обработчиков маркеров безопасности предоставляют эту функцию.</span><span class="sxs-lookup"><span data-stu-id="b1b98-127">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="b1b98-128">Эти классы: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ,,, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> и <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="b1b98-128">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b1b98-129">Коллекция обработчиков маркеров может содержать только один обработчик любого заданного типа.</span><span class="sxs-lookup"><span data-stu-id="b1b98-129">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="b1b98-130">Это означает, например, что если требуется добавить обработчик, производный от <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класса, в коллекцию, необходимо сначала удалить объект <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , который существует по умолчанию, из коллекции.</span><span class="sxs-lookup"><span data-stu-id="b1b98-130">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="b1b98-131">С помощью элемента можно [\<remove>](remove.md) удалить один обработчик из коллекции или использовать [\<clear>](clear.md) элемент для удаления всех обработчиков из коллекции.</span><span class="sxs-lookup"><span data-stu-id="b1b98-131">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="b1b98-132">Параметры, заданные для обработчика, переопределяют эквивалентные параметры, заданные в коллекции обработчика маркеров в [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) элементе, и те, которые указаны на уровне службы в [\<identityConfiguration>](identityconfiguration.md) элементе.</span><span class="sxs-lookup"><span data-stu-id="b1b98-132">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b98-133">Пример</span><span class="sxs-lookup"><span data-stu-id="b1b98-133">Example</span></span>  

 <span data-ttu-id="b1b98-134">В следующем коде XML показано использование `<add>` `<remove>` элементов и для замены обработчика токена сеанса по умолчанию обработчиком пользовательского маркера сеанса.</span><span class="sxs-lookup"><span data-stu-id="b1b98-134">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="b1b98-135">XML взят из `ClaimsAwareWebFarm` примера.</span><span class="sxs-lookup"><span data-stu-id="b1b98-135">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
