---
description: 'Дополнительные сведения: <mexHttpBinding>'
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: b95c73ed0576f769f046547152aff030efd49071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684351"
---
# \<mexHttpBinding>

<span data-ttu-id="e0a16-102">Задает параметры для привязки, используемой для обмена сообщениями WS-MetadataExchange (WS-MEX) по протоколу HTTP.</span><span class="sxs-lookup"><span data-stu-id="e0a16-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="e0a16-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e0a16-103">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0a16-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e0a16-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e0a16-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e0a16-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0a16-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e0a16-106">Attributes</span></span>  
  
|<span data-ttu-id="e0a16-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e0a16-107">Attribute</span></span>|<span data-ttu-id="e0a16-108">Описание</span><span class="sxs-lookup"><span data-stu-id="e0a16-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e0a16-109">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="e0a16-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e0a16-110">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e0a16-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e0a16-111">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e0a16-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="e0a16-112">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="e0a16-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e0a16-113">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="e0a16-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e0a16-114">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="e0a16-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e0a16-115">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0a16-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e0a16-116">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="e0a16-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e0a16-117">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e0a16-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e0a16-118">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e0a16-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e0a16-119">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="e0a16-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e0a16-120">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e0a16-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e0a16-121">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e0a16-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e0a16-122">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="e0a16-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e0a16-123">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e0a16-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e0a16-124">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e0a16-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0a16-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e0a16-125">Child Elements</span></span>  

 <span data-ttu-id="e0a16-126">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e0a16-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0a16-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e0a16-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e0a16-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="e0a16-128">Element</span></span>|<span data-ttu-id="e0a16-129">Описание</span><span class="sxs-lookup"><span data-stu-id="e0a16-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="e0a16-130">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="e0a16-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0a16-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="e0a16-131">Remarks</span></span>  

 <span data-ttu-id="e0a16-132">Эта привязка по существу является привязкой `WSHttpBinding` с отключенной безопасностью.</span><span class="sxs-lookup"><span data-stu-id="e0a16-132">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="e0a16-133">Она поддерживает большинство запросов метаданных.</span><span class="sxs-lookup"><span data-stu-id="e0a16-133">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a16-134">См. также</span><span class="sxs-lookup"><span data-stu-id="e0a16-134">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="e0a16-135">Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e0a16-135">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="e0a16-136">Публикация и получение метаданных через пользовательскую привязку</span><span class="sxs-lookup"><span data-stu-id="e0a16-136">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="e0a16-137">Метаданные</span><span class="sxs-lookup"><span data-stu-id="e0a16-137">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="e0a16-138">Привязки</span><span class="sxs-lookup"><span data-stu-id="e0a16-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e0a16-139">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="e0a16-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e0a16-140">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="e0a16-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
