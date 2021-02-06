---
description: 'Дополнительные сведения: <callbackDebug>'
title: <callbackDebug>
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 911d738764baa800831c19f4e5d181118d1d3e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639215"
---
# \<callbackDebug>

<span data-ttu-id="c8287-102">Указывает отладку службы для объекта обратного вызова Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c8287-102">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackDebug>**  
  
## <a name="syntax"></a><span data-ttu-id="c8287-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c8287-103">Syntax</span></span>  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a><span data-ttu-id="c8287-104">Тип</span><span class="sxs-lookup"><span data-stu-id="c8287-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8287-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c8287-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c8287-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c8287-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8287-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c8287-107">Attributes</span></span>  
  
|<span data-ttu-id="c8287-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c8287-108">Attribute</span></span>|<span data-ttu-id="c8287-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c8287-109">Description</span></span>|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|<span data-ttu-id="c8287-110">Значение, которое указывает, возвращают ли объекты обратного вызова клиента сведения об управляемом исключении в ошибках SOAP назад в службу.</span><span class="sxs-lookup"><span data-stu-id="c8287-110">A value that specifies whether client callback objects return managed exception information in SOAP faults back to the service.</span></span><br /><br /> <span data-ttu-id="c8287-111">Если программным способом задать этому атрибуту значение `true`, в объекте обратного вызова клиента можно включить поток сведений об управляемом исключении назад в службу для отладки.</span><span class="sxs-lookup"><span data-stu-id="c8287-111">If you set this attribute to `true` programmatically, you can enable the flow of managed exception information in a client callback object back to the service for debugging purposes.</span></span> <span data-ttu-id="c8287-112">**Внимание!**  Возврат сведений об управляемом исключении клиентам может представлять угрозу безопасности.</span><span class="sxs-lookup"><span data-stu-id="c8287-112">**Caution:**  Returning managed exception information to clients can be a security risk.</span></span> <span data-ttu-id="c8287-113">Это связано с тем, что подробные данные об исключении содержат сведения о внутренней реализации службы, которые могут использоваться неавторизованными клиентами.</span><span class="sxs-lookup"><span data-stu-id="c8287-113">This is because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8287-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c8287-114">Child Elements</span></span>  

 <span data-ttu-id="c8287-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c8287-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8287-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c8287-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c8287-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="c8287-117">Element</span></span>|<span data-ttu-id="c8287-118">Описание</span><span class="sxs-lookup"><span data-stu-id="c8287-118">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c8287-119">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="c8287-119">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8287-120">См. также</span><span class="sxs-lookup"><span data-stu-id="c8287-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
