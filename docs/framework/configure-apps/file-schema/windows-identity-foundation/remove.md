---
description: 'Дополнительные сведения: <remove>'
title: <remove>
ms.date: 03/30/2017
ms.assetid: 4058e2f1-7db4-4d1a-84dd-1b52836f2ae6
author: BrucePerlerMS
ms.openlocfilehash: 942148f677e10bbab7b86acfba2d0fdfb1b10ca7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664071"
---
# \<remove>

<span data-ttu-id="a6cea-102">Удаляет указанный обработчик маркеров безопасности из коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="a6cea-102">Removes the specified security token handler from the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="a6cea-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6cea-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <remove type=xs:string >  
      </remove>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6cea-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a6cea-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a6cea-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a6cea-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6cea-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a6cea-106">Attributes</span></span>  
  
|<span data-ttu-id="a6cea-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a6cea-107">Attribute</span></span>|<span data-ttu-id="a6cea-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a6cea-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6cea-109">type</span><span class="sxs-lookup"><span data-stu-id="a6cea-109">type</span></span>|<span data-ttu-id="a6cea-110">Имя типа CLR удаляемого обработчика токенов.</span><span class="sxs-lookup"><span data-stu-id="a6cea-110">The CLR type name of the token handler to be removed.</span></span> <span data-ttu-id="a6cea-111">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="a6cea-111">For more information about how to specify the `type` attribute, see [Custom Type References](/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span> <span data-ttu-id="a6cea-112">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a6cea-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6cea-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a6cea-113">Child Elements</span></span>  

 <span data-ttu-id="a6cea-114">None</span><span class="sxs-lookup"><span data-stu-id="a6cea-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6cea-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a6cea-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a6cea-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="a6cea-116">Element</span></span>|<span data-ttu-id="a6cea-117">Описание</span><span class="sxs-lookup"><span data-stu-id="a6cea-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="a6cea-118">Указывает коллекцию обработчиков маркеров безопасности, зарегистрированных в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="a6cea-118">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a6cea-119">Пример</span><span class="sxs-lookup"><span data-stu-id="a6cea-119">Example</span></span>  

 <span data-ttu-id="a6cea-120">В следующем коде XML показано использование `<add>` `<remove>` элементов и для замены обработчика токена сеанса по умолчанию обработчиком пользовательского маркера сеанса.</span><span class="sxs-lookup"><span data-stu-id="a6cea-120">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="a6cea-121">XML взят из `ClaimsAwareWebFarm` примера.</span><span class="sxs-lookup"><span data-stu-id="a6cea-121">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
