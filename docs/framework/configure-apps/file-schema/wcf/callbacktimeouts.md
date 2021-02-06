---
description: 'Дополнительные сведения: <callbackTimeouts>'
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: 8e2e05ad23f661c38430ccddc615c37705e6fc44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639202"
---
# \<callbackTimeouts>

<span data-ttu-id="a3561-102">Задает значение времени ожидания при потоке транзакций от сервера к клиенту в сценарии с дуплексным контрактом обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="a3561-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="a3561-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a3561-103">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="a3561-104">Тип</span><span class="sxs-lookup"><span data-stu-id="a3561-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3561-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a3561-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a3561-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a3561-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3561-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a3561-107">Attributes</span></span>  
  
|<span data-ttu-id="a3561-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a3561-108">Attribute</span></span>|<span data-ttu-id="a3561-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a3561-109">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="a3561-110">Значение <xref:System.TimeSpan>, задающее интервал времени, в течение которого транзакции должны завершаться или автоматически прерываться.</span><span class="sxs-lookup"><span data-stu-id="a3561-110">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="a3561-111">Значение по умолчанию — "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="a3561-111">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3561-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a3561-112">Child Elements</span></span>  

 <span data-ttu-id="a3561-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a3561-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3561-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a3561-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a3561-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="a3561-115">Element</span></span>|<span data-ttu-id="a3561-116">Описание</span><span class="sxs-lookup"><span data-stu-id="a3561-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a3561-117">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a3561-117">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a3561-118">См. также</span><span class="sxs-lookup"><span data-stu-id="a3561-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
