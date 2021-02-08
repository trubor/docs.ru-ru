---
description: 'Дополнительные сведения: <compositeDuplex>'
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 0a9ec47027618a5f4fb30b627ccb9ad04c547f48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782186"
---
# \<compositeDuplex>

<span data-ttu-id="d8c20-102">Определяет элемент привязки, который используется, когда клиенту необходимо предоставить службе конечную точку для отправки сообщений обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="d8c20-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="d8c20-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8c20-103">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8c20-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d8c20-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d8c20-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d8c20-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8c20-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d8c20-106">Attributes</span></span>  
  
|<span data-ttu-id="d8c20-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="d8c20-107">Attribute</span></span>|<span data-ttu-id="d8c20-108">Описание</span><span class="sxs-lookup"><span data-stu-id="d8c20-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8c20-109">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="d8c20-109">clientBaseAddress</span></span>|<span data-ttu-id="d8c20-110">Универсальный код ресурса (URI), который задает адрес обратного канала при работе в дуплексном режиме.</span><span class="sxs-lookup"><span data-stu-id="d8c20-110">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="d8c20-111">Служба использует данный адрес для осуществления контакта и создания подключения к клиенту.</span><span class="sxs-lookup"><span data-stu-id="d8c20-111">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="d8c20-112">Если этот атрибут не задан, создается адрес по умолчанию `full qualified name+default port\TemporaryIndigoAddress\guid` .</span><span class="sxs-lookup"><span data-stu-id="d8c20-112">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="d8c20-113">Значение по умолчанию — `null`.</span><span class="sxs-lookup"><span data-stu-id="d8c20-113">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8c20-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d8c20-114">Child Elements</span></span>  

 <span data-ttu-id="d8c20-115">None</span><span class="sxs-lookup"><span data-stu-id="d8c20-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8c20-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d8c20-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d8c20-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="d8c20-117">Element</span></span>|<span data-ttu-id="d8c20-118">Описание</span><span class="sxs-lookup"><span data-stu-id="d8c20-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d8c20-119">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="d8c20-119">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8c20-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8c20-120">Remarks</span></span>  

 <span data-ttu-id="d8c20-121">Данный элемент конфигурации используется с теми типами транспорта, которые не имеют встроенной поддержки дуплексной связи, например HTTP.</span><span class="sxs-lookup"><span data-stu-id="d8c20-121">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="d8c20-122">Напротив, протокол TCP имеет встроенную поддержку дуплексной связи, и для него не требуется использовать этот элемент привязки для службы при отправке сообщений обратно клиенту.</span><span class="sxs-lookup"><span data-stu-id="d8c20-122">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="d8c20-123">Для осуществления контакта и установления подключения клиент должен предоставить службе адрес.</span><span class="sxs-lookup"><span data-stu-id="d8c20-123">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="d8c20-124">Этот адрес клиента предоставляется атрибутом `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="d8c20-124">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="d8c20-125">Обратите внимание, что Windows Communication Foundation (WCF) автоматически создает атрибут ClientBaseAddress в том случае, если он не был явно задан пользователем.</span><span class="sxs-lookup"><span data-stu-id="d8c20-125">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8c20-126">Пример</span><span class="sxs-lookup"><span data-stu-id="d8c20-126">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d8c20-127">См. также</span><span class="sxs-lookup"><span data-stu-id="d8c20-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d8c20-128">Привязки</span><span class="sxs-lookup"><span data-stu-id="d8c20-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d8c20-129">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="d8c20-129">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d8c20-130">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="d8c20-130">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
