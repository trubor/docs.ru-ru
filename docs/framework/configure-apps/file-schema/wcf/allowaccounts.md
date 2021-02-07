---
description: 'Дополнительные сведения: <allowAccounts>'
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 5211d694e5318faf0cfc31b404764acb405bd096
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749991"
---
# \<allowAccounts>

<span data-ttu-id="c4b37-102">Содержит коллекцию элементов конфигурации, указывающих учетные записи пользователей для процессов, на которых размещены службы Windows Communication Foundation (WCF) и которым предоставляется доступ к службе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="c4b37-102">Contains a collection of configuration elements that specify user accounts for processes that host Windows Communication Foundation (WCF) services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<allowAccounts>**  
  
## <a name="syntax"></a><span data-ttu-id="c4b37-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c4b37-103">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4b37-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c4b37-104">Attributes and Elements</span></span>  

 <span data-ttu-id="c4b37-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c4b37-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4b37-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c4b37-106">Attributes</span></span>  

 <span data-ttu-id="c4b37-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="c4b37-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4b37-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c4b37-108">Child Elements</span></span>  
  
|<span data-ttu-id="c4b37-109">attribute</span><span class="sxs-lookup"><span data-stu-id="c4b37-109">Attribute</span></span>|<span data-ttu-id="c4b37-110">Описание</span><span class="sxs-lookup"><span data-stu-id="c4b37-110">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|<span data-ttu-id="c4b37-111">Добавляет учетную запись пользователя для процессов, на которых размещаются службы WCF, и предоставляет доступ к подключению к службе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="c4b37-111">Adds a user account for processes that host WCF services, and are granted connection access to the sharing service</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c4b37-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c4b37-112">Parent Elements</span></span>  
  
|<span data-ttu-id="c4b37-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="c4b37-113">Element</span></span>|<span data-ttu-id="c4b37-114">Описание</span><span class="sxs-lookup"><span data-stu-id="c4b37-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4b37-115">[\<net.pipe>](net-pipe.md) или [\<net.tcp>](net-tcp.md)</span><span class="sxs-lookup"><span data-stu-id="c4b37-115">[\<net.pipe>](net-pipe.md) or [\<net.tcp>](net-tcp.md)</span></span>|<span data-ttu-id="c4b37-116">Задает параметры конфигурации для совместно используемых служб Net Pipe или TCP.</span><span class="sxs-lookup"><span data-stu-id="c4b37-116">Specifies configuration settings for the Net Pipe or TCP sharing services.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c4b37-117">См. также</span><span class="sxs-lookup"><span data-stu-id="c4b37-117">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
