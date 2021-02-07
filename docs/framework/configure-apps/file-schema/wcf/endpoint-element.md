---
description: 'Дополнительные сведения о: <endpoint> element'
title: <endpoint> - элемент
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: d5555ae895e6655d1ce6e3dcb026ddec3ff8cf44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725809"
---
# <a name="endpoint-element"></a><span data-ttu-id="fa8f4-103">Элемент \<endpoint></span><span class="sxs-lookup"><span data-stu-id="fa8f4-103">\<endpoint> element</span></span>

<span data-ttu-id="fa8f4-104">Задает свойства привязки, контракта и адреса для конечной точки службы, которая используется для предоставления доступа к службам.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-104">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="fa8f4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa8f4-105">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa8f4-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fa8f4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fa8f4-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa8f4-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fa8f4-108">Attributes</span></span>  
  
|<span data-ttu-id="fa8f4-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fa8f4-109">Attribute</span></span>|<span data-ttu-id="fa8f4-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fa8f4-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa8f4-111">address</span><span class="sxs-lookup"><span data-stu-id="fa8f4-111">address</span></span>|<span data-ttu-id="fa8f4-112">Строка, содержащая адрес конечной точки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-112">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="fa8f4-113">Адрес может быть указан как абсолютный или относительный адрес.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-113">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="fa8f4-114">Если указан относительный адрес, от соответствующего узла ожидается предоставление базового адреса, подходящего для схемы транспорта, используемой в привязке.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-114">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="fa8f4-115">Если адрес не настроен, в качестве базового адреса используется адрес соответствующей конечной точки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-115">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="fa8f4-116">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-116">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa8f4-117">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa8f4-117">behaviorConfiguration</span></span>|<span data-ttu-id="fa8f4-118">Строка, содержащая имя поведения для использования в конечной точке.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-118">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="fa8f4-119">binding</span><span class="sxs-lookup"><span data-stu-id="fa8f4-119">binding</span></span>|<span data-ttu-id="fa8f4-120">Требуемый строковый атрибут, указывающий тип используемой привязки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-120">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="fa8f4-121">Чтобы на тип можно было ссылаться, он должен иметь зарегистрированный раздел конфигурации.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-121">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="fa8f4-122">Тип регистрируется по имени раздела, а не по имени типа привязки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-122">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="fa8f4-123">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa8f4-123">bindingConfiguration</span></span>|<span data-ttu-id="fa8f4-124">Строка, указывающая имя привязки для использования при создании экземпляра конечной точки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-124">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="fa8f4-125">Имя привязки должно входить в область в точке определения конечной точки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-125">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="fa8f4-126">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-126">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="fa8f4-127">Этот атрибут используется вместе с атрибутом `binding` для ссылки на конкретную конфигурацию привязки в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-127">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="fa8f4-128">Задайте этот атрибут, если выполняется попытка использовать пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-128">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="fa8f4-129">В противном случае может быть создано исключение.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-129">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="fa8f4-130">bindingName</span><span class="sxs-lookup"><span data-stu-id="fa8f4-130">bindingName</span></span>|<span data-ttu-id="fa8f4-131">Строка, указывающая уникальное полное имя привязки для экспорта определения посредством WSDL.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-131">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="fa8f4-132">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa8f4-133">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="fa8f4-133">bindingNamespace</span></span>|<span data-ttu-id="fa8f4-134">Строка, указывающая уникальное полное имя пространства имен привязки для экспорта определения посредством WSDL.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-134">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="fa8f4-135">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-135">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa8f4-136">contract</span><span class="sxs-lookup"><span data-stu-id="fa8f4-136">contract</span></span>|<span data-ttu-id="fa8f4-137">Строка, указывающая, к какому контракту предоставляется доступ этой конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="fa8f4-138">В сборке должен быть реализован данный тип контракта.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-138">The assembly must implement the contract type.</span></span> <span data-ttu-id="fa8f4-139">Если реализация службы реализует один тип контракта, это свойство может быть опущено.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-139">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="fa8f4-140">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-140">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa8f4-141">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="fa8f4-141">endpointConfiguration</span></span>|<span data-ttu-id="fa8f4-142">Строка, указывающая имя стандартной конечной точки, задаваемой атрибутом `kind`, который ссылается на дополнительные сведения конфигурации этой конечной точки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-142">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="fa8f4-143">Такое же имя должно быть задано в разделе `<standardEndpoints>`.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-143">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="fa8f4-144">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="fa8f4-144">isSystemEndpoint</span></span>|<span data-ttu-id="fa8f4-145">Логическое значение, указывающее, является ли конечная точка конечной точкой инфраструктуры.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-145">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="fa8f4-146">kind</span><span class="sxs-lookup"><span data-stu-id="fa8f4-146">kind</span></span>|<span data-ttu-id="fa8f4-147">Строка, указывающая тип применяемой стандартной конечной точки.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-147">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="fa8f4-148">Тип должен быть зарегистрирован в разделе `<extensions>` или файле machine.config. Если ничего не указано, создается общая конечная точка службы.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-148">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="fa8f4-149">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="fa8f4-149">listenUriMode</span></span>|<span data-ttu-id="fa8f4-150">Указывает способ обработки транспортом значения `ListenUri`, предоставленного для ожидания передачи данных службой.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-150">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="fa8f4-151">Допустимы следующие значения:</span><span class="sxs-lookup"><span data-stu-id="fa8f4-151">Valid values are</span></span><br /><br /> <span data-ttu-id="fa8f4-152">-Explicit</span><span class="sxs-lookup"><span data-stu-id="fa8f4-152">-   Explicit</span></span><br /><span data-ttu-id="fa8f4-153">— Уникальный</span><span class="sxs-lookup"><span data-stu-id="fa8f4-153">-   Unique</span></span><br /><br /> <span data-ttu-id="fa8f4-154">Значение по умолчанию - Explicit.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-154">The default value is Explicit.</span></span>|  
|<span data-ttu-id="fa8f4-155">listenUri</span><span class="sxs-lookup"><span data-stu-id="fa8f4-155">listenUri</span></span>|<span data-ttu-id="fa8f4-156">Строка, указывающая URI, по которому конечная точка службы ожидает передачи данных.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-156">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="fa8f4-157">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-157">The default is an empty string.</span></span>|  
|<span data-ttu-id="fa8f4-158">name</span><span class="sxs-lookup"><span data-stu-id="fa8f4-158">name</span></span>|<span data-ttu-id="fa8f4-159">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-159">Optional attribute.</span></span> <span data-ttu-id="fa8f4-160">Строка, указывающая имя конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-160">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="fa8f4-161">По умолчанию используется объединение имени привязки и имя описания контракта.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-161">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="fa8f4-162">Службы могут иметь несколько конечных точек, поэтому атрибут конечной точки `name` отличается от имени службы.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-162">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa8f4-163">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fa8f4-163">Child Elements</span></span>  
  
|<span data-ttu-id="fa8f4-164">Элемент</span><span class="sxs-lookup"><span data-stu-id="fa8f4-164">Element</span></span>|<span data-ttu-id="fa8f4-165">Описание</span><span class="sxs-lookup"><span data-stu-id="fa8f4-165">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="fa8f4-166">Коллекция заголовков адреса.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-166">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="fa8f4-167">Удостоверение, обеспечивающее проверку подлинности конечной точки другими конечными точками, которые обмениваются с ней сообщениями.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-167">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa8f4-168">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fa8f4-168">Parent Elements</span></span>  
  
|<span data-ttu-id="fa8f4-169">Элемент</span><span class="sxs-lookup"><span data-stu-id="fa8f4-169">Element</span></span>|<span data-ttu-id="fa8f4-170">Описание</span><span class="sxs-lookup"><span data-stu-id="fa8f4-170">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="fa8f4-171">Раздел конфигурации, определяющий список конечных точек, к которым может подключаться клиент.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-171">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa8f4-172">Пример</span><span class="sxs-lookup"><span data-stu-id="fa8f4-172">Example</span></span>  

 <span data-ttu-id="fa8f4-173">Ниже приведен пример конфигурации конечной точки службы.</span><span class="sxs-lookup"><span data-stu-id="fa8f4-173">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="fa8f4-174">См. также</span><span class="sxs-lookup"><span data-stu-id="fa8f4-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="fa8f4-175">Конечные точки: адреса, привязки и контракты</span><span class="sxs-lookup"><span data-stu-id="fa8f4-175">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="fa8f4-176">Практическое руководство. Создание конечной точки службы в конфигурации</span><span class="sxs-lookup"><span data-stu-id="fa8f4-176">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
