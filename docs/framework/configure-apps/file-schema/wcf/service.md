---
description: 'Дополнительные сведения: <service>'
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c3870a170847d773996625235c75591ced75e315
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786789"
---
# \<service>

<span data-ttu-id="a659a-102">Элемент `service` содержит параметры для службы Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a659a-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="a659a-103">Он также содержит конечные точки, предоставляющие доступ к службе.</span><span class="sxs-lookup"><span data-stu-id="a659a-103">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="a659a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a659a-104">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a659a-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a659a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="a659a-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a659a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a659a-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a659a-107">Attributes</span></span>  
  
|<span data-ttu-id="a659a-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a659a-108">Attribute</span></span>|<span data-ttu-id="a659a-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a659a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a659a-110">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="a659a-110">behaviorConfiguration</span></span>|<span data-ttu-id="a659a-111">Строка, содержащая имя поведения, которое следует использовать для создания экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="a659a-111">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="a659a-112">Имя поведения должно входить в область действия в точке определения службы.</span><span class="sxs-lookup"><span data-stu-id="a659a-112">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="a659a-113">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="a659a-113">The default value is an empty string.</span></span>|  
|<span data-ttu-id="a659a-114">name</span><span class="sxs-lookup"><span data-stu-id="a659a-114">name</span></span>|<span data-ttu-id="a659a-115">Требуемый строковый атрибут, указывающий тип службы, экземпляр которой создается.</span><span class="sxs-lookup"><span data-stu-id="a659a-115">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="a659a-116">Этот параметр должен иметь значение допустимого типа.</span><span class="sxs-lookup"><span data-stu-id="a659a-116">This setting must equate to a valid type.</span></span> <span data-ttu-id="a659a-117">Формат должен быть `Namespace.Class.`.</span><span class="sxs-lookup"><span data-stu-id="a659a-117">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a659a-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a659a-118">Child Elements</span></span>  
  
|<span data-ttu-id="a659a-119">Элемент</span><span class="sxs-lookup"><span data-stu-id="a659a-119">Element</span></span>|<span data-ttu-id="a659a-120">Описание</span><span class="sxs-lookup"><span data-stu-id="a659a-120">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="a659a-121">Коллекция элементов `endpoint`, которые обеспечивают доступ к данной службе.</span><span class="sxs-lookup"><span data-stu-id="a659a-121">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="a659a-122">Задает узел данного экземпляра службы.</span><span class="sxs-lookup"><span data-stu-id="a659a-122">Specifies the host of this service instance.</span></span> <span data-ttu-id="a659a-123">Это элемент типа <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="a659a-123">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a659a-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a659a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a659a-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="a659a-125">Element</span></span>|<span data-ttu-id="a659a-126">Описание</span><span class="sxs-lookup"><span data-stu-id="a659a-126">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="a659a-127">Корневой элемент всех элементов конфигурации WCF.</span><span class="sxs-lookup"><span data-stu-id="a659a-127">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a659a-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="a659a-128">Remarks</span></span>  

 <span data-ttu-id="a659a-129">Службы задаются в разделе `services` файла конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a659a-129">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="a659a-130">Сборка может содержать любое число служб.</span><span class="sxs-lookup"><span data-stu-id="a659a-130">An assembly can contain any number of services.</span></span> <span data-ttu-id="a659a-131">Для каждой службы используется собственный раздел конфигурации `service`.</span><span class="sxs-lookup"><span data-stu-id="a659a-131">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="a659a-132">В этом разделе определяются контракт, поведение и конечные точки конкретной службы.</span><span class="sxs-lookup"><span data-stu-id="a659a-132">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="a659a-133">Элемент `behaviorConfiguration` также является необязательным.</span><span class="sxs-lookup"><span data-stu-id="a659a-133">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="a659a-134">Он указывает поведение, используемое службой.</span><span class="sxs-lookup"><span data-stu-id="a659a-134">It identifies the behavior the service uses.</span></span> <span data-ttu-id="a659a-135">Поведение, заданное в данном атрибуте, должно быть связано с поведением в области в том же файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="a659a-135">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="a659a-136">Каждая служба предоставляет доступ к одной или нескольким конечным точкам, которые имеют собственные адреса и привязки.</span><span class="sxs-lookup"><span data-stu-id="a659a-136">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="a659a-137">Все привязки в файле конфигурации должны быть определены в области файла.</span><span class="sxs-lookup"><span data-stu-id="a659a-137">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="a659a-138">Привязки связаны с конечными точками с помощью сочетания атрибутов `name` и `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a659a-138">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="a659a-139">Атрибут `name` описывает раздел, в котором определена привязка.</span><span class="sxs-lookup"><span data-stu-id="a659a-139">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="a659a-140">Атрибут `bindingConfiguration` указывает, какая конфигурация из раздела привязок используется.</span><span class="sxs-lookup"><span data-stu-id="a659a-140">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="a659a-141">В разделе привязки может определяться несколько конфигураций.</span><span class="sxs-lookup"><span data-stu-id="a659a-141">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a659a-142">Пример</span><span class="sxs-lookup"><span data-stu-id="a659a-142">Example</span></span>  

 <span data-ttu-id="a659a-143">Ниже приведен пример конфигурации службы.</span><span class="sxs-lookup"><span data-stu-id="a659a-143">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="a659a-144">См. также</span><span class="sxs-lookup"><span data-stu-id="a659a-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="a659a-145">Настройка служб</span><span class="sxs-lookup"><span data-stu-id="a659a-145">Configuring Services</span></span>](../../../wcf/configuring-services.md)
