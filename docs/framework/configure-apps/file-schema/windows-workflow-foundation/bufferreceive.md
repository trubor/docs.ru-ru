---
description: 'Дополнительные сведения: <bufferReceive>'
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 8f5e58e0e72a81d8b3a20a68e0890be907c20d2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698093"
---
# \<bufferReceive>

<span data-ttu-id="7d205-102">Поведение, позволяющее службе рабочего процесса использовать обработку буфера получения, благодаря чему можно обрабатывать неупорядоченные сообщения.</span><span class="sxs-lookup"><span data-stu-id="7d205-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="7d205-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7d205-103">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d205-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="7d205-104">Attributes and Elements</span></span>  

 <span data-ttu-id="7d205-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="7d205-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d205-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="7d205-106">Attributes</span></span>  
  
|<span data-ttu-id="7d205-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="7d205-107">Attribute</span></span>|<span data-ttu-id="7d205-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7d205-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d205-109">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="7d205-109">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="7d205-110">Целочисленное значение, указывающее максимальное число отложенных сообщений для каждого канала.</span><span class="sxs-lookup"><span data-stu-id="7d205-110">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="7d205-111">Значение по умолчанию — 512.</span><span class="sxs-lookup"><span data-stu-id="7d205-111">The default value is 512.</span></span> <span data-ttu-id="7d205-112">Это свойство ограничивает число внеочередных сообщений, которые могут быть получены службой рабочего процесса.</span><span class="sxs-lookup"><span data-stu-id="7d205-112">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d205-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="7d205-113">Child Elements</span></span>  

 <span data-ttu-id="7d205-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="7d205-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d205-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="7d205-115">Parent Elements</span></span>  
  
|<span data-ttu-id="7d205-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="7d205-116">Element</span></span>|<span data-ttu-id="7d205-117">Описание</span><span class="sxs-lookup"><span data-stu-id="7d205-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d205-118">\<behavior> из \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7d205-118">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7d205-119">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="7d205-119">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d205-120">См. также</span><span class="sxs-lookup"><span data-stu-id="7d205-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
