---
description: 'Дополнительные сведения: <client>'
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 9765460602738f49963ea521b3f00ed7c63cc568
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638864"
---
# \<client>

<span data-ttu-id="50708-102">Элемент `client` определяет список конечных точек, к которым может подключаться клиент.</span><span class="sxs-lookup"><span data-stu-id="50708-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<client>**

## <a name="syntax"></a><span data-ttu-id="50708-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="50708-103">Syntax</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50708-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="50708-104">Attributes and Elements</span></span>

 <span data-ttu-id="50708-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="50708-105">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="50708-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="50708-106">Attributes</span></span>

 <span data-ttu-id="50708-107">None</span><span class="sxs-lookup"><span data-stu-id="50708-107">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="50708-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="50708-108">Child Elements</span></span>

|<span data-ttu-id="50708-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="50708-109">Element</span></span>|<span data-ttu-id="50708-110">Описание</span><span class="sxs-lookup"><span data-stu-id="50708-110">Description</span></span>|
|-------------|-----------------|
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="50708-111">Содержит коллекцию элементов Endpoint, указывающих конечные точки, к которым может подключаться этот клиент.</span><span class="sxs-lookup"><span data-stu-id="50708-111">Contains a collection of endpoint elements that specify the endpoints that this client can connect to.</span></span>|
|[\<metadata>](metadata.md)|<span data-ttu-id="50708-112">Содержит параметры обработки метаданных.</span><span class="sxs-lookup"><span data-stu-id="50708-112">Contains settings for processing metadata.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="50708-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="50708-113">Parent Elements</span></span>

|<span data-ttu-id="50708-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="50708-114">Element</span></span>|<span data-ttu-id="50708-115">Описание</span><span class="sxs-lookup"><span data-stu-id="50708-115">Description</span></span>|
|-------------|-----------------|
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="50708-116">Корневой элемент всех элементов конфигурации Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="50708-116">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="50708-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="50708-117">Remarks</span></span>

 <span data-ttu-id="50708-118">В разделе `client` определяется список конечных точек, к которым может подключаться клиент.</span><span class="sxs-lookup"><span data-stu-id="50708-118">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="50708-119">Каждая конечная точка, указанная в разделе клиента, определяет свои собственные привязку, поведение и контракт.</span><span class="sxs-lookup"><span data-stu-id="50708-119">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="50708-120">Она однозначно определяется сочетанием атрибутов `name` и `contract`.</span><span class="sxs-lookup"><span data-stu-id="50708-120">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="50708-121">В коде клиента указывается атрибут `name` для подключения к конечной точке службы, выполняемой клиентом.</span><span class="sxs-lookup"><span data-stu-id="50708-121">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="50708-122">Если атрибут `name` отсутствует, конечная точка действует как конечная точка по умолчанию для контракта, который она реализует.</span><span class="sxs-lookup"><span data-stu-id="50708-122">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>

 <span data-ttu-id="50708-123">Кроме того, в данном разделе также задаются параметры обработки метаданных.</span><span class="sxs-lookup"><span data-stu-id="50708-123">In addition, this section also specifies settings for processing metadata.</span></span>

## <a name="example"></a><span data-ttu-id="50708-124">Пример</span><span class="sxs-lookup"><span data-stu-id="50708-124">Example</span></span>

```xml
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```

## <a name="see-also"></a><span data-ttu-id="50708-125">См. также</span><span class="sxs-lookup"><span data-stu-id="50708-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="50708-126">Конфигурация клиента WCF</span><span class="sxs-lookup"><span data-stu-id="50708-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="50708-127">Клиенты</span><span class="sxs-lookup"><span data-stu-id="50708-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
