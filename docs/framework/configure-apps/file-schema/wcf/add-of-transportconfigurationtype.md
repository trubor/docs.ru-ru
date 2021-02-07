---
description: 'Дополнительные сведения <add> о: <transportConfigurationType>'
title: <add> из <transportConfigurationType>
ms.date: 03/30/2017
ms.assetid: 03d79db9-571d-4534-acef-d05e5467b257
ms.openlocfilehash: 4a4a68e1f70bcb2ec7d55d5d6c3b530e71ddc55d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750017"
---
# <a name="add-of-transportconfigurationtype"></a><span data-ttu-id="3bc43-103">\<add> из \<transportConfigurationType></span><span class="sxs-lookup"><span data-stu-id="3bc43-103">\<add> of \<transportConfigurationType></span></span>

<span data-ttu-id="3bc43-104">Данный элемент представляет собой пару ключ/значение, которая идентифицирует тип конкретного транспорта.</span><span class="sxs-lookup"><span data-stu-id="3bc43-104">This element is a key/value pair, which identifies the type of a particular transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<transportConfigurationTypes>**](transportconfigurationtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="3bc43-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3bc43-105">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3bc43-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="3bc43-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3bc43-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="3bc43-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3bc43-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="3bc43-108">Attributes</span></span>  
  
|<span data-ttu-id="3bc43-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="3bc43-109">Attribute</span></span>|<span data-ttu-id="3bc43-110">Описание</span><span class="sxs-lookup"><span data-stu-id="3bc43-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3bc43-111">name</span><span class="sxs-lookup"><span data-stu-id="3bc43-111">name</span></span>|<span data-ttu-id="3bc43-112">Обязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="3bc43-112">Required String attribute.</span></span><br /><br /> <span data-ttu-id="3bc43-113">Содержит ключ, определяемый пользователем, который является уникальным идентификатором типа транспорта.</span><span class="sxs-lookup"><span data-stu-id="3bc43-113">Contains a user-defined key that uniquely identifies the transport type.</span></span>|  
|<span data-ttu-id="3bc43-114">transportConfigurationType</span><span class="sxs-lookup"><span data-stu-id="3bc43-114">transportConfigurationType</span></span>|<span data-ttu-id="3bc43-115">Строка, содержащая тип, реализующий конкретный транспорт.</span><span class="sxs-lookup"><span data-stu-id="3bc43-115">A string that contains the type that implements the specific transport.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3bc43-116">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="3bc43-116">Child Elements</span></span>  

 <span data-ttu-id="3bc43-117">None</span><span class="sxs-lookup"><span data-stu-id="3bc43-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3bc43-118">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="3bc43-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3bc43-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="3bc43-119">Element</span></span>|<span data-ttu-id="3bc43-120">Описание</span><span class="sxs-lookup"><span data-stu-id="3bc43-120">Description</span></span>|  
|-------------|-----------------|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="3bc43-121">Коллекция типов, реализующих конкретный транспорт.</span><span class="sxs-lookup"><span data-stu-id="3bc43-121">A collection of types that implement the specific transport.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3bc43-122">Пример</span><span class="sxs-lookup"><span data-stu-id="3bc43-122">Example</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <transportConfigurationTypes>
    <add name="net.udp"
         transportConfigurationType="Microsoft.ServiceModel.Samples.Hosting.HostedUdpTransportConfiguration, UdpActivation, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6fa904d2da1848d6" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="see-also"></a><span data-ttu-id="3bc43-123">См. также</span><span class="sxs-lookup"><span data-stu-id="3bc43-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="3bc43-124">Размещение</span><span class="sxs-lookup"><span data-stu-id="3bc43-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
