---
description: 'Дополнительные сведения <secureConversationAuthentication> о: <serviceCredential>'
title: <secureConversationAuthentication> из <serviceCredential>
ms.date: 03/30/2017
ms.assetid: 0bd3fac7-befd-4a45-ba51-c200b33be0fd
ms.openlocfilehash: 8f95b4009111996d2a5c1133c9ef762375b4e3e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683324"
---
# <a name="secureconversationauthentication-of-servicecredential"></a><span data-ttu-id="bdabc-103">\<secureConversationAuthentication> из \<serviceCredential></span><span class="sxs-lookup"><span data-stu-id="bdabc-103">\<secureConversationAuthentication> of \<serviceCredential></span></span>

<span data-ttu-id="bdabc-104">Задает параметры службы безопасного обмена данными.</span><span class="sxs-lookup"><span data-stu-id="bdabc-104">Specifies the settings for a secure conversation service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<secureConversationAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="bdabc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bdabc-105">Syntax</span></span>  
  
```xml  
<secureConversationAuthentication securityStateEncoderType="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdabc-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="bdabc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="bdabc-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="bdabc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdabc-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="bdabc-108">Attributes</span></span>  
  
|<span data-ttu-id="bdabc-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="bdabc-109">Attribute</span></span>|<span data-ttu-id="bdabc-110">Описание</span><span class="sxs-lookup"><span data-stu-id="bdabc-110">Description</span></span>|  
|---------------|-----------------|  
|`securityStateEncoderType`|<span data-ttu-id="bdabc-111">Строка, указывающая используемый тип <xref:System.ServiceModel.Security.SecurityStateEncoder>.</span><span class="sxs-lookup"><span data-stu-id="bdabc-111">A string that specifies the type of <xref:System.ServiceModel.Security.SecurityStateEncoder> to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdabc-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="bdabc-112">Child Elements</span></span>  

 <span data-ttu-id="bdabc-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="bdabc-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdabc-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="bdabc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bdabc-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="bdabc-115">Element</span></span>|<span data-ttu-id="bdabc-116">Описание</span><span class="sxs-lookup"><span data-stu-id="bdabc-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="bdabc-117">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="bdabc-117">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdabc-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="bdabc-118">Remarks</span></span>  

 <span data-ttu-id="bdabc-119">Данный элемент конфигурации используется для указания списка известных типов утверждений для сериализации файлов cookie маркера контекста безопасности (SCT), а также в качестве кодировщика для шифрования и защиты данных файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="bdabc-119">Use this configuration element to specify a list of known claim types for the Security Context Token (SCT) cookies serialization, as well as an encoder to encode and secure cookies information.</span></span> <span data-ttu-id="bdabc-120">Дополнительные сведения о маркерах контекста безопасности см. в разделе <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span><span class="sxs-lookup"><span data-stu-id="bdabc-120">For more information on SCT, see <xref:System.ServiceModel.Security.SecureConversationServiceCredential>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdabc-121">См. также</span><span class="sxs-lookup"><span data-stu-id="bdabc-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.SecureConversationAuthentication%2A>
- <xref:System.ServiceModel.Security.SecureConversationServiceCredential>
