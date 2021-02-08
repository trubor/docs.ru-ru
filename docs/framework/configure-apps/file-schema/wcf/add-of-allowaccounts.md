---
description: 'Дополнительные сведения <add> о: <allowAccounts>'
title: <add> из <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 275631c4467a888966e89a2f664b186f989ae101
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782225"
---
# <a name="add-of-allowaccounts"></a><span data-ttu-id="fe0cd-103">\<add> из \<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="fe0cd-103">\<add> of \<allowAccounts></span></span>

<span data-ttu-id="fe0cd-104">Указывает учетную запись пользователя для процессов, на которых размещаются службы WCF, и им предоставляется доступ к службе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-104">Specifies a user account for processes that host WCF services, and are granted connection access to the sharing service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<net.pipe>**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<allowAccounts>**](allowaccounts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="fe0cd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fe0cd-105">Syntax</span></span>  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe0cd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fe0cd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="fe0cd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe0cd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fe0cd-108">Attributes</span></span>  
  
|<span data-ttu-id="fe0cd-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="fe0cd-109">Attribute</span></span>|<span data-ttu-id="fe0cd-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fe0cd-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe0cd-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="fe0cd-111">securityIdentifier</span></span>|<span data-ttu-id="fe0cd-112">Строка, задающая уникальный идентификатор, который используется для идентификации учетной записи пользователя.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="fe0cd-113">Значениями по умолчанию являются LocalSystem, Administrators, NS, LS и IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe0cd-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fe0cd-114">Child Elements</span></span>  

 <span data-ttu-id="fe0cd-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe0cd-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fe0cd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fe0cd-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="fe0cd-117">Element</span></span>|<span data-ttu-id="fe0cd-118">Описание</span><span class="sxs-lookup"><span data-stu-id="fe0cd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="fe0cd-119">Коллекция элементов конфигурации, которая содержит `securityIdentifier` атрибут для указания учетных записей пользователей для процессов, размещающий службы WCF, и которым предоставляется доступ к службе общего доступа.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe0cd-120">Пример</span><span class="sxs-lookup"><span data-stu-id="fe0cd-120">Example</span></span>  

 <span data-ttu-id="fe0cd-121">В следующем примере конфигурации к данной коллекции добавляется пять идентификаторов по умолчанию для учетных записей пользователей.</span><span class="sxs-lookup"><span data-stu-id="fe0cd-121">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>
  <!-- LocalSystem account -->
  <add securityIdentifier="S-1-5-18" />
  <!-- LocalService account -->
  <add securityIdentifier="S-1-5-19" />
  <!-- Administrators account -->
  <add securityIdentifier="S-1-5-20" />
  <!-- Network Service account -->
  <add securityIdentifier="S-1-5-32-544" />
  <!-- IIS_IUSRS account (Vista only) -->
  <add securityIdentifier="S-1-5-32-568" />
</allowAccounts>
```  
  
## <a name="see-also"></a><span data-ttu-id="fe0cd-122">См. также</span><span class="sxs-lookup"><span data-stu-id="fe0cd-122">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
