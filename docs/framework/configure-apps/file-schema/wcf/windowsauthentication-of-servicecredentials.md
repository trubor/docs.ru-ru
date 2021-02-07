---
description: 'Дополнительные сведения <windowsAuthentication> о: <serviceCredentials>'
title: <windowsAuthentication> из <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: e0709473-0997-4de3-8f49-783527309a48
ms.openlocfilehash: 94f5804ac22a8c3ee1b8fc646ece8521ff639aec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682414"
---
# <a name="windowsauthentication-of-servicecredentials"></a><span data-ttu-id="347b8-103">\<windowsAuthentication> из \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="347b8-103">\<windowsAuthentication> of \<serviceCredentials></span></span>

<span data-ttu-id="347b8-104">Задает параметры учетной записи службы Windows.</span><span class="sxs-lookup"><span data-stu-id="347b8-104">Specifies the settings of a Windows service credential.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="347b8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="347b8-105">Syntax</span></span>  
  
```xml  
<windowsAuthentication allowAnonymousLogons="Boolean"
                       includeWindowsGroups="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="347b8-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="347b8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="347b8-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="347b8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="347b8-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="347b8-108">Attributes</span></span>  
  
|<span data-ttu-id="347b8-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="347b8-109">Attribute</span></span>|<span data-ttu-id="347b8-110">Описание</span><span class="sxs-lookup"><span data-stu-id="347b8-110">Description</span></span>|  
|---------------|-----------------|  
|`includeWindowsGroups`|<span data-ttu-id="347b8-111">Необязательный логический атрибут, который задает, включает ли система группы Windows в контекст безопасности.</span><span class="sxs-lookup"><span data-stu-id="347b8-111">An optional Boolean attribute that specifies whether the system includes Windows groups in the security context.</span></span> <span data-ttu-id="347b8-112">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="347b8-112">The default is `true`.</span></span><br /><br /> <span data-ttu-id="347b8-113">Установка для этого атрибута значения `true` влияет на производительность, поскольку приводит к расширению всей группы.</span><span class="sxs-lookup"><span data-stu-id="347b8-113">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="347b8-114">Если нет необходимости устанавливать список групп, к которым принадлежит пользователь, установите для этого атрибута значение `false`.</span><span class="sxs-lookup"><span data-stu-id="347b8-114">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`allowAnonymousLogons`|<span data-ttu-id="347b8-115">Необязательный логический атрибут, который указывает, разрешены ли анонимные, не прошедшие проверку подлинности вызывающие объекты.</span><span class="sxs-lookup"><span data-stu-id="347b8-115">An optional Boolean attribute that specifies whether anonymous, unauthenticated callers are allowed.</span></span> <span data-ttu-id="347b8-116">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="347b8-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="347b8-117">Когда атрибуту `clientCredentialType` привязки задано значение `Windows`, система не разрешает анонимные вызывающие объекты.</span><span class="sxs-lookup"><span data-stu-id="347b8-117">When the `clientCredentialType` attribute of a binding is set to `Windows`, the system does not allow anonymous callers.</span></span> <span data-ttu-id="347b8-118">Это значит, что доступ к системе разрешен только прошедшим проверку подлинности вызывающим объектам домена или рабочей группы.</span><span class="sxs-lookup"><span data-stu-id="347b8-118">This means that only domain or workgroup authenticated callers are allowed to access the system.</span></span> <span data-ttu-id="347b8-119">Это поведение можно переопределить с помощью данного атрибута.</span><span class="sxs-lookup"><span data-stu-id="347b8-119">You can override this behavior by using this attribute.</span></span><br /><br /> <span data-ttu-id="347b8-120">Используйте этот режим с особой осторожностью.</span><span class="sxs-lookup"><span data-stu-id="347b8-120">Use this setting with extreme caution.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="347b8-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="347b8-121">Child Elements</span></span>  

 <span data-ttu-id="347b8-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="347b8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="347b8-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="347b8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="347b8-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="347b8-124">Element</span></span>|<span data-ttu-id="347b8-125">Описание</span><span class="sxs-lookup"><span data-stu-id="347b8-125">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="347b8-126">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="347b8-126">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="347b8-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="347b8-127">Remarks</span></span>  

 <span data-ttu-id="347b8-128">Этот элемент используется, чтобы указать, разрешается ли доступ анонимных пользователей Windows путем установки атрибута `allowAnonymousLogons`.</span><span class="sxs-lookup"><span data-stu-id="347b8-128">Use this element to specify whether to allow anonymous Windows users access by setting the `allowAnonymousLogons` attribute.</span></span> <span data-ttu-id="347b8-129">Также можно указать, включать ли сведения о группе, к которой принадлежат пользователи в AuthorizationContext, путем установки атрибута `includeWindowsGroups`.</span><span class="sxs-lookup"><span data-stu-id="347b8-129">You can also specify whether to include group information to which users belong in the AuthorizationContext by setting the `includeWindowsGroups` attribute.</span></span> <span data-ttu-id="347b8-130">Если атрибуту задано значение `true` (по умолчанию), служба может определить группы Windows, к которым принадлежит клиент.</span><span class="sxs-lookup"><span data-stu-id="347b8-130">If it is set to `true` (the default setting), the service can determine the Windows groups to which the client belongs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347b8-131">См. также</span><span class="sxs-lookup"><span data-stu-id="347b8-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.WindowsServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.WindowsAuthentication%2A>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
