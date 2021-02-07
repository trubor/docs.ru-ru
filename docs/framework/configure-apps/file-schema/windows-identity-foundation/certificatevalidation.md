---
description: 'Дополнительные сведения: <certificateValidation>'
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: a12e46487b4fb2ac8071ba1cf9bc5c6057ded060
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740071"
---
# \<certificateValidation>

<span data-ttu-id="c77a9-102">Управляет параметрами, которые обработчики маркеров используют для проверки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="c77a9-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="c77a9-103">Эти параметры переопределяются, если для определенного обработчика настроен собственный проверяющий элемент управления.</span><span class="sxs-lookup"><span data-stu-id="c77a9-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="c77a9-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c77a9-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c77a9-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="c77a9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c77a9-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="c77a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c77a9-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="c77a9-107">Attributes</span></span>  
  
|<span data-ttu-id="c77a9-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="c77a9-108">Attribute</span></span>|<span data-ttu-id="c77a9-109">Описание</span><span class="sxs-lookup"><span data-stu-id="c77a9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c77a9-110">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="c77a9-110">certificateValidationMode</span></span>|<span data-ttu-id="c77a9-111"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Значение типа, указывающее режим проверки, используемый для сертификата X. 509.</span><span class="sxs-lookup"><span data-stu-id="c77a9-111">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c77a9-112">Значение по умолчанию — "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="c77a9-112">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="c77a9-113">Чтобы указать настраиваемый проверяющий элемент управления, установите для этого атрибута значение "Custom" и укажите проверяющий элемент управления с помощью [\<certificateValidator>](certificatevalidator.md) элемента.</span><span class="sxs-lookup"><span data-stu-id="c77a9-113">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="c77a9-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="c77a9-114">Optional.</span></span>|  
|<span data-ttu-id="c77a9-115">revocationMode</span><span class="sxs-lookup"><span data-stu-id="c77a9-115">revocationMode</span></span>|<span data-ttu-id="c77a9-116"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Значение типа, указывающее режим отзыва, используемый для сертификата X. 509.</span><span class="sxs-lookup"><span data-stu-id="c77a9-116">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c77a9-117">Значение по умолчанию — "Online".</span><span class="sxs-lookup"><span data-stu-id="c77a9-117">The default value is "Online".</span></span> <span data-ttu-id="c77a9-118">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="c77a9-118">Optional.</span></span>|  
|<span data-ttu-id="c77a9-119">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="c77a9-119">trustedStoreLocation</span></span>|<span data-ttu-id="c77a9-120"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Значение типа, указывающее хранилище сертификатов X. 509.</span><span class="sxs-lookup"><span data-stu-id="c77a9-120">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="c77a9-121">Значение по умолчанию — LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="c77a9-121">The default value is "LocalMachine".</span></span> <span data-ttu-id="c77a9-122">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="c77a9-122">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c77a9-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="c77a9-123">Child Elements</span></span>  
  
|<span data-ttu-id="c77a9-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="c77a9-124">Element</span></span>|<span data-ttu-id="c77a9-125">Описание</span><span class="sxs-lookup"><span data-stu-id="c77a9-125">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="c77a9-126">Указывает пользовательский тип для проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="c77a9-126">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="c77a9-127">Этот тип используется только в том случае, если `certificateValidationMode` атрибут [\<certificateValidation>](certificatevalidation.md) элемента имеет значение Custom.</span><span class="sxs-lookup"><span data-stu-id="c77a9-127">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c77a9-128">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="c77a9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="c77a9-129">Элемент</span><span class="sxs-lookup"><span data-stu-id="c77a9-129">Element</span></span>|<span data-ttu-id="c77a9-130">Описание</span><span class="sxs-lookup"><span data-stu-id="c77a9-130">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="c77a9-131">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="c77a9-131">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="c77a9-132">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="c77a9-132">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c77a9-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="c77a9-133">Remarks</span></span>  

 <span data-ttu-id="c77a9-134">`<certificateValidation>`Элемент можно указать на уровне службы в `<identityConfiguration>` элементе или на уровне коллекции обработчика маркеров безопасности под `<securityTokenHandlerConfiguration>` элементом.</span><span class="sxs-lookup"><span data-stu-id="c77a9-134">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="c77a9-135">Параметры коллекции обработчиков маркеров переопределяют указанные в службе.</span><span class="sxs-lookup"><span data-stu-id="c77a9-135">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="c77a9-136">Некоторые обработчики маркеров позволяют указать параметры проверки сертификата в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c77a9-136">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="c77a9-137">Параметры отдельных обработчиков маркеров переопределяют те, которые указаны как на уровне службы, так и в коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="c77a9-137">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c77a9-138">Пример</span><span class="sxs-lookup"><span data-stu-id="c77a9-138">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
