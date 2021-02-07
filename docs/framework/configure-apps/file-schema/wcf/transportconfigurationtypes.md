---
description: 'Дополнительные сведения: <transportConfigurationTypes>'
title: <transportConfigurationTypes>
ms.date: 03/30/2017
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
ms.openlocfilehash: d6ef92cf3bdd10fdc9b374f10aaa748cf4300529
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749276"
---
# \<transportConfigurationTypes>

<span data-ttu-id="e6ba8-102">Представляет коллекцию элементов конфигурации, которые определяют тип конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="e6ba8-102">Represents a collection of configuration elements that identify the type of a particular transport.</span></span> <span data-ttu-id="e6ba8-103">Может использоваться для добавления пользовательских протоколов WAS.</span><span class="sxs-lookup"><span data-stu-id="e6ba8-103">This can be used to add custom WAS protocols.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transportConfigurationTypes>**  
  
## <a name="syntax"></a><span data-ttu-id="e6ba8-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6ba8-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6ba8-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e6ba8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e6ba8-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e6ba8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6ba8-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e6ba8-107">Attributes</span></span>  
  
|<span data-ttu-id="e6ba8-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e6ba8-108">Attribute</span></span>|<span data-ttu-id="e6ba8-109">Описание</span><span class="sxs-lookup"><span data-stu-id="e6ba8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6ba8-110">name</span><span class="sxs-lookup"><span data-stu-id="e6ba8-110">name</span></span>|<span data-ttu-id="e6ba8-111">Имя транспорта</span><span class="sxs-lookup"><span data-stu-id="e6ba8-111">The name of the transport</span></span>|  
|<span data-ttu-id="e6ba8-112">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="e6ba8-112">transportConfigurationType</span></span>|<span data-ttu-id="e6ba8-113">Тип, реализующий транспорт</span><span class="sxs-lookup"><span data-stu-id="e6ba8-113">The type that implements the transport</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6ba8-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e6ba8-114">Child Elements</span></span>  
  
|<span data-ttu-id="e6ba8-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="e6ba8-115">Element</span></span>|<span data-ttu-id="e6ba8-116">Описание</span><span class="sxs-lookup"><span data-stu-id="e6ba8-116">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-transportconfigurationtype.md)|<span data-ttu-id="e6ba8-117">Добавляет элемент конфигурации, который определяет тип конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="e6ba8-117">Adds a configuration element that identifies the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6ba8-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e6ba8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e6ba8-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="e6ba8-119">Element</span></span>|<span data-ttu-id="e6ba8-120">Описание</span><span class="sxs-lookup"><span data-stu-id="e6ba8-120">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="e6ba8-121">Определяет, какой тип среда размещения служб создает для конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="e6ba8-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6ba8-122">См. также</span><span class="sxs-lookup"><span data-stu-id="e6ba8-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>
- [<span data-ttu-id="e6ba8-123">Размещение</span><span class="sxs-lookup"><span data-stu-id="e6ba8-123">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
