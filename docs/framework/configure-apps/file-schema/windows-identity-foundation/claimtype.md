---
description: 'Дополнительные сведения: <claimType>'
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 55fd32edc7fb810742c3cf678b434675aebba00e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664227"
---
# \<claimType>

<span data-ttu-id="ec4f3-102">Указывает одно необязательное или обязательное утверждение для входящих токенов безопасности.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="ec4f3-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec4f3-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec4f3-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ec4f3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="ec4f3-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec4f3-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ec4f3-106">Attributes</span></span>  
  
|<span data-ttu-id="ec4f3-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ec4f3-107">Attribute</span></span>|<span data-ttu-id="ec4f3-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ec4f3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ec4f3-109">type</span><span class="sxs-lookup"><span data-stu-id="ec4f3-109">type</span></span>|<span data-ttu-id="ec4f3-110">Тип утверждения.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-110">The claim type.</span></span> <span data-ttu-id="ec4f3-111">Обычно это URI.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-111">Typically a URI.</span></span> <span data-ttu-id="ec4f3-112">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-112">Required.</span></span>|  
|<span data-ttu-id="ec4f3-113">необязательно</span><span class="sxs-lookup"><span data-stu-id="ec4f3-113">optional</span></span>|<span data-ttu-id="ec4f3-114">Логическое значение, указывающее, является ли тип утверждения необязательным.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-114">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="ec4f3-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-115">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec4f3-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ec4f3-116">Child Elements</span></span>  

 <span data-ttu-id="ec4f3-117">None</span><span class="sxs-lookup"><span data-stu-id="ec4f3-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec4f3-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ec4f3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ec4f3-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="ec4f3-119">Element</span></span>|<span data-ttu-id="ec4f3-120">Описание</span><span class="sxs-lookup"><span data-stu-id="ec4f3-120">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="ec4f3-121">Указывает набор обязательных утверждений для входящих маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="ec4f3-121">Specifies the set of required claims for incoming security tokens.</span></span>|
