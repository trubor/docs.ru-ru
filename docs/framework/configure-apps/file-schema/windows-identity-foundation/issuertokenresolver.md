---
description: 'Дополнительные сведения: <issuerTokenResolver>'
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 535b6f098e168a198eb0949d6baba6659e5140db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664097"
---
# \<issuerTokenResolver>

<span data-ttu-id="8e04a-102">Регистрирует сопоставитель маркеров издателя, используемый обработчиками в коллекции обработчиков маркеров.</span><span class="sxs-lookup"><span data-stu-id="8e04a-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="8e04a-103">Сопоставитель токенов издателя используется для разрешения маркера подписывания входящих токенов и сообщений.</span><span class="sxs-lookup"><span data-stu-id="8e04a-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="8e04a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8e04a-104">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e04a-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8e04a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8e04a-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8e04a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e04a-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8e04a-107">Attributes</span></span>  
  
|<span data-ttu-id="8e04a-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8e04a-108">Attribute</span></span>|<span data-ttu-id="8e04a-109">Описание</span><span class="sxs-lookup"><span data-stu-id="8e04a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e04a-110">type</span><span class="sxs-lookup"><span data-stu-id="8e04a-110">type</span></span>|<span data-ttu-id="8e04a-111">Указывает тип сопоставителя маркеров издателя.</span><span class="sxs-lookup"><span data-stu-id="8e04a-111">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="8e04a-112">Должен быть либо <xref:System.IdentityModel.Tokens.IssuerTokenResolver> классом, либо типом, производным от <xref:System.IdentityModel.Tokens.IssuerTokenResolver> класса.</span><span class="sxs-lookup"><span data-stu-id="8e04a-112">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="8e04a-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8e04a-113">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e04a-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8e04a-114">Child Elements</span></span>  

 <span data-ttu-id="8e04a-115">None</span><span class="sxs-lookup"><span data-stu-id="8e04a-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e04a-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8e04a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8e04a-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="8e04a-117">Element</span></span>|<span data-ttu-id="8e04a-118">Описание</span><span class="sxs-lookup"><span data-stu-id="8e04a-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8e04a-119">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="8e04a-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e04a-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="8e04a-120">Remarks</span></span>  

 <span data-ttu-id="8e04a-121">Сопоставитель токенов издателя используется для разрешения маркера подписывания входящих токенов и сообщений.</span><span class="sxs-lookup"><span data-stu-id="8e04a-121">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="8e04a-122">Он используется для получения криптографического материала, используемого для проверки подписи.</span><span class="sxs-lookup"><span data-stu-id="8e04a-122">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="8e04a-123">Необходимо указать `type` атрибут.</span><span class="sxs-lookup"><span data-stu-id="8e04a-123">You must specify the `type` attribute.</span></span> <span data-ttu-id="8e04a-124">Указанный тип может быть либо либо <xref:System.IdentityModel.Tokens.IssuerTokenResolver> пользовательским типом, производным от <xref:System.IdentityModel.Tokens.IssuerTokenResolver> класса.</span><span class="sxs-lookup"><span data-stu-id="8e04a-124">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="8e04a-125">Некоторые обработчики маркеров позволяют задавать параметры сопоставителя маркеров издателя в конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8e04a-125">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="8e04a-126">Параметры отдельных обработчиков маркеров переопределяют те, которые указаны в коллекции обработчика маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="8e04a-126">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e04a-127">Указание `<issuerTokenResolver>` элемента в качестве дочернего элемента [\<identityConfiguration>](identityconfiguration.md) элемента является устаревшим, но по-прежнему поддерживается для обратной совместимости.</span><span class="sxs-lookup"><span data-stu-id="8e04a-127">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8e04a-128">Параметры `<securityTokenHandlerConfiguration>` элемента переопределяют их для `<identityConfiguration>` элемента.</span><span class="sxs-lookup"><span data-stu-id="8e04a-128">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e04a-129">Пример</span><span class="sxs-lookup"><span data-stu-id="8e04a-129">Example</span></span>  

 <span data-ttu-id="8e04a-130">В следующем коде XML показана конфигурация для сопоставителя маркеров издателя, основанного на пользовательском классе, производном от <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="8e04a-130">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="8e04a-131">Сопоставитель токенов поддерживает словарь пар ключей аудитории, которые инициализируются из настраиваемого элемента конфигурации ( `<AddAudienceKeyPair>` ), определенного для класса.</span><span class="sxs-lookup"><span data-stu-id="8e04a-131">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="8e04a-132">Класс переопределяет <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> метод для обработки этого элемента.</span><span class="sxs-lookup"><span data-stu-id="8e04a-132">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="8e04a-133">Переопределение показано в следующем примере. Однако методы, которые он вызывает, не отображаются для краткости.</span><span class="sxs-lookup"><span data-stu-id="8e04a-133">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="8e04a-134">Полный пример см `CustomToken` . в примере.</span><span class="sxs-lookup"><span data-stu-id="8e04a-134">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="8e04a-135">Пример</span><span class="sxs-lookup"><span data-stu-id="8e04a-135">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="8e04a-136">См. также</span><span class="sxs-lookup"><span data-stu-id="8e04a-136">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
