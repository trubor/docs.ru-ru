---
description: 'Дополнительные сведения <add> о: <backupList>'
title: <add> из <backupList>
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 9855d93be011b4eaa2890c4d24392fde3b65d05a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804079"
---
# <a name="add-of-backuplist"></a><span data-ttu-id="723e3-103">\<add> из \<backupList></span><span class="sxs-lookup"><span data-stu-id="723e3-103">\<add> of \<backupList></span></span>

<span data-ttu-id="723e3-104">Представляет элемент конфигурации, в котором задается элемент резервной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="723e3-104">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupList>**](backuplist.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="723e3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="723e3-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="723e3-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="723e3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="723e3-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="723e3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="723e3-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="723e3-108">Attributes</span></span>  
  
|<span data-ttu-id="723e3-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="723e3-109">Attribute</span></span>|<span data-ttu-id="723e3-110">Описание</span><span class="sxs-lookup"><span data-stu-id="723e3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="723e3-111">name</span><span class="sxs-lookup"><span data-stu-id="723e3-111">name</span></span>|<span data-ttu-id="723e3-112">Строка, задающая имя резервной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="723e3-112">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="723e3-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="723e3-113">Child Elements</span></span>  

 <span data-ttu-id="723e3-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="723e3-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="723e3-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="723e3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="723e3-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="723e3-116">Element</span></span>|<span data-ttu-id="723e3-117">Описание</span><span class="sxs-lookup"><span data-stu-id="723e3-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="723e3-118">Содержит список конечных точек, которые служба маршрутизации будет использовать, если основная конечная точка недоступна.</span><span class="sxs-lookup"><span data-stu-id="723e3-118">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="723e3-119">См. также</span><span class="sxs-lookup"><span data-stu-id="723e3-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType>
