---
description: 'Дополнительные сведения: <mexTcpBinding>'
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: d13d9f5eb4bae13a39d4f0cdb57129eb9216ab5d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684299"
---
# \<mexTcpBinding>

<span data-ttu-id="d3b3d-102">Задает параметры для привязки, используемой для обмена сообщениями WS-MetadataExchange (WS-MEX) по TCP.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="d3b3d-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d3b3d-103">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3b3d-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d3b3d-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d3b3d-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3b3d-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d3b3d-106">Attributes</span></span>  
  
|<span data-ttu-id="d3b3d-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d3b3d-107">Attribute</span></span>|<span data-ttu-id="d3b3d-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d3b3d-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d3b3d-109">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d3b3d-110">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3b3d-111">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="d3b3d-112">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d3b3d-113">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d3b3d-114">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d3b3d-115">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="d3b3d-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d3b3d-116">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d3b3d-117">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3b3d-118">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d3b3d-119">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d3b3d-120">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3b3d-121">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d3b3d-122">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d3b3d-123">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d3b3d-124">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3b3d-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d3b3d-125">Child Elements</span></span>  

 <span data-ttu-id="d3b3d-126">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3b3d-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d3b3d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d3b3d-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="d3b3d-128">Element</span></span>|<span data-ttu-id="d3b3d-129">Описание</span><span class="sxs-lookup"><span data-stu-id="d3b3d-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="d3b3d-130">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="d3b3d-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3b3d-131">См. также</span><span class="sxs-lookup"><span data-stu-id="d3b3d-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="d3b3d-132">Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="d3b3d-132">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d3b3d-133">Публикация и получение метаданных через пользовательскую привязку</span><span class="sxs-lookup"><span data-stu-id="d3b3d-133">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="d3b3d-134">Метаданные</span><span class="sxs-lookup"><span data-stu-id="d3b3d-134">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="d3b3d-135">Привязки</span><span class="sxs-lookup"><span data-stu-id="d3b3d-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d3b3d-136">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="d3b3d-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d3b3d-137">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="d3b3d-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
