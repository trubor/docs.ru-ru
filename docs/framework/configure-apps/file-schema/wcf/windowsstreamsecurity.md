---
description: 'Дополнительные сведения: <windowsStreamSecurity>'
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: c623dc23ca67d0341b66a2a4d97de564be77dcc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682401"
---
# \<windowsStreamSecurity>

<span data-ttu-id="16cbf-102">Задает параметры безопасности потока Windows пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="16cbf-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="16cbf-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16cbf-103">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16cbf-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="16cbf-104">Attributes and Elements</span></span>  

 <span data-ttu-id="16cbf-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="16cbf-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16cbf-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="16cbf-106">Attributes</span></span>  
  
|<span data-ttu-id="16cbf-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="16cbf-107">Attribute</span></span>|<span data-ttu-id="16cbf-108">Описание</span><span class="sxs-lookup"><span data-stu-id="16cbf-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16cbf-109">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="16cbf-109">protectionLevel</span></span>|<span data-ttu-id="16cbf-110">Определяет систему безопасности уровня сообщений.</span><span class="sxs-lookup"><span data-stu-id="16cbf-110">Defines message-level security.</span></span> <span data-ttu-id="16cbf-111">Подпись сообщений уменьшает риск подделки сообщения сторонними лицами при его передаче.</span><span class="sxs-lookup"><span data-stu-id="16cbf-111">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="16cbf-112">Шифрование обеспечивает конфиденциальность на уровне данных во время транспортировки.</span><span class="sxs-lookup"><span data-stu-id="16cbf-112">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="16cbf-113">Допустимые значения.</span><span class="sxs-lookup"><span data-stu-id="16cbf-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="16cbf-114">-None: защита отсутствует.</span><span class="sxs-lookup"><span data-stu-id="16cbf-114">-   None: No protection.</span></span><br /><span data-ttu-id="16cbf-115">-Sign: сообщения подписываются.</span><span class="sxs-lookup"><span data-stu-id="16cbf-115">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="16cbf-116">-EncryptAndSign: сообщения подписываются и шифруются.</span><span class="sxs-lookup"><span data-stu-id="16cbf-116">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="16cbf-117">Значение по умолчанию - EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="16cbf-117">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="16cbf-118">Это атрибут типа <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="16cbf-118">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16cbf-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="16cbf-119">Child Elements</span></span>  

 <span data-ttu-id="16cbf-120">None</span><span class="sxs-lookup"><span data-stu-id="16cbf-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16cbf-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="16cbf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="16cbf-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="16cbf-122">Element</span></span>|<span data-ttu-id="16cbf-123">Описание</span><span class="sxs-lookup"><span data-stu-id="16cbf-123">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="16cbf-124">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="16cbf-124">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16cbf-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="16cbf-125">Remarks</span></span>  

 <span data-ttu-id="16cbf-126">Транспорты, использующие такой поточно-ориентированный протокол, как TCP и именованные каналы, поддерживают потоковые обновления транспорта.</span><span class="sxs-lookup"><span data-stu-id="16cbf-126">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="16cbf-127">В частности, WCF обеспечивает обновления системы безопасности.</span><span class="sxs-lookup"><span data-stu-id="16cbf-127">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="16cbf-128">Конфигурация этой защиты транспорта инкапсулирована этим элементом конфигурации, а также с [\<sslStreamSecurity>](sslstreamsecurity.md) , который можно настроить и добавить в пользовательскую привязку.</span><span class="sxs-lookup"><span data-stu-id="16cbf-128">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16cbf-129">См. также</span><span class="sxs-lookup"><span data-stu-id="16cbf-129">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="16cbf-130">Привязки</span><span class="sxs-lookup"><span data-stu-id="16cbf-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="16cbf-131">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="16cbf-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="16cbf-132">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="16cbf-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
