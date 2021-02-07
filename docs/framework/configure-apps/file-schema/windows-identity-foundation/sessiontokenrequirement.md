---
description: 'Дополнительные сведения: <sessionTokenRequirement>'
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 8f2868df4939dc0dc7c779eb9ca5a35a6b996fc6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698275"
---
# \<sessionTokenRequirement>

<span data-ttu-id="a2841-102">Предоставляет конфигурацию для <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> класса или производных классов.</span><span class="sxs-lookup"><span data-stu-id="a2841-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="a2841-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2841-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2841-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a2841-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a2841-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a2841-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2841-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a2841-106">Attributes</span></span>  
  
|<span data-ttu-id="a2841-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a2841-107">Attribute</span></span>|<span data-ttu-id="a2841-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a2841-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2841-109">lifetime</span><span class="sxs-lookup"><span data-stu-id="a2841-109">lifetime</span></span>|<span data-ttu-id="a2841-110">Указывает время существования маркеров сеанса.</span><span class="sxs-lookup"><span data-stu-id="a2841-110">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2841-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a2841-111">Child Elements</span></span>  

 <span data-ttu-id="a2841-112">None</span><span class="sxs-lookup"><span data-stu-id="a2841-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2841-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a2841-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a2841-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="a2841-114">Element</span></span>|<span data-ttu-id="a2841-115">Описание</span><span class="sxs-lookup"><span data-stu-id="a2841-115">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="a2841-116">Добавляет указанный обработчик маркеров безопасности в коллекцию обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="a2841-116">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a2841-117">Пример</span><span class="sxs-lookup"><span data-stu-id="a2841-117">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
