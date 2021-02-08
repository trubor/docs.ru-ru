---
description: 'Дополнительные сведения: <issuerNameRegistry>'
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 73eb0d9d4d19f8e25f2db501e8cb3858d346ac2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803858"
---
# \<issuerNameRegistry>

<span data-ttu-id="067a0-102">Настраивает реестр имен издателя, используемый обработчиками в коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="067a0-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="067a0-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="067a0-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="067a0-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="067a0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="067a0-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="067a0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="067a0-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="067a0-106">Attributes</span></span>  
  
|<span data-ttu-id="067a0-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="067a0-107">Attribute</span></span>|<span data-ttu-id="067a0-108">Описание</span><span class="sxs-lookup"><span data-stu-id="067a0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="067a0-109">type</span><span class="sxs-lookup"><span data-stu-id="067a0-109">type</span></span>|<span data-ttu-id="067a0-110">Тип, производный от <xref:System.IdentityModel.Tokens.IssuerNameRegistry> класса.</span><span class="sxs-lookup"><span data-stu-id="067a0-110">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="067a0-111">Дополнительные сведения о том, как указать пользовательский параметр `type` , см. в разделе [ссылки на пользовательские типы].</span><span class="sxs-lookup"><span data-stu-id="067a0-111">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="067a0-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="067a0-112">Child Elements</span></span>  
  
|<span data-ttu-id="067a0-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="067a0-113">Element</span></span>|<span data-ttu-id="067a0-114">Описание</span><span class="sxs-lookup"><span data-stu-id="067a0-114">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="067a0-115">Если `type` атрибут указывает реестр имен издателя на основе конфигурации ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> класс), [\<trustedIssuers>](trustedissuers.md) необходимо указать элемент.</span><span class="sxs-lookup"><span data-stu-id="067a0-115">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="067a0-116">[\<trustedIssuers>](trustedissuers.md)Элемент может принимать `<add>` элементы, `<clear>` или `<remove>` как дочерние элементы.</span><span class="sxs-lookup"><span data-stu-id="067a0-116">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="067a0-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="067a0-117">Parent Elements</span></span>  
  
|<span data-ttu-id="067a0-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="067a0-118">Element</span></span>|<span data-ttu-id="067a0-119">Описание</span><span class="sxs-lookup"><span data-stu-id="067a0-119">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="067a0-120">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="067a0-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="067a0-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="067a0-121">Remarks</span></span>  

 <span data-ttu-id="067a0-122">Все маркеры издателя проверяются с помощью реестра имени издателя.</span><span class="sxs-lookup"><span data-stu-id="067a0-122">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="067a0-123">Это объект, производный от <xref:System.IdentityModel.Tokens.IssuerNameRegistry> класса.</span><span class="sxs-lookup"><span data-stu-id="067a0-123">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="067a0-124">Реестр имен издателей используется для связывания назначенного имени с криптографическим материалом, необходимым для проверки подписей маркеров, созданных соответствующим издателем.</span><span class="sxs-lookup"><span data-stu-id="067a0-124">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="067a0-125">В реестре имен издателей хранится список издателей, которым доверяет приложение проверяющей стороны (RP).</span><span class="sxs-lookup"><span data-stu-id="067a0-125">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="067a0-126">Тип реестра имени издателя указывается с помощью `type` атрибута.</span><span class="sxs-lookup"><span data-stu-id="067a0-126">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="067a0-127">`<issuerNameRegistry>`Элемент может иметь один или несколько дочерних элементов, которые предоставляют конфигурацию для указанного типа.</span><span class="sxs-lookup"><span data-stu-id="067a0-127">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="067a0-128">Вы предоставляете логику, которая обрабатывает эти дочерние элементы, переопределяя <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="067a0-128">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="067a0-129">WIF предоставляет один тип реестра имени поставщика из поля, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> класс.</span><span class="sxs-lookup"><span data-stu-id="067a0-129">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="067a0-130">Этот класс использует набор сертификатов доверенных издателей, указанных в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="067a0-130">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="067a0-131">Для этого требуется дочерний элемент конфигурации, `<trustedIssuers>` в котором настроена Коллекция сертификатов доверенных издателей.</span><span class="sxs-lookup"><span data-stu-id="067a0-131">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="067a0-132">Доверенные сертификаты указываются с помощью формы отпечатка сертификата в кодировке ASN. 1, которые добавляются или удаляются из коллекции с помощью `<add>` `<clear>` элементов, или `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="067a0-132">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="067a0-133">`<issuerNameRegistry>`Элемент представлен <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> классом.</span><span class="sxs-lookup"><span data-stu-id="067a0-133">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="067a0-134">Указание `<issuerNameRegistry>` элемента в качестве дочернего элемента [\<identityConfiguration>](identityconfiguration.md) элемента является устаревшим, но по-прежнему поддерживается для обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="067a0-134">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="067a0-135">Параметры `<securityTokenHandlerConfiguration>` элемента переопределяют их для `<identityConfiguration>` элемента.</span><span class="sxs-lookup"><span data-stu-id="067a0-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="067a0-136">Пример</span><span class="sxs-lookup"><span data-stu-id="067a0-136">Example</span></span>  

 <span data-ttu-id="067a0-137">В следующем коде XML показано, как указать реестр имен поставщиков на основе конфигурации.</span><span class="sxs-lookup"><span data-stu-id="067a0-137">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="067a0-138">См. также</span><span class="sxs-lookup"><span data-stu-id="067a0-138">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
