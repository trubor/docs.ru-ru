---
description: 'Дополнительные сведения: <backupLists>'
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 9647c507f85eba6bfd001b34dbf617bc881d3f2e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749705"
---
# \<backupLists>

<span data-ttu-id="84998-102">Представляет раздел конфигурации для определения набора резервных служб, используемых при обработке ошибок.</span><span class="sxs-lookup"><span data-stu-id="84998-102">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="84998-103">Каждый дочерний элемент является резервным списком, в котором перечислен набор конечных точек, используемых службой маршрутизации в случае, если основная конечная точка становится недоступной.</span><span class="sxs-lookup"><span data-stu-id="84998-103">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="84998-104">Если первая конечная точка в списке недоступна, то служба маршрутизации автоматически переключается на следующую точку в списке.</span><span class="sxs-lookup"><span data-stu-id="84998-104">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="84998-105">Этот метод позволяет быстро повысить надежность приложения, не реализуя в клиентском приложении обработку сложных схем и не задавая расположение всех служб.</span><span class="sxs-lookup"><span data-stu-id="84998-105">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="84998-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="84998-106">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84998-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="84998-107">Attributes and Elements</span></span>  

 <span data-ttu-id="84998-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="84998-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84998-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="84998-109">Attributes</span></span>  

 <span data-ttu-id="84998-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="84998-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84998-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="84998-111">Child Elements</span></span>  
  
|<span data-ttu-id="84998-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="84998-112">Element</span></span>|<span data-ttu-id="84998-113">Описание</span><span class="sxs-lookup"><span data-stu-id="84998-113">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="84998-114">Содержит список конечных точек, которые служба маршрутизации будет использовать, если основная конечная точка недоступна.</span><span class="sxs-lookup"><span data-stu-id="84998-114">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="84998-115">.</span><span class="sxs-lookup"><span data-stu-id="84998-115">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84998-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="84998-116">Parent Elements</span></span>  
  
|<span data-ttu-id="84998-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="84998-117">Element</span></span>|<span data-ttu-id="84998-118">Описание</span><span class="sxs-lookup"><span data-stu-id="84998-118">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="84998-119">Представляет раздел конфигурации для определения набора фильтров маршрутизации, которые определяют тип Windows Communication Foundation (WCF), <xref:System.ServiceModel.Dispatcher.MessageFilter> используемый при оценке входящих сообщений, а также таблицы маршрутизации, определяющие целевые конечные точки для отправки сообщений при совпадении фильтра.</span><span class="sxs-lookup"><span data-stu-id="84998-119">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84998-120">См. также</span><span class="sxs-lookup"><span data-stu-id="84998-120">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
