---
description: 'Дополнительные сведения: <workflowInstanceManagement>'
title: <workflowInstanceManagement>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 63ac89ba-c844-4ae2-96ae-cd752a90a109
ms.openlocfilehash: 528c0c923be93d9581b8e3bfccc382eab11c5da1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697924"
---
# \<workflowInstanceManagement>

<span data-ttu-id="dab81-102">Поведение службы, которое позволяет указать параметры, управляющие выполнением экземпляров рабочего процесса, включая сохраняемость, необработанное поведение исключения и неактивное поведение.</span><span class="sxs-lookup"><span data-stu-id="dab81-102">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceManagement>**  
  
## <a name="syntax"></a><span data-ttu-id="dab81-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dab81-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowInstanceManagement authorizedWindowsGroup="" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dab81-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="dab81-104">Attributes and Elements</span></span>  

 <span data-ttu-id="dab81-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="dab81-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dab81-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="dab81-106">Attributes</span></span>  
  
|<span data-ttu-id="dab81-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dab81-107">Attribute</span></span>|<span data-ttu-id="dab81-108">Описание</span><span class="sxs-lookup"><span data-stu-id="dab81-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dab81-109">authorizedWindowsGroup</span><span class="sxs-lookup"><span data-stu-id="dab81-109">authorizedWindowsGroup</span></span>||  
  
### <a name="child-elements"></a><span data-ttu-id="dab81-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="dab81-110">Child Elements</span></span>  

 <span data-ttu-id="dab81-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="dab81-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dab81-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="dab81-112">Parent Elements</span></span>  
  
|<span data-ttu-id="dab81-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="dab81-113">Element</span></span>|<span data-ttu-id="dab81-114">Описание</span><span class="sxs-lookup"><span data-stu-id="dab81-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dab81-115">\<behavior> из \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="dab81-115">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="dab81-116">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="dab81-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dab81-117">См. также</span><span class="sxs-lookup"><span data-stu-id="dab81-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowInstanceManagementBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowInstanceManagementElement>
