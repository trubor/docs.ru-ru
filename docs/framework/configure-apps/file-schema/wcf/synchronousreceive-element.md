---
description: 'Дополнительные сведения о: <synchronousReceive> element'
title: <synchronousReceive> - элемент
ms.date: 03/30/2017
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
ms.openlocfilehash: afcd10b4ad41bd6ff12dbf246f66ef7fac4e759a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682622"
---
# <a name="synchronousreceive-element"></a><span data-ttu-id="15c6a-103">Элемент \<synchronousReceive></span><span class="sxs-lookup"><span data-stu-id="15c6a-103">\<synchronousReceive> element</span></span>

<span data-ttu-id="15c6a-104">Этот элемент конфигурации используется, чтобы задавать поведение времени выполнения при получении сообщений в службе или в клиентском приложении.</span><span class="sxs-lookup"><span data-stu-id="15c6a-104">This configuration element is used to specify run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="15c6a-105">Он не имеет атрибутов или дочерних элементов.</span><span class="sxs-lookup"><span data-stu-id="15c6a-105">It does not have any attributes or child elements.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<synchronousReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="15c6a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="15c6a-106">Syntax</span></span>  
  
```xml  
<synchronousReceive />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15c6a-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="15c6a-107">Attributes and Elements</span></span>  

 <span data-ttu-id="15c6a-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="15c6a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15c6a-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="15c6a-109">Attributes</span></span>  

 <span data-ttu-id="15c6a-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="15c6a-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15c6a-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="15c6a-111">Child Elements</span></span>  

 <span data-ttu-id="15c6a-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="15c6a-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15c6a-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="15c6a-113">Parent Elements</span></span>  
  
|<span data-ttu-id="15c6a-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="15c6a-114">Element</span></span>|<span data-ttu-id="15c6a-115">Описание</span><span class="sxs-lookup"><span data-stu-id="15c6a-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="15c6a-116">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="15c6a-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15c6a-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="15c6a-117">Remarks</span></span>  

 <span data-ttu-id="15c6a-118">Используйте это поведение, чтобы дать указание прослушивателю каналов использовать синхронное получение вместо асинхронного получения по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="15c6a-118">Use this behavior to instruct the channel listener to use a synchronous receive rather than the default, asynchronous.</span></span> <span data-ttu-id="15c6a-119">Windows Communication Foundation (WCF) выдает новый поток для приема для каждого принятого канала.</span><span class="sxs-lookup"><span data-stu-id="15c6a-119">Windows Communication Foundation (WCF) issues a new thread to pump for each accepted channel.</span></span> <span data-ttu-id="15c6a-120">При наличии множества каналов существует вероятность недостатка потоков.</span><span class="sxs-lookup"><span data-stu-id="15c6a-120">If there are a lot of channels, there is the possibility of running out of threads.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c6a-121">См. также</span><span class="sxs-lookup"><span data-stu-id="15c6a-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
