---
description: 'Дополнительные сведения: <certificateReference>'
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 3404d44457849fb78ae88617d049a2199f2b5509
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681790"
---
# \<certificateReference>

<span data-ttu-id="20b3e-102">Задает параметры, используемые для поиска и проверки сертификата X. 509 в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="20b3e-102">Specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateReference>**  
  
## <a name="syntax"></a><span data-ttu-id="20b3e-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="20b3e-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20b3e-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="20b3e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="20b3e-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="20b3e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20b3e-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="20b3e-106">Attributes</span></span>  
  
|<span data-ttu-id="20b3e-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="20b3e-107">Attribute</span></span>|<span data-ttu-id="20b3e-108">Описание</span><span class="sxs-lookup"><span data-stu-id="20b3e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="20b3e-109">storeName</span><span class="sxs-lookup"><span data-stu-id="20b3e-109">storeName</span></span>|<span data-ttu-id="20b3e-110">Имя хранилища сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="20b3e-110">The name of the X.509 certificate store.</span></span> <span data-ttu-id="20b3e-111">Значение по умолчанию — "My".</span><span class="sxs-lookup"><span data-stu-id="20b3e-111">The default is "My".</span></span> <span data-ttu-id="20b3e-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="20b3e-112">Optional.</span></span>|  
|<span data-ttu-id="20b3e-113">storeLocation</span><span class="sxs-lookup"><span data-stu-id="20b3e-113">storeLocation</span></span>|<span data-ttu-id="20b3e-114"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Значение, указывающее расположение хранилища сертификатов X. 509.</span><span class="sxs-lookup"><span data-stu-id="20b3e-114">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the location of the X.509 certificate store.</span></span> <span data-ttu-id="20b3e-115">Значение по умолчанию — LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="20b3e-115">The default value is "LocalMachine".</span></span> <span data-ttu-id="20b3e-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="20b3e-116">Optional.</span></span>|  
|<span data-ttu-id="20b3e-117">x509FindType</span><span class="sxs-lookup"><span data-stu-id="20b3e-117">x509FindType</span></span>|<span data-ttu-id="20b3e-118"><xref:System.Security.Cryptography.X509Certificates.X509FindType>Значение типа, указывающее тип выполняемого поиска.</span><span class="sxs-lookup"><span data-stu-id="20b3e-118">An <xref:System.Security.Cryptography.X509Certificates.X509FindType> value that specifies the type of search that is to be executed.</span></span> <span data-ttu-id="20b3e-119">Значение по умолчанию — "Финдбисубжектдистингуишеднаме".</span><span class="sxs-lookup"><span data-stu-id="20b3e-119">The default is "FindBySubjectDistinguishedName".</span></span> <span data-ttu-id="20b3e-120">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="20b3e-120">Optional.</span></span>|  
|<span data-ttu-id="20b3e-121">findValue</span><span class="sxs-lookup"><span data-stu-id="20b3e-121">findValue</span></span>|<span data-ttu-id="20b3e-122">Значение для поиска в хранилище сертификатов X.509.</span><span class="sxs-lookup"><span data-stu-id="20b3e-122">The value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="20b3e-123">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="20b3e-123">Optional.</span></span>|  
|<span data-ttu-id="20b3e-124">isChainIncluded</span><span class="sxs-lookup"><span data-stu-id="20b3e-124">isChainIncluded</span></span>|<span data-ttu-id="20b3e-125">Указывает, следует ли выполнять проверку с помощью цепочки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="20b3e-125">Specifies whether validation should be performed by using the certificate chain.</span></span> <span data-ttu-id="20b3e-126">Значение по умолчанию — true; Проверка выполняется с помощью цепочки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="20b3e-126">The default is "true"; validation is performed by using the certificate chain.</span></span> <span data-ttu-id="20b3e-127">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="20b3e-127">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20b3e-128">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="20b3e-128">Child Elements</span></span>  

 <span data-ttu-id="20b3e-129">None</span><span class="sxs-lookup"><span data-stu-id="20b3e-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20b3e-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="20b3e-130">Parent Elements</span></span>  
  
|<span data-ttu-id="20b3e-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="20b3e-131">Element</span></span>|<span data-ttu-id="20b3e-132">Описание</span><span class="sxs-lookup"><span data-stu-id="20b3e-132">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="20b3e-133">Настраивает сертификат, используемый для шифрования и расшифровки маркеров.</span><span class="sxs-lookup"><span data-stu-id="20b3e-133">Configures the certificate that is used to encrypt and decrypt tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20b3e-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="20b3e-134">Remarks</span></span>  

 <span data-ttu-id="20b3e-135">`<certificateReference>`Элемент задает параметры, используемые для поиска и проверки сертификата X. 509 в хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="20b3e-135">The `<certificateReference>` element specifies settings that are used to find and validate an X.509 certificate in a certificate store.</span></span> <span data-ttu-id="20b3e-136">Если он указан как дочерний элемент `<serviceCertificate>` , он указывает параметры расположения и проверки сертификата X. 509, который используется для шифрования и расшифровки токенов.</span><span class="sxs-lookup"><span data-stu-id="20b3e-136">When it is specified as the child element of the `<serviceCertificate>` element, it specifies the location and verification settings of the X.509 certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="20b3e-137">`<certificateReference>`Элемент представлен <xref:System.ServiceModel.Configuration.CertificateReferenceElement> классом.</span><span class="sxs-lookup"><span data-stu-id="20b3e-137">The `<certificateReference>` element is represented by the <xref:System.ServiceModel.Configuration.CertificateReferenceElement> class.</span></span>
