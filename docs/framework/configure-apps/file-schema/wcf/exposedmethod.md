---
description: 'Дополнительные сведения: <exposedMethod>'
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 7bf271ba03ee16c6a45726e2bcb522bf6f55d441
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664734"
---
# \<exposedMethod>

<span data-ttu-id="d968c-102">Представляет метод COM+, предоставляемый, когда интерфейс компонента COM+ предоставляется как веб-служба.</span><span class="sxs-lookup"><span data-stu-id="d968c-102">Represents a COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a><span data-ttu-id="d968c-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d968c-103">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d968c-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d968c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d968c-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d968c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d968c-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d968c-106">Attributes</span></span>  
  
|<span data-ttu-id="d968c-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d968c-107">Attribute</span></span>|<span data-ttu-id="d968c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d968c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d968c-109">name</span><span class="sxs-lookup"><span data-stu-id="d968c-109">name</span></span>|<span data-ttu-id="d968c-110">Строка, которая содержит метод COM+, предоставляемый, когда интерфейс компонента COM+ предоставляется как веб-служба.</span><span class="sxs-lookup"><span data-stu-id="d968c-110">A string that contains the COM+ method that is exposed when the interface on a COM+ component is exposed as a Web service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d968c-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d968c-111">Child Elements</span></span>  

 <span data-ttu-id="d968c-112">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d968c-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d968c-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d968c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d968c-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="d968c-114">Element</span></span>|<span data-ttu-id="d968c-115">Описание</span><span class="sxs-lookup"><span data-stu-id="d968c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|<span data-ttu-id="d968c-116">Коллекция [\<exposedMethod>](exposedmethod.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="d968c-116">A collection of [\<exposedMethod>](exposedmethod.md) elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d968c-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="d968c-117">Remarks</span></span>  

 <span data-ttu-id="d968c-118">Средство конфигурации интеграции COM+ (ComSvcConfig.exe) может применяться для добавления определенных методов COM-интерфейса для использования в созданном контракте службы.</span><span class="sxs-lookup"><span data-stu-id="d968c-118">The COM+ integration configuration tool (ComSvcConfig.exe) can be used to add specific methods from a COM interface to appear on the generated service contract.</span></span>  
  
 <span data-ttu-id="d968c-119">Например, для добавления в созданный контракт службы трех именованных методов из COM-интерфейса `IFinances` компонента `ItemOrders`.Financial можно использовать приведенную ниже команду.</span><span class="sxs-lookup"><span data-stu-id="d968c-119">For example, you can use the following command to add the three named methods from the `IFinances` COM interface on the `ItemOrders`.Financial component, to the generated service contract.</span></span>  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 <span data-ttu-id="d968c-120">При запуске ComSvcConfig.exe также создается следующий контракт службы, в котором перечислены упомянутые выше методы как [\<exposedMethod>](exposedmethod.md) элементы.</span><span class="sxs-lookup"><span data-stu-id="d968c-120">When you also run the ComSvcConfig.exe, it then generates the following service contract listing the previously mentioned methods as [\<exposedMethod>](exposedmethod.md) elements.</span></span>  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 <span data-ttu-id="d968c-121">Во время инициализации службы среда выполнения пытается создать контракт службы, отражая и добавляя только методы, входящие в список [\<exposedMethod>](exposedmethod.md) элементов.</span><span class="sxs-lookup"><span data-stu-id="d968c-121">At service initialization time, the runtime attempts to generate a service contract by reflecting over and adding only the methods included in the list of [\<exposedMethod>](exposedmethod.md) elements.</span></span> <span data-ttu-id="d968c-122">Для каждого метода интерфейса, который не включен в контракт службы, создается трассировка.</span><span class="sxs-lookup"><span data-stu-id="d968c-122">A trace is produced for every interface method that is not included on the service contract.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d968c-123">См. также</span><span class="sxs-lookup"><span data-stu-id="d968c-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="d968c-124">Интеграция с приложениями COM+</span><span class="sxs-lookup"><span data-stu-id="d968c-124">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="d968c-125">Практическое руководство. Настройка параметров службы COM+</span><span class="sxs-lookup"><span data-stu-id="d968c-125">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
