---
description: 'Дополнительные сведения: <endToEndTracing>'
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 2ac4a7563d7d7881cdb503e843d34f84fd9c95a9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782121"
---
# \<endToEndTracing>

<span data-ttu-id="b0aa8-102">Элемент конфигурации, который позволяет включать и отключать различные аспекты сквозной отслеживания во время выполнения приложения службы.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="b0aa8-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0aa8-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0aa8-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b0aa8-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b0aa8-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0aa8-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b0aa8-106">Attributes</span></span>  
  
|<span data-ttu-id="b0aa8-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b0aa8-107">Attribute</span></span>|<span data-ttu-id="b0aa8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b0aa8-108">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="b0aa8-109">Логическое значение, указывающее, включено ли отслеживание действия.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-109">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="b0aa8-110">Логическое значение, указывающее, включено ли отслеживание потока сообщений.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-110">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="b0aa8-111">Логическое значение, указывающее, задано ли атрибуту propagate значение true.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-111">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0aa8-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b0aa8-112">Child Elements</span></span>  

 <span data-ttu-id="b0aa8-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0aa8-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b0aa8-114">Parent Elements</span></span>  
  
|<span data-ttu-id="b0aa8-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="b0aa8-115">Element</span></span>|<span data-ttu-id="b0aa8-116">Описание</span><span class="sxs-lookup"><span data-stu-id="b0aa8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="b0aa8-117">Определяет параметры WCF для проверки во время выполнения и управления администратором.</span><span class="sxs-lookup"><span data-stu-id="b0aa8-117">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0aa8-118">См. также</span><span class="sxs-lookup"><span data-stu-id="b0aa8-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="b0aa8-119">Сквозная трассировка</span><span class="sxs-lookup"><span data-stu-id="b0aa8-119">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
