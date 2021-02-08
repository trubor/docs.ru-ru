---
description: 'Дополнительные сведения: <serviceAuthenticationManager>'
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: ae9c8d7f74b3ad7d0c61a77d20f38f228c695970
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786776"
---
# \<serviceAuthenticationManager>

<span data-ttu-id="fcd45-102">Обеспечивает элемент конфигурации рабочего процесса, который устанавливает на уровне службы действительность передачи, сообщения или инициатора.</span><span class="sxs-lookup"><span data-stu-id="fcd45-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="fcd45-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fcd45-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcd45-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fcd45-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fcd45-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fcd45-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcd45-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fcd45-106">Attributes</span></span>  
  
|<span data-ttu-id="fcd45-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fcd45-107">Attribute</span></span>|<span data-ttu-id="fcd45-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fcd45-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcd45-109">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="fcd45-109">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="fcd45-110">Строка, в которой указан тип политики проверки подлинности для текущего поведения.</span><span class="sxs-lookup"><span data-stu-id="fcd45-110">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcd45-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fcd45-111">Child Elements</span></span>  

 <span data-ttu-id="fcd45-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fcd45-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fcd45-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fcd45-113">Parent Elements</span></span>  
  
|<span data-ttu-id="fcd45-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="fcd45-114">Element</span></span>|<span data-ttu-id="fcd45-115">Описание</span><span class="sxs-lookup"><span data-stu-id="fcd45-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fcd45-116">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="fcd45-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fcd45-117">См. также</span><span class="sxs-lookup"><span data-stu-id="fcd45-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
