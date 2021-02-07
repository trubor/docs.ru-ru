---
description: 'Дополнительные сведения: <mexHttpsBinding>'
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 1e6eb66e1379cb8f351e34d4fd406dd3cc1f9a4e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684338"
---
# \<mexHttpsBinding>

<span data-ttu-id="bb5b0-102">Задает параметры для привязки, используемой для обмена сообщениями WS-MetadataExchange (WS-MEX) посредством HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="bb5b0-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb5b0-103">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb5b0-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bb5b0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="bb5b0-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb5b0-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bb5b0-106">Attributes</span></span>  
  
|<span data-ttu-id="bb5b0-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="bb5b0-107">Attribute</span></span>|<span data-ttu-id="bb5b0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="bb5b0-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bb5b0-109">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции закрытия.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bb5b0-110">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb5b0-111">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-111">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bb5b0-112">Строка, содержащая имя конфигурации привязки.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-112">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bb5b0-113">Это значение должно быть уникальным, поскольку оно используется в качестве идентификатора привязки.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-113">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bb5b0-114">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-114">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bb5b0-115">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bb5b0-115">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bb5b0-116">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции открытия.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-116">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bb5b0-117">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-117">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb5b0-118">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-118">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bb5b0-119">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции получения.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-119">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bb5b0-120">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-120">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb5b0-121">Значение по умолчанию - 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-121">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bb5b0-122">Значение <xref:System.TimeSpan>, которое задает длительность времени ожидания для завершения операции отправки.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bb5b0-123">Это значение должно быть больше или равно <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bb5b0-124">Значение по умолчанию - 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-124">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb5b0-125">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bb5b0-125">Child Elements</span></span>  

 <span data-ttu-id="bb5b0-126">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb5b0-127">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bb5b0-127">Parent Elements</span></span>  
  
|<span data-ttu-id="bb5b0-128">Элемент</span><span class="sxs-lookup"><span data-stu-id="bb5b0-128">Element</span></span>|<span data-ttu-id="bb5b0-129">Описание</span><span class="sxs-lookup"><span data-stu-id="bb5b0-129">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="bb5b0-130">Этот элемент содержит коллекцию стандартных и пользовательских привязок.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-130">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb5b0-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="bb5b0-131">Remarks</span></span>  

 <span data-ttu-id="bb5b0-132">Эта привязка по существу является привязкой `WSHttpBinding`, которая поддерживает безопасность уровня транспорта с помощью сертификатов.</span><span class="sxs-lookup"><span data-stu-id="bb5b0-132">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="bb5b0-133">Дополнительные сведения о настройке и использовании такой конечной точки метаданных см. в разделе [как настроить настраиваемую привязку WS-Metadata Exchange](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [как получить метаданные через ПРИвязку обмена метаданными](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), а также как образец [настраиваемой конечной точки безопасных метаданных](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="bb5b0-133">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5b0-134">См. также</span><span class="sxs-lookup"><span data-stu-id="bb5b0-134">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="bb5b0-135">Практическое руководство. Публикация метаданных для службы с использованием файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="bb5b0-135">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bb5b0-136">Публикация и получение метаданных через пользовательскую привязку</span><span class="sxs-lookup"><span data-stu-id="bb5b0-136">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bb5b0-137">Практическое руководство. Настройка пользовательской привязки для обмена WS-Metadata</span><span class="sxs-lookup"><span data-stu-id="bb5b0-137">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="bb5b0-138">Практическое руководство. Получение метаданных через привязку, не использующую MEX</span><span class="sxs-lookup"><span data-stu-id="bb5b0-138">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="bb5b0-139">Пользовательская конечная точка защищенных метаданных</span><span class="sxs-lookup"><span data-stu-id="bb5b0-139">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="bb5b0-140">Метаданные</span><span class="sxs-lookup"><span data-stu-id="bb5b0-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bb5b0-141">Привязки</span><span class="sxs-lookup"><span data-stu-id="bb5b0-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bb5b0-142">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="bb5b0-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bb5b0-143">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="bb5b0-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
