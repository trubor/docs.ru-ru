---
description: 'Дополнительные сведения: <dispatcherSynchronization>'
title: <dispatcherSynchronization>
ms.date: 03/30/2017
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
ms.openlocfilehash: 93664dec3648ed58df7e3e5c0760f1694c60ba7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749610"
---
# \<dispatcherSynchronization>
  
<span data-ttu-id="88f58-102">Указывает поведение конечной точки, которое позволяет службе отправлять ответы в асинхронном режиме.</span><span class="sxs-lookup"><span data-stu-id="88f58-102">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dispatcherSynchronization>**  
  
## <a name="syntax"></a><span data-ttu-id="88f58-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="88f58-103">Syntax</span></span>  
  
```xml  
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean"
                                   maxPendingReceives="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="88f58-104">Тип</span><span class="sxs-lookup"><span data-stu-id="88f58-104">Type</span></span>  
  
`Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88f58-105">Элементы и атрибуты</span><span class="sxs-lookup"><span data-stu-id="88f58-105">Attributes and elements</span></span>  
  
<span data-ttu-id="88f58-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="88f58-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88f58-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="88f58-107">Attributes</span></span>

| <span data-ttu-id="88f58-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="88f58-108">Attribute</span></span>               | <span data-ttu-id="88f58-109">Описание</span><span class="sxs-lookup"><span data-stu-id="88f58-109">Description</span></span>       |
| ----------------------- | ----------------- |
| <span data-ttu-id="88f58-110">asynchronousSendEnabled</span><span class="sxs-lookup"><span data-stu-id="88f58-110">asynchronousSendEnabled</span></span> | <span data-ttu-id="88f58-111">Логическое значение, указывающее, включено ли поведение, которое позволяет отправлять ответы в асинхронном режиме.</span><span class="sxs-lookup"><span data-stu-id="88f58-111">A Boolean that specifies whether asynchronous send behavior is enabled.</span></span> |
| `maxPendingReceives`    | <span data-ttu-id="88f58-112">Целочисленное значение, которое указывает число возможных получений по одному каналу.</span><span class="sxs-lookup"><span data-stu-id="88f58-112">An integer that specifies the number of concurrent receives that can be issued on the channel.</span></span><br /><br /> <span data-ttu-id="88f58-113">Это значение должно настраиваться только после правильной настройки поведения регулирования службы.</span><span class="sxs-lookup"><span data-stu-id="88f58-113">This value should be configured only after you have properly configured service throttling behavior.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="88f58-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="88f58-114">Child elements</span></span>

<span data-ttu-id="88f58-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="88f58-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="88f58-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="88f58-116">Parent elements</span></span>

| <span data-ttu-id="88f58-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="88f58-117">Element</span></span> | <span data-ttu-id="88f58-118">Описание</span><span class="sxs-lookup"><span data-stu-id="88f58-118">Description</span></span> |  
| ------- | ----------- |  
| [\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="88f58-119">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="88f58-119">Specifies an endpoint behavior.</span></span> |

## <a name="see-also"></a><span data-ttu-id="88f58-120">См. также</span><span class="sxs-lookup"><span data-stu-id="88f58-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement>
- <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>
