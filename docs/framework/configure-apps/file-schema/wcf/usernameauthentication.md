---
description: 'Дополнительные сведения: <userNameAuthentication>'
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 0edd92ba343ec38207d60c99616058d0b28f045b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664448"
---
# \<userNameAuthentication>

<span data-ttu-id="0b5fc-102">Задает учетные данные службы, основанные на имени пользователя и пароле.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-102">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="0b5fc-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b5fc-103">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0b5fc-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0b5fc-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0b5fc-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0b5fc-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0b5fc-106">Attributes</span></span>  
  
|<span data-ttu-id="0b5fc-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="0b5fc-107">Attribute</span></span>|<span data-ttu-id="0b5fc-108">Описание</span><span class="sxs-lookup"><span data-stu-id="0b5fc-108">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="0b5fc-109">Объект <xref:System.TimeSpan>, определяющий максимальный срок кэширования маркера.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-109">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="0b5fc-110">Значение по умолчанию - 00:15:00.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-110">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="0b5fc-111">Логическое значение, которое указывает, кэшируются ли маркеры входа.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-111">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="0b5fc-112">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-112">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="0b5fc-113">Строка, указывающая тип настраиваемого проверяющего элемента управления для проверки имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-113">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="0b5fc-114">Значение по умолчанию - пустая строка.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-114">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="0b5fc-115">Логическое значение, указывающее, включаются ли группы Windows в контекст безопасности.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-115">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="0b5fc-116">Значение по умолчанию — `true`.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-116">The default is `true`.</span></span><br /><br /> <span data-ttu-id="0b5fc-117">Установка для этого атрибута значения `true` влияет на производительность, поскольку приводит к расширению всей группы.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-117">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="0b5fc-118">Если нет необходимости устанавливать список групп, которым принадлежит пользователь, установите значение `false`.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-118">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="0b5fc-119">Целое число, указывающее максимальное количество маркеров входа для кэширования.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-119">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="0b5fc-120">Значение должно быть больше нуля.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-120">This value should be larger than zero.</span></span> <span data-ttu-id="0b5fc-121">Значение по умолчанию — 128.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-121">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="0b5fc-122">Если атрибуту `clientCredentialType` привязки задано значение `username`, имя пользователя сопоставляется с учетными записями Windows.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-122">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="0b5fc-123">Такое поведение можно переопределить с помощью этого атрибута, который является строкой, содержащей имя значения <xref:System.Web.Security.MembershipProvider>, предоставляющего соответствующий механизм проверки пароля.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-123">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="0b5fc-124">Указывает способ проверки пароля.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-124">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="0b5fc-125">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="0b5fc-125">Valid values are:</span></span><br /><br /> <span data-ttu-id="0b5fc-126">— Windows</span><span class="sxs-lookup"><span data-stu-id="0b5fc-126">-   Windows</span></span><br /><span data-ttu-id="0b5fc-127">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="0b5fc-127">-   MembershipProvider</span></span><br /><span data-ttu-id="0b5fc-128">— Пользовательский</span><span class="sxs-lookup"><span data-stu-id="0b5fc-128">-   Custom</span></span><br /><br /> <span data-ttu-id="0b5fc-129">По умолчанию используется Windows.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-129">The default is Windows.</span></span> <span data-ttu-id="0b5fc-130">Это атрибут типа <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-130">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0b5fc-131">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0b5fc-131">Child Elements</span></span>  

 <span data-ttu-id="0b5fc-132">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0b5fc-133">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0b5fc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="0b5fc-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="0b5fc-134">Element</span></span>|<span data-ttu-id="0b5fc-135">Описание</span><span class="sxs-lookup"><span data-stu-id="0b5fc-135">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="0b5fc-136">Задает учетные данные, используемые при проверке подлинности службы, а также параметры, относящиеся к проверке учетных данных клиента.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-136">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b5fc-137">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b5fc-137">Remarks</span></span>  

 <span data-ttu-id="0b5fc-138">Если ни одна из используемых службой привязок не настроена для проверки подлинности на основании имени пользователя и пароля, атрибуты этого элемента пропускаются.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-138">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="0b5fc-139">К ним относятся `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName` и `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-139">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="0b5fc-140">Если ни одна из используемых службой привязок не настроена на использование проверки подлинности Windows для имени и пароля пользователя, параметры, относящиеся к кэшированию маркеров входа, пропускаются.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-140">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="0b5fc-141">К ним относятся `cacheLogonTokenLifetime`, `cacheLogonTokens` и `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="0b5fc-141">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b5fc-142">См. также</span><span class="sxs-lookup"><span data-stu-id="0b5fc-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>
