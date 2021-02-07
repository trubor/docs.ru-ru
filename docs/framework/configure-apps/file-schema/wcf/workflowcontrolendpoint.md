---
description: 'Дополнительные сведения: <workflowControlEndpoint>'
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 5205edf159bd947531231e69fd23f6cdf9c77d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682349"
---
# \<workflowControlEndpoint>

<span data-ttu-id="0409f-102">Этот элемент конфигурации определяет стандартную конечную точку для управления выполнением экземпляров рабочего процесса (создание, выполнение, приостановка, завершение и т. д.).</span><span class="sxs-lookup"><span data-stu-id="0409f-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0409f-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0409f-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0409f-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0409f-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0409f-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0409f-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0409f-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0409f-106">Attributes</span></span>  
  
|<span data-ttu-id="0409f-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0409f-107">Attribute</span></span>|<span data-ttu-id="0409f-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0409f-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0409f-109">name</span><span class="sxs-lookup"><span data-stu-id="0409f-109">name</span></span>|<span data-ttu-id="0409f-110">Строка, указывающая имя конфигурации стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="0409f-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="0409f-111">Это имя используется в атрибуте `endpointConfiguration` конечной точки службы для связывания стандартной конечной точки с ее конфигурацией.</span><span class="sxs-lookup"><span data-stu-id="0409f-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0409f-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0409f-112">Child Elements</span></span>  

 <span data-ttu-id="0409f-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0409f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0409f-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0409f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0409f-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="0409f-115">Element</span></span>|<span data-ttu-id="0409f-116">Описание</span><span class="sxs-lookup"><span data-stu-id="0409f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0409f-117">Коллекция стандартных конечных точек, одно или несколько свойств которых (адрес, привязка, контракт) являются фиксированными.</span><span class="sxs-lookup"><span data-stu-id="0409f-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0409f-118">См. также</span><span class="sxs-lookup"><span data-stu-id="0409f-118">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
