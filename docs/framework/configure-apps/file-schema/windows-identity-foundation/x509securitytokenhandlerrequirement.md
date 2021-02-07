---
description: 'Дополнительные сведения: <x509SecurityTokenHandlerRequirement>'
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 21a05cfeee6365bd677a6f35e984cb64fa4dd078
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748977"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="a78c6-102">Предоставляет необязательную конфигурацию для <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> класса или производных классов.</span><span class="sxs-lookup"><span data-stu-id="a78c6-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="a78c6-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a78c6-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a78c6-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a78c6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="a78c6-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a78c6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a78c6-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a78c6-106">Attributes</span></span>  
  
|<span data-ttu-id="a78c6-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a78c6-107">Attribute</span></span>|<span data-ttu-id="a78c6-108">Описание</span><span class="sxs-lookup"><span data-stu-id="a78c6-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a78c6-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a78c6-109">certificateValidationMode</span></span>|<span data-ttu-id="a78c6-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Значение типа, указывающее режим проверки, используемый для сертификата X. 509.</span><span class="sxs-lookup"><span data-stu-id="a78c6-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a78c6-111">Значение по умолчанию — "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="a78c6-111">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="a78c6-112">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="a78c6-112">mapToWindows</span></span>|<span data-ttu-id="a78c6-113">Указывает, должен ли обработчик маркера сопоставлять проверяющий токен с учетной записью Windows, используя входящее утверждение имени участника-пользователя.</span><span class="sxs-lookup"><span data-stu-id="a78c6-113">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="a78c6-114">Значение по умолчанию — «false».</span><span class="sxs-lookup"><span data-stu-id="a78c6-114">The default is "false".</span></span>|  
|<span data-ttu-id="a78c6-115">revocationMode</span><span class="sxs-lookup"><span data-stu-id="a78c6-115">revocationMode</span></span>|<span data-ttu-id="a78c6-116"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Значение типа, указывающее режим отзыва, используемый для сертификата X. 509.</span><span class="sxs-lookup"><span data-stu-id="a78c6-116">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="a78c6-117">Значение по умолчанию — "Online".</span><span class="sxs-lookup"><span data-stu-id="a78c6-117">The default value is "Online".</span></span>|  
|<span data-ttu-id="a78c6-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a78c6-118">trustedStoreLocation</span></span>|<span data-ttu-id="a78c6-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Значение типа, указывающее хранилище сертификатов X. 509.</span><span class="sxs-lookup"><span data-stu-id="a78c6-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="a78c6-120">Значение по умолчанию — LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a78c6-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="a78c6-121">цертификатевалидатор</span><span class="sxs-lookup"><span data-stu-id="a78c6-121">certificateValidator</span></span>|<span data-ttu-id="a78c6-122">Пользовательский тип, производный от <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="a78c6-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a78c6-123">Если `certificateValidationMode` атрибут имеет значение Custom, для проверки сертификата издателя используется экземпляр этого типа.</span><span class="sxs-lookup"><span data-stu-id="a78c6-123">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a78c6-124">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a78c6-124">Child Elements</span></span>  

 <span data-ttu-id="a78c6-125">None</span><span class="sxs-lookup"><span data-stu-id="a78c6-125">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a78c6-126">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a78c6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a78c6-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="a78c6-127">Element</span></span>|<span data-ttu-id="a78c6-128">Описание</span><span class="sxs-lookup"><span data-stu-id="a78c6-128">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="a78c6-129">Добавляет указанный обработчик маркеров безопасности в коллекцию обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="a78c6-129">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a78c6-130">Пример</span><span class="sxs-lookup"><span data-stu-id="a78c6-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
