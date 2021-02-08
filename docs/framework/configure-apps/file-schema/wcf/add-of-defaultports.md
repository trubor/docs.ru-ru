---
description: 'Дополнительные сведения <add> о: <defaultPorts>'
title: <add> из <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 9db7afa5183b185eb842530b051d98236e7fa381
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803962"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="b747f-103">\<add> из \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="b747f-103">\<add> of \<defaultPorts></span></span>

<span data-ttu-id="b747f-104">Конечная точка связи по умолчанию, которую прослушивает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="b747f-104">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="b747f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b747f-105">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b747f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b747f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b747f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b747f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b747f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b747f-108">Attributes</span></span>  
  
|<span data-ttu-id="b747f-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b747f-109">Attribute</span></span>|<span data-ttu-id="b747f-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b747f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b747f-111">порт</span><span class="sxs-lookup"><span data-stu-id="b747f-111">port</span></span>|<span data-ttu-id="b747f-112">Целочисленное значение, определяющее номер COM-порта по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b747f-112">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="b747f-113">схема</span><span class="sxs-lookup"><span data-stu-id="b747f-113">scheme</span></span>|<span data-ttu-id="b747f-114">Строка, в которой указана группа параметров протокола, связанных с COM-портом.</span><span class="sxs-lookup"><span data-stu-id="b747f-114">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b747f-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b747f-115">Child Elements</span></span>  

 <span data-ttu-id="b747f-116">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b747f-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b747f-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b747f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b747f-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="b747f-118">Element</span></span>|<span data-ttu-id="b747f-119">Описание</span><span class="sxs-lookup"><span data-stu-id="b747f-119">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="b747f-120">Коллекция портов по умолчанию со списком конечных точек связи по умолчанию, которые прослушивает клиентское приложение.</span><span class="sxs-lookup"><span data-stu-id="b747f-120">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b747f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="b747f-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
