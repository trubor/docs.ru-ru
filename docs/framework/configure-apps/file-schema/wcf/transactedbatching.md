---
description: 'Дополнительные сведения: <transactedBatching>'
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 9a57226c3a2f2b026c69324e37b00e87fd3dd693
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773697"
---
# \<transactedBatching>

<span data-ttu-id="c9d0c-102">Указывает, поддерживается ли объединение транзакций для операций получения.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-102">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="c9d0c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c9d0c-103">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9d0c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c9d0c-104">Attributes and Elements</span></span>

<span data-ttu-id="c9d0c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9d0c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c9d0c-106">Attributes</span></span>

|<span data-ttu-id="c9d0c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c9d0c-107">Attribute</span></span>|<span data-ttu-id="c9d0c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c9d0c-108">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="c9d0c-109">Целое число, указывающее максимальное число операций получения, которые могут быть объединены в одну транзакцию.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-109">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="c9d0c-110">Значение по умолчанию — 0.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-110">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c9d0c-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c9d0c-111">Child Elements</span></span>

<span data-ttu-id="c9d0c-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9d0c-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c9d0c-113">Parent Elements</span></span>

|<span data-ttu-id="c9d0c-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="c9d0c-114">Element</span></span>|<span data-ttu-id="c9d0c-115">Описание</span><span class="sxs-lookup"><span data-stu-id="c9d0c-115">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c9d0c-116">Задает поведение конечной точки.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-116">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c9d0c-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="c9d0c-117">Remarks</span></span>

<span data-ttu-id="c9d0c-118">Транзакция, настроенная на попытки объединения в один пакет нескольких операций получения.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-118">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="c9d0c-119">Это позволяет избежать относительно высоких затрат ресурсов на создание и отправку транзакции для каждой операции получения.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-119">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="c9d0c-120">Пример</span><span class="sxs-lookup"><span data-stu-id="c9d0c-120">Example</span></span>

<span data-ttu-id="c9d0c-121">В следующем примере показано, как добавить поведение объединения транзакций для службы в файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c9d0c-121">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a><span data-ttu-id="c9d0c-122">См. также</span><span class="sxs-lookup"><span data-stu-id="c9d0c-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
