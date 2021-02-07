---
description: 'Дополнительные сведения: <chunkedCookieHandler>'
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b0090706d3d7a9f62e17ae63ec16e4b3a869a812
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664292"
---
# \<chunkedCookieHandler>

<span data-ttu-id="8882e-102">Настраивает <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="8882e-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="8882e-103">Этот элемент может присутствовать только в том случае, если `mode` атрибут `<cookieHandler>` элемента имеет значение "default" или "фрагментированный".</span><span class="sxs-lookup"><span data-stu-id="8882e-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="8882e-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8882e-104">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8882e-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="8882e-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8882e-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="8882e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8882e-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="8882e-107">Attributes</span></span>  
  
|<span data-ttu-id="8882e-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="8882e-108">Attribute</span></span>|<span data-ttu-id="8882e-109">Описание</span><span class="sxs-lookup"><span data-stu-id="8882e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8882e-110">chunkSize</span><span class="sxs-lookup"><span data-stu-id="8882e-110">chunkSize</span></span>|<span data-ttu-id="8882e-111">Максимальный размер (в символах) данных cookie HTTP для одного файла cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="8882e-111">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="8882e-112">При изменении размера фрагмента данных необходимо соблюдать осторожность.</span><span class="sxs-lookup"><span data-stu-id="8882e-112">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="8882e-113">Веб-браузеры имеют разные ограничения на размер файлов cookie и число допустимых для каждого домена.</span><span class="sxs-lookup"><span data-stu-id="8882e-113">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="8882e-114">Например, исходная спецификация Netscape поменяет такие ограничения: 300 cookies Total, 4096 байт на заголовок файла cookie (включая метаданные, а не только значение файла cookie) и 20 файлов cookie на домен.</span><span class="sxs-lookup"><span data-stu-id="8882e-114">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="8882e-115">Значение по умолчанию — 2000.</span><span class="sxs-lookup"><span data-stu-id="8882e-115">The default is 2000.</span></span> <span data-ttu-id="8882e-116">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8882e-116">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8882e-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="8882e-117">Child Elements</span></span>  

 <span data-ttu-id="8882e-118">None</span><span class="sxs-lookup"><span data-stu-id="8882e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8882e-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="8882e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8882e-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="8882e-120">Element</span></span>|<span data-ttu-id="8882e-121">Описание</span><span class="sxs-lookup"><span data-stu-id="8882e-121">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="8882e-122">Настраивает <xref:System.IdentityModel.Services.CookieHandler> , что <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) использует для чтения и записи файлов cookie.</span><span class="sxs-lookup"><span data-stu-id="8882e-122">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8882e-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="8882e-123">Remarks</span></span>  

 <span data-ttu-id="8882e-124">При указании, <xref:System.IdentityModel.Services.ChunkedCookieHandler> задав `mode` `<cookieHandler>` для атрибута элемента значение "по умолчанию" или "фрагментированный", можно указать размер фрагмента, который обработчик файлов cookie использует для чтения и записи файлов cookie, включая `<chunkedCookieHandler>` дочерний элемент и устанавливая его `chunkSize` атрибут.</span><span class="sxs-lookup"><span data-stu-id="8882e-124">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="8882e-125">Если `<chunkedCookieHandler>` элемент отсутствует, используется размер фрагмента по умолчанию (2000 байт).</span><span class="sxs-lookup"><span data-stu-id="8882e-125">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="8882e-126">Этот элемент не может быть указан, если `mode` для атрибута задано значение Custom.</span><span class="sxs-lookup"><span data-stu-id="8882e-126">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="8882e-127">`<chunkedCookieHandler>`Элемент представлен <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> классом.</span><span class="sxs-lookup"><span data-stu-id="8882e-127">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8882e-128">Пример</span><span class="sxs-lookup"><span data-stu-id="8882e-128">Example</span></span>  

 <span data-ttu-id="8882e-129">В следующем примере настраивается обработчик фрагментированных файлов cookie, который записывает файлы cookie в фрагменты 3000 байт.</span><span class="sxs-lookup"><span data-stu-id="8882e-129">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8882e-130">См. также</span><span class="sxs-lookup"><span data-stu-id="8882e-130">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
