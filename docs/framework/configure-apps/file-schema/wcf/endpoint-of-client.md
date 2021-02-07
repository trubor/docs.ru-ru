---
description: 'Дополнительные сведения <endpoint> о: <client>'
title: <endpoint> из <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: 4ace6d49ba18524729925b20cf08e5d57bcc40c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725785"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="a36d4-103">\<endpoint> из \<client></span><span class="sxs-lookup"><span data-stu-id="a36d4-103">\<endpoint> of \<client></span></span>

<span data-ttu-id="a36d4-104">Задает свойства контракта, привязки и адреса конечной точки канала, которая используется клиентами для подключения к конечным точкам службы на сервере.</span><span class="sxs-lookup"><span data-stu-id="a36d4-104">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="a36d4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a36d4-105">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a36d4-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a36d4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a36d4-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a36d4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a36d4-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a36d4-108">Attributes</span></span>  
  
|<span data-ttu-id="a36d4-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a36d4-109">Attribute</span></span>|<span data-ttu-id="a36d4-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a36d4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a36d4-111">address</span><span class="sxs-lookup"><span data-stu-id="a36d4-111">address</span></span>|<span data-ttu-id="a36d4-112">Обязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="a36d4-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="a36d4-113">Задает адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-113">Specifies the address of the endpoint.</span></span> <span data-ttu-id="a36d4-114">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="a36d4-114">The default is an empty string.</span></span> <span data-ttu-id="a36d4-115">Адрес должен быть абсолютным универсальным кодом ресурса (URI).</span><span class="sxs-lookup"><span data-stu-id="a36d4-115">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="a36d4-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a36d4-116">behaviorConfiguration</span></span>|<span data-ttu-id="a36d4-117">Строка, содержащая имя поведения, используемое для создания экземпляра конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-117">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="a36d4-118">Имя поведения должно входить в область действия в точке определения службы.</span><span class="sxs-lookup"><span data-stu-id="a36d4-118">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="a36d4-119">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="a36d4-119">The default is an empty string.</span></span>|  
|<span data-ttu-id="a36d4-120">binding</span><span class="sxs-lookup"><span data-stu-id="a36d4-120">binding</span></span>|<span data-ttu-id="a36d4-121">Обязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="a36d4-121">Required string attribute.</span></span><br /><br /> <span data-ttu-id="a36d4-122">Строка, указывающая тип привязки для использования.</span><span class="sxs-lookup"><span data-stu-id="a36d4-122">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="a36d4-123">Чтобы на тип можно было ссылаться, он должен иметь зарегистрированный раздел конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a36d4-123">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="a36d4-124">Тип регистрируется по имени раздела, а не по имени типа привязки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-124">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="a36d4-125">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="a36d4-125">bindingConfiguration</span></span>|<span data-ttu-id="a36d4-126">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a36d4-126">Optional.</span></span> <span data-ttu-id="a36d4-127">Строка, содержащая имя конфигурации привязки для использования при создании экземпляра конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-127">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="a36d4-128">Конфигурация привязки должна входить в область действия в точке определения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-128">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="a36d4-129">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="a36d4-129">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a36d4-130">Этот атрибут используется вместе с атрибутом `binding` для ссылки на конкретную конфигурацию привязки в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a36d4-130">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="a36d4-131">Задайте этот атрибут, если выполняется попытка использовать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="a36d4-131">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="a36d4-132">В противном случае может быть создано исключение.</span><span class="sxs-lookup"><span data-stu-id="a36d4-132">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="a36d4-133">contract</span><span class="sxs-lookup"><span data-stu-id="a36d4-133">contract</span></span>|<span data-ttu-id="a36d4-134">Обязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="a36d4-134">Required string attribute.</span></span><br /><br /> <span data-ttu-id="a36d4-135">Строка, указывающая, к какому контракту предоставляется доступ этой конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="a36d4-135">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="a36d4-136">В сборке должен быть реализован данный тип контракта.</span><span class="sxs-lookup"><span data-stu-id="a36d4-136">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="a36d4-137">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="a36d4-137">endpointConfiguration</span></span>|<span data-ttu-id="a36d4-138">Строка, указывающая имя стандартной конечной точки, задаваемой атрибутом `kind`, который ссылается на дополнительные сведения конфигурации этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-138">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="a36d4-139">Такое же имя должно быть задано в разделе `<standardEndpoints>`.</span><span class="sxs-lookup"><span data-stu-id="a36d4-139">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="a36d4-140">kind</span><span class="sxs-lookup"><span data-stu-id="a36d4-140">kind</span></span>|<span data-ttu-id="a36d4-141">Строка, указывающая тип применяемой стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="a36d4-141">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="a36d4-142">Тип должен быть зарегистрирован в разделе `<extensions>` или в файле machine.config. Если ничего не указано, создается общая конечная точка канала.</span><span class="sxs-lookup"><span data-stu-id="a36d4-142">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="a36d4-143">name</span><span class="sxs-lookup"><span data-stu-id="a36d4-143">name</span></span>|<span data-ttu-id="a36d4-144">Необязательный строковый атрибут.</span><span class="sxs-lookup"><span data-stu-id="a36d4-144">Optional string attribute.</span></span> <span data-ttu-id="a36d4-145">Этот атрибут уникальным образом идентифицирует конечную точку для данного контракта.</span><span class="sxs-lookup"><span data-stu-id="a36d4-145">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="a36d4-146">Для данного типа контракта можно определить несколько клиентов.</span><span class="sxs-lookup"><span data-stu-id="a36d4-146">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="a36d4-147">Определения должны отличаться друг от друга уникальным именем конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a36d4-147">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="a36d4-148">Если этот атрибут опущен, соответствующая конечная точка используется как конечная точка по умолчанию, связанная с заданным типом контракта.</span><span class="sxs-lookup"><span data-stu-id="a36d4-148">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="a36d4-149">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="a36d4-149">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="a36d4-150">Атрибут `name` привязки используется для экспорта определения посредством языка WSDL.</span><span class="sxs-lookup"><span data-stu-id="a36d4-150">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a36d4-151">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a36d4-151">Child Elements</span></span>  
  
|<span data-ttu-id="a36d4-152">Элемент</span><span class="sxs-lookup"><span data-stu-id="a36d4-152">Element</span></span>|<span data-ttu-id="a36d4-153">Описание</span><span class="sxs-lookup"><span data-stu-id="a36d4-153">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="a36d4-154">Коллекция заголовков адреса.</span><span class="sxs-lookup"><span data-stu-id="a36d4-154">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="a36d4-155">Удостоверение, обеспечивающее проверку подлинности конечной точки другими конечными точками, которые обмениваются с ней сообщениями.</span><span class="sxs-lookup"><span data-stu-id="a36d4-155">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a36d4-156">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a36d4-156">Parent Elements</span></span>  
  
|<span data-ttu-id="a36d4-157">Элемент</span><span class="sxs-lookup"><span data-stu-id="a36d4-157">Element</span></span>|<span data-ttu-id="a36d4-158">Описание</span><span class="sxs-lookup"><span data-stu-id="a36d4-158">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="a36d4-159">Раздел конфигурации, определяющий список конечных точек, к которым может подключаться клиент.</span><span class="sxs-lookup"><span data-stu-id="a36d4-159">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a36d4-160">Пример</span><span class="sxs-lookup"><span data-stu-id="a36d4-160">Example</span></span>  

 <span data-ttu-id="a36d4-161">Далее приведен пример конфигурации конечной точки канала.</span><span class="sxs-lookup"><span data-stu-id="a36d4-161">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="a36d4-162">См. также</span><span class="sxs-lookup"><span data-stu-id="a36d4-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="a36d4-163">Конфигурация клиента WCF</span><span class="sxs-lookup"><span data-stu-id="a36d4-163">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="a36d4-164">Клиенты</span><span class="sxs-lookup"><span data-stu-id="a36d4-164">Clients</span></span>](../../../wcf/feature-details/clients.md)
