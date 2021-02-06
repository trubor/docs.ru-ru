---
description: 'Дополнительные сведения: <comContract>'
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: fde1188a087f13da6629460bcebcea16ceefc0e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638669"
---
# \<comContract>

<span data-ttu-id="5d883-102">Указывает контракт службы интеграции COM+.</span><span class="sxs-lookup"><span data-stu-id="5d883-102">Specifies a COM+ integration service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a><span data-ttu-id="5d883-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5d883-103">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d883-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5d883-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5d883-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5d883-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d883-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5d883-106">Attributes</span></span>  
  
|<span data-ttu-id="5d883-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5d883-107">Attribute</span></span>|<span data-ttu-id="5d883-108">Описание</span><span class="sxs-lookup"><span data-stu-id="5d883-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5d883-109">contract</span><span class="sxs-lookup"><span data-stu-id="5d883-109">contract</span></span>|<span data-ttu-id="5d883-110">Строка, содержащая тип контракта.</span><span class="sxs-lookup"><span data-stu-id="5d883-110">A string that contains the contract type.</span></span>|  
|<span data-ttu-id="5d883-111">name</span><span class="sxs-lookup"><span data-stu-id="5d883-111">name</span></span>|<span data-ttu-id="5d883-112">Строка, содержащая имя контракта.</span><span class="sxs-lookup"><span data-stu-id="5d883-112">A string that contains the contract name.</span></span>|  
|<span data-ttu-id="5d883-113">пространство имен</span><span class="sxs-lookup"><span data-stu-id="5d883-113">namespace</span></span>|<span data-ttu-id="5d883-114">Строка, содержащая пространство имен контракта.</span><span class="sxs-lookup"><span data-stu-id="5d883-114">A string that contains the contract namespace.</span></span>|  
|<span data-ttu-id="5d883-115">requiresSession</span><span class="sxs-lookup"><span data-stu-id="5d883-115">requiresSession</span></span>|<span data-ttu-id="5d883-116">Логическое значение, указывающее, ограничено ли использование контракта только сеансовыми привязками.</span><span class="sxs-lookup"><span data-stu-id="5d883-116">A Boolean value that specifies whether the contract can only be used on sessionful bindings.</span></span> <span data-ttu-id="5d883-117">При инициализации службы среда выполнения интеграции обеспечивает согласованность этого параметра с типом используемой привязки.</span><span class="sxs-lookup"><span data-stu-id="5d883-117">When the service is initialized, the integration runtime ensures that this setting is consistent with the type of binding to be used.</span></span> <span data-ttu-id="5d883-118">В случае конфликта одной или нескольких привязок для контракта создается исключение.</span><span class="sxs-lookup"><span data-stu-id="5d883-118">An exception is generated if one or more of the bindings for the contract are in conflict.</span></span> <span data-ttu-id="5d883-119">Если это свойство имеет значение `false`, то при использовании одностороннего канала и наличии параметров [out] также создается исключение.</span><span class="sxs-lookup"><span data-stu-id="5d883-119">If this property is `false`, and a one-way channel is in use and there are any [out] parameters, an exception is also generated.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d883-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5d883-120">Child Elements</span></span>  
  
|<span data-ttu-id="5d883-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="5d883-121">Element</span></span>|<span data-ttu-id="5d883-122">Описание</span><span class="sxs-lookup"><span data-stu-id="5d883-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d883-123">persistableTypes</span><span class="sxs-lookup"><span data-stu-id="5d883-123">persistableTypes</span></span>|<span data-ttu-id="5d883-124">Все сохраняемые типы.</span><span class="sxs-lookup"><span data-stu-id="5d883-124">All the persistable types.</span></span>|  
|<span data-ttu-id="5d883-125">userDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="5d883-125">userDefinedTypes</span></span>|<span data-ttu-id="5d883-126">Коллекция пользовательских типов (UDT), подлежащая включению в контракт службы.</span><span class="sxs-lookup"><span data-stu-id="5d883-126">A collection of User Defined Types (UDT) that is to be included in the service contract.</span></span>|  
|<span data-ttu-id="5d883-127">exposedMethods</span><span class="sxs-lookup"><span data-stu-id="5d883-127">exposedMethods</span></span>|<span data-ttu-id="5d883-128">Коллекция методов COM+, которые предоставляются при предоставлении интерфейса компонента COM+ как веб-службы.</span><span class="sxs-lookup"><span data-stu-id="5d883-128">A collection of COM+ methods that are exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d883-129">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5d883-129">Parent Elements</span></span>  
  
|<span data-ttu-id="5d883-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="5d883-130">Element</span></span>|<span data-ttu-id="5d883-131">Описание</span><span class="sxs-lookup"><span data-stu-id="5d883-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5d883-132">comContracts</span><span class="sxs-lookup"><span data-stu-id="5d883-132">comContracts</span></span>|<span data-ttu-id="5d883-133">Содержит коллекцию элементов `comContract`.</span><span class="sxs-lookup"><span data-stu-id="5d883-133">Contains a collection of `comContract` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d883-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="5d883-134">Remarks</span></span>  

 <span data-ttu-id="5d883-135">Контракты службы интеграции COM+ в настоящее время ограничены `http://tempuri.org` пространством имен, а имя контракта является производным от поддерживающего COM-интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5d883-135">COM+ integration service contracts are currently restricted to the `http://tempuri.org` namespace, and contract name is derived from the supporting COM interface.</span></span> <span data-ttu-id="5d883-136">Однако можно указать альтернативы, используя раздел `comContracts`, а также элемент `comContract` в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="5d883-136">You can, however, specify alternatives by using the `comContracts` section, as well as the `comContract` element in the configuration file.</span></span> <span data-ttu-id="5d883-137">Например, для указания пространства имен, имени контракта и подлежащих включению пользовательских типов, а также других параметров контракта службы можно использовать следующую конфигурацию.</span><span class="sxs-lookup"><span data-stu-id="5d883-137">For example, you can use the following configuration to specify the namespace, contract name, and user defined types to be included, as well as other settings for a service contract.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="5d883-138">После инициализации службы указанные пространства имен и имена контрактов применяются к созданным описаниям служб.</span><span class="sxs-lookup"><span data-stu-id="5d883-138">When the service is initialized, the specified namespaces and contract names are applied to the generated service descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d883-139">См. также</span><span class="sxs-lookup"><span data-stu-id="5d883-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="5d883-140">Интеграция с приложениями COM+</span><span class="sxs-lookup"><span data-stu-id="5d883-140">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5d883-141">Практическое руководство. Настройка параметров службы COM+</span><span class="sxs-lookup"><span data-stu-id="5d883-141">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
