---
description: 'Дополнительные сведения: <customCookieHandler>'
title: <customCookieHandler>
ms.date: 03/30/2017
ms.assetid: a03b153d-5ec6-4915-9031-6f0c3fd348be
author: BrucePerlerMS
ms.openlocfilehash: 6b433769c429ed4149efb324d7c4b216d6042705
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664084"
---
# \<customCookieHandler>

<span data-ttu-id="54160-102">Задает тип обработчика пользовательских файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="54160-102">Sets the custom cookie handler type.</span></span> <span data-ttu-id="54160-103">Этот элемент может присутствовать только в том случае, если `mode` атрибут `<cookieHandler>` элемента имеет значение Custom.</span><span class="sxs-lookup"><span data-stu-id="54160-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Custom".</span></span> <span data-ttu-id="54160-104">Пользовательский тип должен быть производным от <xref:System.IdentityModel.Services.CookieHandler> класса.</span><span class="sxs-lookup"><span data-stu-id="54160-104">The custom type must be derived from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="54160-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="54160-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Custom">  
      <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" >  
      </customCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54160-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="54160-106">Attributes and Elements</span></span>  

 <span data-ttu-id="54160-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="54160-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54160-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="54160-108">Attributes</span></span>  
  
|<span data-ttu-id="54160-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="54160-109">Attribute</span></span>|<span data-ttu-id="54160-110">Описание</span><span class="sxs-lookup"><span data-stu-id="54160-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54160-111">type</span><span class="sxs-lookup"><span data-stu-id="54160-111">type</span></span>|<span data-ttu-id="54160-112">Указывает пользовательский тип, производный от <xref:System.IdentityModel.Services.CookieHandler> класса.</span><span class="sxs-lookup"><span data-stu-id="54160-112">Specifies a custom type that derives from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span> <span data-ttu-id="54160-113">Дополнительные сведения об указании `type` атрибута см. в разделе [ссылки на пользовательские типы](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="54160-113">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54160-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="54160-114">Child Elements</span></span>  

 <span data-ttu-id="54160-115">None</span><span class="sxs-lookup"><span data-stu-id="54160-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54160-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="54160-116">Parent Elements</span></span>  
  
|<span data-ttu-id="54160-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="54160-117">Element</span></span>|<span data-ttu-id="54160-118">Описание</span><span class="sxs-lookup"><span data-stu-id="54160-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="54160-119">Настраивает <xref:System.IdentityModel.Services.CookieHandler> , что <xref:System.IdentityModel.Services.SessionAuthenticationModule> использует для чтения и записи файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="54160-119">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54160-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="54160-120">Remarks</span></span>  

 <span data-ttu-id="54160-121">При указании пользовательского обработчика файлов cookie путем присвоения `mode` атрибуту `<cookieHandler>` элемента значения "Custom" необходимо указать тип пользовательского обработчика файлов cookie, добавив `<customCookieHandler>` дочерний элемент, ссылающийся на тип обработчика файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="54160-121">When you specify a custom cookie handler by setting the `mode` attribute of the `<cookieHandler>` element to "Custom", you must specify the type of the custom cookie handler by including a `<customCookieHandler>` child element that references the cookie handler type.</span></span> <span data-ttu-id="54160-122">Этот элемент не может быть указан, если `mode` для атрибута задано значение "фрагментированный" или "по умолчанию".</span><span class="sxs-lookup"><span data-stu-id="54160-122">This element cannot be specified when the `mode` attribute is set to "Chunked" or "Default".</span></span> <span data-ttu-id="54160-123">Пользовательские обработчики файлов cookie должны быть производными от <xref:System.IdentityModel.Services.CookieHandler> класса.</span><span class="sxs-lookup"><span data-stu-id="54160-123">Custom cookie handlers must derive from the <xref:System.IdentityModel.Services.CookieHandler> class.</span></span>  
  
 <span data-ttu-id="54160-124">`<customCookieHandler>`Элемент представлен <xref:System.IdentityModel.Configuration.CustomTypeElement> классом.</span><span class="sxs-lookup"><span data-stu-id="54160-124">The `<customCookieHandler>` element is represented by the <xref:System.IdentityModel.Configuration.CustomTypeElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54160-125">Пример</span><span class="sxs-lookup"><span data-stu-id="54160-125">Example</span></span>  

 <span data-ttu-id="54160-126">В следующем примере SAM настраивается для использования пользовательского обработчика файлов cookie типа `MyNamespace.MyCustomCookieHandler` .</span><span class="sxs-lookup"><span data-stu-id="54160-126">The following example configures the SAM to use a custom cookie handler of type `MyNamespace.MyCustomCookieHandler`.</span></span>  
  
```xml  
<cookieHandler mode="Custom">  
    <customCookieHandler type="MyNamespace.MyCustomCookieHandler, MyAssembly" />  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54160-127">См. также</span><span class="sxs-lookup"><span data-stu-id="54160-127">See also</span></span>

- <xref:System.IdentityModel.Services.CookieHandler>
