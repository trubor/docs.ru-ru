---
description: Дополнительные сведения о <behaviors> рабочем процессе
title: <behaviors> рабочего процесса
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 5154a389aded34065cc7bdb11d1c73d71ca9f9f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698197"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="a2c6d-103">\<behaviors> рабочего процесса</span><span class="sxs-lookup"><span data-stu-id="a2c6d-103">\<behaviors> of workflow</span></span>

<span data-ttu-id="a2c6d-104">Этот элемент содержит коллекцию **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="a2c6d-104">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="a2c6d-105">Каждый элемент в коллекции определяет элементы поведения, используемые службами рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="a2c6d-105">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="a2c6d-106">Каждый элемент поведения определяется с помощью уникального атрибута **имени** .</span><span class="sxs-lookup"><span data-stu-id="a2c6d-106">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="a2c6d-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2c6d-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2c6d-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a2c6d-108">Attributes and Elements</span></span>  

 <span data-ttu-id="a2c6d-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a2c6d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2c6d-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a2c6d-110">Attributes</span></span>  

 <span data-ttu-id="a2c6d-111">None</span><span class="sxs-lookup"><span data-stu-id="a2c6d-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a2c6d-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a2c6d-112">Child Elements</span></span>  
  
|<span data-ttu-id="a2c6d-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="a2c6d-113">Element</span></span>|<span data-ttu-id="a2c6d-114">Описание</span><span class="sxs-lookup"><span data-stu-id="a2c6d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="a2c6d-115">В данном разделе конфигурации представлены все поведения, определенные для конкретной службы рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="a2c6d-115">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2c6d-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a2c6d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a2c6d-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="a2c6d-117">Element</span></span>|<span data-ttu-id="a2c6d-118">Описание</span><span class="sxs-lookup"><span data-stu-id="a2c6d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="a2c6d-119">Корневой элемент всех элементов конфигурации рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="a2c6d-119">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a2c6d-120">См. также</span><span class="sxs-lookup"><span data-stu-id="a2c6d-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="a2c6d-121">Настройка и расширение среды выполнения с помощью поведений</span><span class="sxs-lookup"><span data-stu-id="a2c6d-121">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
