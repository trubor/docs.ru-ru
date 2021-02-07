---
description: 'Дополнительные сведения: <persistenceProvider>'
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 60ddaf9f26f496bd7d79ccab84f84135e46963d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683558"
---
# \<persistenceProvider>

<span data-ttu-id="26e6b-102">Задает тип используемой реализации поставщика сохраняемости, а также время ожидания операций сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="26e6b-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="26e6b-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26e6b-103">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26e6b-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="26e6b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="26e6b-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="26e6b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26e6b-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="26e6b-106">Attributes</span></span>  
  
|<span data-ttu-id="26e6b-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="26e6b-107">Attribute</span></span>|<span data-ttu-id="26e6b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="26e6b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26e6b-109">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="26e6b-109">persistenceOperationTimeout</span></span>|<span data-ttu-id="26e6b-110">Значение <xref:System.TimeSpan>, которое задает время ожидания, используемое для операций сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="26e6b-110">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="26e6b-111">Значение по умолчанию — "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="26e6b-111">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="26e6b-112">тип</span><span class="sxs-lookup"><span data-stu-id="26e6b-112">type</span></span>|<span data-ttu-id="26e6b-113">Строка, указывающая тип используемой фабрики поставщика сохраняемости.</span><span class="sxs-lookup"><span data-stu-id="26e6b-113">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26e6b-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="26e6b-114">Child Elements</span></span>  

 <span data-ttu-id="26e6b-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="26e6b-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26e6b-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="26e6b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="26e6b-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="26e6b-117">Element</span></span>|<span data-ttu-id="26e6b-118">Описание</span><span class="sxs-lookup"><span data-stu-id="26e6b-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="26e6b-119">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="26e6b-119">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26e6b-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="26e6b-120">Remarks</span></span>  

 <span data-ttu-id="26e6b-121">Этот элемент задает поставщика сохраняемости, используемого для сериализации состояния службы WCF.</span><span class="sxs-lookup"><span data-stu-id="26e6b-121">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="26e6b-122">Он должен использоваться вместе с атрибутом `wsHttpContextBinding`, который передает сведения о состоянии в HTTP-заголовки.</span><span class="sxs-lookup"><span data-stu-id="26e6b-122">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26e6b-123">См. также</span><span class="sxs-lookup"><span data-stu-id="26e6b-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
