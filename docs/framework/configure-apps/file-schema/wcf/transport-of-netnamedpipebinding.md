---
description: 'Дополнительные сведения <transport> о: <netNamedPipeBinding>'
title: <transport> из <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a54c429bcac192ddc46df7232c33ab98bd1a4c58
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773489"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="a97b3-103">\<transport> из \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a97b3-103">\<transport> of \<netNamedPipeBinding></span></span>

<span data-ttu-id="a97b3-104">Определяет параметры безопасности транспорта для именованного канала.</span><span class="sxs-lookup"><span data-stu-id="a97b3-104">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="a97b3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a97b3-105">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a97b3-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a97b3-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a97b3-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a97b3-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a97b3-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a97b3-108">Attributes</span></span>  
  
|<span data-ttu-id="a97b3-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a97b3-109">Attribute</span></span>|<span data-ttu-id="a97b3-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a97b3-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a97b3-111">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a97b3-111">protectionLevel</span></span>|<span data-ttu-id="a97b3-112">Определяет уровень защиты именованного канала.</span><span class="sxs-lookup"><span data-stu-id="a97b3-112">Defines protection level of the named pipe.</span></span> <span data-ttu-id="a97b3-113">Подпись сообщений уменьшает риск подделки сообщения сторонними лицами при его передаче.</span><span class="sxs-lookup"><span data-stu-id="a97b3-113">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a97b3-114">Шифрование обеспечивает конфиденциальность на уровне данных во время транспортировки.</span><span class="sxs-lookup"><span data-stu-id="a97b3-114">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a97b3-115">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="a97b3-115">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a97b3-116">-None: защита отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a97b3-116">-   None: No protection.</span></span><br /><span data-ttu-id="a97b3-117">-Sign: сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="a97b3-117">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a97b3-118">-EncryptAndSign: сообщения шифруются и подписываются.</span><span class="sxs-lookup"><span data-stu-id="a97b3-118">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="a97b3-119">Значение по умолчанию - EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="a97b3-119">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a97b3-120">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a97b3-120">Child Elements</span></span>  

 <span data-ttu-id="a97b3-121">None</span><span class="sxs-lookup"><span data-stu-id="a97b3-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a97b3-122">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a97b3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a97b3-123">Элемент</span><span class="sxs-lookup"><span data-stu-id="a97b3-123">Element</span></span>|<span data-ttu-id="a97b3-124">Описание</span><span class="sxs-lookup"><span data-stu-id="a97b3-124">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="a97b3-125">Определяет параметры безопасности для привязки.</span><span class="sxs-lookup"><span data-stu-id="a97b3-125">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a97b3-126">См. также</span><span class="sxs-lookup"><span data-stu-id="a97b3-126">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="a97b3-127">Защита служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="a97b3-127">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a97b3-128">Привязки</span><span class="sxs-lookup"><span data-stu-id="a97b3-128">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a97b3-129">Настройка привязок, предоставляемых системой</span><span class="sxs-lookup"><span data-stu-id="a97b3-129">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a97b3-130">Использование привязок для настройки служб и клиентов</span><span class="sxs-lookup"><span data-stu-id="a97b3-130">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
