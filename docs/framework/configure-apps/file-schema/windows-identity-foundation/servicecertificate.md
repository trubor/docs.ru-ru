---
description: 'Дополнительные сведения: <serviceCertificate>'
title: <serviceCertificate>
ms.date: 03/30/2017
ms.assetid: 42c7f291-2ec3-43c5-8872-35897ff3c660
author: BrucePerlerMS
ms.openlocfilehash: d9940fd96667211b1f9fd672b824af84e0d5143a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725328"
---
# \<serviceCertificate>

<span data-ttu-id="fcbf9-102">Настраивает сертификат X. 509, используемый для шифрования и расшифровки токенов.</span><span class="sxs-lookup"><span data-stu-id="fcbf9-102">Configures the X.509 certificate that is used to encrypt and decrypt tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="fcbf9-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fcbf9-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcbf9-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="fcbf9-104">Attributes and Elements</span></span>  

 <span data-ttu-id="fcbf9-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="fcbf9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcbf9-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="fcbf9-106">Attributes</span></span>  

 <span data-ttu-id="fcbf9-107">None</span><span class="sxs-lookup"><span data-stu-id="fcbf9-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fcbf9-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="fcbf9-108">Child Elements</span></span>  
  
|<span data-ttu-id="fcbf9-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="fcbf9-109">Element</span></span>|<span data-ttu-id="fcbf9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="fcbf9-110">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateReference>](certificatereference.md)|<span data-ttu-id="fcbf9-111">Задает параметры, используемые для поиска и проверки сертификата X. 509 в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="fcbf9-111">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcbf9-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="fcbf9-112">Parent Elements</span></span>  
  
|<span data-ttu-id="fcbf9-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="fcbf9-113">Element</span></span>|<span data-ttu-id="fcbf9-114">Описание</span><span class="sxs-lookup"><span data-stu-id="fcbf9-114">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="fcbf9-115">Содержит параметры, которые настраивают свойства <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (всфам) и <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span><span class="sxs-lookup"><span data-stu-id="fcbf9-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fcbf9-116">Пример</span><span class="sxs-lookup"><span data-stu-id="fcbf9-116">Example</span></span>  

 <span data-ttu-id="fcbf9-117">В следующем коде XML показано использование \<serviceCertificate> элемента.</span><span class="sxs-lookup"><span data-stu-id="fcbf9-117">The following XML shows the use of the \<serviceCertificate> element.</span></span> <span data-ttu-id="fcbf9-118">XML взят из `CustomToken` примера.</span><span class="sxs-lookup"><span data-stu-id="fcbf9-118">The XML is taken from the `CustomToken` sample.</span></span>  
  
```xml  
<serviceCertificate>  
  <certificateReference x509FindType="FindBySubjectName" findValue="localhost" storeLocation="LocalMachine" storeName="My"/>  
</serviceCertificate>  
```
