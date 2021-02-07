---
description: 'Дополнительные сведения: <serviceTokenResolver>'
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: ab24c92eee43324365adb3bb3a64c8a765017a53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698301"
---
# \<serviceTokenResolver>

<span data-ttu-id="835fe-102">Регистрирует сопоставитель маркеров службы, используемый обработчиками в коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="835fe-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="835fe-103">Сопоставитель токенов службы используется для разрешения маркера шифрования входящих токенов и сообщений.</span><span class="sxs-lookup"><span data-stu-id="835fe-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="835fe-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="835fe-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="835fe-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="835fe-105">Attributes and Elements</span></span>  

 <span data-ttu-id="835fe-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="835fe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="835fe-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="835fe-107">Attributes</span></span>  
  
|<span data-ttu-id="835fe-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="835fe-108">Attribute</span></span>|<span data-ttu-id="835fe-109">Описание</span><span class="sxs-lookup"><span data-stu-id="835fe-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="835fe-110">type</span><span class="sxs-lookup"><span data-stu-id="835fe-110">type</span></span>|<span data-ttu-id="835fe-111">Указывает тип сопоставителя токенов службы.</span><span class="sxs-lookup"><span data-stu-id="835fe-111">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="835fe-112">Либо <xref:System.IdentityModel.Selectors.SecurityTokenResolver> тип, либо тип, производный от <xref:System.IdentityModel.Selectors.SecurityTokenResolver> класса.</span><span class="sxs-lookup"><span data-stu-id="835fe-112">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="835fe-113">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы].</span><span class="sxs-lookup"><span data-stu-id="835fe-113">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="835fe-114">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="835fe-114">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="835fe-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="835fe-115">Child Elements</span></span>  

 <span data-ttu-id="835fe-116">None</span><span class="sxs-lookup"><span data-stu-id="835fe-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="835fe-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="835fe-117">Parent Elements</span></span>  
  
|<span data-ttu-id="835fe-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="835fe-118">Element</span></span>|<span data-ttu-id="835fe-119">Описание</span><span class="sxs-lookup"><span data-stu-id="835fe-119">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="835fe-120">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="835fe-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="835fe-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="835fe-121">Remarks</span></span>  

 <span data-ttu-id="835fe-122">Сопоставитель токенов службы можно использовать для разрешения маркера шифрования входящих токенов и сообщений.</span><span class="sxs-lookup"><span data-stu-id="835fe-122">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="835fe-123">Он используется для получения ключа, который должен использоваться для расшифровки входящих токенов.</span><span class="sxs-lookup"><span data-stu-id="835fe-123">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="835fe-124">Необходимо указать `type` атрибут.</span><span class="sxs-lookup"><span data-stu-id="835fe-124">You must specify the `type` attribute.</span></span> <span data-ttu-id="835fe-125">Указанный тип может быть либо либо <xref:System.IdentityModel.Selectors.SecurityTokenResolver> пользовательским типом, производным от <xref:System.IdentityModel.Selectors.SecurityTokenResolver> класса.</span><span class="sxs-lookup"><span data-stu-id="835fe-125">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="835fe-126">Некоторые обработчики маркеров позволяют задавать параметры сопоставителя токенов служб в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="835fe-126">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="835fe-127">Параметры отдельных обработчиков маркеров переопределяют те, которые указаны в коллекции обработчика маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="835fe-127">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="835fe-128">Указание `<serviceTokenResolver>` элемента в качестве дочернего элемента [\<identityConfiguration>](identityconfiguration.md) элемента является устаревшим, но по-прежнему поддерживается для обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="835fe-128">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="835fe-129">Параметры `<securityTokenHandlerConfiguration>` элемента переопределяют их для `<identityConfiguration>` элемента.</span><span class="sxs-lookup"><span data-stu-id="835fe-129">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="835fe-130">Пример</span><span class="sxs-lookup"><span data-stu-id="835fe-130">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
