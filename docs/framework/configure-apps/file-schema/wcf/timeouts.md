---
description: 'Дополнительные сведения: <timeOuts>'
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 097569d1742f6486ddfb5fb3c3d98ba106424f45
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786594"
---
# \<timeOuts>

<span data-ttu-id="b5d87-102">Элемент конфигурации, который задает допустимый интервал времени для открытия или закрытия узла службы.</span><span class="sxs-lookup"><span data-stu-id="b5d87-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="b5d87-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5d87-103">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5d87-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b5d87-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b5d87-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b5d87-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5d87-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b5d87-106">Attributes</span></span>  
  
|<span data-ttu-id="b5d87-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b5d87-107">Attribute</span></span>|<span data-ttu-id="b5d87-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b5d87-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b5d87-109">Значение <xref:System.TimeSpan>, которое задает временной интервал, выделенный для операции закрытия узла службы.</span><span class="sxs-lookup"><span data-stu-id="b5d87-109">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="b5d87-110">Значение <xref:System.TimeSpan>, которое задает временной интервал, выделенный для операции открытия узла службы.</span><span class="sxs-lookup"><span data-stu-id="b5d87-110">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5d87-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b5d87-111">Child Elements</span></span>  

 <span data-ttu-id="b5d87-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b5d87-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5d87-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b5d87-113">Parent Elements</span></span>  
  
|<span data-ttu-id="b5d87-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="b5d87-114">Element</span></span>|<span data-ttu-id="b5d87-115">Описание</span><span class="sxs-lookup"><span data-stu-id="b5d87-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="b5d87-116">Элемент конфигурации, который задает параметры узла службы.</span><span class="sxs-lookup"><span data-stu-id="b5d87-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5d87-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b5d87-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="b5d87-118">Размещение</span><span class="sxs-lookup"><span data-stu-id="b5d87-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
