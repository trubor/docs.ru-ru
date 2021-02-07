---
description: 'Дополнительные сведения: <backupList>'
title: <backupList>
ms.date: 03/30/2017
ms.assetid: a3d9d1f9-4a53-45e9-a880-86c8bee0b833
ms.openlocfilehash: 5323c8dad827ebb95e3cad65b3ad527d04517e3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749718"
---
# \<backupList>

<span data-ttu-id="13651-102">Представляет раздел конфигурации для определения резервного списка, в котором перечислен набор конечных точек, используемых службой маршрутизации в случае, если основная конечная точка становится недоступной.</span><span class="sxs-lookup"><span data-stu-id="13651-102">Represents a configuration section for defining a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="13651-103">Если первая конечная точка в списке недоступна, то служба маршрутизации автоматически переключается на следующую точку в списке.</span><span class="sxs-lookup"><span data-stu-id="13651-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="13651-104">Этот метод позволяет быстро повысить надежность приложения, не реализуя в клиентском приложении обработку сложных схем и не задавая расположение всех служб.</span><span class="sxs-lookup"><span data-stu-id="13651-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<backupLists>**](backuplists.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupList>**  
  
## <a name="syntax"></a><span data-ttu-id="13651-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13651-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13651-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="13651-106">Attributes and Elements</span></span>  

 <span data-ttu-id="13651-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="13651-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13651-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="13651-108">Attributes</span></span>  
  
|<span data-ttu-id="13651-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="13651-109">Attribute</span></span>|<span data-ttu-id="13651-110">Описание</span><span class="sxs-lookup"><span data-stu-id="13651-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13651-111">name</span><span class="sxs-lookup"><span data-stu-id="13651-111">name</span></span>|<span data-ttu-id="13651-112">Строка, в которой приведено имя, используемое для указания этого списка конечных точек.</span><span class="sxs-lookup"><span data-stu-id="13651-112">A string that specifies the name used to identify this endpoint list.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13651-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="13651-113">Child Elements</span></span>  
  
|<span data-ttu-id="13651-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="13651-114">Element</span></span>|<span data-ttu-id="13651-115">Описание</span><span class="sxs-lookup"><span data-stu-id="13651-115">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)||  
  
### <a name="parent-elements"></a><span data-ttu-id="13651-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="13651-116">Parent Elements</span></span>  
  
|<span data-ttu-id="13651-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="13651-117">Element</span></span>|<span data-ttu-id="13651-118">Описание</span><span class="sxs-lookup"><span data-stu-id="13651-118">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="13651-119">Список резервных конечных точек.</span><span class="sxs-lookup"><span data-stu-id="13651-119">A list of backup endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13651-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="13651-120">Remarks</span></span>  

 <span data-ttu-id="13651-121">Этот раздел содержит упорядоченную коллекцию конечных точек, в которые будет передаваться сообщение в случае, если при отправке в основную конечную точку возникает исключение связи.</span><span class="sxs-lookup"><span data-stu-id="13651-121">This section contains an ordered collection of endpoints that a message will be transmitted to in the event of a communications exception when sending to the primary endpoint.</span></span>  
  
 <span data-ttu-id="13651-122">Если отправка в основную конечную точку, указанную в `endpointName` атрибуте, [\<add>](add-of-entries.md) завершается с исключением связи, служба Routing Service попытается отправить сообщение в первую конечную точку в этом разделе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="13651-122">If a send to the primary endpoint listed in the `endpointName` attribute of [\<add>](add-of-entries.md) fails with a communications exception, the Routing Service will attempt to send the message to the first endpoint in this configuration section.</span></span> <span data-ttu-id="13651-123">Если эта отправка также приведет к возникновению исключения связи, служба маршрутизации попытается отправить сообщение в следующую точку, указанную в этом разделе, пока отправка не завершится успешно или не возвратит ошибку, не связанную с исключением связи, либо пока ошибки не будут возвращены для всех конечных точек из коллекции.</span><span class="sxs-lookup"><span data-stu-id="13651-123">If this also fails with a communications exception, the Routing Service will attempt to send the message to the next message contained in this section until the send attempt succeeds, returns a failure other than a communication exception, or all endpoints in the collection have returned a failure.</span></span>  
  
 <span data-ttu-id="13651-124">В следующем примере, если отправка в основную конечную точку с именем "Destination" возвращает исключение связи, Служба попытается отправить сообщение в "Алтернатесервицекуеуе".</span><span class="sxs-lookup"><span data-stu-id="13651-124">In the following example, if a send to the primary endpoint named "Destination" returns a communication exception, the service will attempt to send the message to the "alternateServiceQueue".</span></span> <span data-ttu-id="13651-125">Если эта попытка также возвращает исключение связи, то служба маршрутизации попытается отправить сообщение в следующую конечную точку в коллекции.</span><span class="sxs-lookup"><span data-stu-id="13651-125">If this attempt also returns a communication exception, the Routing Service will attempt to send the message to the next endpoint in the collection.</span></span>  
  
```xml  
<filterTables>
  <filterTable name="filterTable1">
    <add filterName="MatchAllFilter1"
         endpointName="Destination"
         backupList="backupEndpointList" />
  </filterTable>
</filterTables>
<backupLists>
  <backupList name="backupEndpointList">
    <add endpointName="backupServiceQueue" />
    <add endpointName="alternateServiceQueue" />
  </backupList>
</backupLists>
```  
  
## <a name="see-also"></a><span data-ttu-id="13651-126">См. также</span><span class="sxs-lookup"><span data-stu-id="13651-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>
