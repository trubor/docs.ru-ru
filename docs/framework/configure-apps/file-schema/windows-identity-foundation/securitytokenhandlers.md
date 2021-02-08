---
description: 'Дополнительные сведения: <securityTokenHandlers>'
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 14937f6763644f9b7f43c0f7be71ea2352b21402
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782030"
---
# \<securityTokenHandlers>

<span data-ttu-id="bf317-102">Указывает коллекцию обработчиков маркеров безопасности, зарегистрированных в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="bf317-102">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="bf317-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bf317-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf317-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bf317-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bf317-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bf317-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf317-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bf317-106">Attributes</span></span>  
  
|<span data-ttu-id="bf317-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="bf317-107">Attribute</span></span>|<span data-ttu-id="bf317-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bf317-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf317-109">name</span><span class="sxs-lookup"><span data-stu-id="bf317-109">name</span></span>|<span data-ttu-id="bf317-110">Указывает имя коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="bf317-110">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="bf317-111">Платформа принимает только те значения, которые распознаются платформой: "ActAs" и "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="bf317-111">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="bf317-112">Если коллекции обработчиков маркеров указаны с одним из этих имен, коллекция будет использоваться при обработке маркеров ActAs или OnBehalfOf соответственно.</span><span class="sxs-lookup"><span data-stu-id="bf317-112">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf317-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bf317-113">Child Elements</span></span>  
  
|<span data-ttu-id="bf317-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="bf317-114">Element</span></span>|<span data-ttu-id="bf317-115">Описание</span><span class="sxs-lookup"><span data-stu-id="bf317-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="bf317-116">Добавляет обработчик маркеров безопасности в коллекцию обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="bf317-116">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="bf317-117">Удаляет все обработчики маркеров безопасности из коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="bf317-117">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="bf317-118">Удаляет обработчик маркера безопасности из коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="bf317-118">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="bf317-119">Предоставляет конфигурацию для коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="bf317-119">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf317-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bf317-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bf317-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="bf317-121">Element</span></span>|<span data-ttu-id="bf317-122">Описание</span><span class="sxs-lookup"><span data-stu-id="bf317-122">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="bf317-123">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="bf317-123">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf317-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf317-124">Remarks</span></span>  

 <span data-ttu-id="bf317-125">В конфигурации службы можно указать одну или несколько именованных коллекций обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="bf317-125">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="bf317-126">Имя коллекции можно указать с помощью `name` атрибута.</span><span class="sxs-lookup"><span data-stu-id="bf317-126">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="bf317-127">Единственными именами, которые обрабатывает платформа, являются "ActAs" и "OnBehalfOf".</span><span class="sxs-lookup"><span data-stu-id="bf317-127">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="bf317-128">Если в этих коллекциях есть обработчики, они используются службой маркеров безопасности (STS) вместо обработчиков по умолчанию при обработке `ActAs` и `OnBehalfOf` токенах.</span><span class="sxs-lookup"><span data-stu-id="bf317-128">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="bf317-129">По умолчанию коллекция заполняется следующими типами обработчиков: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,,,, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> и <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="bf317-129">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="bf317-130">Коллекцию можно изменить с помощью `<add>` `<remove>` элементов, и `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="bf317-130">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="bf317-131">Необходимо убедиться, что в коллекции существует только один обработчик любого определенного типа.</span><span class="sxs-lookup"><span data-stu-id="bf317-131">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="bf317-132">Например, если создать производный обработчик от <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> класса, то либо обработчик, либо <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> может быть настроен в одной коллекции, но не в обоих.</span><span class="sxs-lookup"><span data-stu-id="bf317-132">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="bf317-133">Используйте `<securityTokenHandlerConfiguration>` элемент, чтобы указать параметры конфигурации для обработчиков в коллекции.</span><span class="sxs-lookup"><span data-stu-id="bf317-133">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="bf317-134">Параметры, заданные с помощью этого элемента, переопределяют указанные в службе элементы с помощью [\<identityConfiguration>](identityconfiguration.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="bf317-134">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="bf317-135">Некоторые обработчики (включая несколько встроенных типов обработчиков) могут поддерживать дополнительную конфигурацию через дочерний элемент `<add>` элемента.</span><span class="sxs-lookup"><span data-stu-id="bf317-135">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="bf317-136">Параметры, заданные для обработчика, переопределяют эквивалентные параметры, указанные в коллекции или службе.</span><span class="sxs-lookup"><span data-stu-id="bf317-136">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>
