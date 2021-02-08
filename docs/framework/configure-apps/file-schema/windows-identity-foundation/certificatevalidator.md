---
description: 'Дополнительные сведения: <certificateValidator>'
title: <certificateValidator>
ms.date: 03/30/2017
ms.assetid: 86161897-c20f-4ad8-9d7f-050c247251bf
author: BrucePerlerMS
ms.openlocfilehash: 0b92eada916b239ca56342021bb958da6d02c2e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802168"
---
# \<certificateValidator>

<span data-ttu-id="1950a-102">Указывает пользовательский тип для проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="1950a-102">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1950a-103">Этот тип используется только в том случае, если `certificateValidationMode` атрибут [\<certificateValidation>](certificatevalidation.md) элемента имеет значение Custom.</span><span class="sxs-lookup"><span data-stu-id="1950a-103">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<certificateValidation>**](certificatevalidation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidator>**  
  
## <a name="syntax"></a><span data-ttu-id="1950a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1950a-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation>  
      <certificateValidator type=xs:string>  
      </certificateValidator>  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1950a-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1950a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1950a-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1950a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1950a-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1950a-107">Attributes</span></span>  
  
|<span data-ttu-id="1950a-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1950a-108">Attribute</span></span>|<span data-ttu-id="1950a-109">Описание</span><span class="sxs-lookup"><span data-stu-id="1950a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1950a-110">type</span><span class="sxs-lookup"><span data-stu-id="1950a-110">type</span></span>|<span data-ttu-id="1950a-111">Указывает пользовательский тип, производный от <xref:System.IdentityModel.Selectors.X509CertificateValidator> класса.</span><span class="sxs-lookup"><span data-stu-id="1950a-111">Specifies a custom type that derives from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="1950a-112">`certificateValidationMode`Чтобы использовать этот тип, присвойте атрибуту [\<certificateValidation>](certificatevalidation.md) элемента значение Custom.</span><span class="sxs-lookup"><span data-stu-id="1950a-112">Set the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element to "Custom" to use this type.</span></span> <span data-ttu-id="1950a-113">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="1950a-113">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="1950a-114">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="1950a-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1950a-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1950a-115">Child Elements</span></span>  

 <span data-ttu-id="1950a-116">None</span><span class="sxs-lookup"><span data-stu-id="1950a-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1950a-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1950a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1950a-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="1950a-118">Element</span></span>|<span data-ttu-id="1950a-119">Описание</span><span class="sxs-lookup"><span data-stu-id="1950a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="1950a-120">Управляет параметрами, которые обработчики маркеров используют для проверки сертификатов.</span><span class="sxs-lookup"><span data-stu-id="1950a-120">Controls the settings that token handlers use to validate certificates.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1950a-121">Пример</span><span class="sxs-lookup"><span data-stu-id="1950a-121">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="Custom"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine">  
    <certificateValidator type="MyNamespace.CustomValidator, MyAssembly" />
</certificateValidation>
```
