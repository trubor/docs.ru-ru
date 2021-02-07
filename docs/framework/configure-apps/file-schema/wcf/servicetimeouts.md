---
description: 'Дополнительные сведения: <serviceTimeouts>'
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: bc9ef99078f8c6fa3b441604e14df928eec054e1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682732"
---
# \<serviceTimeouts>

<span data-ttu-id="81c96-102">Задает время ожидания для службы.</span><span class="sxs-lookup"><span data-stu-id="81c96-102">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="81c96-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="81c96-103">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="81c96-104">Тип</span><span class="sxs-lookup"><span data-stu-id="81c96-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81c96-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="81c96-105">Attributes and Elements</span></span>  

 <span data-ttu-id="81c96-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="81c96-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81c96-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="81c96-107">Attributes</span></span>  
  
|<span data-ttu-id="81c96-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="81c96-108">Attribute</span></span>|<span data-ttu-id="81c96-109">Описание</span><span class="sxs-lookup"><span data-stu-id="81c96-109">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="81c96-110">Значение <xref:System.TimeSpan>, задающее интервал времени, в течение которого транзакция должна дойти от клиента до сервера.</span><span class="sxs-lookup"><span data-stu-id="81c96-110">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="81c96-111">Значение по умолчанию — "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="81c96-111">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81c96-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="81c96-112">Child Elements</span></span>  

 <span data-ttu-id="81c96-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="81c96-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81c96-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="81c96-114">Parent Elements</span></span>  
  
|<span data-ttu-id="81c96-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="81c96-115">Element</span></span>|<span data-ttu-id="81c96-116">Описание</span><span class="sxs-lookup"><span data-stu-id="81c96-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="81c96-117">Указывает элемент поведения.</span><span class="sxs-lookup"><span data-stu-id="81c96-117">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81c96-118">См. также</span><span class="sxs-lookup"><span data-stu-id="81c96-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
