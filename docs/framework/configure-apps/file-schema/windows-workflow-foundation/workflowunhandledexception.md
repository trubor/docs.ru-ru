---
description: 'Дополнительные сведения: <workflowUnhandledException>'
title: <workflowUnhandledException>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 57adeab5-f06a-44b2-916b-0e177cf0f4a6
ms.openlocfilehash: b9258c986ffa154e490f80bead1dc53d8f7ef44d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697781"
---
# \<workflowUnhandledException>

<span data-ttu-id="41f00-102">Поведение службы, позволяющее задать действие, которое будет выполнено при появлении необработанного исключения в службе рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="41f00-102">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowUnhandledException>**  
  
## <a name="syntax"></a><span data-ttu-id="41f00-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="41f00-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f00-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="41f00-104">Attributes and Elements</span></span>  

 <span data-ttu-id="41f00-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="41f00-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f00-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="41f00-106">Attributes</span></span>  
  
|<span data-ttu-id="41f00-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="41f00-107">Attribute</span></span>|<span data-ttu-id="41f00-108">Описание</span><span class="sxs-lookup"><span data-stu-id="41f00-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41f00-109">action</span><span class="sxs-lookup"><span data-stu-id="41f00-109">action</span></span>|<span data-ttu-id="41f00-110">Строка, указывающая действие, которое должно быть предпринято при возникновении необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="41f00-110">A string that specifies the action to take when an unhandled exception occurs.</span></span> <span data-ttu-id="41f00-111">Это атрибут типа <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction>.</span><span class="sxs-lookup"><span data-stu-id="41f00-111">This attribute is of type <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction></span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41f00-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="41f00-112">Child Elements</span></span>  

 <span data-ttu-id="41f00-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="41f00-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41f00-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="41f00-114">Parent Elements</span></span>  
  
|<span data-ttu-id="41f00-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="41f00-115">Element</span></span>|<span data-ttu-id="41f00-116">Описание</span><span class="sxs-lookup"><span data-stu-id="41f00-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41f00-117">\<behavior> из \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="41f00-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="41f00-118">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="41f00-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41f00-119">См. также</span><span class="sxs-lookup"><span data-stu-id="41f00-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowUnhandledExceptionElement>
