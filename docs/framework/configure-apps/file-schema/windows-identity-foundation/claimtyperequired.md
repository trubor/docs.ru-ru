---
description: 'Дополнительные сведения: <claimTypeRequired>'
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: ba95c56af431a6dd81323751a42ce47160544cc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664175"
---
# \<claimTypeRequired>

<span data-ttu-id="35c82-102">Указывает набор обязательных утверждений для входящих маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="35c82-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="35c82-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="35c82-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35c82-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="35c82-104">Attributes and Elements</span></span>  

 <span data-ttu-id="35c82-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="35c82-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35c82-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="35c82-106">Attributes</span></span>  

 <span data-ttu-id="35c82-107">None</span><span class="sxs-lookup"><span data-stu-id="35c82-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="35c82-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="35c82-108">Child Elements</span></span>  
  
|<span data-ttu-id="35c82-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="35c82-109">Element</span></span>|<span data-ttu-id="35c82-110">Описание</span><span class="sxs-lookup"><span data-stu-id="35c82-110">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="35c82-111">Указывает одно необязательное или обязательное утверждение для входящих токенов безопасности.</span><span class="sxs-lookup"><span data-stu-id="35c82-111">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35c82-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="35c82-112">Parent Elements</span></span>  
  
|<span data-ttu-id="35c82-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="35c82-113">Element</span></span>|<span data-ttu-id="35c82-114">Описание</span><span class="sxs-lookup"><span data-stu-id="35c82-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="35c82-115">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="35c82-115">Specifies service-level identity settings.</span></span>|
