---
description: 'Дополнительные сведения: <workflowIdle>'
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: c1707ab5c633a358846a8ddf529bbfab90d3012d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99697963"
---
# \<workflowIdle>

<span data-ttu-id="9ab5c-102">Поведение службы, управляющее выгрузкой и сохранением простаивающих экземпляров рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="9ab5c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9ab5c-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan"
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ab5c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="9ab5c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="9ab5c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ab5c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="9ab5c-106">Attributes</span></span>  
  
|<span data-ttu-id="9ab5c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="9ab5c-107">Attribute</span></span>|<span data-ttu-id="9ab5c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9ab5c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ab5c-109">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="9ab5c-109">timeToPersist</span></span>|<span data-ttu-id="9ab5c-110">Значение Timespan, указывающее интервал, который возникает между моментом, когда рабочий процесс становится неактивным, и его сохранением.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-110">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="9ab5c-111">Значением по умолчанию является TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-111">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="9ab5c-112">Начало интервала определяется моментом, когда экземпляр рабочего процесса становится неактивным.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-112">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="9ab5c-113">Этот атрибут может оказаться полезным в том случае, если необходимо более интенсивно сохранять экземпляр рабочего процесса, оставляя его в памяти как можно дольше.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-113">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="9ab5c-114">Этот атрибут допустим только в том случае, если его значение меньше, чем атрибут **тиметаунлоад** .</span><span class="sxs-lookup"><span data-stu-id="9ab5c-114">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="9ab5c-115">Если значение больше, оно не учитывается.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-115">If it is greater, it is ignored.</span></span> <span data-ttu-id="9ab5c-116">Если этот атрибут истекает до значения, заданного атрибутом **тиметаунлоад** , сохраняемость должна завершиться до выгрузки рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-116">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="9ab5c-117">Это означает, что операция выгрузки может быть задержана, пока рабочий процесс не будет сохранен.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-117">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="9ab5c-118">Уровень сохраняемости ответственен за обработку повторений для временных ошибок и выдает исключения только для неустранимых ошибок.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-118">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="9ab5c-119">В связи с этим все исключения, возникшие во время сохранения, считаются неустранимыми, и производится прерывание работы экземпляра рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-119">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9ab5c-120">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="9ab5c-120">timeToUnload</span></span>|<span data-ttu-id="9ab5c-121">Значение Timespan, указывающее интервал времени от момента, когда рабочий процесс стал неактивным, до его выгрузки.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-121">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="9ab5c-122">Значение по умолчанию - 1 минута.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-122">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="9ab5c-123">При выгрузке рабочего процесса подразумевается, что было произведено его сохранение.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-123">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="9ab5c-124">Если этот атрибут имеет нулевое значение, экземпляр рабочего процесса сохраняется и выгружается сразу после того, как становится неактивным.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-124">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="9ab5c-125">Если задать этому атрибуту значение TimeSpan.MaxValue, операция выгрузки будет фактически отключена.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-125">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="9ab5c-126">Простаивающие экземпляры рабочего процесса не выгружаются.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-126">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ab5c-127">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="9ab5c-127">Child Elements</span></span>  

 <span data-ttu-id="9ab5c-128">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ab5c-129">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="9ab5c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9ab5c-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="9ab5c-130">Element</span></span>|<span data-ttu-id="9ab5c-131">Описание</span><span class="sxs-lookup"><span data-stu-id="9ab5c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ab5c-132">\<behavior> из \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9ab5c-132">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="9ab5c-133">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="9ab5c-133">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ab5c-134">См. также</span><span class="sxs-lookup"><span data-stu-id="9ab5c-134">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
